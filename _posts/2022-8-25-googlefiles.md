---
layout: post
title: How to Create Google File links Without Editting Function?
date: 2022-08-25
tags:
  - HTML+CSS
---

Google Drive is a powerful app to store files of pdf, word, excel and other formats. If you create a copy link from google drive and embed the link into your webpage directly, the default setting is that when user click on the download link, browser will open a new tab in google doc viewer.

It's a handy soluction when it comes to pdf files, but for Word, Excel and other formats when you need to use other software to open and edit, it's sometimes annoying because you have to download the files on google doc viewer window again and then use an outside software to open them.

The default download link is like this:

`https://docs.google.com/document/d/DOC_FILE_ID/edit...`

Replace `/edit` with `/export?format=...`, add the file format that the file should be saved as your new download link is ready:

```html
https://docs.google.com/document/d/DOC_FILE_ID/export?format=pdf
https://docs.google.com/document/d/DOC_FILE_ID/export?format=doc
```

When users click on the link, the file will be downloaded instead of opened in the viewer. Bravo!

<br>
