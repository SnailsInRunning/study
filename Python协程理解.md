# 了解基础概念
 1. yield：生成器中的关键字（可以决定控制器的中断和继续）；可以实现迭代器（例如Fib:菲波那切数列）
    n = yield r #函数执行到yield时，函数中断并返回r。

2. yield from：1.简化迭代器的遍历，相当于For循环，会依次遍历from后面的对象。
               2.在调用方和被调用方建立双向通道，简化带有yield的函数的send（）方法（即，可以省略写）


3. 协程：又称微线程，纤程。英文名Coroutine。正在执行当前事件时中断当前事件去执行其他事件，待当前事件执行完后，再返回原先事件继续执行。它不同于函数调用。
4. 异步：是一个概念，实现是通过：单线程、多线程、多进程。是为了充分考虑计算机的工作效率。
5. 异步协程：是为了计算机高效的工作效率。是指，将消耗时间的IO操作，用协程放到EventLoop中监管，当某个协程处于阻塞状态时，loop对象会从EventLoop中执行其他协程，当先前的协程执行完毕（返回一个消息给EventLoop，告诉执行状态），会返回协程继续执行。

            asynic def init():
                await asyncio.sleep(1)
    优点：轻量级的，而且没有线程之间来回切换的时间消耗，可以提高效率
         没有全局变量解释器锁，大大提高了性能。

6. （*args、**kw)：*args是非关键字参数，用于元组，**kw是关键字参数，用于字典。
        def foo(*args, **kwargs):    print 'args = ', args    print 'kwargs = ', kwargs    print '---------------------------------------'if __name__ == '__main__':
   foo(1,2,3,4)
   foo(a=1,b=2,c=3)
   foo(1,2,3,4, a=1,b=2,c=3)
   foo('a', 1, None, a=1, b='2', c=3)
输出结果如下：

args =  (1, 2, 3, 4) 
kwargs =  {} 
--------------------------------------- 
args =  () 
kwargs =  {'a': 1, 'c': 3, 'b': 2} 
--------------------------------------- 
args =  (1, 2, 3, 4) 
kwargs =  {'a': 1, 'c': 3, 'b': 2} 
--------------------------------------- 
args =  ('a', 1, None) 
kwargs =  {'a': 1, 'c': 3, 'b': '2'} 
---------------------------------------

可以看到，这两个是python中的可变参数。*args表示任何多个无名参数，它是一个tuple；**kwargs表示关键字参数，它是一个dict。并且同时使用*args和**kwargs时，必须*args参数列要在**kwargs前，像foo(a=1, b='2', c=3, a', 1, None, )这样调用的话，会提示语法错误“SyntaxError: non-keyword arg after keyword arg”