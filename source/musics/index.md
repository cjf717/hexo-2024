---
title: musics
date: 2024-11-20 10:33:10
type: "musics"
layout: "musics"
aplayer: true
---

## 基本参数
```
{% aplayer title author url [picture_url, narrow, autoplay, width:xxx, lrc:xxx] %}
```

## 播放列表
```
{% aplayerlist %}
{
    "narrow": false, // （可选）播放器袖珍风格
    "autoplay": true,      // （可选）自动播放，移动端浏览器暂时不支持此功能
    "mode": "random",      // （可选）曲目循环类型，有 'random'（随机播放）, 'single' (单曲播放), 'circulation' (循环播放), 'order' (列表播放)， 默认：'circulation' 
    "showlrc": 3,    // （可选）歌词显示配置项，可选项有：1,2,3
    "mutex": true,   // （可选）该选项开启时，如果同页面有其他 aplayer 播放，该播放器会暂停
    "theme": "#e6d0b2", // （可选）播放器风格色彩设置，默认：#b7daff
    "preload": "metadata", // （可选）音乐文件预载入模式，可选项： 'none' 'metadata' 'auto', 默认: 'auto'
    "listmaxheight": "513px", // (可选) 该播放列表的最大长度
    "music": [
        {
            "title": "CoCo",
            "author": "Jeff Williams",
            "url": "caffeine.mp3",
            "pic": "caffeine.jpg",
            "lrc": "caffeine.txt"
        },
        {
            "title": "アイロニ",
            "author": "鹿乃",
            "url": "irony.mp3",
            "pic": "irony.jpg"
        }
    ]
}
{% endaplayerlist %}
```

{% aplayerlist %}
{
  "narrow": false,
  "autoplay": false,
  "mode": "random",
  "showlrc": 1, 
  "mutex": true,
  "theme": "#e6d0b2",
  "preload": "none",
  "listmaxheight": "513px",
  "music": [
      {
          "title": "怀集音乐之声",
          "author": "蜻蜓FM",
          "url": "https://lhttp.qingting.fm/live/4804/64k.mp3",
          "pic": "https://img1.mydrivers.com/img/20241120/8351c0be-83f1-47a0-8b13-ec4b4056b842.jpg",
          "lrc": "[00:00.000]怀集音乐之声_蜻蜓FM"
      },
      {
          "title": "羊城交通台",
          "author": "蜻蜓FM",
          "url": "https://lhttp.qtfm.cn/live/1262/64k.mp3",
          "pic": "https://img1.mydrivers.com/img/20241120/8351c0be-83f1-47a0-8b13-ec4b4056b842.jpg"
      },
      {
          "title": "广州交通电台",
          "author": "蜻蜓FM",
          "url": "https://lhttp.qtfm.cn/live/4955/64k.mp3",
          "pic": "https://img1.mydrivers.com/img/20241120/8351c0be-83f1-47a0-8b13-ec4b4056b842.jpg"
      }
  ]
}
{% endaplayerlist %}


## 导入CDN js
<!-- require APlayer -->
<link rel="stylesheet" href="https://cdn.staticfile.net/aplayer/1.10.1/APlayer.min.css">
<script src="https://cdn.staticfile.net/aplayer/1.10.1/APlayer.min.js"></script>
<!-- require MetingJS -->
<script src="https://cdn.staticfile.net/meting/2.0.1/Meting.min.js"></script>

<meting-js
	server="netease"
	type="search"
	id="少年在志">
</meting-js>
