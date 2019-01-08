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

### NodeJs回调地狱Callback - 很像俄罗斯套娃
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

```
回调是切片（其实是俄罗斯套娃），可是在真实的业务场景，一个流程会有几十，上百个步骤，这样的话，回调就有如下问题：
1. 每次切片，表达的真实意义是“剩余其他步骤” - 这样的话函数命名就非常混乱，因为词不达义啊
2. 每片里边都需要包括错误处理，要不程序一旦出错就挂住了 - 这样会产生大量冗余代码，可维护性特别差
3. 真实场景，一般是说“这个流程中只要有一步错了，就报错” - 回调实现这个比较困难
4. 真实场景，还有经常有if-else这样的分支逻辑 - 而回调只能处理简单的自上而下的调用关系
```

### NodeJs中的Promise - 很像叠罗汉
- 俄罗斯套娃很有趣，可是业务场景稍微复杂一点，一般来说超过5层套娃，就较难维护了
- 于是产生了Promise,这个是叠罗汉
```
Promise.call(A)
  .then(B)
  .then(C)
  .then(D)
  .catch(error)
```

```
Promise可以轻松解决套娃面临的1-2-3-4问题，可是对真实的业务场景，它也有较难满足的情景
1. 只能连续切片，较难对切片进行组合 - 这个解决不了callback面临的分支异步问题
2. 每片的值只能传递，无法共享 - 这个就严重限制了它的使用空间，同时也造成代码冗余
3. 只有一个尾部异常处理 - 较难满足多异常分情况处理的真实场景
```

- [NodeJs内置的回调转Promise函数](https://nodejs.org/api/util.html#util_util_promisify_original)
- [Promise.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)
### NodeJs中的Async-Await - 程序员要的真正的乐高积木
- 叠罗汉超过10层之后，也会相对较难维护 - 它也有点像烤串，串多了，沉重啊，想中间扯下一块来，太困难
- async-await 相怎么搭，就怎么搭

```
const makeRequest = async () => {
  await callAPromise()
  await callAPromise()
  await callAPromise()
  await callAPromise()
  await callAPromise()
  throw new Error("oops");
}
```

[为什么await强于Promise](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
## 最简单快速的实现静态文件服务器

## 万能的ExpressJs

## 桌面神器ElectronJs

## 百花齐放的Javascript

