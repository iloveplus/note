## 求数组中连续最大值的子串？

```js
function seqMaxSubArr(arr) {
    if (arr.length <= 0) return;

    let res = {
        max: arr[0],
        sublist: [],
    };
    let sum = 0;
    let subArr = [];
    arr.forEach((item, index) => {
        if (sum > 0) {
            sum += item;
            subArr.push(item);
        } else {
            sum = item;
            subArr = [item];
        }

        if (sum > res.max) {
            res = {
                max: sum,
                sublist: [subArr],
            };
        } else if (sum === res.max) {
            res.sublist.push([...subArr]);
        }
    });

    return res;
}
```

测试用例:
```js
var arr = [1, -2, 6, 8, -6, 7, -4, -8, -9, -10, 10, 5, -20, 7, 8]
seqMaxSubArr(arr)
```

Result:
```js
{"max":15,"sublist":[[6,8,-6,7,-4,-8,-9],[10,5],[7,8]]}
```
