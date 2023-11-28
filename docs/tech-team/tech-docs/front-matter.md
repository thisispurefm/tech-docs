---
layout: default
title: Front Matter
parent: Tech Docs Docs
grand_parent: Tech Team
nav_order: 1
---

# Front Matter

Front Matter is the bit which comes at the start of the Markdown files which get converted to webpages. These few lines help JTD to know what to do with the page (where to put it in the navigation, if it has children page, etc). Its vitally important that the front matter is always set correctly on all pages.

## Example Front Matters

Shown below are example front matters for different page types. These should be copied and pasted then the relevant fields edited to ensure all pages are consistently configured.

### Top-Level Nav Item
A top-level nav item will be an item which is at the root of the navigation tree. For example: `/` or `/tech-team`.
```
---
layout: default
title: [TITLE OF PAGE]
has_children: [true / false]
nav_order: [NAVIGATION ORDER]
has_toc: false
---
```

### Second-Level Nav Item
A second-level nav item will be a child page of the top level nav item. For example `/home/getting-started`.
```
---
layout: default
title: [TITLE OF PAGE]
parent: [TITLE OF TOP LEVEL NAV ITEM]
has_children: [true / false]
has_toc: false
nav_order: [NAVIGATION ORDER]
---
```

### Third-Level Nav Item
A third-level nav item will be a grand-child page of the top level nav item and a child page of the second level nav item. For example `/tech-team/tech-docs/front-matter`
```
---
layout: default
title: [TITLE OF PAGE]
parent: [TITLE OF TOP LEVEL NAV ITEM]
grand_parent: [TITLE OF SECOND LEVEL NAV ITEM]
nav_order: [NAV ORDER]
---
```

## Front Matter General Principles

{: .important}
These principles somewhat form a style guide for PureFM's tech docs, so please try to stick to them where possible.

* Pages with children should not have an automatic table of contents (they get appended to the end of the page and look really hideous). Manually inserted TOCs are fine
* `nav_order` should be set if possible. This will keep things in the same places, making it easier for users to find what they want to find