---
tags:
  - golang/接口
---
> 参考：[青蛙小白——理解 Go interface 的两种底层实现：iface 和 eface](https://blog.frognew.com/2018/11/go-interface-iface-eface.html)
>
> 具体 iface 的实现细节建议阅读原文，
> 或者进一步阅读 [Go 程序员面试笔试宝典——接口](https://golang.design/go-questions/interface/) 部分内容。

## 区别

Go 的 interface 分两类，
一类是拥有方法集（MethodSet）的接口；
另一个类是没有方法的空接口，也就是 `interface{}`。
iface 和 eface 就分别在运行时表示这两个类接口类型的变量:

- iface - 表示拥有方法的接口类型变量
- eface - 表示没有方法的空接口（empty interface）类型变量，即 `interface{}` 类型的变量

> [!note]
> iface 的实现会比较复杂，需要存储具体类型、接口类型和方法集合等，涉及较多细节；
> 而 eface 由于只需要存储具体类型就十分简单
