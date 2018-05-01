* line-height 详细作用
* 布局的细粒度
span 作为行内元素，为什么可以设置height, 再回顾一下 高度，浮动相关的东西
高度宽度 在什么时候该设置 什么时候自动
块级的宽是会沾满全部的

行级 ，宽高是line-height 顶起来的
块级，高是顶起来的，宽是默认顶满父元素
浮动后 ，都变成inline-block
脱离文档流，即 别的元素的定位 都不考虑它，也不再在父元素中占据位置,且 宽高 变成了内容顶起来的 

问题分析：
描述："数码城" 三个字，在font-size设置为14px之后，就会使得 外围的li变成36px高，但是line-height是35px,
或者设置block 可以变35， 
line-height 和font-size的关系，行级元素的高怎么计算
结论：
当结构如：
<div><a>sss</a></div>的块级包围行级的结构，那么如果设置了行级font-size 大于某个值（14，15），那么即使块级设置了line-height为0 
也会把父块高度顶 N px, 而如果单独一个block,里面就是文字，不是行级元素，那么按照这种方式不会被顶高, 
但是具体的原因，并不知道是为什么

切透明图的方法，打开一个背景为透明的新建，然后把图片放进来选择png,色板选透明，导出之后看起来小图片是带白色背景的，实际是透明的

行内元素盒模型同样有效，但是margin padding top和bottom 无效

line-height: 指的是两行文字 基线到基线的高度，也可以指的是一个 line-box的高，line-box指的是一行的box的高，取决于这一行的最大line-height,
line-box是一个 如果是中文 那么沿着文字水平中分线 上下相等的范围， 如果是英文，那么按照按照拼音线来的范围，两行的line-box，就是那四条线拼在一起

关于 为什么字母 不自动换行：
word-wrap : normal | break-word
参数： normal :  允许内容顶开指定的容器边界break-word :  内容将在边界内换行。如果需要，词内换行（word-break）也行发生

关于line-block ,如果一个line-block 有innertext 并height小于 line-height 那么 ，块顶着父元素的顶线，而如果没有innertext，
那么inline-block 就在line-height的高度范围内居中，

inline-block 会被 父级的tetx-aling影响，被整个居住，所以它其实还是有行级元素的性质的

浮动的元素，挤开了文本和图片，即使设置了img为block,也别想和浮动 的元素重合，
且因为脱离了文本流，所以 挤开的文本，图片，


绝对定位，如果 父元素没有定位，默认的static也是没有定位，那么，就会相对原始元素定位。

问题在于 ,浮动可以影响block inline 内的文字产生浮动影响,但是 浮动并不能影响,inline-block内的文字,  A:这是因为inline-block产生了BFC,
所以没有被浮动产生环绕.

inline-block ,如果 没有内部文字,但是却有height, 那么,基线存在在height的底部, 

块级内部的line-box 是所有inline-box的累加 ,能包住所有的 行高就行,没有要求是最大的inline-box的行高

用inline-block 代替float 的可能性, 问题: inline-block的间隙, vertical-align 的对其影响 ,
用inline-block的横向布局 会产生麻烦的对其问题,需要使用vertical-align来解决,或者overflow:hidden 可以神奇的让他基线变成块的底线

font-size=0 ,或者在写html的时候 可以消除 inline-block之间的间隙

感觉css的布局方式 ,怪怪的, 相对cs的布局方式

em是相对父块 font-size 大小,font-size可以为0 ,


子元素的行高可以影响父元素的行高?