谈到CSS3特性,就一定不会不谈css的动画,下面就通过简单的方式总结一下自己在css动画方面的理解

首先对于css3的动画(animate)来谈,很大程度css的动画都要依赖css的另外两个属性,一个是变形(transform),一个则是过渡(transtion),很多人在学习的过程中都会对这三个概念产生疑惑,分不清都是干嘛用到,这里先简单说一下。

# translate变形
**2D的translate属性**

方法|描述
---|:--
matrix(n,n,n,n,n,n)|定义 2D 转换，使用六个值的矩阵。
translate(x,y)|定义 2D 转换，沿着 X 和 Y 轴移动元素。
translateX(n)|定义 2D 转换，沿着 X 轴移动元素。
translateY(n)|定义 2D 转换，沿着 Y 轴移动元素。
scale(x,y)|定义 2D 缩放转换，改变元素的宽度和高度。
scaleX(n)|定义 2D 缩放转换，改变元素的宽度。
scaleY(n)|定义 2D 缩放转换，改变元素的高度。
rotate(angle)|定义 2D 旋转，在参数中规定角度。
skew(x-angle,y-angle)|定义 2D 倾斜转换，沿着 X 和 Y 轴。
skewX(angle)|定义 2D 倾斜转换，沿着 X 轴。
skewY(angle)|定义 2D 倾斜转换，沿着 Y 轴。


**3D的translate属性**

方法|描述
---|:--
rotateX(angle) |元素围绕其 X 轴以给定的度数进行旋转。
rotateY(angle) |元素围绕其 Y 轴以给定的度数进行旋转。

另外除了2D和3D的translate属性之外还有以下属性

**其它translate属性**

方法|描述
---|:--
transform-origin: x-axis y-axis z-axis|设置旋转元素基于哪个点进行变换
transform-style: flat/preserve-3d|规定如何在 3D 空间中呈现被嵌套的元素
perspective: number/none|定义 3D 元素距视图的距离，以像素计
perspective-origin: x-axis y-axis|定义 3D 元素所基于的 X 轴和 Y 轴
backface-visibility: visible/hidden|定义当元素不面向屏幕时是否可见

上面的表格就是经常用到的translate属性方法和怎么使用这些属性

# transtion过渡
过渡(transtion)对于动画来说也是一个相当重要的概念，动画要实现的好就一定离不开过渡。过渡是元素从一种样式逐渐改变为另一种的效果。

要实现这一点，必须规定两项内容：
- 规定您希望把效果添加到哪个 CSS 属性上
- 规定效果的时长

下面先来看一下transtion的一些属性和含义

方法|描述
---|:--
transition	|简写属性，用于在一个属性中设置四个过渡属性。												|
transition-property: none/all/property|规定应用过渡的 CSS 属性的名称。												|
transition-duration: time|定义过渡效果花费的时间。默认是 0。												|
transition-timing-function	|规定过渡效果的时间曲线。默认是 "ease"。											|
transition-delay: time			|规定过渡效果何时开始。默认是 0。	

#### transition-timing-function的一些描述

方法|描述
---|:--			
linear	|规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
ease	|规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
ease-in	|规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
ease-out	|规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
ease-in-out	|规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
cubic-bezier(n,n,n,n)	|在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。
		
		
![transition-timing-function的曲线图](http://cdn1.w3cplus.com/cdn/farfuture/iEpdD5HOE9exHIfIWCd2bZ0JXYBaB73pEaokX4-8X9U/mtime:1341237812/sites/default/files/transition-timing-function.png)

上面就是translate和transtion的相关内容，下面就到了动画（annimate)属性了。

# animate动画
谈到css的动画，其在日常场景中应用十分广泛，按照分类，也可以把动画分成两类，一种就是逐帧动画，另外一种就是关键帧动画。

那么我们还是先来看看animate的一些相关属性方法和介绍吧。

**animate属性**

属性						|描述			
---|:--		
@keyframes					|规定动画。													
animation					|所有动画属性的简写属性，除了 animation-play-state 属性。	
animation-name				|规定 @keyframes 动画的名称。								
animation-duration: time	|规定动画完成一个周期所花费的秒或毫秒。默认是 0，意味着没有动画效果。		
animation-timing-function	|规定动画的速度曲线。默认是 "ease"。						
animation-delay:time				|规定动画何时开始。默认是 0。								
animation-iteration-count	|规定动画被播放的次数。默认是 1。						
animation-direction: normal/alternate;			|规定动画是否在下一周期逆向地播放。默认是 "normal"。		
animation-play-state: paused/running		|规定动画是否正在运行或暂停。默认是 "running"。				
animation-fill-mode			|规定对象动画时间之外的状态。								
animation-iteration-count: n/infinite|定义动画播放次数的数值，infinite规定动画应该无限次播放

---

先谈谈关键帧动画，这个属性是动画的核心，通过描述一个动画播放时几个比较关键的帧的形态，控制这个动画的行为，最终实现动画效果，下面是代码。

```
@keyframes animateName    //动画的名称
{
0%   {<!-- 0%的形态 -->}
50%  {<!-- 50%的形态 -->}
75%  {<!-- 75%的形态 -->}
100% {<!-- 100%的形态 -->}
}
@keyframes animateName    //动画的名称
{
from {<!-- 相当于0%的形态 -->}
to {<!-- 相当于100%的形态 -->}
}
```

使用@keyframes定义好的动画 animateName就可以在html结构中添加动画了.当然实现添加也很容易,只需要在样式中使用animation-name:animateName即可.


再来说下逐帧动画，又名定格动画，是一种动画技术，其原理即将每帧不同的图像连续播放，从而产生动画效果。
简而言之，实现逐帧动画需要两个条件：
- （1）相关联的不同图像，即动画帧；
- （2）连续播放。

顾名思义，他的实现方法就是通过设置若干张图片，每一张图片设定为一帧，然后再通过（播放）行为把帧连接起来变成动画。

在真实应用场景中,一般会把多张图片压缩成一张雪碧图,然后通过使用不同的background-position来使用。但是仅仅这样是不够的，这种方法实现之后会产生帧数连续拼接的效果出现，而不是一帧一帧出现，这时候就需要step(1,start)来控制每一帧的呈现

```
@-webkit-keyframes run{   
            0%{   
                background-position: 0 0;   
            }   
            20%{   
                background-position: -140px 0;   
            }   
            40%{   
                background-position: -280px 0 ;   
            }   
            60%{   
                background-position: -420px 0 ;   
            }   
            80%{   
                background-position: -560px 0 ;   
            }   
            100%{   
                background-position: 0 0 ;   
            }   
        }   
<!-- 使用 -->
		.Useannimate{
			background:url();
			animate-name:run;
			animation-timing-function:steps(1,start);
		}
	
```

**动画相关属性**

另外动画还有一些其它属性要解释一下

#### animation-fill-mode : none | forwards | backwards | both;
值			|描述
---|:--		|
none		|不改变默认行为。																				|
forwards	|当动画完成后，保持最后一个属性值（在最后一个关键帧中定义）。									|
backwards	|在 animation-delay 所指定的一段时间内，在动画显示之前，应用开始属性值（在第一个关键帧中定义）。|
|both		|向前和向后填充模式都被应用。																	|


下面是我自己写的一个动画库,使用也很简单,下载文件然后在文件中引入,想使用什么方法直接在结构中添加对应的类名即可,修改也很方便,直接即可修改
[模仿Animate.css制作的一个库](https://github.com/JferLao/AnimateCSS/blob/master/animate.less)
