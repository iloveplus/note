## 写一个根据id字段查找记录的缓存函数

```js
function cacheArr(arr) {
    var cache = {};

    return id => {
        if (cache[id]) {
            console.log('cache data....');
            return cache[id];
        } else {
            var item = arr.find(item => item.id === id);
            if (item) {
                console.log('new data....');
                cache[item.id] = item;
                return item;
            } else {
                return null;
            }
        }
    };
}
```

测试数据:
```js
var scoresTable=[
    {id:11,name:"小张",score:80},
    {id:22,name:"小王",score:95},
    {id:33,name:"小李",score:50},
    {id:44,name:"小刘",score:65},
    {id:55,name:"小徐",score:84}
]

var findById = cacheArr(scoresTable);
findById(11)
findById(22)
findById(11)
findById(22)
```
