---
title: "Better Fonts on Manjaro/Arch Linux"
date: 2020-09-11T22:15:59+05:30
tags: [typography, macOS]
draft: true
---

Fonts and Typography were never the strong suit of Linux. After some fiddiling around I came across a not so ugly setup that works for me. So if you want to make your Linux Distro a tad bit better to look at follow along.

### Installation
All the fonts that are used here can be found on the Arch Repositories, and on Google Fonts. You are free to replace everything with the ones you find great.

- tex-gyre-fonts, free alternative to Helvetica and Arial and looks really really similar
- DM Mono from Google Fonts, for monospace fonts that look great
- noto-fonts-emoji, get some colorful emojis

### Font Setup
Everything about fonts can be configured from a single file located at `/etc/fonts/local.conf` if the file doesn't exist create it. You do require `sudo` for it. After creating that file just paste all this.

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>

<match target="font">
  <edit name="autohint" mode="assign">
    <bool>true</bool>
  </edit>
  <edit name="hinting" mode="assign">
    <bool>true</bool>
  </edit>
  <edit mode="assign" name="hintstyle">
    <const>hintslight</const>
  </edit>
  <edit mode="assign" name="lcdfilter">
   <const>lcddefault</const>
 </edit>
</match>


<!-- Default sans-serif font -->
 <match target="pattern">
   <test qual="any" name="family"><string>-apple-system</string></test>
   <!--<test qual="any" name="lang"><string>ja</string></test>-->
   <edit name="family" mode="prepend" binding="same"><string>Tex Gyre Heros</string>  </edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>Helvetica Neue</string></test>
   <!--<test qual="any" name="lang"><string>ja</string></test>-->
   <edit name="family" mode="prepend" binding="same"><string>Tex Gyre Heros</string>  </edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>Helvetica</string></test>
   <!--<test qual="any" name="lang"><string>ja</string></test>-->
   <edit name="family" mode="prepend" binding="same"><string>Tex Gyre Heros</string>  </edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>arial</string></test>
   <!--<test qual="any" name="lang"><string>ja</string></test>-->
   <edit name="family" mode="prepend" binding="same"><string>Tex Gyre Heros</string>  </edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>sans-serif</string></test>
   <!--<test qual="any" name="lang"><string>ja</string></test>-->
   <edit name="family" mode="prepend" binding="same"><string>Tex Gyre Heros</string>  </edit>
 </match>
 
<!-- Default serif fonts -->
 <match target="pattern">
   <test qual="any" name="family"><string>serif</string></test>
   <edit name="family" mode="prepend" binding="same"><string>Noto Serif</string>  </edit>
   <edit name="family" mode="prepend" binding="same"><string>Noto Color Emoji</string>  </edit>
   <edit name="family" mode="append" binding="same"><string>IPAPMincho</string>  </edit>
   <edit name="family" mode="append" binding="same"><string>HanaMinA</string>  </edit>
 </match>

<!-- Default monospace fonts -->
 <match target="pattern">
   <test qual="any" name="family"><string>SFMono-Regular</string></test>
   <edit name="family" mode="prepend" binding="same"><string>DM Mono</string></edit>
   <edit name="family" mode="prepend" binding="same"><string>Space Mono</string></edit>
   <edit name="family" mode="append" binding="same"><string>Inconsolatazi4</string></edit>
   <edit name="family" mode="append" binding="same"><string>IPAGothic</string></edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>Menlo</string></test>
   <edit name="family" mode="prepend" binding="same"><string>DM Mono</string></edit>
   <edit name="family" mode="prepend" binding="same"><string>Space Mono</string></edit>
   <edit name="family" mode="append" binding="same"><string>Inconsolatazi4</string></edit>
   <edit name="family" mode="append" binding="same"><string>IPAGothic</string></edit>
 </match>

 <match target="pattern">
   <test qual="any" name="family"><string>monospace</string></test>
   <edit name="family" mode="prepend" binding="same"><string>DM Mono</string></edit>
   <edit name="family" mode="prepend" binding="same"><string>Space Mono</string></edit>
   <edit name="family" mode="append" binding="same"><string>Inconsolatazi4</string></edit>
   <edit name="family" mode="append" binding="same"><string>IPAGothic</string></edit>
 </match>

<!-- Fallback fonts preference order -->
 <alias>
  <family>sans-serif</family>
  <prefer>
   <family>Noto Sans</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
   <family>Open Sans</family>
   <family>Droid Sans</family>
   <family>Ubuntu</family>
   <family>Roboto</family>
   <family>NotoSansCJK</family>
   <family>Source Han Sans JP</family>
   <family>IPAPGothic</family>
   <family>VL PGothic</family>
   <family>Koruri</family>
  </prefer>
 </alias>
 <alias>
  <family>serif</family>
  <prefer>
   <family>Noto Serif</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
   <family>Droid Serif</family>
   <family>Roboto Slab</family>
   <family>IPAPMincho</family>
  </prefer>
 </alias>
 <alias>
  <family>monospace</family>
  <prefer>
   <family>Noto Sans Mono</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
   <family>Inconsolatazi4</family>
   <family>Ubuntu Mono</family>
   <family>Droid Sans Mono</family>
   <family>Roboto Mono</family>
   <family>IPAGothic</family>
  </prefer>
 </alias>

</fontconfig>
```