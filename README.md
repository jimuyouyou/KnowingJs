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
- 单线程
- 事件驱动
- 天生异步
- 快速高并发
- 非常适合高I/O，高并发的场景 - Web开发
- 不适合高CPU的场景 - 数据分析计算

## NodeJs异步流程控制(Async, Promise, Callback)
- 假设一个起床上班的场景流程：1.先穿衣服(3min) 2.打开音乐(1min) 3.刷牙并同时听音乐(2-5min) 4.刷牙结束并且音乐结束后，开始吃饭(10min) 5.吃饭结束上班走人，如果时间到8点了没吃完也得走人

## 最简单快速的实现静态文件服务器

## 万能的ExpressJs

## 桌面神器ElectronJs

## 百花齐放的Javascript

