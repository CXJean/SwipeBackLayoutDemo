# SwipeBackLayoutDemo

使用SwipeBackLayout实现滑动返回上一级页面

先贴一下作者的Github地址:https://github.com/ikew0ng/SwipeBackLayout

先来看效果图:
http://img.blog.csdn.net/20171211185230877?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGNqZWFu/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast

下面来说说使用:
1. 在module的build.gradle添加依赖:
[java] view plain copy
dependencies {  
  ......  
    //SwipeBackActivity左滑关闭  
    compile 'me.imid.swipebacklayout.lib:library:1.1.0'  
}  
2.新建Activity继承SwipeBackActivity
[java] view plain copy
public class DemoActivity extends SwipeBackActivity {  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_demo);  
  
    }  
}  
完了.......，竟然就完了，
对，就完了...
然而在实际使用中，滑动时Activity的背景一片黑，咋解决，easy啦.....
问题1：页面滑动过程中背景黑屏：
1.在res的values文件夹下的styles.xml内:
[java] view plain copy
<!-- 给非首页Activity设置透明） -->  
  <style name="transparent" parent="AppTheme">  
      <item name="android:windowBackground">@color/transparent</item>  
      <item name="android:windowIsTranslucent">true</item>  
      <item name="android:windowNoTitle">true</item>  
      <item name="android:windowAnimationStyle">@android:style/Animation.Translucent</item>  
  </style>  
2.颜色--values文件夹下colors.xml内:
[java] view plain copy
<!--背景改为透明-->  
    <color name="transparent">#03000000</color>  
3.样式写完了，当然得用啊，在AndroidManifest.xml内给继承SwipeBackActivity的Activity添加透明主题，
[java] view plain copy
<activity android:name=".DemoActivity"  
           android:theme="@style/transparent"  
           ></activity>  
完事..............

更多相似的控件:
SwipeBack:https://github.com/liuguangqiang/SwipeBack

向右滑动关闭界面（仿iOS）SlidingClose:https://github.com/wangchenyan/SlidingClose#slidingclose

SwipeBackLayout:https://github.com/gongwen/SwipeBackLayout

参考:
Android 使用SwipeBackLayout实现滑动返回上一级页面——实战来袭

android设置Activity背景色为透明的3种方
