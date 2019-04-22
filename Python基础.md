第四章   Python 基础
4.3.1  list列表
   1、list是python内置的一种数据类型，它是一种有序的集合，可以随时添加和删除其中的元素。
  例如：班级里所有同学的名字就可以用一个list表示：classmates = ['zhangsan' , 'lisi' ,'wanger']
  3、用索引来访问list中每一个位置的元素，索引是从0开始的：classmates[0]
  4、list是一个可变的有序表，所以，可以追加元素到末尾（用append：附加）：classmates.append('字符串')
  5、也可以插入到指定位置：classmates.insert(索引号，内容) 例如：classmates.insert(1, ’zhangsan‘)
  6、要删除指定位置的元素，用pop(i)方法，i为索引位置。
  7、要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：classmates[1] = 'mazi'
  8、list内的元素数据类型也可以不同。例如：L = ['apple', 123 , True]
  9、list元素也可以是另外一个list。例如：S = ['python' , 'Java' , ['asp', 'php'] , 'scheme']
 4.3.2    tuple 元组
  1、它和list非常类似，但是tuple一旦初始化就不能修改，所以说也就没有append(), insert()，替换这样的方法。
     其他获取元素的方法是跟list相同的。比如：查找
  2、不可变的tuple意义：因为不可变，所以代码更安全。如果可能尽量用tuple。
  3、tuple的陷阱：当定义一个tuple时，在定义的时候tuple的元素就必须被定下来。例如：t = (1,2)
  4、定义空的tuple，可以写成（）：例如：t = ()
  5、 定义只有一个元素的tuple时必须加一个（，）逗号，来消除歧义：t = (1,)  。
      Python在显示只有1个元素的tuple时，也会加一个逗号,，以免误解成数学计算意义上的括号
  6、“可变的”tuple：
           t = ('a', 'b' , ['A' , 'B'])
           t [2][0] = 'X'
           t [2][1] = 'Y'
           则结果t 为('a' , 'b', ['X' , 'Y'])
4.6.1   dict(dictionary)
 1、Python内置了字典：dict的支持，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度 。
    例如：假设要根据同学的名字查找对应的成绩，如果用list实现，需要两个list：
               names = ['Michael', 'Bob', 'Tracy']
               scores = [95, 75, 85]
     给定一个名字，要查找对应的成绩，就先要在names中找到对应的位置，再从scores取出对应的成绩，list越长，耗时越长。
     如果用dict实现，只需要一个“名字”-“成绩”的对照表，直接根据名字查找成绩，无论这个表有多大，查找速度都不会变慢。
     用Python写一个dict如下：d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}

2、把数据放入dict的方法，除了初始化时指定外，还可以通过key放入：d['Adam'] = 67
3、由于一个key只能对应一个value，所以，多次对一个key放入value，后面的值会把前面的值冲掉。
4、如果dict内的key不存在，dict就会报错。（key = 内容）
        要避免key不存在的错误，有两种办法：
              一是通过in判断key是否存在：
                'Thomas' in d   #'Thomas' = key
              二是通过dict提供的get()方法，如果key不存在，可以返回None，或者自己指定的value：
                 d.get('Thomas')
                 d.get('Thomas', -1)
              注意：返回None的时候Python的交互环境不显示结果。
5、要删除一个key，用pop(key)方法，对应的value也会从dict中删除：
     例如： d.pop('Bob')

     请务必注意，dict内部存放的顺序和key放入的顺序是没有关系的。
总结：
       和list比较，dict有以下几个特点：
             查找和插入的速度极快，不会随着key的增加而变慢；
             需要占用大量的内存，内存浪费多。
        而list相反：
              查找和插入的时间随着元素的增加而增加；
              占用空间小，浪费内存很少。
所以，dict是用空间来换取时间的一种方法。
dict可以用在需要高速查找的很多地方，在Python代码中几乎无处不在，正确使用dict非常重要，
**需要牢记的第一条就是dict的key必须是不可变对象。
为什么dict的key必须是不可变对象？
          因为dict根据key来计算value的存储位置，如果每次计算相同的key得出的结果不同，
          那dict内部就完全混乱了。这个通过key计算位置的算法称为哈希算法（Hash）。
          要保证hash的正确性，作为key的对象就不能变。在Python中，字符串、整数等都是不可变的，
          因此，可以放心地作为key。而list是可变的，就不能作为key：
4.6.2    set
set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。
1、要创建一个set，需要提供一个list作为输入集合：s = set([1, 2, 3])
     注意：传入的参数[1, 2, 3]是一个list，而显示的{1, 2, 3}只是告诉你这个set内部有1，2，3这3个元素，显示的顺序也不表示set是有序的。

2、重复元素在set中自动被过滤：s = set([1, 1, 2, 2, 3, 3])  结果s 为：{1, 2, 3}
3、通过add(key)方法可以添加元素到set中，可以重复添加，但不会有效果：s.add(i)
4、通过remove(key)方法可以删除元素：s.remove(i)
5、set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作：
     >>> s1 = set([1, 2, 3])
     >>> s2 = set([2, 3, 4])
     >>> s1 & s2 = {2, 3}
     >>> s1 | s2 = {1, 2, 3, 4}
总结：set和dict的唯一区别仅在于没有存储对应的value，但是，set的原理和dict一样，所以，同样不可以放入可变对象，
          因为无法判断两个可变对象是否相等，也就无法保证set内部“不会有重复元素”。
4.6.3   不可变对象


第五章 函数
5.1.1  函数的定义
在python中定义函数要是用def语句，依次写出函数名、括号、括号中的参数和冒号（：），然后，在缩进块中编写函数体，
函数的返回值用return语句返回。
例如：def my_abs(x):
              if x >= 0:
                  return x
               else:
                   return -x
5.1.2  空函数
如果在编译代码时还没想好函数怎么写，可以先放一个pass语句来作为占位符，能让代码先运行起来。
 例如：def nop():
               pass
5.1.3   参数检查
调用函数时，如果参数类型或个数不对，解释器会自动检查出来。也可以用内置函数对函数进行检查。
例如：只允许整数和浮点数类型的参数，数据类型检查可以用内置函数isinstance()实现。
练习：请定义一个函数quadratic(a, b, c)，接收3个参数，返回一元二次方程：ax2 + bx + c = 0的两个解
# -*- coding: utf-8 -*-
import math    #表示导入math包，并允许后续代码引用math包里的函数
def quadratic(a,b,c):
#par = input('please enter the parameter')
#print('a = ,b = ,c = ',par)
        s = b**2-4*a*c
        if not isinstance(a+b+c, (int ,float)):  #对参数类型做检查，只允许整数和浮点数类型的参数。数据类型检查可以用内置函数isinstance()实现
            raise TabError('Bad Operand Type')
        if a == 0:
            x = -c/b
            return x
        elif s < 0:
            return '无实数根'
        elif s == 0:
            x = -b/2*a
            return x
        else:
            x1 = (-b+math.sqrt(b**2-4*a*c))/(2*a)
            x2 = (-b-math.sqrt(b**2-4*a*c))/(2*a)
            return x1 , x2
5.1.4   函数返回多个值
比如在游戏中经常需要从一个点移动到另一个点，给出坐标、位移和角度，就可以计算出新的新的坐标
import math
def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
5.3   函数的参数

定义函数的时候，我们把参数的名字和位置确定下来，函数的接口定义就完成了。
5.3.1、位置参数
 例如：定义一个计算x**2的函数：
			def power(x):
                 return x * x
 对于power(x)函数，参数x就是一个位置参数。当我们调用power函数时，必须传入有且仅有的一个参数x。
 但是如果要计算x**4、x**5……怎么办？
 可以把power(x)修改为power(x, n)，用来计算x**n，
 def power(x, n):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
 修改后的power(x, n)函数有两个参数：x和n，这两个参数都是位置参数，
 调用函数时，传入的两个值按照位置顺序依次赋给参数x和n。
5.3.2、默认参数
 1、默认参数可以简化函数的调用。设置默认参数时，有几点要注意：
	一是必选参数在前，默认参数在后，否则Python的解释器会报错
	二是如何设置默认参数。
		当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。变化小的参数就可以作为默认参数。
	使用默认参数有什么好处？
		最大的好处是能降低调用函数的难度.
  注意：定义默认参数要牢记一点：默认参数必须指向不变对象！
5.3.3、可变参数
  1、在Python函数中，还可以定义可变参数。顾名思义，可变参数就是传入的参数个数是可变的，
        可以是1个、2个到任意个，还可以是0个。
  2、def calc(*numbers): #定义函数的可变参数numbers
			sum = 0
		for n in numbers:
			sum = sum + n * n
		return sum
   定义可变参数和定义一个list或tuple参数相比，仅仅在参数前面加了一个*号。
  3、Python允许你在list或tuple前面加一个*号，把list或tuple的元素变成可变参数传进去：
		>>> nums = [1, 2, 3]
		>>> calc(*nums)
		14
	*nums表示把nums这个list的所有元素作为可变参数传进去。这种写法相当有用，而且很常见
5.3.4、关键字参数
   1、可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。
	  而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。
		例如：def person(name, age, **kw):
				  print('name:', name, 'age:', age, 'other:', kw)
		函数person除了必选参数name和age外，还接受关键字参数kw。
		在调用该函数时，可以只传入必选参数：
			>>> person('Michael', 30)
				   name: Michael age: 30 other: {}  #关键字参数在函数内部自动组装为一个dict
   2、关键字参数有什么用？     它可以扩展函数的功能。
   3、和可变参数类似，也可以先组装出一个dict，然后，把该dict转换为关键字参数传进去：
         >>> extra = {'city': 'Beijing', 'job': 'Engineer'}
		 >>> person('Jack', 24, city=extra['city'], job=extra['job'])
		   name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
        可以简化为：
		>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
		>>> person('Jack', 24, **extra)
		name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'
	**extra表示把extra这个dict的所有key-value用关键字参数传入到函数的**kw参数，kw将获得一个dict，
	注意：kw获得的dict是extra的一份拷贝，对kw的改动不会影响到函数外的extra。
5.3.5、命名关键字参数
    1、对于关键字参数，函数的调用者可以传入任意不受限制的关键字参数。至于到底传入了哪些，就需要在函数内部通过kw检查。
		 仍以person()函数为例，我们希望检查是否有city和job参数：
		  def person(name, age, **kw):
			 if 'city' in kw:
				# 有city参数
				 pass
			 if 'job' in kw:
				# 有job参数
				 pass
			 print('name:', name, 'age:', age, 'other:', kw  ）
   2、但是调用者仍可以传入不受限制的关键字参数：
		>>> person('Jack', 24, city='Beijing', addr='Chaoyang', zipcode=123456)
        如果要限制关键字参数的名字，就可以用命名关键字参数，
		例如，只接收city和job作为关键字参数。这种方式定义的函数如下：
		def person(name, age, *, city, job):
			print(name, age, city, job)
			和关键字参数**kw不同，命名关键字参数需要一个特殊分隔符*，*后面的参数被视为命名关键字参数
    3、调用方式如下：
		>>> person('Jack', 24, city='Beijing', job='Engineer')
			   Jack 24 Beijing Engineer
    4、如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符*了：
			def person(name, age, *args, city, job):
			print(name, age, args, city, job)
    5、命名关键字参数必须传入参数名，这和位置参数不同。如果没有传入参数名，调用将报错：
 











