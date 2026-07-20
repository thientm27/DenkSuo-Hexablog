---
title: {{ title }} # [Required] Page title
date: {{ date }} # [Required] Page creation date
updated: # [Optional] Page update date
tags: # [Optional] Article tags
categories: # [Optional] Article categories
keywords: # [Optional] SEO keywords
description: # [Optional] Article description
top: # 1 = Pinned to top
top_img: # [Optional] Top image of the article
comments: # [Optional] Enable comments (default: true)
cover: https://img.090227.xyz/file/ae62475a131f3734a201c.png # [Optional] Thumbnail (used if top_img not set)
toc: # [Optional] Show Table of Contents (default: theme config)
toc_number: # [Optional] Show TOC numbers
toc_style_simple: # [Optional] Use simplified TOC style
copyright: # [Optional] Show copyright block (default: theme config)
copyright_author: # [Optional] Author name for copyright block
copyright_author_href: # [Optional] Author URL
copyright_url: # [Optional] URL of the original article
copyright_info: # [Optional] Custom copyright text
mathjax: # [Optional] Enable MathJax rendering
katex: # [Optional] Enable KaTeX rendering
aplayer: # [Optional] Load APlayer (for music embedding)
highlight_shrink: # [Optional] Collapse code blocks (true/false)
aside: # [Optional] Show sidebar (default: true)
swiper_index: 10 # [Optional] Homepage carousel index (lower = earlier)
top_group_index: 10 # [Optional] Right-side homepage card group index
ai: # [Optional] AI-generated article summary
background: "#fff" # [Optional] Article background color (6-digit hex only)
---

<div class="video-container">
  [Embed code here, e.g. <iframe ...></iframe>]
</div>

<style>
.video-container {
    position: relative;
    width: 100%;
    padding-top: 56.25%; /* 16:9 aspect ratio (height/width = 9/16 * 100%) */
}

.video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>
