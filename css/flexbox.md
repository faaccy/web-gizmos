# flexbox
# flex容器属性
- ```flex-wrap```:内容超出容器是否换行 wrap(换行第一行在上) nowrap(不换行) wrap-reverse(换行第一行在下)
- ```flex-direction```: row(水平) row-reverse(水平右向左排列) column(垂直) column-revers(垂直下到上)
- ```flex-flow```:(是flex-direction flex-wrap的简写)
```css
.box {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```
- ```justify-content```:flex项目在主轴上的对齐方式
  - ```center```:主轴居中对齐
  - ```flex-start```:主轴左对齐
  - ```flex-end```:主轴右对齐
  - ```space-between```:项目在主轴的两端对齐,中间的间隔相等
  - ```space-around```:项目两边间隔相等，项目与项目之间的间隔是与主轴两边的间隔大一倍
- ```align-items```:项目在交叉轴上的对齐方式
  - ```center```:居中对齐
  - ```flex start```:交叉轴起始位置对齐
  - ```flex end```:交叉轴结束位置对齐
  - ```baseline```:交叉轴flex项目的基准线对齐
  - ```stretch```:交叉轴上伸展（（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度）
- ```align-content```:容器有多行的时候,设置多行与交叉轴的对齐方式，如果容器内只有一行该属性没有效果
    - ```center```:交叉轴中心对齐
    - ```flex-start```:交叉轴起始点对齐
    - ```flex-end```:交叉轴结点对齐
    - ```stretch```:与交叉轴两端对齐，轴线之间的间隔平均分布。
    - ```space-between```:与交叉轴两端对齐，轴线之间的间隔平均分布。
    - ```space-around```:与交叉轴两端对齐，轴线之间的间隔平均分布。
- ```row-gap```:两行之间的间距
- ```column-gap```:两列之间的间距

# flex项目属性
- ```order```:项目在容器中的顺序，默认其出现的顺序，数值越小越靠前可以为负数，默认0
- ```flex-grow```:默认0，项目放大的速率:0代表不出现剩余的空间时不放大,值相对其他项目越大放大的速率越大占用的剩余空间越大。和flex-shrink一样是比例关系 2:1 和 1：0.5一样    
- ```flex-shrink```:默认1，项目缩小的速率,0代表空间不足的时候不缩小,大于0代表缩放的速率大小
- ```flex-basis```:默认auto即本身大小,可以设置px em %代表项目占用固定宽度
- ```flex ```(是flex-grow flex-shrink flex-basis的简写)该属性有两个快捷值：auto (代表1 1 auto) 和 none (代表0 0 auto)。flex:4 代表 4 1 0
- ```align-self```:项目自身在交叉轴上的对齐方式不影响其他项目

# Example
- ### [骰子](../css/example/flexbox/index.html)
- ### [网格布局](../css/example/flexbox/mesh.html)
# flex 与 border-box
看一个例子,
```html
<div class="row">
    <div class="cell cell-1-2">1-2</div>
    <div class="cell cell-1-4">1-4</div>
    <div class="cell cell-1-4">1-4</div>
    <div class="cell cell-1-2">1-2</div>
    <div class="cell cell-1-4">1-4</div>
    <div class="cell cell-1-4">1-4</div>
</div>
```
```css
.row {
    display: -webkit-flex;
    display: flex;
    height: 5vh;
    flex-wrap: wrap;
}

.cell {
    border: 1px solid;
    flex: 1;
    box-sizing: border-box;//更该盒子模型让flex将border属性考虑在内
}

.cell.cell-full {
    flex: 0 0 100%;
}

.cell.cell-1-2 {
    flex: 0 0 50%;
}

.cell.cell-1-4 {
    flex: 0 0 25%;
}
```
当实现一个卡片，你希望卡片或者单元格的宽高与设计稿一样，如果采用默认的盒模型，但是样式包含padding或者border属性，最终卡片大于设计稿的宽高，且flex-wrap属性换行会考虑padding和border宽高如果使用不当会导致意外
这是因为默认的盒模型宽高没有考虑border和padding的宽高，在flex布局中需要将卡片或者单元格的box-sizin：```boreder-box```

# 参考链接 
- [css-tutorial](https://github.com/wangdoc/css-tutorial/blob/master/docs/layout/flexbox.md)
- [MDN-flexbox](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)
- [a-guide-to-flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox)
