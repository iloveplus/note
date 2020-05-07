## 将元素插入数组指定位置 

```js
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

function insertTag(data, insertMap) {
        let lastIndex = -1;
        let result = [...data];
        let __insertIndex = 0;

        function insertLoopTag(index, position, list,  insertData = {}) {
            __insertIndex++;

            list.splice(index, 0, {  ...insertData,  __insert: true, __insertIndex, __insertTypeNum: __insertIndex - insertData.index   });

            const startIndex = index + position + 1;
            if (position !== 0 && list[startIndex]) {
                return insertLoopTag(startIndex, position,  list,  insertData);
            } else {
                return list;
            }
        }

        for (let index = 0; index < insertMap.length; index++) {
            const item = insertMap[index];
            item.index = index;
            lastIndex += item.interval + 1;

            if (item.loop) {
                result = insertLoopTag(lastIndex, item.interval, result, item);
                break;
            } else {
                result = insertLoopTag(lastIndex, 0, result, item);
            }
        }

        return result;
    }



console.log(insertTag(arr, [{interval: 1, component: 'a'}]))
console.log(insertTag(arr, [{interval: 1, component: 'a'}, {interval: 2, component: 'b' }]))
console.log(insertTag(arr, [{interval: 1, component: 'a'}, {interval: 2, component: 'b', loop: true }]))
console.log(insertTag(arr, [{interval: 1, component: 'a'}, {interval: 3, component: 'b' }, {interval: 2, component: 'c', loop: true }]))
console.log(insertTag(arr, [{interval: 1, component: 'a'}, {interval: 3, component: 'b', loop: true }, {interval: 2, component: 'c', loop: true }]))
```
