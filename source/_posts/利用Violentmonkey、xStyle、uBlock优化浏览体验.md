---
title: 利用Violentmonkey、xStyle、uBlock优化浏览体验
date: 2020-07-16 11:35:49
tags: Css
categories:
---

![avatar](https://cdn.jsdelivr.net/gh/xfjiang0818/pictures@1.0/20200705.jpg)

<!-- more -->

## 去广告

使用 uBlock，设定自定义静态规则如下

```
{
"timeStamp": 1582433973515,
"version": "1.24.4",
"userSettings": {
"advancedUserEnabled": true,
"alwaysDetachLogger": false,
"autoUpdate": true,
"cloudStorageEnabled": false,
"collapseBlocked": true,
"colorBlindFriendly": false,
"contextMenuEnabled": false,
"dynamicFilteringEnabled": true,
"externalLists": "https://gitee.com/xinggsf/Adblock-Rule/raw/master/mv.txt\nhttps://gitee.com/xinggsf/Adblock-Rule/raw/master/rule.txt\nhttps://raw.githubusercontent.com/xinggsf/Adblock-Plus-Rule/master/ABP-FX.txt",
"firewallPaneMinimized": true,
"hyperlinkAuditingDisabled": true,
"ignoreGenericCosmeticFilters": false,
"largeMediaSize": 50,
"parseAllABPHideFilters": true,
"prefetchingDisabled": true,
"requestLogMaxEntries": 1000,
"showIconBadge": false,
"tooltipsDisabled": true,
"webrtcIPAddressHidden": false
},
"selectedFilterLists": [
"user-filters",
"ublock-filters",
"ublock-badware",
"ublock-privacy",
"ublock-abuse",
"ublock-unbreak",
"easylist",
"easyprivacy",
"CHN-1",
"CHN-0",
"https://gitee.com/xinggsf/Adblock-Rule/raw/master/rule.txt",
"https://gitee.com/xinggsf/Adblock-Rule/raw/master/mv.txt"
],
"hiddenSettings": {
"allowGenericProceduralFilters": false,
"assetFetchTimeout": 30,
"autoCommentFilterTemplate": "{{date}} {{origin}}",
"autoUpdateAssetFetchPeriod": 120,
"autoUpdateDelayAfterLaunch": 180,
"autoUpdatePeriod": 7,
"blockingProfiles": "11111/#F00 11011/#C0F 11001/#00F 00001",
"cacheStorageAPI": "unset",
"cacheStorageCompression": true,
"cacheControlForFirefox1376932": "no-cache, no-store, must-revalidate",
"consoleLogLevel": "unset",
"debugScriptlets": false,
"debugScriptletInjector": false,
"disableWebAssembly": false,
"extensionUpdateForceReload": false,
"ignoreRedirectFilters": false,
"ignoreScriptInjectFilters": false,
"filterAuthorMode": false,
"loggerPopupType": "popup",
"manualUpdateAssetFetchPeriod": 500,
"popupFontSize": "unset",
"requestJournalProcessPeriod": 1000,
"selfieAfter": 11,
"strictBlockingBypassDuration": 120,
"suspendTabsUntilReady": "unset",
"updateAssetBypassBrowserCache": false,
"userResourcesLocation": "unset"
},
"whitelist": [
"about-scheme",
"chrome-extension-scheme",
"chrome-scheme",
"moz-extension-scheme",
"opera-scheme",
"vivaldi-scheme",
"wyciwyg-scheme"
],
"netWhitelist": "about-scheme\nchrome-extension-scheme\nchrome-scheme\nmoz-extension-scheme\nopera-scheme\nvivaldi-scheme\nwyciwyg-scheme",
"dynamicFilteringString": "behind-the-scene * * noop\nbehind-the-scene * inline-script noop\nbehind-the-scene * 1p-script noop\nbehind-the-scene * 3p-script noop\nbehind-the-scene * 3p-frame noop\nbehind-the-scene * image noop\nbehind-the-scene * 3p noop",
"urlFilteringString": "",
"hostnameSwitchesString": "no-large-media: behind-the-scene false",
"userFilters": "||vali.cp31.ott.cibntv.net^$domain=v.youku.com,third-party\n@@mp4.ts\n"
}
```



## bilibili

使用 Bilibili Evolved 简化页面并设置弹幕为自动关闭

使用 xStyle 脚本屏蔽番剧评论区等元素

```css
@-moz-document domain("bilibili.com") {
    .gui-settings-icon-panel {
        display: none;
    }
    #comment_module {
        display: none !important;
    }
    .international-footer {
        display: none !important;
    }
}
```



## Baidu

打开 xStyle 样式网站 https://userstyles.org/，找到

* 百度百科-屏蔽和优化

* 百度经验-屏蔽和优化

* 百度知道-屏蔽和排版

* 百度文库-屏蔽

使用 Violentmonkey 的 贴吧全能助手 脚本优化百度贴吧界面



## CSDN

使用 Violentmonkey 脚本 https://greasyfork.org/zh-CN/scripts/378351 设定宽屏并净化浮窗广告

使用 xStyle 脚本去除顶端及侧边的栏目

```css
@-moz-document domain("csdn.net") {
    .pulllog-box,
    .tool-box,
    #csdn-toolbar,
    #reportContent,
    .indexSuperise,
    .meau-gotop-box,
    #dmp_ad_58,
    .mediav_ad,
    .ad,
    .recommend-box,
    .recommend-fixed-box,
    .recommend-right,
    aside {
        display: none !important;
    }
    main {
        position: absolute;
        width: 1300px !important;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
    }
}
```



## 简书

使用 xStyle 脚本

```css
@-moz-document url-prefix("http://www.jianshu.com"),
url-prefix("https://www.jianshu.com") {
    /*拓宽简书的文章阅读界面,更好利用宽屏*/
    ._gp-ck {
        width: 100%
    }
    ._3Pnjry {
        display: none;
    }
    /*去除不必要的元素*/
    ._1CSgtu,
    .VYwngI,
    ._2xr8G8,
    aside {
        display: none!important;
    }
    ._3VRLsv,
    main {
        position: absolute;
        width: 1300px !important;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
    }
}
```



## 斗鱼

打开 xStyle 样式网站 https://userstyles.org/，找到 Douyu Cleaner 清爽斗鱼，添加自建代码

```css
/*---------自建---------*/
    .layout-Header,
    .Header-left,
    .Header-follow-wrap,
    .Header-broadcast-wrap,
    .layout-Aside,
    .layout-Player-toolbar,
    .layout-Player-title {
        display: none!important;
    }
    .layout-Main {
        padding-left: 10px!important;
        padding-right: 10px!important;
        padding-top: 0px!important;
        margin-left: 0px!important;
    }
    .layout-Container {
        padding-top: 50px!important;
    }
```



## 知乎

使用 xStyle 脚本

```css
@-moz-document domain("www.zhihu.com"),
domain("zhihu.com") {
    .Sticky.AppHeader.is-fixed {
        top: -45px !important;
        -moz-transition: top 200ms ease-out 500ms;
        -webkit-transition: top 200ms ease-out 500ms;
        transition: top 200ms ease-out 500ms;
    }
    .Sticky.AppHeader:hover {
        -webkit-backdrop-filter: blur(20px);
        backdrop-filter: blur(20px);
        background-color: rgba(255, 255, 255, 0.8);
        top: 0 !important;
        -moz-transition-delay: 0s;
        -webkit-transition-delay: 0s;
        transition-delay: 0s;
    }
    @supports ((-webkit-backdrop-filter:blur(20px)) or (backdrop-filter:blur(20px))) {
        .Sticky.AppHeader:hover {
            -webkit-filter: none;
            filter: none
        }
    }
    .GlobalSideBar-categoryList,
    .GlobalSideBar-navList,
    .Question-sideColumn {
        display: none !important;
    }
    .TopstoryMain,
    .Topstory-mainColumn,
    .Question-mainColumn {
        width: 1000px;
        min-height: 100vh;
    }
    .Footer {
        display: none;
    }
}
```



## 爱奇艺

使用 xStyle 脚本，屏蔽评论区等元素

```css
@-moz-document domain("www.iqiyi.com") {
    .qy-logo,
    #nav_logo,
    .qy-nav,
    .search-box,
    .header-vip,
    .header-upload,
    .header-download,
    .player-mnb-left,
    .intro-mn,
    .intro-sd,
    .qy-play-con,
    .channel-footer-warp,
    #block-D,
    #block-V,
    .qy-player-side-ear,
    aside {
        display: none
    }
}
```



## 微博

使用 xStyle 脚本 https://userstyles.org/styles/158902/weibox 简化页面



## Feeder.co

使用 xStyle 脚本

```css
@-moz-document domain("feeder.co") {
    /*更改字体*/
    p {
        font-family: "Hiragino Sans GB", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif !important;
    }
    /*增大阅读区的宽度*/
    .__e390d .wrapper {
        width: 1156px;
        padding: 0 24px;
        margin: 0 auto;
        position: relative;
    }
    /*增大字号*/
    body {
        font-size: 16px;
        font-weight: 400;
        padding: 0;
        color: #ff00ff;
    }
}
```



## 补充

stylish 上的 xStyle 脚本可以安装为 Violentmonkey 脚本
