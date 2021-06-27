---
layout: post
title: Using Excel/VBA to code simple games (2048, Minesweeper)
category: EN
tags: [Coding, Excel/VBA]
---

![Notepad++ Screenshot](/images/Posts/2020/2020-09-22_Image1.png){: .center-image }

A long time ago I found myself with a task that required with fairly large load times and I decided to use that time in order to create some simple games in Excel/VBA, it was a good way to get familiar with Excel/VBA which is always a nice skill to have. In this case, the games that I coded were 2048 and the classic Minesweeper.

<!-- more -->


I must warn anyone wanting to see the code, that the games are "as they were coded three years ago" and I have not bothered to rewrite or organise the code since 2017. Obviously, you will require to trust me, and allow macros in order to be able to use them.

## 2048


The game is pretty straight forward and follows the same rules that the android game with the same name. Select a cell, and then press one of the arrows to push the cell in that direction. Cells need to be pushed against one of the same value until you will manage to reach 2048. The game won't tell you when there are no more available moves. The game has been tested and works on LibreOffice 7.

[Download](https://github.com/RMRubert/ExcelsUtils/blob/master/Games/2048.xlsm){:target="_blank" class="r-save-link"}.

![Notepad++ Screenshot](/images/Posts/2020/2020-09-22_Image2.png){: .center-image }
## Minesweeper (v2)

Apparently, there was a version 1 of this game that I must have lost at some point. You will require to tag all the mines until there all of them are tagged. To tag or dig, select a cell and click on the tag or dig button. Mind that the routine that checks all mine-empty terrain has not been optimised so it might take a few seconds to get all revealed. You could technically go to the second page to see the results, but please don't (or do it, but it won't be a fair play!). The game is unable to work on LibreOffice 7, which is not surprising as it was designed for Excel 2013.

[Download](https://github.com/RMRubert/ExcelsUtils/blob/master/Games/MineSweeper.v2.xlsm){:target="_blank" class="r-save-link"}.


