# JavaScript 日期格式化

```javascript
 /**
 * 时间格式化
 * @param date 日期
 * @param format 格式
 * @returns {*|string}
 */
function parseDate(date, format = 'yyyy-MM-dd HH:mm:ss') {
    date = new Date(date);
    let obj = {
        yyyy: date.getFullYear(),
        MM: date.getMonth() + 1,
        dd: date.getDate(),
        HH: date.getHours(),
        mm: date.getMinutes(),
        ss: date.getSeconds()
    };
    $.each(obj, (key, val) => {
        if (val < 10) val = '0' + val;
        format = format.replace(`${key}`, val);
    })
    return format;
}
```



