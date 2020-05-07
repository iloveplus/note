## 写出冒泡（或排序）算法对int数组的所有正整数进行从小到大排序，暂停2s后，再对所有的负整数进行从大到小排序，然后输出最终排序结果。
要求：
* 每次交换暂停1s
* 排序正整数时，非正整数的数字对应的位置保持不变，反之亦然
* 不要用async/await
* 考虑代码的可读性及代码复用

```js
var arr = [11, -7, 6, 5, -4, -10, 9, 8, -1];

function sort(arr) {
    const sortArr = (origin)  => { 
        let result = [];
        for (let i = 0; i < arr.length; i++) {
            let tempIndex = i;
            if (arr[i] > 0 && origin > 0) {
                for (let j = i; j < arr.length; j++) {
                    if (arr[j] > 0 && arr[j] < arr[tempIndex]) {
                        tempIndex = j;
                    }
                }
            } else if (arr[i] < 0 && origin < 0) {
                for (let j = i; j < arr.length; j++) {
                    if (arr[j] < 0 && arr[j] > arr[tempIndex]) {
                        tempIndex = j;
                    }
                }
            }

           
            if (tempIndex !== i) {
				 let temp = arr[i];
                arr[i] = arr[tempIndex];
                arr[tempIndex] = temp;
                result.push([...arr]);
            }
        }
        return result;
    }

    const resultList = [...sortArr(1), [], ...sortArr(-1)];

    var tic = function(_arr, callBack) {
        setTimeout(function() {
            const printData = _arr.shift();
            
            if (printData) {
                printData.length && console.log('交换后数据：', printData);
                callBack(_arr, tic);
            }
        }, 1000);
    };
    
    tic(resultList, tic);
	return arr;
}

sort(arr);
```
