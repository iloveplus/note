## 利用map,every,filter,some,reduce,sort对数组进行最优化处理，例如： 成绩表如下：
```js
var scoresTable=[
    {id:11,name:"小张",score:80},
    {id:22,name:"小王",score:95},
    {id:33,name:"小李",score:50},
    {id:44,name:"小刘",score:65},
    {id:55,name:"小徐",score:84}
]
```

> 快速获取最高score值（采用map,Max.sum和apply）
```js
var scores=scoresTable.map(function(item){return item.score});
var maxScore=Math.max.apply(this,scores)
console.log(maxScore)
```

> 是否包含不及格学生（some）
```js
var hasFail=scoresTable.some(function(item){return item.score<60;})
console.log(hasFail)
```

> 求平均分（reduce）
```
var averageScore=scoresTable.reduce(function(a,b){return a + b.score;},0)/scoresTable.length;
console.log(averageScore)
```

> 按成绩从高到低排序（sort）
```js
var score=scoresTable.sort(function(a,b){return a.score<b.score;})
console.log(score)
```

> 找出不及格学生（filter）
```js
var failStudents=scoresTable.filter(function(item){return item.score<60;})
console.log(failStudents)
```

> 是否所有学生的学号都是11的倍数（every）
```js
var t=scoresTable.every(function(item){return item.id%11==0;})
console.log(t)
```
