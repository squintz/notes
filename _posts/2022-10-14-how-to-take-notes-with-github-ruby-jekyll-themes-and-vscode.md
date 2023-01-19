---
title: How-to take Notes with GitHub, Jekyll Themes, Ruby, and VSCode
author: Squintz
categories: [How-To]
tags: [Jekyll, Ruby, Gem, GitHub, VSCode]
math: true
mermaid: true
---

Enjoying the Squintz's Notes? Want to make your own? Here are some of the things I'm using to keep this website updated.

Q: Why VSCode?
A: Becuase I already work in it daily.

Q: What other note taking tools have you tried?
A: Until now I have been taking all my notes in google docs because they are easy to access from anywhere. However, I find that once I write stuff down I never look at it again. I have also tried other task manager type tools and project management tools not worth mentioning. 

## Dev Environment Setup

There are better ways of setting up a dev environment for jekyll themes so if your looking at this page you should probably follow someone elses instructions.

1. Download ruby from https://rubyinstaller.org/downloads/
2. Install ruby by selecting MSYS2 and MINGW development tool chain from the menu
3. If not automatically added (it should have been) the ruby bin directory (C:\Ruby31-x64\bin) to path in the Windows Environment Variables.
4. From newly opened Powershell install bundler. Closing VSCodes Power Shell terminal and re-opening it didn't work for me. Restarting VSCode worked as well as opening a new Power Shell form the start bar also worked. This is because the terminal didn't know about the PATH yet.

```
gem install jekyll bundler
```

5. CD to root directory of Jekyll Theme and run the following to install all the dependensies

```
cd [to local path of cloned github repo]
bundle
```

## Previewing

From Powershell:

```
cd [to local path of cloned github repo]
bundle exec jekyll s
```

This will start a local webserver so you can preview your changes without uploading to GitHub every 5 seconds (like I was doing at first).

## Visual Studio Code (VSCode)

* Install Extension: Mardown Editor by zaaack
  This is a WYSIWYG editor. Restart VSCode after installing. Right click on the tab of an open markdown file and open the editor. Change to split view to see a simple preview of the markdown rendering.
* The VSCode built in git works well for staging, committing, and pushing changes.
* Install GitHub Actions by Christopher Schleiden
  The Jekyll theme I'm using uses workflows to automate the testing when a change is pushed. This extension lets you view the results and status of those actions.
* Install Code Spell Checker by Street Side Software.

