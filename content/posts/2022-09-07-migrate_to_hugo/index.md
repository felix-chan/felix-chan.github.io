---
title: 更新網誌系統到 Hugo
date: 2022-09-07T12:10:42+08:00
author: HaNg~
url: /2022/09/07/migrate_to_hugo/
categories:
  - 網誌
tags:
  - Wordpress
  - Hugo
  - Go
  - PHP
---

好耐都冇更新過 [Wordpress][1] 同網誌，Wordpress 嘅版本已經不合時宜，而且太耐冇用 PHP 已經唔太記得佢哋嘅話法。所以今次襯伺服器要更新，決定搵過新嘅 Blog platform 去重建呢個 blog。

<!--more-->

因為呢個 blog 比較少更新，[Dynamic website][2] 其實都冇需要，所以今次目標係後台產新 static files 的 blog framework。而下列三個 framework 都係我考慮之列︰

 1. [Heco][3]
 2. [Hugo][4]
 3. [Jekyll][5]

其實好耐之前已經試用過 **Jekyll**，用落嘅感覺唔太好，寫網頁比較複雜。反而 **Hugo** 同 **Hexo** 比較類近，兩個 framework 我都試左一次。兩個 framework 都係食 **markdown** 出內容，對於我呢 D 平時係 Git Repo 寫開 `README.md` 嘅人嚟講真係非常方便，File 又細又容易閱讀，生成的 HTML files 又唔會好似唔少 [WYSIWYG][6] Editor 咁會出現大量無用 html tag，啱晒我呢啲強逼症人事。

其實用落我對 **Hexo** 感覺比較好，佢以 node.js 寫嘅，對於我嚟講係比較易修改，加埋 **Hexo** 嘅 theme 簡單直接，要改都易好多。相反，**Hugo** 的優點就係又快又新，而且 theme 的設計比較貼近現代技術，使用者多支援又多一點。

最後係考慮埋 [Swiftzer][7] 為左方便管理，會用埋 Hugo 去產新首頁網站，所以統一用晒 **Hugo** 去作為 blog platform，到時更新修改都學少樣野。


 [1]: https://wordpress.org
 [2]: https://blog.hubspot.com/website/static-vs-dynamic-website
 [3]: https://hexo.io/
 [4]: https://gohugo.io/
 [5]: https://jekyllrb.com/
 [6]: https://zh.wikipedia.org/zh-hk/%E6%89%80%E8%A7%81%E5%8D%B3%E6%89%80%E5%BE%97
 [7]: http://swiftzer.net