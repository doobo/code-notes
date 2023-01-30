# 日常怎样使用GIT

## 同分支开发
个人项目，小项目，基于这种方式使用GIT，也是初入编码时，使用的最对的方式。

## 切换合并法
基于特定分支切换出新分支，开发好功能，再合并到特定分支去；这种方法，特别适合那种很多人同时开发的大型项目，一个功能一个新的分支，
也是在工作中用的最多的一种方式。

## 解决冲突
### 同分支
同分支，有冲突，如果用工具，如idea，就直接拉取代码，点击有冲突到代码，进行合并即可。

### 切换合并
每次使用新分支开发功能的，新分支有冲突同上所述；但更多的是合并到其它分支时，有冲突，这个时候，推荐的方法是：
* 先从要合并去的目的分支，比如master切换一个merge分支
* 把新功能的分支，合并到新切换的merge分支，解决有冲突的代码
* 把解决冲突的merge分支，再合并最终想要合并的(master)分支去
这样在新分支再次补充新代码，就可以直接合并到master分支去，很少会有新到冲突产生。

### 命令行
``` shell
# 抓取origin仓库master分支的代码
git fetch origin master
# 将origin仓库master分支的代码与当前分支的代码合并(先fetch再merge)
git merge origin/master
# 将origin仓库master分支的代码与当前分支的代码强制合并
git merge origin/master --allow-unrelated-histories
# 查看合并后的情况（包括冲突文件）
git diff

# 解决有冲突的提交
git stash           #将本地修改存储起来
git stash list      #查看保存的信息
git pull            #暂存了本地修改之后，就可以pull了
git stash pop stash@{0}        #还原暂存的内容, 最后解决文件中冲突的的部分
-- Updated upstream 和=====之间的内容就是pull下来的内容，====和stashed changes之间的内容就是本地修改的内容
```