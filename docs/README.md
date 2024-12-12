
```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:cjf717/hexo-2024.git
git push -u origin main
```
建议部署分支与主分支分开，避免覆盖配置代码。
发布到分支：gh-hexo-pages


## 添加多个远程仓库
```
# 添加第一个远程仓库
git remote add origin https://github.com/user/repo1.git
 
# 添加第二个远程仓库
git remote add upstream https://github.com/otheruser/repo2.git
 
# 查看远程仓库
git remote -v
 
# 从origin仓库拉取master分支的代码
git pull origin master
 
# 将代码推送到upstream仓库的main分支
git push upstream main
```

```
git remote add gitlab git@gitlab.com:cjf717/hexo-demo.git
git push gitlab main
```

## 相关文章
### 官方文档
官方文档 https://hexo.io/zh-cn/
### Butterfly主题
- github：https://github.com/jerryc127/hexo-theme-butterfly
- 官方文档：https://butterfly.js.org/
- gitee 官网：https://gitee.com/immyw/hexo-theme-butterfly
### 入门文章
《hexo+github搭建博客(超级详细版，精细入微)》，https://blog.csdn.net/victoryxa/article/details/103733655

## 上传
- 更新到服务器
```
rsync -avz --chmod=755 --delete -e 'D:\tools\cwrsync_6.2.12_x64_free\bin\ssh.exe -p 38220 -i ~/.ssh/id_ed25519' public/ jeff@8.134.209.242:/var/www/html/hexo-2024/
```
