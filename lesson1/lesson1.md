#ionic学习笔记 (ionicframe中文版教程)
##ionic安装
  
>安装依赖npm，需要先安装 nodejs [戳这里下载Node.js](http://nodejs.org/) 。  
>安装完成后，在终端输入 `node -v` 有版本号输出就是安装成功了，一直搞到成功为止哦，网上看其他教程。 

+ 全局安装ionic工具和cordova。  
	<pre>npm install -g cordova ionic </pre>
+ 创建第一个非空白的项目,并启动。（创建空白的后面怎么玩。。。）
  	<pre>
  	ionic start myApp tabs
  	cd myApp/
  	ionic serve
  	</pre>
 完工后，会自动打开浏览器 http://localhost:8100，如果你选择了localhost的话。
 下面代码是一些其他的项目创建方式。
 	<pre>
  	ionic start myApp blank //空白项目
  	ionic start myApp sidemenu //滑动导航项目
  	</pre>

>ps：因为墙的问题，npm安装过程中可能会失败，需要切换下npm源。
<pre>
npm config set registry https://registry.npm.taobao.org 
npm info underscore （如果上面配置正确这个命令会有字符串response）
</pre>
>ps：同样因为墙的问题，你可能会有`org.apache.cordova.device`安装失败问题，`cordova plugin add org.apache.cordova.device`执行后一直等待之类的问题，其实就是被墙。
>
>你可以在[github](https://github.com)上搜索相关关键字   
> `org.apache.cordova.device`换成`cordova-plugin-device`类似的方式搜索找到git地址，终端执行`cordova plugin add https://github.com/apache/cordova-plugin-device.git`一样可以安装(github都被墙的话，自己想办法。。)  
> 
>新增其他插件也是这种方式 [戳这查看ngcordova63＋插件](http://ngcordova.com)
	

+ 项目自动化，安装gulp （其实前面已经自动化啦，下面这个可以装上sass）
  	<pre>
  	npm install gulp －g //全局安装gulp
  	//在项目目录里执行
  	npm install //安装package.json中的依赖文件
  	</pre>
  	
>如果你习惯于用sass来写css，这时候可以在终端执行`ionic setup sass`将开启sass功能。    
>在目录`www/lib/ionic/scss`下`_platform.scss`用于iOS全屏处理，`_variables.scss`参数定义，比如头部高度要多，字体大小等等。可以自己看一下，学习下。


+ 环境安装       
 
>造iOS app的mac先安装xcode。造android app的么，洗洗睡吧，反正卡，学起来都没劲了。

	装完xcode后
  	npm install ios-sim －g 
  	npm install ios-deploy －g
>应该没有缺的了，都装好了。

	在项目目录执行
	ionic platform add ios //添加iOS
	ionic build ios //构建
	ionic emulate ios //运行xcode里面那个模拟器。能跑啦。
>到这里应该可以把`ionic`自带的`tabs demo`在模拟器里面跑起来了。
  
  
  
  