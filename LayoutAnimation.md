#为ListView 的item 添加动画效果

	LayoutAnimationController 
	用于为一个layout 布局或ViewGroup 里面的控件设置动画

	有两种方法：
	1.在XML文件中设置
	2.在Java代码中设置

***

#在XML文件中设置



>####1. 在res/anim 文件夹下新建anim_item.xml 文件

	<?xml version="1.0" encoding="utf-8"?>
	<set xmlns:android="http://schemas.android.com/apk/res/android" 
		 android:fillAfter="true">

    	<translate 
 			android:fromXDelta="0"
    	    android:toXDelta="0"
   			android:fromYDelta="-100%"
    	    android:toYDelta="0"
    	    android:duration="388"/>
	   <alpha 
  	       android:fromAlpha="0.1"
   	       android:toAlpha="1"
   	       android:duration="238"/>
	</set>

>####2. 在res/anim 文件夹下新建anim_layout.xml 文件


	<layoutAnimation 
		xmlns:android="http://schemas.android.com/apk/res/android" 
		android:delay="30%"  
    	android:animationOrder="normal"  
    	android:animation="@anim/anim_item" />  

	属性说明：

	android:delay   
	子元素的动画时间间隔（单位为秒），写作“30%”或“0.3f”，表示0.3秒

	android:animationOrder
	子元素的显示方式，有以下几种可选值：
	normal	0	  默认
	reverse	1	  倒序
	random	2	  随机

	android:animation
	子元素要显示的具体动画，也就是在第1步创建的动画文件

>####3. 在主布局文件中为控件配置如下属性：

	android:layoutAnimation="@anim/anim_layout"


***

#在Java代码中设置

1． 创建**anim_item.xml** 文件，与上一种方法相同

2． 在Java 文件中添加如下代码：
       
	Animation anim = 
			AnimationUtils.loadAnimation(context, R.anim.anim_item);

    LayoutAnimationController lac = new LayoutAnimationController(anim);

    lac.setDelay(0.3f);
    lac.setOrder(LayoutAnimationController.ORDER_NORMAL);

    listView.setLayoutAnimation(lac);

	参数说明：第一句中的context 为上下文对象，视具体情况而定

