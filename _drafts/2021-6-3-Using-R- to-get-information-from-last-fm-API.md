---
layout: post
title: Using R to get music information from Last FM API
category: EN
tags: [Coding, R, Raspberry]
---

![Notepad++ Screenshot](/images/Posts/2020/2020-09-22_Image1.png){: .center-image }

I have been having a raspberry PI project in mind for way too long time that required to have my music library collection organised. Pretty well organised. I mean at the moment it was fairly good organised, by folders with letters and by the name of the artist after. Title and artist tag where on spot but there was one tag that was a nightmare... The genre tag.

Just so you know the rasperry PI project I have in mind is to have an old radio reconverted into a jukebox, but done in such a way that moving the dial would change to <<other radio stations>> with different genre. This implies I need to classify my music into 20 or 30 genres at much. The whole task has consumed most of my free time since November last year. In this post I will tell you why is complicated, what alternatives are to do so, and how did I do it (The title of the post will give you a clue).

## Why clasifying by Genre is complicated.

Music genre is like asses. Every single person has one and they are all different. Music bands, artist try to have their own style. Mixing, or combining different styles into their own style. If a band decides to combine punk with metal. Is it punk? Is it metal? Is it a bird? Is it a plane? Is it a birdplane?

<div class="x-frame video" data-video="https://www.youtube.com/watch?v=Vx6hmUv06tg"> </div>

<!-- more -->


I must warn anyone wanting to see the code, that the games are "as they were coded three years ago" and I have not bothered to rewrite or organise the code since 2017. Obviously, you will require to trust me, and allow macros in order to be able to use them.

## 2048

<!--
The game is pretty straight forward and follows the same rules that the android game with the same name. Select a cell, and then press one of the arrows to push the cell in that direction. Cells need to be pushed against one of the same value until you will manage to reach 2048. The game won't tell you when there are no more available moves. The game has been tested and works on LibreOffice 7.

[Download](https://github.com/RMRubert/ExcelsUtils/blob/master/Games/2048.xlsm){:target="_blank" class="r-save-link"}.

![Notepad++ Screenshot](/images/Posts/2020/2020-09-22_Image2.png){: .center-image }
## Minesweeper (v2)

Apparently, there was a version 1 of this game that I must have lost at some point. You will require to tag all the mines until there all of them are tagged. To tag or dig, select a cell and click on the tag or dig button. Mind that the routine that checks all mine-empty terrain has not been optimised so it might take a few seconds to get all revealed. You could technically go to the second page to see the results, but please don't (or do it, but it won't be a fair play!). The game is unable to work on LibreOffice 7, which is not surprising as it was designed for Excel 2013.

[Download](https://github.com/RMRubert/ExcelsUtils/blob/master/Games/MineSweeper.v2.xlsm){:target="_blank" class="r-save-link"}.

-->

