## 剑指offer46-把数字翻译成字符串

给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

示例 1:
```
输入: 12258
输出: 5
解释: 12258有5种不同的翻译，分别是"bccfi", "bwfi", "bczi", "mcfi"和"mzi"
``` 

提示：
```
0 <= num < 231
```

### JavaScript
```javascript
/**
 * @param {number} num
 * @return {number}
 */
var translateNum = function(num) {
    let str = num.toString();
    let a = 1, b = 1;
    for(let i = 2; i <= str.length; i++) {
        let tmp = str.substring(i-2, i);        
        let c = (tmp >= "10" && tmp <= "25") ? (a + b) : b;
        a = b;
        b = c;        
    }
    return b;
};
```