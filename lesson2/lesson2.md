#ionic学习笔记 (ionicframe中文版教程)
##ionic js框架之AngularJs指令／路由
### AngularJs指令
>ionic框架中把很多移动端常用的UI封装成了AngularJS的扩展指令。[官方js框架api地址](http://ionicframework.com/docs/api/)		
	
>例如`ion-slide-box`指令》一般app都有的引导页面效果

![实例图](http://ionicframework.com.s3.amazonaws.com/docs/controllers/slideBox.gif)

	<ion-slide-box on-slide-changed="slideHasChanged($index)">
  		<ion-slide>
    		<div class="box blue"></div>
  		</ion-slide>
  		<ion-slide>
    		<div class="box yellow"><h1>YELLOW</h1></div>
 		</ion-slide>
  		<ion-slide>
    		<div class="box pink"><h1>PINK</h1></div>
  		</ion-slide>
	</ion-slide-box>

>部分指令会区分iOS和android，如 `ion-checkbox`指令》checkbox（ps:该指令，iOS对应圆形选择框，android对应方型选择框。[$ionicConfigProvider](http://ionicframework.com/docs/api/provider/$ionicConfigProvider/)配置，可以进行统一圆或者方)

	<ion-checkbox ng-model="isChecked">Checkbox Label</ion-checkbox>

>选项卡指令 `ion-tabs`  这个指令配上不同的class值会出现不同的效果，`tabs-icon-only`仅有图标的选项卡，`tabs-icon-left`图标在左边的选项卡，`tabs-icon-top`图标在顶部的选项卡。
		
		<ion-tabs class="tabs-positive tabs-icon-only">
  			<ion-tab title="Home" icon-on="ion-ios-filing" icon-off="ion-ios-filing-outline">
  			</ion-tab>
  		</ion-tabs>
  		
>侧栏指令 `ion-side-menus`	跟现在iOS版本的qq差不多，指令提供方法，可以左右侧栏。		

>首先明白自己需要一个什么样的功能,然后去api底下找下，每个api都会有实列，有些还带方法。看到这里就要知道，想用ionic来做一个hybird app必须得先明白angularjs。

![实例图](http://ionicframework.com.s3.amazonaws.com/docs/controllers/sidemenu.gif)
### AngularJs路由／ng-route模块
>ionic没有使用AngularJS内置的ng-route模块，而是选择了AngularUI项目的ui-router模块。
ui-router的核心理念是将子视图集合抽象为一个状态机，导航意味着状态的切换。在不同的状态下，ionic渲染对应的子视图（动态加载的HTML片段）就实现了路由导航的功能。说着很复杂的样子，[来戳实例](http://www.oschina.net/translate/angularjs-ui-router-nested-routes)