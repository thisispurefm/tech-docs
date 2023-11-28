---
layout: default
title: NAS
parent: Tech Team
has_children: true
has_toc: false
nav_order: 1
---

# NAS

A critical part of PureFM's networked infrastructure is our NAS - this Network Attached Storage Device provides us access our files from any device connected to the network. We use TrueNAS Core to power the NAS.

The NAS is comprised of a number of *Datasets*, each of which comprise of a *share*. We can apply an Access Control List (ACL) to a Dataset (and therefore shares within) which allows us to restrict who can access what data. 