# KnowingJs
## 为什么要学习NodeJs
- [阿特伍德定律：任何可以用JavaScript来写的应用，最终都将用JavaScript来写](https://blog.codinghorror.com/the-principle-of-least-power/)

## 神奇的Javascript
- 1行代码选取百度首页的实时热点DOM元素列表：
`$$('ul li.news-meta-item')`
- 1行代码选取百度首页的实时热点文字列表：
`$$('ul li.news-meta-item').map(e => e.innerText)`
- 1行代码选取百度首页的实时热点链接列表：
`$$('ul li.news-meta-item a').map(e => e.href)`

## NodeJs的特性和优缺点
- 1 单线程
- 2 事件驱动
- 3 天生异步
- 4 快速高并发
- 5 非常适合高I/O，高并发的场景 - Web开发
- 6 不适合高CPU的场景 - 数据分析计算
- 总结：注意下面的推理不够严谨，更多的是为了快速理解上述特性。。。
```
7 因为是单线程，相比其他编程语言，在处理高并发时，少了线程管理相关资源的开销，所以更快速，更高并发
8 因为是单线程，它没有什么好办法去处理并发，所以才有了事件循环机制来单独应对并发这个事情，自然就天生异步了
9 因为是单线程，再加上事件循环机制，如果有一个函数执行卡住了，就会整个程序被卡住
10 因为单线程，一个卡住会卡全程序，所以不适合高CPU场景，因为高CPU必然会卡（CPU是电脑里边运行最快的部件了）
```

## NodeJs异步流程控制(Async, Promise, Callback)
- 假设一个起床上班的场景流程：1.先穿衣服(3min) 2.打开音乐(1min) 3.刷牙并同时听音乐(2-5min) 4.刷牙结束并且音乐结束后，开始吃饭(10min) 5.吃饭结束上班走人，如果时间到8点了没吃完也得走人

### NodeJs回调地狱Callback
- 根本上讲，程序员的代码决定了NodeJs更快，还是更卡
```
1 用传统编程语言的思维，相当然的认为完这一步，执行下一步，再下一步，最终会导致程序卡卡卡，卡死没反应
2 想要高并发，更快，那就必须用回调，Promise和Async-Await
```
- 在最初期，NodeJS很大程度上是用回调来让程序飞起来的
```
简单点说，事件循环机制就是把一个流程进行切片细分，每次运行一片。
这样的话，运行快的就会被循环的次数多，慢的往后排，最终极大的提升了整体速度。
那么在NodeJS里边的每一个切片是什么呢，是函数。
所以，我们需要把运行不同运行速度的函数给他区分开来，不断切片，划分子函数。
一片运行完，运行下一片，这个就是循环机制运行的回调函数了
```
- [入门callback](http://www.runoob.com/nodejs/nodejs-callback.html)
- [深入callback](https://blog.csdn.net/u013451157/article/details/78755708)
- [避免Node.js中回调地狱](https://www.cnblogs.com/greatluoluo/p/6288931.html)

### NodeJs中的Promise

### NodeJs中的Async-Await

## 最简单快速的实现静态文件服务器

## 万能的ExpressJs

## 桌面神器ElectronJs

## 百花齐放的Javascript

