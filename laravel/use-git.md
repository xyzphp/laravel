git的使用操作
===
1. git安装
		
		brew install git    //MAC OS 使用 brew 包管理工具安装
		
		apt-get install git	 //linux ububtu/Debian版本安装

2. 创建git仓库

		git init                              //创建本地git仓库

		git init --brae gitname.git           //创建裸仓库用于搭建git远程仓库
			
			
			
3. 配置git仓库

		git config --global user.name "Your Name"             //配置用户名
		
		git config --global user.email "email@example.com"    //配置邮箱

4. 链接远程git仓库
	
		git remote add origin ssh://servername:/url/gitname.git //链接远程git仓库
		
		git remote -v                                           //查看远程版本库的信息
	
5. 克隆一个git仓库
		
		git colone ssh://servername:/url/gitname.git

6. 获取远程git仓库的文件
		
		git pull origin master     //获取主分支中的内容

7. 将文件 添加到缓存区
		
		git add filename          //将一个文件添加到缓存区
		
		git add .                 //将全部文件添加到缓存区
		
		git add --all             //将全部文件添加到缓存区
		
8. 撤销文件修改

		git checkout -- filename.txt     //撤销工作区的文件
		
		git reset HEAD filename.txt	     //撤销缓存区的文件
			
9. 查看文件的状态

		git status

10. 将缓存区的文件提交到本地仓库中
		
		git commit -m "commit info"

11. 把本地git库的提交到远程git仓库
		
		git push origin master   //把本地的master分支提交到远程master 分支

12. git分支

		git branch             //查看分支
		
		git branch name        //创建分支
		
		git checkout name      //切换分支
		
		git checkout -b name   //切换+创建分支
		
		git merge name         //合并某分支到当前分支
		
		git merge name         //合并某分支到当前分支
		
		git merge --no-ff -m "info" name  //禁用Fast forward合并分支
		
		git branch -D feature-vulcan
		
13. git版本回退/版本恢复

		git reset --hard HEAD^               //回到上一个版本
	
		git reset --hard HEAD commit_id      //回到指定的版本

14. 查看git 提交日志和 commit_id
		
		git reflog                          //查看命令历史方便切换版本

		git log                             //查看git提交记录
		
		git log --pretty=oneline            //查看日志并查看git的提交id方便回退到某个版本
		
		git log --abbrev-commit             //查看日志并查看git的提交id方便回退到某个版本
		
		git log --graph                     //查看分支的合并情况
		
		git log --pretty=oneline --abbrev-commit --graph  //以上3种情况的结合

15. 工作现场的操作

		git stash 							//保存工作现场
		
		git stash list                     //查看工作现场
		
		git stash apply                    //还原工作现场
		
		git stash drop                     //删除工作现场 stash 中的内容
		
		git stash pop                      //恢复工作现场并删除 stash 中的内容
		
16. 标签操作
		
		git tag                                         //查看标签

		git tag tagname                                 //添加标签
		
		git tag -a tagname -m "标签信息" commit_id       //添加标签并制定给标签提交的版本
		
		git tag -s tagname -m "标签信息" commit_id       //用私钥签名一个标签
		
		git show tagname                                //查看标签
		