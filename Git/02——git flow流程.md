02——git flow流程

1. git flow 流程图：

   ![git flow 流程](E:\wzq\笔记(电子版)\Git\git flow 流程.png)

2. 分支类别：

   1. GitFlow 使用两个分支来记录项目开发的历史：

      ```javascript
      1.master 分支：(只是用于保存官方的发布历史)
              // 换而言之，可以拉取其中的任一commit，无须修改即可对外发布，只能从release branches或		hotfixes两个分支中合并，每次commit必须打标签
      2.develop 分支：develop分支才是用于集成各种功能开发的分支
      ```

   2. feature 分支：用于功能开发的分支

      ```javascript
      // 每一个新功能的开发都应该各自使用独立的分支。当功能开发完成时，改动的代码应该被合并（merge）到	develop分支。
      // 功能开发永远不应该直接牵扯到master。
      ```

   3. release 分支：用于发布的分支（检测分支上是否有 bug）：

      ```javascript
      // 在这个分支上只能修复bug，做一些文档工作或者跟发布相关的任务。在一切准备就绪的时候，这个分支会被	合并入master，并且用版本号打上标签。
      // 发布分支上的改动还应该合并入develop分支——在发布周期内，develop分支仍然在被使用（一些开发者会把	其他功能集成到develop分支）。
      ```

   4. hotfix 分支：用于 master 上的错误修复

      ```javascript
      // 这是唯一一种可以直接基于master创建的分支。
      // bug 解决后，应与 master和develop 分支进行合并
      ```

3. 流程：

   1. 如果要完成一个功能：

      ```javascript
      1.创建 feature 分支（基于 develop）
      2.完成功能后（add,commit）（循环操作）
      3.切换到 develop 分支上，将 feature 合并到 develop 上
      4.删除 feature 分支（也可不删除）
      5.如果 feature 被推送到了远程：
      	删除远程：
         		git push origin --delete 分支名
      ```

   2. 版本发布：

      ```javascript
      1.创建 release 分支（基于 develop）
      2.修复 bug （add,commit）（循环操作）
      3.切换到 develop 分支，将 release 分支合并到 develop上
      4.切换到 master 分支，将 release 分支合并到 master 上
      5.删除 release 分支
      6.给 master 打标签，并且携带标签推送
      7.切换到 develop 分支
      ```

   3. 修复 master bug：

      ```javascript
      1.创建 hotfix 分支（基于 master）
      2.修复 bug （add,commit）（循环操作）
      3.切换到 master 分支上，将 hotfix 分支合并到 master
      4.给 master 打标签，并且携带标签推送
      5.切换到 develop 分支上
      6.将 hotfix 合并到 develop 上
      7.删除 hotfix 分支
      ```

