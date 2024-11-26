---
title: metingJs音乐播放器接口API
tags:
- 播放器
date: 2024-11-26 13:02:59
# aplayer: true
disableNunjucks: true
---

<!DOCTYPE html>
<html lang="zh-cn">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="https://cdn.staticfile.net/aplayer/1.10.1/APlayer.min.css">
  <title>metingJs音乐播放器接口</title>
  <style>
    h5 {
      margin: 0;
    }
    .form {
      margin: 5px 3px;
      border: 1px solid #e2e2e2;
      border-radius: 10px;
      box-sizing: border-box;
      padding: 10px;
      max-width: 375px;
      line-height: 2;
      text-align: right;
    }
    .card {
      display: flex;
      margin: 5px 3px;
      border: 1px solid #e2e2e2;
      border-radius: 10px;
      box-sizing: border-box;
      overflow: hidden;
      max-width: 375px;
    }
    .album {
      width: 150px;
      height: 150px;
    }
    .cover {
      width: inherit;
    }
    .content {
      flex: 1;
      padding: 5px;
      box-sizing: border-box;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .title {
      text-align: center;
    }
    .playmusic {
      text-align: right;
    }
  </style>
</head>
<body>
  <div id="app">
    <div id="aplayer"></div>
    <div class="form">
      <h3 class="title">meting接口高级搜索</h3>
      <div>
        <label for="server">选择平台</label>
        <select name="server" id="server" v-model="server">
          <option value="">--Please choose an option--</option>
          <option value="netease">网易云netease</option>
          <option value="tencent">tencent</option>
          <option value="kugou">kugou</option>
          <option value="xiami">xiami</option>
          <option value="baidu">baidu</option>
        </select>
      </div>
      <div>
        <label for="types">选择类型</label>
        <select name="types" id="types" v-model="types">
          <option value="">--Please choose an option--</option>
          <option value="search">搜索</option>
          <option value="song">song</option>
          <option value="playlist">playlist</option>
          <option value="album">albumt</option>
          <option value="artist">artist</option>
        </select>
      </div>
      <div>
        <label for="keyword">关键字id</label>
        <input type="text" v-model="id" id="keyword">
      </div>
      <div><button @click="sumitBtn()">提交</button></div>
    </div>
    <div v-for="item in musicList" :key="item" class="card">
      <div class="album"><img class="cover" :src="item.pic" :alt="item.title"></div>
      <div class="content">
        <h5 class="title">{{ item.title }}</h5>
        <div class="author">{{ item.author }}</div>
        <div><a :href="item.url">url</a></div>
        <div><a :href="item.lrc">lrc</a></div>
        <div class="playmusic"><button @click="playMusic(item)">播放</button></div>
      </div>
    </div>
  </div>
  <script src="https://cdn.staticfile.net/aplayer/1.10.1/APlayer.min.js"></script>
  <script src="https://cdn.staticfile.net/vue/3.3.4/vue.global.min.js"></script>
  <script src="https://cdn.staticfile.net/axios/1.6.5/axios.min.js"></script>
  <script>
    const { createApp } = Vue
    createApp({
      data() {
        return {
          ap: null,
          server: "netease",
          types: "search",
          id: "中国人",
          musicList: null,
          baseUrl: "https://api.i-meto.com/meting/api"
        }
      },
      methods: {
        getMusic() {
          axios.get(this.baseUrl, {
            "Access-Control-Allow-Origin": true,
            params: {
              server: this.server,
              type: this.types,
              id: this.id,
              r: Math.random()
            }
          })
            .then(res => { console.log(res); this.musicList = res.data })
            .catch((error) => console.log(error));
        },
        sumitBtn() {
          // console.log("点击了按钮", this.id, this.server, this.types)
          this.getMusic()
        },
        playMusic(music) {
          // console.log(music);
          this.ap.list.add([{
            name: music.title,
            artist: music.author,
            url: music.url,
            cover: music.pic,
            lrc: music.lrc
          }]);
          console.log(this.ap.list.audios.length);
          this.ap.list.switch(this.ap.list.audios.length - 1)
          this.ap.play()
        }
      },
      mounted() {
        console.log("mounted")
        this.ap = new APlayer({
          container: document.getElementById('aplayer'),
          preload: "none",
          audio: [{
            name: '怀集音乐之声',
            artist: '蜻蜓FM',
            url: 'https://lhttp.qingting.fm/live/4804/64k.mp3',
            cover: '/hexo-2024/cover.jpg'
          },
          {
            name: '羊城交通台',
            artist: '蜻蜓FM',
            url: 'https://lhttp.qtfm.cn/live/1262/64k.mp3',
            cover: '/hexo-2024/cover.jpg'
          },]
        });
      }
    }).mount('#app')
  </script>
</body>
</html>
