关闭openwrt的led灯
==================

华为HG255D路由器刷了openwrt，有四个led灯亮，分别是电源power，无线wireless，usb口USB，外网internet。这个外网对应的led灯是第4个接口的灯亮。在openwrt路由器web管理界面有led灯的调节选项，在`system`下的`LED configure`栏目下：

第一个是USB选项，led name是hg255d:usb，trigger本来是usbdev，改为none，然后save&apply，再看openwrt，usb的led显示灯灭了。接下来修改其他的选项。

WLAN选项，led name是hg255d:wlan更改原来trigger是netdev，在下面有一个下拉选择框，里面是ra0，对应的是无线网卡，再下面有三个复选框，分别是Linkon表示连接时亮，transmit和recieve估计是传输和接受数据时亮。将trigger改为none，save&apply后这个led灯就不亮了。

INTERNET是外网连接led控制，对应名字hg255d:internet，原理同上，更改trigger为none，关闭显示。

其他都可以类似如此设置，设置完保持配置文件backup-CHEN-PandoraBox-2014-10-27.shutdownled.tar