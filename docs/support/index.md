---
layout: main
title: Common questions and answers - Arrigo Local
description: QnA
---

# Common questions and answers

## Broken image links

### Question

I'm getting broken image links in my views with the error `400 Bad Request`.

Why, and how do I fix it?

![Broken image links](./images/broken_image_links_1.png)

![Browser errors](./images/broken_image_links_2.png)

### Answer

This is an error in the IIS web server. The default limitation of "url parts" (segments) to 260 characters, so if you have long(er) nested area names this error can occur. This setting can be modified in the Windows Registry using the Registry Editor.

> This solution contains steps that tell you how to modify the registry. However, serious problems might occur if you modify the registry incorrectly. Therefore, make sure that you follow these steps carefully. For added protection, back up the registry before you modify it. Then, you can restore the registry if a problem occurs. For more information about how to back up and restore the registry, see [How to back up and restore the registry in Windows](https://support.microsoft.com/help/322756)

Start the Registry Editor with administrative privileges.

Navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`.

Create a new `REG_DWORD` in called `UrlSegmentMaxLength`.

Set its value to 400 hex or 1024 decimal.

![Registry Editor](./images/broken_image_links_3.png)

Restart the computer for the changes to take effect.