**和 Python 一起走过的日子**

- [Python语言相关](#python语言相关)
 - [一道lambda排序问题](#1-一道lambda排序问题)
 - [汉诺塔递归玄学](#2-汉诺塔递归玄学)
- [Flask漫游指南](#flask漫游指南)
  -[HTTP响应码]()
- [其他说明](其他说明)

---
# python语言相关
## 1 一道lambda排序问题
对一个列表进行排序，`lists = [7, -8, 5, 4, 0, -2, -5]`

要求：

- 正数在前，负数在后
- 整数从小到大
- 负数从大到小

- 来源：[V2EX](https://www.v2ex.com/t/286691)

### 代码

 `lists = [ 7, -8, 5, 4, 0, -2, -5 ]`

`sort_lists = sorted  ( lists , key = lambda x : ( x<0 , abs (x)  )`

### 解释

逐个分析，sorted 中 key 可接受函数作为排序的条件，此处将 lambda 匿名函数传入

在 lambda 中 **x<0** 起到的作用是将列表中数映射为 True 和 False ，对布尔型进行比较

```
>>>False < True 
True
```

不考虑 abs( x ) ，此处列表由：

`[ 7, -8, 5, 4, 0, -2, -5]`

变为：

False 在前  `7 , 5 , 4 , 0`     True 在后  `-8 , -2 ,-5`

abs( x )，作用为对列表中元素进行取绝对值，再进行排序

 `0 , 4 , 5, 7`   与  `-2 , -5 ,-8` 

综合可得出： [0, 4, 5, 7, -2, -5, -8]

## 2 汉诺塔递归玄学
### 要解决汉诺塔问题，首先得解决(汉诺塔-1)的问题

在汉诺塔问题中，a 是出发地，c 是目的地，b作用是缓冲区，而整个递归的过程，就是随着 a 上盘子数目的减少导致缓冲区位置的不断变化

```
def han ( n , a , b , c )
  if n == 1:
    print( a ,'-->' c )  # 只有一个，轻松从 a 到 c
  return #函数出口
  han ( n-1 , a , c , b ) #如果不止一个，以 c 为缓冲区，把上面的 n-1 个搬到 b
  han ( 1, a , b ,c ) #前面搬到了b，把a 剩下的最后一个搬到 c ，接下来搬 b 到 c 
  han ( n-1 , b , a ,c ) #风水轮流转，a 当缓冲区，把 (n-1) 的b 搬到 c
  
## 3
---

# flask漫游指南



