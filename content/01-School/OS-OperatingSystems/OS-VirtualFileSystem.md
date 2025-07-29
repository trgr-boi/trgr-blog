---
title: OS-VirtualFileSystem
aliases:
  - Virtual File System
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
  - "[[MOC-Linux]]"
---

## Overview

- **Windows:** elk bestandssysteem krijgt drive letter (C, D, ...)
- **Linux/macOS:** "virtual file system"
	- één hiërarchische structuur
	- Lijkt één bestandssysteem

- Werking

## Werking

- Processen: algemene OS-functies (POSIX) spreken VFS aan
- VFS: vertaalt naar drivers van elk bestandssysteem
- Verbergt verschillen tussen file systems
- Processen: uniforme bewerking

- **Mount:** inladen root directory bestandssysteem in VFS-map
- **Unmount:** loskoppelen ingeladen bestandssysteem