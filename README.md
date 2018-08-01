#TBcart
###1. 功能描述
主要是练习H5C3属性，利用Fullpage插件实现全屏滚动功能，模仿淘宝购物车活动宣传页。
###2. FullPage插件介绍
- 插件功能介绍
    + 基于 jQuery 的插件，它能够帮你很方便、很轻松的制作出全屏网站。
    + 支持鼠标滚动，支持前进后退和键盘控制，多个回调函数，
      支持手机、平板触摸事件，支持 CSS3 动画，支持窗口缩放，窗口缩放时自动调整，
      可设置滚动宽度、背景颜色、滚动速度、循环选项、回调、文本对齐方式等等。
    + 参考文档：http://www.dowebok.com/demo/2014/77/
    + 原理：window.onmousewheel = function(){ console.log('ok') };
- 使用步骤
    + 引用文件
    ```html
        <link rel="stylesheet" href="css/jquery.fullPage.css">
        <script src="js/jquery.min.js"></script>
        <script src="js/jquery.fullPage.js"></script>
    ```
    + html结构
    ```html
       <div id="fullpage">
          <div class="section">第一屏</div>
          <div class="section">第二屏</div>
          <div class="section">
            <div class="slide">第三屏的第一屏</div>
            <div class="slide">第三屏的第二屏</div>
            <div class="slide">第三屏的第三屏</div>
            <div class="slide">第三屏的第四屏</div>
          </div>
          <div class="section">第四屏</div>
       </div>
    ```
    + js初始化
    ```javascript
       $(function(){
           $('#fullpage').fullpage();
       });
    ```
-  配置选项
   + verticalCentered	字符串	true	内容是否垂直居中
   + resize	布尔值	false	字体是否随着窗口缩放而缩放
   + slidesColor	函数	无	设置背景颜色
   + anchors	数组	无	定义锚链接
   + scrollingSpeed	整数	700	滚动速度，单位为毫秒
   + easing	字符串	easeInQuart	滚动动画方式
   + menu	布尔值	false	绑定菜单，设定的相关属性与 anchors 的值对应后，菜单可以控制滚动
   + navigation	布尔值	false	是否显示项目导航
   + navigationPosition	字符串	right	项目导航的位置，可选 left 或 right
   + navigationColor	字符串	#000	项目导航的颜色
   + navigationTooltips	数组	空	项目导航的 tip
   + slidesNavigation	布尔值	false	是否显示左右滑块的项目导航
   + slidesNavPosition	字符串	bottom	左右滑块的项目导航的位置，可选 top 或 bottom
   + controlArrowColor	字符串	#fff	左右滑块的箭头的背景颜色
   + loopBottom	布尔值	false	滚动到最底部后是否滚回顶部
   + loopTop	布尔值	false	滚动到最顶部后是否滚底部　
   + loopHorizontal	布尔值	true	左右滑块是否循环滑动　
   + autoScrolling	布尔值	true	是否使用插件的滚动方式，如果选择 false，则会出现浏览器自带的滚动条
   + scrollOverflow	布尔值	false	内容超过满屏后是否显示滚动条
   + css3	布尔值	false	是否使用 CSS3 transforms 滚动
   + paddingTop	字符串	0	与顶部的距离
   + paddingBottom	字符串	0	与底部距离
   + fixedElements	字符串	无	
   + normalScrollElements		无	
   + keyboardScrolling	布尔值	true	是否使用键盘方向键导航
   + touchSensitivity	整数	5	
   + continuousVertical	布尔值	false	是否循环滚动，与 loopTop 及 loopBottom 不兼容
   + animateAnchor	布尔值	true	
   + normalScrollElementTouchThreshold	整数	5	

###3.在这次练习中遇到的问题和学到的东西
#####1.在屏幕中可以设置一个内容容器，这样定位会更加方便
```css
   .content {
    width: 900px;
    height: 600px;
    background: rgba(0, 0, 0, 0.1);
    position: absolute;
    bottom: 0;
    left: 50%;
    margin-left: -450px;
   }
```
#####2.使用transform的时候会提高层级
```css
   left:50%
   transform: translateX(-50%);
```
#####3. z-index必须和position一起用
#####4.transition和animation同时操作一个东西的时候不会生效
#####5.使用位移动画的时候要使用块级元素
#####6.定位最好不用top，用bottom是为了防止屏幕分辨率比较大的情况
#####7.第五屏鼠标线超出的问题
- 把内容容器高度设置为100%然后设置鼠标overflow: hidden;
#####8.第六屏背景图的百分比的问题
- 背景图的百分比不是按照容器的大小换算的。百分比的背景定位：基于容器的宽度-背景的宽度。公式：背景X的定位=（容器的宽-背景的宽）*百分比。 还有移动的时候图片超出的问题可以设置为100%就正好了。
