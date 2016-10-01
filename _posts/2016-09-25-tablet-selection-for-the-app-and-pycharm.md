---
layout: post
title:  Tablet selection for the application and PyCharm
tags:
- Blog
- Post
---

During our Skype meeting Maksim and I discussed possible tablet solutions for the application. The laboratory would like to buy a Tablet
and I need to decide between Android and Windows OS.

The application needs to be able to read a barcode or QR code. Options are:
* USB barcode reader - PRO - easy to retrieve input CON - Tablet has only mini USB connector, cannot read QR Code-review
* Camera on the tablet - PRO - does not require additional hardware CON - more difficult to parse input to a form

If I use the camera on the tablet Maksim suggested to look into the Android barcode scanner application by  <a href="https://play.google.com/store/apps/details?id=com.google.zxing.client.android&hl=hr">ZXing</a>.

On Android, you can invoke Barcode Scanner from a web page and have the result returned to your site via a callback URL. This is described <a href="https://github.com/zxing/zxing/wiki/Scanning-From-Web-Pages">here</a>.

Here is the github page for <a href="https://github.com/zxing/zxing">ZXing</a> and <a href="http://stackoverflow.com/questions/tagged/zxing">Stackoverflow questions on ZXing to help me along the way</a>.

As regards to PyCharm I had a question on the debugging mode. I could not find the way to step through the code and observe variables and the stack. It turned out I need to setup breakpoints (red dot near the number of the line) and ran the debugger. Then I can step over or into the lines of code with the little arrows.
