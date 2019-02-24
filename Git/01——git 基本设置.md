01——git 基本设置

1. 安装完 git 想要使用就必须设置用户名和邮箱（只需要设置一次即可）

   ```javascript
   git config --global user.name '用户名'
   git config --global user.email '邮箱'
   ```

2. 安装插件 ： git history

3. git 基本命令：

   ```javascript
   1.克隆仓库：
       git clone 仓库地址
   2.暂存：
       git add . (或： git add 文件名)
   3.提交本地仓库
       git commit -m '描述信息' (git commit ------进去后，填写描述信息，esc，:wq 退出)
   4.推送到远程仓库
       git push
   5.拉取远程仓库最新内容
       git pull
   6.创建新分支
       点击底部 master
   7. 合并分支
       命令面板-----git merge Branch
   ```

4. 推荐文章
   https://www.cnblogs.com/cnblogsfans/p/5075073.html

