# NavigationView 中设置 headerLayout 中 TextView 的控件

`NavigationView` 中的 `headerLayout` 中的控件无法直接获取，通过 `inflate` 也不行。

比如 `headerLayout` 中的 `TextView`，如果直接通过 `fidViewById` 获取会直接报 `NPE（空指针异常）`,如果通过 布局引入器 ，如 `View.inflate` 或者 `LayoutInflate.from` 的方式去获取此 `TextView`, 能够正常获取到，但是无法给此 `TextView` 使用 `setText()`，没有效果。

>解决办法：

先获取到  `NavigationView`，然后通过 `NavigationView` 的 `getHeaderView(0)` 的方法去获取到 `header` 布局，然后通过获取到的 `header` 布局去获取 `TextView`