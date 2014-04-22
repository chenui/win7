Cygwin下的git配置
================

### **git显示中文文件名**

应用apt-cyg安装了git，但是默认配置下git的命令下不能显示中文的文件名和内容。比如：

> git status

	# On branch master
	# Untracked files:
	#   (use "git add <file>..." to include in what will be committed)
	#
	#       "Cygwin\347\232\204\345\256\211\350\243\205\345\222\214\351\205\215\347\275\256apt-cyg\346\272\220.md"
	nothing added to commit but untracked files present (use "git add" to track)

配置变量core.quotepath设置为false就可以中文名在git命令中显示正常的问题：

> git config --global core.quotepath false
>
> git status

	# On branch master
	# Untracked files:
	#   (use "git add <file>..." to include in what will be committed)
	#
	#       Cygwin的安装和配置apt-cyg源.md
	nothing added to commit but untracked files present (use "git add" to track)

### **git输出开启颜色显示**

> git config --system color.ui true
