# JavaScript es6 连续导入导出

现在有一个需求：比如我想在 `utils.js` 中导入 `reg_utils.js` 和 `str_utils.js` 中的所有方法，然后在 `use.js` 中使用

**实现：**

1. reg_utils.js

   ```javascript
   export function regFun(arg){
       return '';
   }
   ```

   

2. str_utils.js

   ```javascript
   export function strFun(arg){
       return '';
   }
   ```

   

3. utils.js

   ```javascript
   import * as regUtils from 'reg_utils.js' // 导入 reg_utils.js 中所有
   import * as strUtils from 'str_utils.js' // 导入 str_utils.js 中所有
   export default{ // 导出
       regUtils,
       strUtils
   }
   ```

   

4. use.js

   ```javascript
   import * as utils from 'utils.js' // 导入 utils.js 中所有
   
   cosole.log(utils.regUtils.regFun('1234')) // 使用 reg_utils.js 中的函数
   cosole.log(utils.strUtils.strFun('1234')) // 使用 str_utils.js 中的函数
   ```



记录一下，虽然很鸡肋，一般也不这么用，但是了解下 es6 的导入导出还是比较有意义的。

告辞！

