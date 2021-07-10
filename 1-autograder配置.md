之前发过一篇召集学习队友的文章，一起学习伯克利大学的Java数据结构课程。最近也到了总结的时候。



## autograder使用

设置好autograder，我们就可以自己写作业并查看反馈了。

首先在这里说一下原理，知乎上有一些回答可以作为参考。

[知乎参考1](https://zhuanlan.zhihu.com/p/115229260)

[知乎参考2](https://www.zhihu.com/search?type=content&q=autograder)

首先，你自己建一个仓库，这个仓库的名字叫什么无所谓，关键是仓库内部需要有规定好的文件夹的框架（这个框架就是课程的专属github），文件的组织顺序（如果你自己想多写几个README啥的，对评分没有影响的）。我们要做的就是填好对应的文件里的内容，然后在自动评分网站和我们的仓库关联，网站就可以找到对应的文件来评分。

分为2步：
1. 在github上注册自己的仓库，并下载别人写好的代码框架。如果是熟练使用git的老鸟，其实就是把`https://github.com/Berkeley-CS61B/skeleton-sp18.git`内容放到自己建的一个仓库里即可。
    - 如何在github上建一个空仓库，并且把空仓库下载到本地。这部分建议上网搜索。
    
        
    
    - 假设你的仓库名字叫做`cs61b`，那么右键`git bash`打开这个文件夹。
    
        
    
    - 依次输入以下指令：
        `git remote add skeleton https://github.com/Berkeley-CS61B/skeleton-sp18.git`
        
    - ` git pull skeleton master --allow-unrelated-histories`
        `git push -u origin main`
        
    - 做完这些，在github的网页上你可以看到多了很多文件夹。
2. 在[gradescope.com](https://gradescope.com/)网站上注册自己的账号，关联github，写好代码后，提交到github上，到网站上查看分数。
    点击对应的lab，按照指示选择自己的仓库名字等，就会评分了。