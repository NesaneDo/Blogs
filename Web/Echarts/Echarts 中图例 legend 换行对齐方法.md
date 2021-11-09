# Echarts 中图例 legend 换行对齐方法

使用 **Echarts** 组件作图表时，有时在遇到有多个图例的情况，一行显示不完，则换行显示，但是为了美观，需要进行对齐，可以使用以下方法：

```javascript
option.legend ={
	orient:'horizontal',
	bottom: 8,
	icon:'rect',
	width:'60%',
	formatter:['{a|{name}}\t\t'].join('\n'), // \t 制表符
	textStyle:{
		rich:{
			a:{
                width:120 // 具体根据图例文字长度设置
            }
		}
	},
	itemHeight:4,
	itemWidth:72,
    data:// your legend data
}
```

其中重要的地方就是 **`formatter`** 和 **`textStyle`**。官方文档中说道：

> 注意：如果不定义 `rich`，不能指定文字块的 `width` 和 `height`



**效果图：**

![image-20211109170443708](https://nesanedo.github.io/pics_bed_static/img/picbed/blog/echarts_legend_align/1.png)

