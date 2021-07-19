参考：https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html

## 一、Flex 布局是什么？

Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。

任何一个容器都可以指定为 Flex 布局。



```
.box{
  display: flex;
}
```



行内元素也可以使用 Flex 布局。



```
.box{
  display: inline-flex;
}
```



Webkit 内核的浏览器，必须加上-webkit前缀。

注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。

## 二、基本概念

采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。

![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557300467455-07f60190-3503-409d-9147-36ea501e3d36.png)



容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

## 三、容器的属性

以下6个属性设置在容器上。

- flex-direction
- flex-wrap

- flex-flow
- justify-content

- align-items
- align-content

### flex-direction

flex-direction属性决定主轴的方向（即项目的排列方向）。



```
flex-direction: row | row-reverse | column | column-reverse
```



![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557301022937-74f5eea0-62ae-483f-9c14-0685c87fa3b4.png)

它可能有4个值。

- row：横向从左到右排列（左对齐），默认的排列方式。
- row-reverse：反转横向排列（右对齐，从后往前排，最后一项排在最前面。

- column：纵向排列。
- column-reverse：反转纵向排列，从后往前排，最后一项排在最上面。

### flex-wrap

设置或检索伸缩盒对象的子元素超出父容器时是否换行。



![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302103850-ee222d9b-fb23-49ff-b399-d0a530d3ec78.png)



```
flex-wrap: nowrap | wrap | wrap-reverse
```



- nowrap：当子元素溢出父容器时不换行。
- wrap：当子元素溢出父容器时自动换行。

- wrap-reverse：反转 wrap 排列。



（1）nowrap（默认）：不换行。

![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302230069-745f69ae-4418-4f5c-84e4-d5470740bcea.png)



（2）wrap：换行，第一行在上方。

![img](https://cdn.nlark.com/yuque/0/2019/jpeg/271745/1557302264444-8544fbde-97ea-4c34-bc1f-8f1993f6fd18.jpeg)



（3）wrap-reverse：换行，第一行在下方。

![img](https://cdn.nlark.com/yuque/0/2019/jpeg/271745/1557302283246-7f8a1517-e3df-40b8-b832-41fbf53d7855.jpeg)



### flex-flow 

复合属性。设置或检索伸缩盒对象的子元素排列方式。



```
flex-flow: <‘flex-direction’> || <‘flex-wrap’>
```



- [ flex-direction ]：定义弹性盒子元素的排列方向。
- [ flex-wrap ]：定义弹性盒子元素溢出父容器时是否换行。

### justify-content

设置或检索弹性盒子元素在主轴（横轴）方向上的对齐方式。



当弹性盒里一行上的所有子元素都不能伸缩或已经达到其最大值时，这一属性可协助对多余的空间进行分配。当元素溢出某行时，这一属性同样会在对齐上进行控制。



- flex-start：弹性盒子元素将向行起始位置对齐。该行的第一个子元素的主起始位置的边界将与该行的主起始位置的边界对齐，同时所有后续的伸缩盒项目与其前一个项目对齐。
- flex-end：弹性盒子元素将向行结束位置对齐。该行的第一个子元素的主结束位置的边界将与该行的主结束位置的边界对齐，同时所有后续的伸缩盒项目与其前一个项目对齐。

- center：弹性盒子元素将向行中间位置对齐。该行的子元素将相互对齐并在行中居中对齐，同时第一个元素与行的主起始位置的边距等同与最后一个元素与行的主结束位置的边距（如果剩余空间是负数，则保持两端相等长度的溢出）。
- space-between：弹性盒子元素会平均地分布在行里。如果最左边的剩余空间是负数，或该行只有一个子元素，则该值等效于'flex-start'。在其它情况下，第一个元素的边界与行的主起始位置的边界对齐，同时最后一个元素的边界与行的主结束位置的边距对齐，而剩余的伸缩盒项目则平均分布，并确保两两之间的空白空间相等。

- space-around：弹性盒子元素会平均地分布在行里，两端保留子元素与子元素之间间距大小的一半。如果最左边的剩余空间是负数，或该行只有一个伸缩盒项目，则该值等效于'center'。在其它情况下，伸缩盒项目则平均分布，并确保两两之间的空白空间相等，同时第一个元素前的空间以及最后一个元素后的空间为其他空白空间的一半。



![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302455838-e55e0325-daba-4859-80ee-c726c2a1bd5f.png)



### align-items

设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式。



```
align-items: flex-start | flex-end | center | baseline | stretch
```



- flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴（纵轴）起始边界。
- flex-end：弹性盒子元素的侧轴（纵轴）结束位置的边界紧靠住父容器的侧轴结束边界。

- center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
- baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。

- stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。



![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302558513-5836e83c-5cd0-440d-9eea-5f9eb4519846.png)



### align-content

设置或检索弹性盒堆叠伸缩行的对齐方式。如果项目只有一根轴线，该属性不起作用。



```
align-content: flex-start | flex-end | center | space-between | space-around | stretch
```



- flex-start：各行向弹性盒容器的起始位置堆叠。弹性盒容器中第一行的侧轴起始边界紧靠住该弹性盒容器的侧轴起始边界，之后的每一行都紧靠住前面一行。
- flex-end：各行向弹性盒容器的结束位置堆叠。弹性盒容器中最后一行的侧轴起结束界紧靠住该弹性盒容器的侧轴结束边界，之后的每一行都紧靠住前面一行。

- center：各行向弹性盒容器的中间位置堆叠。各行两两紧靠住同时在弹性盒容器中居中对齐，保持弹性盒容器的侧轴起始内容边界和第一行之间的距离与该容器的侧轴结束内容边界与第最后一行之间的距离相等。（如果剩下的空间是负数，则各行会向两个方向溢出的相等距离。）
- space-between：各行在弹性盒容器中平均分布。如果剩余的空间是负数或弹性盒容器中只有一行，该值等效于'flex-start'。在其它情况下，第一行的侧轴起始边界紧靠住弹性盒容器的侧轴起始内容边界，最后一行的侧轴结束边界紧靠住弹性盒容器的侧轴结束内容边界，剩余的行则按一定方式在弹性盒窗口中排列，以保持两两之间的空间相等。

- space-around：各行在弹性盒容器中平均分布，两端保留子元素与子元素之间间距大小的一半。如果剩余的空间是负数或弹性盒容器中只有一行，该值等效于'center'。在其它情况下，各行会按一定方式在弹性盒容器中排列，以保持两两之间的空间相等，同时第一行前面及最后一行后面的空间是其他空间的一半。
- stretch：各行将会伸展以占用剩余的空间。如果剩余的空间是负数，该值等效于'flex-start'。在其它情况下，剩余空间被所有行平分，以扩大它们的侧轴尺寸。



![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302664334-da455489-6379-44a0-a853-17fec569a0e0.png)



## 四、项目的属性

以下6个属性设置在项目上。

- order
- flex-grow

- flex-shrink
- flex-basis

- flex
- align-self

### order属性

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。



```
order: <integer>
```



<integer>：用整数值来定义排列顺序，数值小的排在前面。可以为负值。

![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557302889632-de3a4473-4a10-44e6-90e5-16d22146fb94.png)



### flex-grow

设置或检索弹性盒的扩展比率。根据弹性盒子元素所设置的扩展因子作为比率来分配剩余空间。



```
flex-grow: <number> (default 0)
```



- <number>：用数值来定义扩展比率。不允许负值
- flex-grow的默认值为0，如果没有显示定义该属性，是不会拥有分配剩余空间权利的。

- 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557303019111-91a97dd5-f56e-4c0d-9766-2865875e337a.png)

### flex-shrink

设置或检索弹性盒的收缩比率（根据弹性盒子元素所设置的收缩因子作为比率来收缩空间。），默认为1，即如果空间不足，该项目将缩小。



```
flex-shrink: <number> (default 1)
```



![img](https://cdn.nlark.com/yuque/0/2019/jpeg/271745/1557303166235-8895e0df-5d7a-4279-9e8b-cd3c7197a9e9.jpeg)

### 

### flex-basis

flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。



```
flex-basis: <length> | auto; /* default auto */
```



- auto：无特定宽度值，取决于其它属性值
- <length>：用长度值来定义宽度。不允许负值

- <percentage>：用百分比来定义宽度。不允许负值

它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

### flex

flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。



```
flex：none | [ flex-grow ] || [ flex-shrink ] || [ flex-basis ]
```



- none：none关键字的计算值为: 0 0 auto
- [ flex-grow ]：定义弹性盒子元素的扩展比率。

- [ flex-shrink ]：定义弹性盒子元素的收缩比率。
- [ flex-basis ]：定义弹性盒子元素的默认基准值。

### align-self

设置或检索弹性盒子元素自身在侧轴（纵轴）方向上的对齐方式。



```
align-self: auto | flex-start | flex-end | center | baseline | stretch
```



- auto：如果'align-self'的值为'auto'，则其计算值为元素的父元素的'align-items'值，如果其没有父元素，则计算值为'stretch'。
- flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。

- flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
- center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。

- baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
- stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。

![img](https://cdn.nlark.com/yuque/0/2019/png/271745/1557305343101-98175c67-477d-4520-9c2a-b6cc07d26da6.png)

## 五、演示站

http://zydown.99.com/peixun/flexbox/