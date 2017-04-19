###使用绝对定位和负外边距对块级元素进行垂直居中

html代码：

```html
<div id="box">
    <div id="child">我是测试DIV</div>
</div>
```

css代码：

```css
    #box {
        width: 300px;
        height: 300px;
        background: #ddd;
        position: relative;
    }
    #child {
        width: 100px;
        height: 100px;
        background: orange;
        position: absolute;
        top: 50%;
        left: 50%;
        margin: -50px 0 0 -50px;
        line-height: 100px;
    }
```

运行结果如下：



![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-f8d7b6c6368d4b98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这个方法兼容性不错，但是有一个小缺点：必须提前知道被居中块级元素的尺寸，否则无法准确实现垂直居中。**







###使用绝对定位和transform

html代码：

```html
<div id="box">
    <div id="child">
        我是一串很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长很长的文本
    </div>
</div>
```

css代码：

```css
    #box {
        width: 300px;
        height: 300px;
        background: #ddd;
        position: relative;
    }
    #child {
        background: #93BC49;
        position: absolute;
        top: 50%;
        left: 50%;
        -webkit-transform: translate(-50%,-50%);
        transform: translate(-50%,-50%);
    }
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-661dff9ca7f8ddba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这种方法有一个非常明显的好处就是不必提前知道被居中元素的尺寸了，因为transform中translate偏移的百分比就是相对于元素自身的尺寸而言的。**







###另外一种使用绝对定位和负外边距进行垂直居中的方式

html代码：

```html
<div id="box">
    <div id="child">我也是个测试DIV</div>
</div>
```

css代码：

```css
    #box {
        width: 300px;
        height: 300px;
        background: #ddd;
        position: relative;
    }
    #child {
        width: 50%;
        height: 30%;
        background: pink;
        position: absolute;
        top: 50%;
        margin: -15% 0 0 0;
    }
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-5d59a4405c702677.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这种方式的原理实质上和前两种相同。补充的一点是：margin的取值也可以是百分比，这时这个值规定了该元素基于父元素尺寸的百分比，可以根据实际的使用场景来决定是用具体的数值还是用百分比。**







### 绝对定位结合margin: auto

html代码：

```html
<div id="box">
    <div id="child">我也是个测试DIV</div>
</div>
```

css代码：

```css
    #box {
        width: 300px;
        height: 300px;
        background: #ddd;
        position: relative;
    }
    #child {
        width: 200px;
        height: 100px;
        background: #A1CCFE;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        margin: auto;
        line-height: 100px;
    }
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-7e3b6e994ce6e17d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这种实现方式的两个核心是：把要垂直居中的元素相对于父元素绝对定位，top和bottom设为相等的值，我这里设成了0，当然你也可以设为99999px或者-99999px无论什么，只要两者相等就行，这一步做完之后再将要居中元素的margin设为auto，这样便可以实现垂直居中了。
　　被居中元素的宽高也可以不设置，但不设置的话就必须是图片这种自身就包含尺寸的元素，否则无法实现。**







###使用padding实现子元素的垂直居中

html代码：

```html
<div id="box">
    <div id="child">今天北京的霾严重的吓人，刚看了一眼PM2.5是422</div>
</div>
```

css代码：

```css
    #box {
        width: 300px;
        background: #ddd;
        padding: 100px 0;
    }
    #child {
        width: 200px;
        height: 100px;
        background: #F7A750;
        line-height: 50px;
    }
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-a8803a8c4bf43aa9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这种实现方式非常简单，就是给父元素设置相等的上下内边距，则子元素自然是垂直居中的，当然这时候父元素是不能设置高度的，要让它自动被填充起来，除非设置了一个正好等于上内边距+子元素高度+下内边距的值，否则无法精确的垂直居中。
　　这种方式看似没有什么技术含量，但其实在某些场景下也是非常好用的。**





###设置第三方基准

html代码：

```html


<div id="box">
    <div id="base"></div>
    <div id="child">今天写了第一篇博客，希望可以坚持写下去！</div>
</div>


```

css代码：

```css
#box {
    width: 300px;
    height: 300px;
    background: #ddd;
}
#base {
    height: 50%;
    background: #AF9BD3;
}
#child {
    height: 100px;
    background: rgba(131, 224, 245, 0.6);
    line-height: 50px;
    margin-top: -50px;
}
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-1ba724ef7fdbdca2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**这种方式也非常简单，首先设置一个高度等于父元素高度一半的第三方基准元素，那么此时该基准元素的底边线自然就是父元素纵向上的中分线，做完这些之后再给要垂直居中的元素设置一个margin-top，值的大小是它自身高度的一半取负，则实现垂直居中。**






### 使用flex布局

html代码：

```html
<div id="box">雾霾天气，太久没有打球了</div>
```

css代码：

```css
#box {
    width: 300px;
    height: 300px;
    background: #ddd;
    display: flex;
    align-items: center;
}
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-4c68f5104ea68471.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这种方式同样适用于块级元素：



```html
<div id="box1">
    <div id="child">
        程序员怎么才能保护好眼睛？
    </div>
</div>
```

css代码：

```css
#box1 {
    width: 300px;
    height: 300px;
    background: #ddd;
    display: flex;
    align-items: center;
}
#child {
    width: 300px;
    height: 100px;
    background: #8194AA;
    line-height: 100px;
}
```

运行结果如下：



![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-560051f13488372d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



flex布局（弹性布局/伸缩布局）里门道颇多，这里先针对用到的东西简单说一下，想深入学习的小伙伴可以去看阮一峰老师的博客。（http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html）

　　flex也就是flexible，意为灵活的、柔韧的、易弯曲的。

　　元素可以通过设置display:flex;将其指定为flex布局的容器，指定好了容器之后再为其添加align-items属性，该属性定义项目在交叉轴（这里是纵向轴）上的对齐方式，可能的取值有五个，分别如下：

　　flex-start:：交叉轴的起点对齐；
　　flex-end：交叉轴的终点对齐；

　　center：交叉轴的中点对齐；

　　baseline：项目第一行文字的基线对齐；

　　stretch（该值是默认值）：如果项目没有设置高度或者设为了auto，那么将占满整个容器的高度。






###第二种使用弹性布局的方式

html代码：

```html
<div id="box">
    <div id="child">
        答案当然是多用绿色的背景哈哈
    </div>
</div>
```

css代码：

```css
#box {
    width: 300px;
    height: 300px;
    background: #ddd;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
#child {
    width: 300px;
    height: 100px;
    background: #08BC67;
    line-height: 100px;
}
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-ecbf8b33dce151b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这种方式也是首先给父元素设置display:flex，设置好之后改变主轴的方向flex-direction: column，该属性可能的取值有四个，分别如下：
　　row（该值为默认值）：主轴为水平方向，起点在左端；
　　row-reverse：主轴为水平方向，起点在右端；
　　column：主轴为垂直方向，起点在上沿；
　　column-reverse：主轴为垂直方向，起点在下沿。
　　
　　justify-content属性定义了项目在主轴上的对齐方式，可能的取值有五个，分别如下（不过具体的对齐方式与主轴的方向有关，以下的值都是假设主轴为从左到右的）：
　　flex-start（该值是默认值）：左对齐；
　　flex-end：右对齐；
　　center：居中对齐；
　　space-between：两端对齐，各个项目之间的间隔均相等；
　　space-around：各个项目两侧的间隔相等。








###使用 line-height 对单行文本进行垂直居中

html代码：

```html
<div id="box">
    我是一段测试文本
</div>
```

css代码：

```css
#box{
    width: 300px;
    height: 300px;
    background: #ddd;
    line-height: 300px;
}
```

运行结果如下：



![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-e1937f0a7062cf01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这里有一个小坑需要大家注意：line-height(行高) 的值不能设为100%，我们来看看官方文档中给出的关于line-height取值为百分比时候的描述：基于当前字体尺寸的百分比行间距。所以大家就明白了，这里的百分比并不是相对于父元素尺寸而言，而是相对于字体尺寸来讲的。


###使用 line-height 和 vertical-align 对图片进行垂直居中

html代码：

```html
<div id="box">
    ![](http://upload-images.jianshu.io/upload_images/3877962-0ed295cf93c07f03.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
</div>
```

css代码：

```css
#box{
    width: 300px;
    height: 300px;
    background: #ddd;
    line-height: 300px;
    text-align: center;
}
#box img {
    vertical-align: middle;
}
```

运行结果如下：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-3495ad1afb789c19.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




###使用 display 和 vertical-align 对容器里的文字进行垂直居中

html代码：

```html

<div id="box">
    <div id="child">我也是一段测试文本</div>
</div>
```

css代码：

```css
#box {
    width: 300px;
    height: 300px;
    background: #ddd;
    display: table;
}
#child {
    display: table-cell;
    vertical-align: middle;
}
```

运行结果如下：



![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3877962-a35a2ba0581e22ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



vertical-align属性只对拥有valign特性的html元素起作用，例如表格元素中的<td><th>等等，而像<div><span>这样的元素是不行的。

　　valign属性规定单元格中内容的垂直排列方式，语法：<td valign="value">，value的可能取值有四种：
　　top：对内容进行上对齐
　　middle：对内容进行居中对齐
　　bottom：对内容进行下对齐
　　baseline：基线对齐
 
　　关于baseline值：基线是一条虚构的线。在一行文本中，大多数字母以基线为基准。baseline 值设置行中的所有表格数据都分享相同的基线。该值的效果常常与 bottom 值相同。不过，如果文本的字号各不相同，那么 baseline 的效果会更好。