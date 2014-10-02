ubuntu不能更改启动项的问题解决
===============================

新装的ubuntu启动项无法通过修改/etc/default/grub文件，然后用update-grub的命令使启动项生效。提示信息显示，每次都要生成menu.lst文件。但是即使生成了该文件，启动项还是原来的选项，根本就没有更改。

从网上找了半天，也没有发现问题所在。最近又在网上搜索，发现有个帖子提到update-grub和update-grub2的区别，回复中提到这两个命令是一回事，是用一个symbol link建立的符号连接，于是用update-grub2命令试了一下，竟然提示不存在该命令，建议安装grub2-common。当时就觉得有戏，看来现在这个update-grub是早期版本，所以每次运行并没有更改/boot/grub/grub.cfg文件，而是生成menu.lst文件，而启动文件又不读取menu.lst里的启动信息。所以启动项根本就没有改变。立即安装grub2-common。

	apt-get install grub2-common

然后再用update-grub，现在提示信息没有生成menu.lst的信息了，看来/boot/grub/grub.cfg文件更新成功了。重启，成功！


此外，ubuntu还有个问题是进入系统后无法调节亮度，在网上搜索方法是要修改/etc/default/grub文件内容，找到

	GRUB_CMDLINE_LINUX=“”

更改为：

	GRUB_CMDLINE_LINUX=“acpi-backlight=vendor”

然后update-grub，搞定，现在可以调节亮度了。