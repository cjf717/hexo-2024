---
title: friends
date: 2024-11-19 16:08:34
type: "friends"
layout: "friends"
---

## 变量

<%- date(Date.now()) %>


## 目录测试

<% for (var link in site.data.menu) { %>
  <a href="<%= site.data.menu[link] %>"> <%= link %> </a>
<% } %>


## 友情链接测试

<% for (var item in site.data.friends) 
  { %>
    <a href="<%= site.data.menu[item.url] %>"> <%= item.name %> </a>
  <% } 
%>

## 代码示例
    <!-- <a href="<%= site.data.menu[link] %>"> <%= link %> </a> -->

"avatar": "http://image.luokangyuan.com/1_qq_27922023.jpg",
"name": "码酱",
"introduction": "我不是大佬，只是在追寻大佬的脚步",
"url": "http://luokangyuan.com/",
"title": "前去学习"
