## 笔记
### html
#### 标签概述
``` javascript
  <!DOCTYPE html>   <!--  文档类型   告诉浏览器以HTML5的方式解析此文档 -->
```
#### html起手式
! +  Tab
``` html
<!DOCTYPE html>   <!--  声明文档类型 --> 
<html lang="en">  
<head>
        <!--  网页的语言  可以设置为 zh-CH  中国中文 -->
    <meta charset="UTF-8">   <!-- 网页的字符编码 UTF-8包含了全人类的语言 -->
        <meta name="viewport" content="width=device-width, initial-scale=1.0"><!--定义文档视口,防止网页缩放-->
        <meta http-equiv="X-UA-Compatible" content="ie=edge"><!--使用IE最新内核-->
            <title>标题</title>  <!-- 这里写网页的标题 -->
</head>
<body>
    <!-- 网页上所有看得见的元素都放这里 -->
</body>
</html>           
```





### 常用的字符
``` javascript
    <p>
        &lt; 相当于 < <br> 
        &gt;相当于> <br>
        &nbsp; 相当于一个英文空格<br>
        &copy; © 版权符号
    </p>
```
### 改变浏览器默认样式
默认样式就是我们没有写CSS的情况下浏览器会与自己的样式 ,当然样式很丑所以我们需要重构它
``` javascript
* {                  /* 这里参考别人的  没有固定写法,可以自由设置 */
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
*::before,
*::after {
  box-sizing: border-box;
}
a {
  color: inherit;
  text-decoration: none;
}
input,
button {
  font-family: inherit;
}
ol,
ul {
  list-style: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
```
### 元素浮动
    /* 背下下面的浮动代码 想让谁浮动就给他父级元素取名class=“clearfix” 然后对想浮动的元素的样式添加float: left;或者float；right */
``` css
    /* 背下下面的浮动代码 想让谁浮动就给他父级元素取名class=“clearfix” 然后对想浮动的元素的样式添加float: left; */
.clearfix::after{
        content: '';
        display: block;
        clear: both;
}
```
###
####
 
- 块级元素div高度由什么决定？
答案：div（块级元素）高度由其内部文档流元素的高度总和决定。并不定相等。
- 内联元素span的高度由什么决定呢？
答案：如果span内就是一种文字，那么span高度=字体高度*字体建议行高（比如1.4倍字体）
- 文档流是什么？
答案：文档内元素的流动方向。
- 文档流的流动方向都是什么方向的？
答案：内联元素（display:inline）的流动方向从左到右，比如span标签，流动遇到阻碍就换行。
块级元素 比如div（display:block）每一个div站一行从上到下流动。
```
    <span>span1</span><span>span2</span><span>span3</span><span>span4</span><span>span5</span>
    <div>块1</div>
    <div>块2</div>
    <div>块3</div>
    <div>块4</div>
    <div>块5</div>
```
内联元素细节：当内敛元素是一个很长的英文单词，当遇到阻碍的时候不会换行。
如果是汉字就会换行，这是因为英文都是多个字母组成的单词，所以一般不分开。汉字一个字就是一个字或者词分开也可。 如果你想让长的单词遇到阻碍可换行就加一个属性
``` css
word-break:break-all
```
这样一个很长的英文单词会被切分成以IP如同一个个字母遇到阻碍可以换行。
至于其他属性自己可以试试。
如果你是中文网址建议用上面的属性。
- 不该出现的属性

``` css
display:inline-block
```
效果就是让块级元素想内敛元素一样从左到右流动。

这是很不好的，我们知道想让一个元素浮起来，可以用上面的元素浮动，
内容如下
    /* 背下下面的浮动代码 想让谁浮动就给他父级元素取名class=“clearfix” 然后对想浮动的元素的样式添加float: left;或者float；right */
``` css
    /* 背下下面的浮动代码 想让谁浮动就给他父级元素取名class=“clearfix” 然后对想浮动的元素的样式添加float: left; */
.clearfix::after{
        content: '';
        display: block;
        clear: both;
}
```
这就牵扯到伪元素了。
- 什么是伪元素？
答案：就他不是真的元素啊。不懂那么。。。
你看到::before或者::after是不是很懵圈。
``` html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
</head>
<body>
  <div>
    hi
  </div>
  <div>
    ni
  </div>
</body>
</html>
```
``` css
div::before{
  content:"["
}
div::after{
  content:"]"
}
```
你发现在控制台看到的明明是[hi]
下面是
[ni]
但是为什么复制只能复制hi 和 ni 
[]却复制不了 这就是伪类 他不是真的元素 但是可以让你少写一些div元素

- 什么是伪类？

所有表示某种状态
:hover 当鼠标悬停的时候触发
:nth-child(odd) 当子元素的为第奇数个时触发
::nth-child(even)子元素的偶数
都是表示当符合xx条件时才触发

- 脱离文档流
``` css
    /* 脱离文档流 */
    position: fixed;
```
还有绝对定位
子元素
    /* 绝对定位  子元素相对于父元素绝对定位*/
    position: absolute;
父元素
    /* 相对定位 */
    position: relative;

- 最好不要设置宽高 会引发很多bug
- 背景图居中
``` css
    /* 让背景图居中 */
    background-position: center center;
```
- 背景图自适应

``` css
    /* 让背景自适应所在的div 这样我们拖拽窗口会自适应*/
    background-size: cover;
```
- 为何不用width 用max-width？
width不自适应会产生下方的滚动条
``` css
    /* 不用宽度用最大宽度，最大宽度的意思是你最宽不能超过我 好处就是自适应*/
    max-width: 940px;

```
- 如何让一个固定大小的div居中
``` css
    margin-left: auto;
    margin-right: auto;
```
- span（内联元素diplay：inline）不接受给宽 高 赋值？那么怎么给span内的字体设置大小呢？
新手这么干
``` css
.userCard .welcome{
    background: #E6686A;
    color: white;
    width:78px;
    height: 29px;
/* 内敛样式不支持设置宽高上面宽高设置不生效 使用下面 */
    display: inline-block;
    /* 让字体居中 */
    line-height: 29px;
    text-align:center;
}
```
高手这么干
从内向外做
先看下现在字体的大小 如果是37*22 目标字体大小是宽70，那么70-37=33 左右各16.5就可以,高30， 29-22=7 那么上下各3.5px
```
.userCard .welcome{
    background: #E6686A;
    color: white;

    display: inline-block;


}
```
好处就是 我们没有规定字体宽度 字体可以想多长就多长

- 如何用css画一个直角三角形？或者你直接抄把 css tricks shapes 搜
先画梯形然后让上边长度=0就是三角形\
``` html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
</head>
<body>
  <div>
  </div>
</body>
</html>
```
``` css
div{
  border:10px solid red;
  width:10px;
  height:10px;
}

```
 
``` css
div{
  border:10px solid red;
  width:10px;
  height:10px;

  border-top-color:black;
  border-right-color:blue;
  border-left-color:yellow;
}
```
梯形然后让上边长度=0 和高度都是0 得到4个三角形
``` css
div{
  border:10px solid red;
  width:0px;
  height:0px;

  border-top-color:black;
  border-right-color:blue;
  border-left-color:yellow;
}
```
怎么得到一个三角形？你把其他都变透明就行了 你要的你选个颜色
```
div{
  border:10px solid red;
  width:0px;
  height:0px;
  border-top-color:transparent;
  border-right-color:transparent;
  border-left-color:transparent;
}

```
这样你就得到一个红色的等腰直角三角形。
- 怎么直角在左上的直角三角形？
``` css
div{
  border:10px solid red;
  width:0px;
  height:0px;
  border-top-color:black;
  border-right-color:blue;
  border-left-color:yellow;
}

```
我们把黑色的三角形先干掉
``` css
div{
  border:10px solid red;
  width:0px;
  height:0px;
  /* border-top-color:black; */
  border-right-color:blue;
  border-left-color:yellow;
 /*  中心到最上边的距离 */
   border-top-width:0;
}

```
然后让不需要的变透明色
``` css
div{
  border:10px solid transparent;
  width:0px;
  /* div里面没有内容自然为0 可以不写 */
  /* height:0px; */
  /* border-right-color:transparent; */
  border-left-color:yellow;
  border-top-width:0;
}

```
这样就得到一个左上角是直角的三角形（黄色）


- svg颜色设置 他不是div

``` css
fill: white(选一个颜色)
```
 
 - 如何让main跑到banner上面
 ``` css
body>main{
    margin-top: -400px;
}
 ```
 - 内敛元素要居中，需要在父级元素加东西
 ``` css
text-align:center
 ```

### 添加网址loading动画
思路
- 写loading动画的css
```html
<body>
    <div id="siteWelcome" class="site-welcome active">
        <div class="loading"></div>
    </div>
```

```css
.site-welcome{
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #888;
    z-index: 1;
    justify-content: center;
    align-items: center;
}
.site-welcome.active{
    display: flex;
}
.loading{

    width: 200px;
    height: 200px;
    /* border: 1px solid red; */
    position: relative;
}
.loading::before,.loading::after{
    content: '';
    position: absolute;
    width: 0px;
    height: 0px;
    /* border: 1px solid blue; */
    background: black;
    border-radius: 50%;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    animation: s 1.5s linear infinite;
}
.loading::after{
    animation-delay: 0.75s;
}
@keyframes s {
    0%{
        width: 0;
        height: 0;
        opacity: 1;
    }
    100%{
        width: 100px;
        height: 100px;
        opacity: 0;
    }
    
}
```
- 设定定时器3秒展示loading动画 在body内容的最后一行 因为加载到这里所有都加载完成了。
```js
   <script>
        setTimeout(function(){
            siteWelcome.classList.remove('active')

        },3000)
    </script>
    </body>
```

### sticky navbar 黏着的navbar
- 通过js来添加或者移除class来控制
``` js
        window.onscroll = function(){
            if(window.scrollY > 0){
                topNavBar.classList.add('sticky')
            }else{
                topNavBar.classList.remove('sticky')
            }
        }
```
- 写sticky样式
```css
.topNavBar{

  
    /* 所有动画1s内做完 */
    transition: all 1s;
    color: rgba(255, 255, 255, 0.7);
    
}
.sticky{
    background: white;
    padding: 10px 0;
    /* z-index: 1; */
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.25);
    color: black;
}
```
### sliding border from left to right
之前的css是
```css
.topNavBar>.topNavBarInner>nav>ul>li>a:hover{
    /* 当鼠标悬停在a标签上加上下面样式 */
    /* border: 1px solid red; */
    /* 但是好像鼠标悬停会动 那是因为每个a标签左右各加1px大小 解决方法 提前就要border不不就ok 只不过是透明的 当悬停的时候变红 */
    border-bottom: 3px solid #e06567;
}
```
现在推翻我们重新做，用div来做，
因为相对于a标签相对定位所以得+
```css
.topNavBar>.topNavBarInner>nav>ul>li>a{
    position: relative;

}
```
```css
.topNavBar>.topNavBarInner>nav>ul>li>a:hover::after{
    /* 当鼠标悬停在a标签上加上下面样式 */
    position: absolute;
    content: '';
    display: block;
    top: 100%;
    left: 0;
    width: 100%;
    background: #e06567;
    height: 3px;
    animation: menuSlide 0.3s;
}
@keyframes menuSlide {
    0%{width: 0;}
    100%{width: 100%;}
}

```
### auto highlight navbar
简而言之就是navbar高亮的内容对应屏幕中心位置的内容
当然可以用锚点来做，但是因为我们有topNavbar而且背景色不是透明，有一定宽度
所以我们锚点对应的位置需要调整
所以，我们需要通过一些api来调整
```js
        let aTags = document.querySelectorAll('nav > ul > li > a')
        for(let i=0; i<aTags.length;i++){
            aTags[i].onclick =function(x){
                // 阻止默认动作 即浏览器锚点 你点击没有反应
                x.preventDefault()
                // 获取用户点击的a标签
                let a = x.currentTarget
                // 获取a标签的href属性 即 '#siteAbout'
                let href = a.getAttribute('href')
                // 根据href得到元素
                let element = document.querySelector(href)
                //
                let top = element.offsetTop
                window.scrollTo(0, top - 80)
            }
        }  
```
### 点击关于慢慢的跳转到关于
之前我们做动画都可以用css来做，但是这次不行，这次控制滚动条，只能通过
js来做。[例子](https://github.com/Mcguffen/js-animation)

```js
       let aTags = document.querySelectorAll('nav > ul > li > a')
        for(let i=0; i<aTags.length;i++){
            aTags[i].onclick =function(x){
                // 阻止默认动作 即浏览器锚点 你点击没有反应
                x.preventDefault()
                // 获取用户点击的a标签
                let a = x.currentTarget
                // 获取a标签的href属性 即 '#siteAbout'
                let href = a.getAttribute('href')
                // 根据href得到元素
                let element = document.querySelector(href)
                //
                let top = element.offsetTop
                // 让滚动条缓慢移动
                let n = 25 // 一共动多少次
                // 想在500毫秒 0.5秒内动25次
                let duration = 500 / n // 多久动一次你
                // 当前高度也就是在用户点击之前的高度
                let currentTop = window.scrollY
                // 用户点击后想要定位到的高度
                let targetTop = top - 80
                // 每次动的距离是多少
                let distance = (targetTop - currentTop) / n
                let i = 0
                let id = setInterval(() => {
                    if(i === n){
                        window.clearInterval(id)
                        return
                    }
                    i += 1
                    window.scrollTo(0, currentTop + distance * i)

                }, duration);
            }
        } 
```
虽然功能完成了，但是体验很差，就是我们是匀速，没有启停的感觉，还有就是越后点速度越快。
缓动函数就是描述速度和时间的关系 又叫tween 可以让动画更自然。

### 滑动到指定内容topNavbar自动高亮



### auto scroll smoonthly 点击navbar平滑滚动到对应内容

### menu hover出现二级菜单
```html
                    <li class="menuTigger"><a href="#">作品</a>
                        <ul class="subMenu">
                            <li>作品1</li>
                            <li>作品2</li>
                            <li>作品3</li>
                        </ul>
                    </li>
```
```js
        let liTags = document.getElementsByClassName('menuTigger')
        for(let i=0; i<liTags.length;i++){
            liTags[i].onmouseenter =function(x){
                x.currentTarget.classList.add('active')
            }
            liTags[i].onmouseleave = function(x){
                x.currentTarget.classList.remove('active')
            }
        }
```
首先就是通过判断li是否有active来判断是否出现二级菜单和navbar下滑高亮
所以a:hover变成了li.active
```css
.topNavBar>.topNavBarInner>nav>ul>li.active>a::after{···}
.topNavBar>.topNavBarInner>nav>ul>li{

        position: relative;
    }
.topNavBar .subMenu{
    display: none;
    position: absolute;
    right: 0;
    top: 100%;
    background: #EFEFEF;
    color: #3d4451;
}
.topNavBar .subMenu > li{
    white-space: nowrap;
    padding: 5px 10px;
}
.topNavBar li.active >.subMenu{
    display: block;
}
```
给二级菜单添加动画
```css
.topNavBar li.active >.subMenu{
    display: block;
    animation: subMenuSlide 0.3s;
}
@keyframes subMenuSlide {
    0%{margin-right: 100%;}
    100%{margin-right: 0%;}
}
```
给二级菜单加阴影
.topNavBar .subMenu{
    display: none;
    position: absolute;
    right: 0;
    top: 100%;
    background: #EFEFEF;
    color: #3d4451;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}
解决bug：       
```js
 let liTags = document.querySelectorAll('nav > ul > li')
```
替换
```js
        let liTags = document.getElementsByClassName('menuTigger')

```
### auto hide asdie 自动隐藏侧边栏

### gapless slides 无缝轮播

### animate when scroll