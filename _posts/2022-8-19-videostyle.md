---
layout: post
title: Video Embedding and Styling on Webpages
date: 2022-8-19
tags:
  - HTML
  - CSS
  - JavaScript
---

Table of Contents:

- [Introduction](#introduction)
- [Video From Cloud](#video-from-cloud)
  - [How to find source link](#how-to-find-source-link)
  - [How to style the video](#how-to-style-the-video)

## Introduction

This post is based on content in the posts by [Chris Coyier](https://css-tricks.com/fluid-width-video/) and [Nikhil Azza](https://bytesbin.com/embed-video-from-google-photos/).

By reference to the sources, we can roughly divide the video embedding technique into two categories:

- video sourcing from cloud storage, like google photo
- video sourcing from Youtube

## Video From Cloud

### How to find source link

It's not a question if you store and source your video file from a downloadable link. However, many people choose to store it on google photo, and if you use google photo share link, you cannot embed the video into your webpage correctly!

Nikhil introduced three ways to get the correct downloadlable link to a video file stored on google photo. I found the first one is simplest and tried it bymyself:

1. go to google photo and find the video file you want to embed
2. click on download button (caution: not the share button!)
3. you can wait until it's downloaed, or cancel downloading immediately, it doesn't matter, because what we need is the downloading link. Now, on google chrome, open the download page, the first item on top of the list is the video you want.
4. copy the video's download address, this is the link we can use to embed into our webpage.

### How to style the video

It is straight-forward to embed video into a webpage, the syntax we're using is `video`:

```html
<video width="800" height="600" controls>
  <source src="downloadlink.com" type="video/mp4" />
</video>
```

The above code comes with a problem: it's not fluid. In another word, it's not responsive to the viewport a useer may use to watch the video. For example, if the user is watching the video on a smart phone, the 800px width setting would make the vidwo overflow the screeen.

In a modern web brower that supports HTML5, the solution is astoudingly simple:

```css
video {
  width: 100%;
  height: auto;
}
```
