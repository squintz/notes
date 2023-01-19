---
title: How-To Find the Process ID Holding Open Ports
author: Squintz
categories: [How-To]
tags: [Networking]
math: true
mermaid: true
---

When trying to launch the jekyll serve I got an error saying "Permission denied - bind(2) for 127.0.0.1:4000 (Errno::EACCES)"  Turns out this was caused because the ports we're already open by chrome and some mystery app called "tunxtensvc.exe". The following is how I discovered that.

```
netstat -aon | findstr "4000"

```


Returns the Following process IDs in the right column

```
C:\Users\davep>netstat -aon | findstr "4000"
  TCP    127.0.0.1:4000         0.0.0.0:0              LISTENING       5584
  TCP    127.0.0.1:4000         127.0.0.1:10366        ESTABLISHED     5584
  TCP    127.0.0.1:4000         127.0.0.1:10367        ESTABLISHED     5584
  TCP    127.0.0.1:10366        127.0.0.1:4000         ESTABLISHED     49088
  TCP    127.0.0.1:10367        127.0.0.1:4000         ESTABLISHED     49088
```

Now open task manager and find the process IDs and kill them if you don't want those ports open.

