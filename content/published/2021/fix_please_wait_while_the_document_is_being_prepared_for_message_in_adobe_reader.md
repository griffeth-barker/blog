---
title: "Fix 'Please wait while the document is being preared for' message in Adobe Reader"
tags:
- fix
- software
- adobe
---

Any business user is familiar with the odd-ball errors that Adobe Reader can throw you while working. In this quick knowledgebase article, I'll outline a quick fix I've found that works for me. As always, YMMV (your mileage may vary).

# Problem
When PDFs are opened in Adobe Acrobat, a popup window with the message “Please wait while the document is being prepared for” appears, and takes quite a while to process before the document will display. Sometimes, the document will never actually load.

![](https://audiomgtmoregame.files.wordpress.com/2020/12/image-30.png?w=613)

# Environment
Microsoft Windows 7 or 10 devices (OS architecture agnostic) where Adobe Acrobat Reader DC MUI version 20.012.20043 or newer installed.

# Cause

This message occurs when Adobe Acrobat is preparing an opened document to be interacted with via accessibility features. At the time of writing this article, it is believed that a recent update to the software has provided this feature/function as enabled by default.

# Solution
![](https://audiomgtmoregame.files.wordpress.com/2020/12/image-31.png?w=1024)
*Screenshot of Adobe Reader DC Preferences Window > Accessibility*

Launch Adobe Acrobat and in the menu bar, open the **Edit** menu, then select **Preferences**.

In the navigation pane at the left of the resulting Preferences window, select the **Accessibility** option.

In the Other Accessibility Options section, uncheck the selection box for the feature entitled “**Enable assistive technology support**,” then click **OK**.

The issue should now be resolved for the next time a document is opened in Adobe Acrobat.

---

# Additional resources
- [Adobe Support Community thread](https://www.blogger.com/blog/post/edit/8562458718891840214/1869982778674319275#)
- [BruceB Consulting on other Adobe accessibility issues](https://www.blogger.com/blog/post/edit/8562458718891840214/1869982778674319275#)