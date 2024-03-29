# 1.git introduce
## 什么是版本控制系统？
如果你用Microsoft Word写过长篇大论，那你一定有这样的经历：<br/>
想删除一个段落，又怕将来想恢复找不回来怎么办？有办法，先把当前文件“另存为……”一个新的Word文件，再接着改，改到一定程度，再“另存为……”一个新文件，这样一直改下去。最后你的Word文档变成了这样：<br/>
![](img/word.jpg)<br/>
过了一周，你想找回被删除的文字，但是已经记不清删除前保存在哪个文件里了，只好一个一个文件去找，真麻烦。
看着一堆乱七八糟的文件，想保留最新的一个，然后把其他的删掉，又怕哪天会用上，还不敢删，真郁闷。<br/>
更要命的是，有些部分需要你的财务同事帮助填写，于是你把文件通过Email发送一份给她，然后，你继续修改Word文件。一天后，同事再把Word文件传给你，此时，你必须想想，发给她之后到你收到她的文件期间，你作了哪些改动，得把你的改动和她的部分合并，真困难。<br/>
如果有一个软件，不但能自动帮我记录每次文件的改动，还可以让同事协作编辑，这样就不用自己管理一堆类似的文件了，也不需要把文件传来传去。如果想查看某次改动，只需要在软件里瞄一眼就可以，岂不是很方便？<br/>
这个软件用起来就应该像这个样子，能记录每次文件的改动：
![](img/version.jpg)
这就是版本控制系统做的事

## git:分布式版本管理系统

集中式版本控制系统:<br/>
<img src="img/svn.jpg" width="50%"/><br/>
git:<br/>
<img src="img/git.jpg" width="50%"/><br/>
<img src="img/gitintroduce.jpg" width="60%"/><br/>
<img src="img/gitintroduce2.jpg" width="60%"/><br/>

[详细了解git](http://www.git-scm.com.cn/1479.html)<br/>

# 2.git setup
## download git
[点我下载](https://git-scm.com/download)<br/>
<img src="img/git1.JPG" width="50%"/><br/>
## complete the setup wizard
<img src="img/git2.JPG" width="50%"/><br/>
#### 在任意目录下，可以看到右击菜单多了一个git Bash和git GUI选项，说明已经安装成功。git Bash是指令窗口，git GUI是可视化图形窗口。



# 3.git用户名和邮箱配置 
右击选择git Bash，输入

		$ git config --global user.name "Your Name"
		$ git config --global user.email "email@example.com"

输入 git config --list 检查是否设置成功
![](img/git3.JPG)<br/>


# 4.create remote repository and local repository
## create remote repository
#### 登录github账号，选择repositories-->new
![](img/githubcreaterepositories.jpg)<br/>
#### 输入你的仓库名称、描述、勾选Initialize this repository with a README-->创建
![](img/createanewrepository.jpg)<br/>

## add collaborator
在刚创建的仓库中选择setings-->Collaborators-->输入并选择用户-->add collaborator
![](img/addcollaborators.jpg)<br/>
#### 被添加人员会收到invitation，accept invitation即可加入开发
![](img/addcollaborators2.png)
![](img/addcollaborators3.png)
![](img/addcollaborators4.png)

## ssh key
GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。
### create ssh key
首先检查自己的账户目录下是否存在.ssh文件夹，若没有说明还没有创建ssh key<br/>

打开git bash输入命令

		ssh-keygen -t rsa -C"email@example.com"
创建ssh key<br/>

按回车跳过自定义名称然后输入密码（可以再直接按回车设置空密码）

![](img/git4.JPG)<br/>

### copy ssh public key
#### 在账户目录下找到".ssh"文件夹

![](img/sshlocation.JPG)<br/>

#### 使用记事本打开"id_rsa.pub"文件,复制里面的内容

![](img/ssh.JPG)<br/>

### add ssh public key to github
#### 用浏览器打开github账户，点击头像选择 Settings——>SSH and GPG Keys-->new SSH key

![](img/addssh.JPG)<br/>

#### 把刚才复制的内容粘贴到key栏中，Title一栏给这个key起个名字，选择Add SSH key

![](img/git5.JPG)<br/>

## clone existing repository
#### 在任意目录下右击选择 git GUI here-->clone existing repository

![](img/gitguihere.JPG)<br/>

#### 用浏览器打开创建的remote repository，复制项目地址

![](img/sourcelocation.JPG)<br/>

#### 把地址粘贴到git gui的source location一栏，Target Directory注意要在后面加上一个你要创建的仓库名

<img src="img/git7.JPG" width="60%"/><br/>

#### 选择Clone

稍等片刻，远程仓库就克隆到本地仓库中了

<img src="img/git6.JPG" width="60%"/><br/>


# 5.commit and push
在本地工作目录中对文件进行修改、增加或删除，在git GUI中选择 rescan 重新扫描文件，被增删改的文件会显示在左上窗口

![](img/rescan.JPG)<br/>

部分文件可以看到右边窗口显示乱码，右击右边窗口，选择Encoding——>Unicode(UTF-8) 即可恢复正常，绿色字体是新增加的内容，红色字体是被删除的内容

![](img/encoding.JPG)<br/>

点击左上窗口所有文件的图标，并在右下窗口写上提交信息，选择Commit——>Push


<img src="img/push.JPG" width="60%"/>
<img src="img/push1.JPG" width="60%"/>

上推成功！
#### 这时在远程仓库中新添了文件
![](img/git10.JPG)<br/>

## 远程仓库比本地仓库有更新内容导致上推失败
新的内容上推之前在本地另一个目录创建仓库B并下拉项目，再上推仓库A新的内容，这样仓库B的内容就比远程仓库旧。

修改仓库B的内容并上推，发现上推失败。
![](img/pushfail.JPG)

## 解决办法
#### pull remote repository：GUI菜单 Remote——>Fetch from——>origin
![](img/fetchfromorigin.JPG)

#### merge branch：选择merge——>local merge
![](img/localmerge.JPG)

选择要合并到哪个本地的分支-->merge

![](img/localmerge1.JPG)

这时就可以成功上推了。

![](img/pushsuccess.JPG)<br/>

# 6..gitignore忽略文件
一个本地的项目通常会产生很多编译出来的文件，这些文件我们不需要跟踪。
当我们必须把某些文件放在本地，又不想提交它时，我们创建一个忽略目录
#### 在本地仓库新建一个文本文档
#### 在文档中添加要忽略的内容
忽略文件的格式如下

		classes、classes/	路径中含有classes就被忽略
		/classes/*、/class/、classes/*		.gitignore同级目录classes下所有文件被忽略（建议用第一个）
		
		*.class	文件名以.class结尾的一类文件被忽略
		.class	文件名是.class的一个文件被忽略
		
		WebRoot/WEB-INF/classes、WebRoot/WEB-INF/classes/、WebRoot/WEB-INF/classes/*	.gitignore同级目录WebRoot下的WEB-INF/classes所有文件被忽略
		*/WEB-INF/classes、*/WEB-INF/classes/、*/WEB-INF/classes/*			.gitignore所有同级目录下的WEB-INF/classes下文件被忽略
		**/WEB-INF/classes、**/WEB-INF/classes/、**/WEB-INF/classes/*			所有路径中含有 WEB-INF/classes 的文件被忽略
		.gitignore 放在 .git 文件同级才会生效
<br/>
<img src="img/gitignore.JPG" width="70%" />

#### 另存为所有文件，命名为.gitignore

![](img/savegitignore.JPG)<br/>

# 7.branch manage
## create branch
#### 选择branch菜单下的create选项
![](img/createbranch1.JPG)
#### 输入分支名字，点create
![](img/createbranch2.JPG)
#### 上推新的分支
选择刚刚创建的分支

![](img/pushnewbranch.JPG)
#### 检查远程仓库分支，可以看到刚刚提交的分支
![](img/yuanchengbranch.JPG)

## checkout branch
#### 选择branch菜单下的checkout选项
![](img/checkout1.JPG)
#### 选择分支，点checkout
![](img/checkout2.JPG)

## merge branch
#### 选择merge菜单下的local merge,选择需要合并到master的branch
#### 合并后的分支图
![](img/fetchfromorigingitk.JPG)

## delete branch
#### 选择branch|delete
#### 选择要删除的分支，选择delete
![](img/deletebranch.JPG)

# 8.版本回退
#### 打开git GUI选择repository-->visualize all branch history
可以看到所有commit和merge的历史<br/>
![](img/branchhistory.jpg)<br/>
#### 选择其中一个节点右键-->reset *** branch to here
![](img/reset.png)<br/>
你的文件就会回到当时commit的版本