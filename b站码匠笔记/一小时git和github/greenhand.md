

## git与git hub

### 为什么用git和git hub？

- 当我们多人协同开发时，为了提高效率，避免出现我们做出改动时其他人必须要我们用诸如u盘拷贝的情况，常使用git（git hub），相当于我们共用一个项目空间，做出的修改可以上传到这个空间，别人也可以从空间上拉取你的修改。当然本质上git是版本控制工具，还有版本回溯等的功能

### git和git hub的区别？

- git是一种版本控制工具，是可以在计算机未联机情况下，只在本地使用的一个版本管理工具。可以认为是一个软件
- git hub是一个网站，通过它我们可以为自己的项目创建仓库并提交本地文件，并且也可以被别人看到。

### SSH准备

- 于settings-ssh and gpg keys-new shh keys中添加

- 可以在下载的生成链接中查看教程

- 在添加新ssh前，先检查是否已有

  ```git
  ls -al ~/.ssh
  #这里-al的效果好像是是否展示全部文件的详细信息。
  #ls命令是list的意思，就是列出文件
  ```
- 如果没有ssh，使用命令生成（pub是公钥，rsa是私钥）

  ```git
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  #引号内容用自己的邮箱代替
  ```

- 复制ssh公钥。可以用命令也可以自己去生成的文件件找.pub后缀的文件打开并复制，之后在第一步的地方添加即可

  ```git
  clip < ~/.ssh/id_rsa.pub
  ```

- 注意！！！除了在github上添加公钥，还必须要在git中添加私钥，不然在clone时使用ssh仍然会失败。而添加私钥可能会踩坑。见下

  ```
  $ ssh-add ~/.ssh/id_rsa
  Could not open a connection to your authentication agent.
  #这是因为没有开启ssh-agent
  #下面是正确做法：
  $ eval $(ssh-agent -s)
  Agent pid 1462
  
  ssh-add ~/.ssh/id_rsa
  ```

  

### 基础操作

- git clone url 将仓库下载到本地。注意git bash里面复制粘贴是ctrl/shift+insert
- git add-》 git commit来将修改提交到版本库，但此时远程的仍未更新。通过gitpush可以更新远程。commit时需要提交用户名和邮箱，按提示来即可。
- git status可以查看当前仓库状态
- git log查看仓库提交日志。对于commit后面的一长串代码，我们可以使用git show +代码来查看详细信息