# 自定义滚动条 纯CSS

```css
.c-scroll {
    overflow: auto;
}

.c-scroll::-webkit-scrollbar {
	width: 4px;
    height: 4px;
}

/*鼠标悬浮在该类指向的控件上时滑块的样式*/
.c-scroll:hover::-webkit-scrollbar-thumb {
    background-color: rgba(0, 244, 252, 0.2);
    border-radius: 10px;
    -webkit-box-shadow: inset 1px 1px 0 rgba(0, 0, 0, .1);
}

/*鼠标悬浮在滑块上时滑块的样式*/
.c-scroll::-webkit-scrollbar-thumb:hover {
    background-color: rgba(0, 244, 252, 0.4);
    -webkit-box-shadow: inset 1px 1px 0 rgba(0, 0, 0, .1);
}

/*正常时候的主干部分*/
.c-scroll::-webkit-scrollbar-track {
    border-radius: 10px;
    -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0);
    background-color: rgba(255, 255, 255, 0.16);
}

/*鼠标悬浮在滚动条上的主干部分*/
.c-scroll::-webkit-scrollbar-track:hover {
    -webkit-box-shadow: inset 0 0 6px rgba(0, 244, 252, 0.4);
    background-color: rgba(0, 0, 0, .01);
}
```

**使用方式：**

在需要滚动的元素上添加样式 **`c-scroll`**