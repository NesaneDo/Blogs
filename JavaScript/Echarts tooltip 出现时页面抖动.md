# Echarts tooltip 出现时页面抖动

**解决办法：**

1. 在 `echarts dom容器` 上层再嵌套一层 `div`，并给此 `div` 添加 `overflow:hidden` 样式，如:

   ```html
   <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
   <div style="overflow:hidden">
       <div id="main" style="width: 600px;height:400px;"></div>
   </div>
   ```

2. 在 `echarts.setOption` 中 设置 `tooltip` 属性 `confine:true`：

   ```javascript
    <script type="text/javascript">
           // 基于准备好的dom，初始化echarts实例
           var myChart = echarts.init(document.getElementById('main'));
   
           // 指定图表的配置项和数据
           var option = {
               title: {
                   text: 'ECharts 入门示例'
               },
               tooltip: { // 设置此处
                   confine:true
               },
               legend: {
                   data:['销量']
               },
               xAxis: {
                   data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
               },
               yAxis: {},
               series: [{
                   name: '销量',
                   type: 'bar',
                   data: [5, 20, 36, 10, 10, 20]
               }]
           };
   
           // 使用刚指定的配置项和数据显示图表。
           myChart.setOption(option);
       </script>
   ```

   

