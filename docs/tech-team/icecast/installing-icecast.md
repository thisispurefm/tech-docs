---
layout: default
title: Installing Icecast
parent: Icecast
grand_parent: Tech Team
nav_order: 2
---

# Installing Icecast

We are planning to use Icecast (specifically version 2) as our distribution server. This move is planned as the current distribution server (a VPS hosted and managed by `streamuphosting.co.uk`) is very limited and not cost-effective (400 max listeners, 128kbps max bitrate). There is official documentation available for Icecast2 at [`icecast.org/docs/`](https://icecast.org/docs/) but they are very obtuse and hard to use.

## Requirements

The hardware requirements of an Icecast2 server are very low, the most important factor is the *upload speed* available to your server, as you need enough bandwidth for planned listeners * stream bitrate. (e.g. 1000 listeners * 320kbps = 320000kbps or 320mbps). Most cloud VPSes will have enough bandwidth for several thousand users, but it is still worth checking. You will also need a domain name, and access to change it's DNS records to point at the VPS

{: .information}
This guide has been written working on a Windows machine, and using a Debian 10 VPS hosted by Akamai (Linode). It is also assuming a basic knowledge of the Linux commandline, and a remote server with SSH already set up.

## Part 1: Installing Icecast2

1. Make sure your server is up-to-date using `sudo apt-get update && sudo apt-get upgrade -y`
2. The version of Icecast2 included in the Debian repositories is built without SSL support (blah blah licensing blah blah) so we need to add the repository from Xiph (the foundation which develops Icecast) using the command `sudo sh -c "echo deb http://download.opensuse.org/repositories/multimedia:/xiph/Debian_10/ ./ >> /etc/apt/sources.list.d/icecast.list"`
3. Before this repository can be used, the signing key must be added to apt. Before we can do this, make sure that `wget` is installed using the command `sudo apt-get install wget -y`
4. Now we can download and add the signing key with `wget -qO - https://build.opensuse.org/projects/multimedia:xiph/signing_keys/download?kind=gpg | sudo apt-key add -`
5. We need to update the package cache again, so run `sudo apt-get update`
6. We can finally install Icecast2, but since we need to use a non-standard version, we have to use the command `sudo apt-get install -t Debian_10 icecast2`. This will install the version of Icecast from the repository we just added, rather than the stock Debian version
7. If you want to setup your Icecast server with SSL (you want to), you will need Certbot from the Electronic Frontier Foundation, so install it using `sudo apt-get install certbot`

## Part 2: Configuring Icecast2

- This section depends heavily upon the specific configuration you want for Icecast, so is written with the needs of PureFM in mind.
1. If you wish to use Icecast2 with SSL on port 80 & 443, it must have sufficient permissions to access said ports. In the file `/etc/default/icecast2`, change the lines

```
USERID=icecast2
GROUPID=icecast
```

to

```
USERID=root
GROUPID=root
```

2. Then within the main configuration file (`/etc/icecast2/icecast.xml`) uncomment the `changeowner` block within the *Security* section (usually at the bottom of the file) and set it as following

```xml
<changeowner>
  <user>icecast2</user>
  <group>icecast</user>
</changeowner>
```

3. Set the location of your server, usually to the country the radio station is based in
4. Change the email address of the admin user from `icecast@localhost` to the email you would like people (such as Ofcom) to contact
5. In the *Limits* section, change the maximum number of clients (usually 2 * max listeners) and sources (typically 2 for a main and backup source)
6. In the *Authentication* section, change all of the passwords, but leave the admin username as `admin`.

{: .warning}
Passwords are stored as plaintext! Make sure only authorised users have access to the server over SSH!

7. Change the hostname to be the domain name you will point to the server (This is a great time to setup DNS records as well!)
8. Add a `listen-socket` block as below. The port can be anything you would like, but if you are going to use SSL with port 80 and 443, the HTTP port must be first. If using SSL, also add the second `listen-socket` block.

```xml
<listen-socket>
  <port>80</port>
</listen-socket>

<listen-socket>
  <port>443</port>
  <ssl>1</ssl>
</listen-socket>
```

9. Now setup the mount points you would like to host on your server. You can have as many as you like, as long as it's <= the sources limit set earlier. It is recommended to have 2 mount points, one each for the main and backup stream. There are more settings available in the [Official Documentation](https://icecast.org/docs/icecast-2.4.1/config-file.html#mountsettings)

```xml
<mount type="normal">
  <mount-name>/stream.mp3</mount-name> <!-- The path of the stream, this would result in [domain]/stream.mp3 -->
  <username>source</username> <!-- Can be anything you like, but some older source clients may not support chaning username from the default (cough cough pos-send) -->
  <password>thisisn0tarealp@ssword!</password> <!-- The password needed to stream to this mount point. Once again, plaintext! -->
  <max-listeners>100</max-listeners> <!-- Self explanitory -->
  <fallback-mount>/backup.mp3</fallback-mount> <!-- The mount-name of a secondary mount to be used if the primary is full or offline -->
  <fallback-override>1</fallback-override> <!-- Set to 1 to pull clients back if primary has space available or comes back online -->
  <fallback-when-full>1</fallback-when-full> <!-- Set to 1 to push clients to fallback mount if the primary is full -->
  <public>1</public> <!-- Set to 1 to advertise on Yellowpages-style websites. All related settings are optional if public is set to 0 -->
  <stream-name>PureFM</stream-name> <!-- The name which will display in Yellowpages-style websites -->
  <stream-description>The Portsmouth University Radio Experience, PureFM. Find us online at thisispurefm.com or on Instagram at purefm_</stream-description> <!-- Flavour text which will display on Yellowpages-style websites -->
  <stream-url>https://thisispurefm.com</stream-url> <!-- Website which will display on Yellowpages-style websites -->
  <genre>Pop</genre> <!-- Genre which will display on Yellowpages-style websites -->
</mount>
```

10. In the *Paths* section, make a note of the webroot path, as this is needed when obtaining an SSL certificate
11. If installing an SSL certificate, uncomment and change the `ssl-certificate` line as follows

```xml
<ssl-certificate>/etc/icecast2/bundle.pem</ssl-certificate>
```

12. Restart the Icecast2 server to apply the configuration with `sudo systemctl restart icecast2` and check the status using `sudo systemctl status icecast2` to check for errors. If you get an error about SSL certificates, and are configuring for SSL, you can safely ignore it until the third part is complete

If you're not configuring for SSL, congrats! You're finished!

## Part 3: Configuring Certbot and Installing an SSL Certificate

For this section, you will need certbot installed, and know both the path to the webroot of Icecast and the domain name configured earlier

1. Use certbot to request a new SSL certificate as follows `sudo certbot certonly --webroot-path="[your webroot]" -d "[your domain name]"`. For example, `sudo certbot certonly --webroot-path="/usr/share/icecast2/web" -d "icecast.thisispurefm.com"`. When prompted, select option 2 (webroot)
2. Certbot will then ask you for an email address to which it will send reminders and warnings about certificate renewals
3. If certbot failed, go back and check that port 80 is accessable to the internet (not blocked by a firewall) and that the DNS records for your domain are set correctly
4. Use the `touch` command to create the certificate file, `sudo touch /etc/icecast2/bundle.pem`
5. Change the owner of the certificate file to the icecast user, using `sudo chown icecast2 /etc/icecast2/bundle.pem`
6. Configure certbot so that it automatically writes the certificate to the correct location when automatically renewing. In the `/etc/letsencrypt/renewal/[domain].conf` file (e.g. `/etc/letsencrypt/renewal/icecast.thisispurefm.com.conf`), add the following line in the *\[renewalparams\]* section

```
post_hook = cat /etc/letsencrypt/live/[domain]/fullchain.pem /etc/letsencrypt/live/[domain]/privkey.pem > /etc/icecast2/bundle.pem && systemctl restart icecast2
```

7. Dry-run the certbot renewal process using `sudo certbot renew --dry-run`. This will test the renewal process, and write the new certificate into the correct file for icecast to read.

If everything went well, congrats! You've now setup an Icecast2 server and installed an SSL certificate

## Part 4: Firewall

- This is not a necessary step, but it is recommended to install a firewall to improve the security of your Icecast server.
- The actual details of seting up a firewall are left as an exercise to the reader, as it depends upon distribution and VPS provider, but the following are the rules which are needed for Icecast to work
- SSH (Port 22) - TCP Bidirectional
- HTTP (Port 80 or configured port) - TCP Bidirectional
- HTTPS (Port 443 or configured port) - TCP Bidirectional