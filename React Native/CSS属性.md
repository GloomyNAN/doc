---
title:  ReaceNativeCSS属性
date: 2018-05-18 15:39:22
tags:
---

## View Style

支持Flexbox、ShadowPropTypesIOS、Transforms属性。

背面可见性

```
backfaceVisibility enum('visible', 'hidden')
```

背景颜色

```
backgroundColor string
```

边框颜色

```
borderColor string
borderTopColor string
borderRightColor string
borderBottomColor string
borderLeftColor string
```

边框圆角半径

```
borderRadius number
borderTopLeftRadius number
borderTopRightRadius number
borderBottomLeftRadius number
borderBottomRightRadius number
```

边框样式

```
borderStyle enum('solid', 'dotted', 'dashed')
```

边框宽度

```
borderWidth number
borderTopWidth number
borderRightWidth number
borderBottomWidth number
borderLeftWidth number
```

不透明度

```
opacity number
```

填充

```
overflow enum('visible', 'hidden')
```

测试ID（用来定位视图）

```
testID string
```

##Image Style

支持Flexbox和Transforms

调整大小模式

```
resizeMode Object.keys(ImageResizeMode)
```

背景颜色

```
backgroundColor string
```

边框属性

```
borderColor string
borderWidth number
borderRadius number
```

填充

```
overflow enum('visible', 'hidden')
```

色彩颜色

```
tintColor string
```

不透明度

```
opacity number
```

##Text Style

支持View的样式

字体颜色

```
color string
```

字体

```
fontFamily string
```

字体大小

```
fontSize number
```

字体样式

```
fontStyle enum('normal', 'italic')
```

字体粗细（指定字体的粗细。大多数字体都支持’normal’和’bold’值。并非所有字体都支持所有的数字值。如果某个值不支持，则会自动选择最接近的值。）

```
fontWeight enum("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
```

字间距

```
letterSpacing number
```

行间距

```
lineHeight number
```

字体对齐方式（指定文本的对齐方式。其中’justify’值仅iOS支持。）

```
textAlign enum("auto", 'left', 'right', 'center', 'justify')
```

##Flexbox Style

宽高

```
width number
height number
```

项目对齐


```
alignItems enum('flex-start', 'flex-end', 'center', 'stretch')
```

自身对齐

```
alignSelf enum('auto', 'flex-start', 'flex-end', 'center', 'stretch')
```

边框宽度

```
borderBottomWidth number
borderLeftWidth number
borderRightWidth number
borderTopWidth number
borderWidth number
```

弹性伸缩

```
flex number
```

弹性伸缩方向

```
flexDirection enum('row', 'column')
```

弹性伸缩包裹

```
flexWrap enum('wrap', 'nowrap')
```

证明内容

```
justifyContent enum('flex-start', 'flex-end', 'center', 'space-between', 'space-around')
```

外边距

```
margin number
marginBottom number
marginLeft number
marginRight number
marginTop number
marginHorizontal number
marginVertical number
```

内边距

```
padding number
paddingBottom number
paddingLeft number
paddingRight number
paddingTop number
paddingHorizontal number
paddingVertical number
```

位置（绝对、相对）

```
position enum('absolute', 'relative')
```

上下左右

```
right number
top number
left number
bottom number
```

##Transform

属性变化

```
transform [{perspective: number}, {rotate: string}, {rotateX: string}, {rotateY: string}, {rotateZ: string}, {scale: number}, {scaleX: number}, {scaleY: number}, {translateX: number}, {translateY: number}, {skewX: string}, {skewY: string}] 
```

属性矩阵

```
transformMatrix TransformMatrixPropType 
```

##阴影


```
shadowColor color
Sets the drop shadow color
shadowOffset {width: number, height: number}
Sets the drop shadow offset
shadowOpacity number
Sets the drop shadow opacity (multiplied by the color's alpha component)
shadowRadius number
Sets the drop shadow blur radius
——— react native official docs

```


Valid style props: [
  "alignItems",
  "alignSelf",
  "backfaceVisibility",
  "backgroundColor",
  "borderBottomColor",
  "borderBottomLeftRadius",
  "borderBottomRightRadius",
  "borderBottomWidth",
  "borderColor",
  "borderLeftColor",
  "borderLeftWidth",
  "borderRadius",
  "borderRightColor",
  "borderRightWidth",
  "borderStyle",
  "borderTopColor",
  "borderTopLeftRadius",
  "borderTopRightRadius",
  "borderTopWidth",
  "borderWidth",
  "bottom",
  "color",
  "elevation",
  "flex",
  "flexDirection",
  "flexWrap",
  "fontFamily",
  "fontSize",
  "fontStyle",
  "fontWeight",
  "height",
  "justifyContent",
  "left",
  "letterSpacing",
  "lineHeight",
  "margin",
  "marginBottom",
  "marginHorizontal",
  "marginLeft",
  "marginRight",
  "marginTop",
  "marginVertical",
  "opacity",
  "overflow",
  "overlayColor",
  "padding",
  "paddingBottom",
  "paddingHorizontal",
  "paddingLeft",
  "paddingRight",
  "paddingTop",
  "paddingVertical",
  "position",
  "resizeMode",
  "right",
  "rotation",
  "scaleX",
  "scaleY",
  "shadowColor",
  "shadowOffset",
  "shadowOpacity",
  "shadowRadius",
  "textAlign",
  "textAlignVertical",
  "textDecorationColor",
  "textDecorationLine",
  "textDecorationStyle",
  "textShadowColor",
  "textShadowOffset",
  "textShadowRadius",
  "tintColor",
  "top",
  "transform",
  "transformMatrix",
  "translateX",
  "translateY",
  "width",
  "writingDirection"]

隐藏元素-only Text

```
#1
<Text style={
    {display: this.state.status ? 'block': 'none'}
}>
</Text>
#2
<View style={[styles.data, this.state.status ? '' : styles.hide]}>
    <View style={styles.dataItem}>
        <Text style={styles.dataText}>指标1：xxxxx</Text>
    </View>
    <View style={styles.dataItem}>
        <Text style={styles.dataText}>指标2：xxxxx</Text>
    </View>
</View>
const styles = {
    data: {
        marginTop: 10,
        borderColor: '#ccc',
        borderTopWidth: onePixel,
        borderRightWidth: onePixel,
    },
    dataItem: {
        borderColor: '#ccc',
        borderLeftWidth: onePixel,
        borderBottomWidth: onePixel,
    },
    dataText: {
        padding: 3,
        fontSize: 12,
        color: '#333',
    },
    hide: {
        opacity: 0,
        height: 0,
        marginTop: 0,
        overflow: 'hidden',
    }
};
```


