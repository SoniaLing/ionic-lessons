#ionic学习笔记 (ionicframe中文版教程)

##ionic 开发过程中遇到的一些疑问

   	内容笼统，问答有点随心所欲。
   
1.第一次执行了`ionic serve`时选择了`localhost `之后怎么切换到本机ip？ 

>	先退出，再执行`ionic address `会出现ip选择，选择后再执行`ionic serve`。       

2.在android下，tabs出现在页面顶端。官网的demo都是这样。
>	首先这个不是bug，这是android本身的特性。我们可以通过配置$ionicConfigProvider将tabs放在页面底端  

	$ionicConfigProvider.navBar.alignTitle("center");//iOS android 标题居中显示
  	$ionicConfigProvider.tabs.position("bottom");//tabs底端显示
>其他更多的android/iOS特性在`ionic.bundle.js`中查找`$ionicConfig`,能发现其他的比如转场动画，顶部返回按钮，checkbox圆的还是方的等。

3.[ionic api官方文档](http://ionicframework.com/docs/api/) 打开很慢，左侧的导航无法展开（或许你都没想过那是可以展开的）
>一方面原因么，它在大洋对岸。另一方原因么，ionic官网引用的jquery是google的库，结果你懂的。   
>推荐个插件`gooreplacer`，`gooreplacer`在你打开网页时，检测是否引用了google fonts/apis/themes这些墙外的东西，如果有，进行重定向，重定向到科大为google提供的国内替换库。
>[戳这里安装chrome插件](https://github.com/jiacai2050/gooreplacer4chrome#install)  仔细看安装教程哦，确保你安装成功了，不然还是没用的。  
>不行就买个vpn

4.列表页有tabs，内容页不需要。（隐藏tabs的方式）
>解决方案一

[戳这里看](http://forum.ionicframework.com/t/how-to-hide-the-ion-tabs-in-specified-page/14208/2) ps:官方团队给的评价是`Nice solution`

>解决方案二

	1.tabs 增加ng-class
	<ion-tabs ng-class="{'tabs-item-hide': $root.hideTabs}">tabs</ion-tabs>
	
	2.增加一个hideTabs 指令
	var module = angular.module('app.directives', []);
	module.directive('hideTabs', function($rootScope) {
		    return {
		        restrict: 'A',
		        link: function(scope, element, attributes) {
		            scope.$watch(attributes.hideTabs, function(value){
		                $rootScope.hideTabs = value;
		            });

		            scope.$on('$destroy', function() {
		                $rootScope.hideTabs = false;
		            });
		        }
		    };
	});
	
	3.内容页面加入指令 hide-tabs=true
	<ion-view  hide-tabs=true><!-- view content --></ion-tabs>
	//方式有很多种，其实都不是很完美，会明显少一块的感觉。
	

	
5.ion-view 上使用了 hide-nav-bar="true" 切换视图的时候，会有margintTop负值／抖动现象。
>假设view1 转入 view2，view2上有hide-nav-bar="true"。    
>view1 中`ion-content`需要一个top值 `$bar-height`。框架在切换视图时，如果第二个视图无header，直接在顶上加上了`hide`，暴力啊。 版本`v1.0.0-rc.4 `如此，它更新的那么勤快，其他版本么看。

