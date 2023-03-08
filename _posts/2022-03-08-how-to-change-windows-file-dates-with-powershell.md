---
title: How-to change windows files modified, access and creation dates with Powershell
author: Squintz
categories: [How-To]
tags: [Windows]
math: true
mermaid: true
---

Using PowerShell and the following commands it's possible to change the "Date Modified", "Date Accessed", and "Date Created" show in the file explorer.

## Date Modified
```
 $(Get-Item example_filed_name.txt).lastwritetime=$(Get-Date "03/08/23 12:00")
```

## Date Accessed
```
 $(Get-Item example_filed_name.txt).lastaccesstime=$(Get-Date "03/08/23 12:00")
```

## Date Created
```
$(Get-ChildItem example_filed_name.txt).CreationTime=$(Get-Date "03/08/23 12:00")
```

## Date Created
```
$(Get-ChildItem example_filed_name.txt).CreationTime=$(Get-Date "03/08/23 12:00")
```