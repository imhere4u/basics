# 为什么会废弃 componentwillMount 
Fiber之后，由于任务可中断， willMount可能被执行多次（fiber算法是异步渲染，异步渲染 可能因为高优先级任务的出现被打断现有的任务导致willMount被多次执行）

首先这个函数的功能完全可以使用componentDidMount和constructor来代替，异步获取的数据的情况上面已经说明了，而如果抛去异步获取数据，其余的即是初始化而已，这些功能都可以在constructor中执行，除此之外，如果我们在willMount中订阅事件，但在服务端这并不会执行willUnMount事件，也就是说服务端会导致内存泄漏