学习笔记
####  循环中的continue，break区别
- continue是本次循环不执行
- break是跳出整个循环
######  跳出整个循环方法： 

```
1.循环加名称
    outer:for(let i = 0; i < 3; i++){
      for(let j = 0; j < 3; j++){
        if(pattern[i][j])
          continue
        let tmp = clone(pattern)
        tmp[i][j] = color
        // 留给对方最差局面
        let opp = bestChoice(tmp,3-color)
        if(-opp.result >= result) { 
          result = -opp.result
          point = [i,j]
        }
        if(result === 1)
          break outer
      }
    }
2.添加哨兵
    let flag = false
    for(let i = 0; i < 3; i++){
      if(flag) break
      for(let j = 0; j < 3; j++){
        if(pattern[i][j])
          continue
        let tmp = clone(pattern)
        tmp[i][j] = color
        // 留给对方最差局面
        let opp = bestChoice(tmp,3-color)
        if(-opp.result >= result) { 
          result = -opp.result
          point = [i,j]
        }
        if(result === 1)
          flag = true
          break 
      }
    }
```




#### 判断条件中写赋值操作

```
function expression(a){
    return a
}
let p;
if(p=expression(true)){执行}
if(p=expression(false)){不执行}
console.log(p) // false
```