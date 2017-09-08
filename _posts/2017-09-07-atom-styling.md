---
layout: post
title:  "Color styling in Atom"
date:   2017-09-07 12:40:40 -0400
categories: atom
---

When I project C++ code in `atom` in class, the default commenting color of dark grey
is hard to see. I found [this post](https://stackoverflow.com/questions/37028403/changing-comment-colour-in-atom-editor) on changing the colors in atom.

 I appended

 ```
 // This styles comment text
atom-text-editor .syntax--comment {
    color: #AAAA00;
}

// This styles comment punctuation (i.e. //, and /*...*/)
.syntax--punctuation.syntax--definition.syntax--comment {
    color: #AAAA00;
}
 ```

 to the end of my `~/.atom/styles.less` file for a higher contrast color.
