# arcGIS 不使用 jdk 8 错误

arcGIS 文档上说了需要使用 **`java8`**

```java
compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}
```

否则会报如下错误：

```java
java.lang.RuntimeException: Unable to start activity ComponentInfo{com.lz.weather/com.lz.weather.MainActivity}: android.view.InflateException: Binary XML file line #7 in com.lz.weather:layout/activity_main: Binary XML file line #7 in com.lz.weather:layout/activity_main: Error inflating class com.esri.arcgisruntime.mapping.view.MapView
```







```java

```