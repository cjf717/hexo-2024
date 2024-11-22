
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
