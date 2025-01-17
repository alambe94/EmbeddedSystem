# 性能测试相关概念说明

##  实时性相关概念

- 关中断时间

指的是程序中有一些临界段代码，需要关闭中断才能安全访问那么访问这段代码前关总中断，访问完后打开总中断，在这个时间内，系统是无法响应外部任何中断的。

- 最大关中断时间

指的是这么多个临界段代码的关中断时间中最大的那个，即这个时间就代表了最差最坏情况下中断的关闭时间了，因为实时操作系统中很多时间问题都是基于最差情况下考虑的。

- 中断响应时间

接收到此中断到此中断对应的中断服务函数的第一条语句执行所经历的时间。其计算公式是：


```
中断响应时间 ＝ 最大关中断时间 + 保护 CPU 内部寄存器的时间 + 进入中断服务函数的执行时间（会根据中断向量表找到对应的终端服务函数地址即入口）+ 开始执行中断服务例程 (ISR) 的第一条指令时间。
```

- 中断恢复时间

指从中断响应成功（即开始执行中断服务例程(ISR)的第一条指令时刻）一直到中断服务函数执行完毕再到切换回被中断的任务的接着一条代码执行所经历的时间。其计算公式是：

```
中断恢复时间 = 中断服务函数执行所需时间（这样说不太准确，意思就是基本执行完所需时间，不包括退出中断服务函数前会调用一下 OSIntExit() 函数）+ OSIntExit()（这个函数在中断服务函数末尾调用的，退出中断前来发生任务切换的）+ OSIntCtxSw()（真正发生任务切换的函数，会进行寄存器数据弹出等操作）。
```

## 临界区保护相关概念

- 基本临界区

临界区是提供互斥功能的一种非常原始的方法，进入临界区的方法使用中断锁把中断全部关掉（当然任务也就无法调度）。临界区内的代码必须要有很短的运行时间，否则会反过来**影响中断的相应时间**。

使用中断锁来操作临界区的方法可以应用于任何场合，且其他几类同步方式都是依赖于中断锁而实现的，可以说中断锁是最强大和最高效的同步方法。只是使用中断锁最主要的问题在于，在中断关闭期间，系统将不再响应任何中断，也就不能响应外部的事件。所以中断锁对系统的实时性影响非常巨大，当使用不当的时候会导致系统完全无实时性可言（可能导致系统完全偏离要求的时间需求）。而使用得当，则会变成一种快速、高效的同步方式。

- 任务临界区

挂起调度器也称为锁定调度器。基本临界区是保护一段代码不被其他任务或中断打断，而由挂起调度器实现的临界区只能保护一段代码不被其他任务打断，并不能约束中断，因为在这种方式下，中断是使能的。


