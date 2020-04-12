# InterviewReview
知识点总结复习

---

# 3.16 腾讯WXG后台开发——一面 十几分钟
### 大概就面了十几分钟
### 首先先和我说部门大部分用的是C/C++的比较多，然后让我自我介绍，然后问了一个linux系统和一个MySQL的问题，一面就这样结束了。

---

# 3.20 腾讯IEG运营开发——预备面 一个小时
### 1. 自我介绍
### 2. 聊项目，主要是问项目拓展方面的问题，比如说问你这个新功能你会怎么做
秒杀系统怎么实现：简单的流程是——下单减库存
	
### 3. 锁的问题
### 4. TCP三次握手 四次挥手
### 5. https流程，没回答上，只说了相当于在多了SSL层进行加密
### 6. hashtable，concurrentHashmap为什么线程安全
总结： JDK8中的实现也是锁分离的思想，它把锁分的比segment（JDK1.7）更细一些，只要hash不冲突，就不会出现并发获得锁的情况。
	它首先使用无锁操作CAS插入头结点，如果插入失败，说明已经有别的线程插入头结点了，再次循环进行操作。如果头结点已经存在，
	则通过synchronized获得头结点锁，进行后续的操作。性能比segment分段锁又再次提升。
### 7. redis为什么快 -> 单线程的吗 -> 怎么保证数据安全

---

# 3.21 腾讯IEG运营开发——一面 半个小时
### 1. 自我介绍，还聊了一下
### 2. 接口与抽象类区别
	当时紧张了没想到
### 3. Mysql事务，Java中怎么实现，Spring中用什么注释实现
### 4. 索引
### 5. 操作系统常见的命令有哪些 -> 递归的mkdir怎么弄 
### 6. 实现线程有哪几种方式 
### 7. 前端了解吗
### 8. http头有哪些内容 
	不太记得了，就说了，请求方法，请求地址，用户信息，编码方式
### 9. Spring IOC
### 10. java反射
	forName Class
	
---

# 3.23 腾讯WXG微信客户端IOS开发一面 两个小时
### 1. 一上来就做题，有两道题，花了差不多一个小时，第一次写题有点紧张，第写的有点久，脑子转不过来。第一题花了差不多二三十分钟。第二道写得有bug
	- 合并数组
	- 从字符串种去除掉指定子字符串，返回剩下的字符数。第二题忘记了一个函数怎么用了
### 2. 问了我的项目
### 3. IOS开发的时候我用了什么数据库，我忘记了
	SQLite
### 4. java的内存管理模型
### 5. Java垃圾回收机制
### 6. 线程和进程的区别，什么时候用进程什么时候用线程，你如何选择
### 7. 死锁怎么解决
### 8. mysql数据优化
- 这个没答上来，就瞎说了
- 只返回需要的列尽量少用 Select *，
- 只返回必要的行，使用 WHERE 语句进行查询过滤，有时候也需要使用 LIMIT 语句来限制返回的数据。

### 9. 几种常见的HTTP状态码
### 10. 说一下几种排序算法和其时间复杂度
### 11. 算法，从一堆重复的数中找出最大的重复的数。

# 3.25 10点 腾讯视频 安卓客户端开发 一面 一个小时
### 1. 自我介绍
### 2. 直接上来问Java，synchronized和lock的区别
### 3. hashmap和hashtable的区别
### 4. hashmap线程安全用什么 -> concurrenthashmap
### 5. hashmap扩容； 解决hash冲突不使用链表可以使用什么
### 6. synchronized底层是怎么实现的
### 7. 了解NIO吗
### 8. 线程的实现方式
这个有点难顶 我说了有三种，Thread、Runnable、Callable
### 9. 当然会问这几个的线程实现方式的区别，主要是Runnable和Callable的区别
我说了callable有返回值，且不能直接在Thread中使用
### 10. 当然问到Future，这个我不了解，就知道FutureTask有一个泛型，然后这个是接住Callable的返回
### 11. 二叉树后序遍历递归和非递归
### 12. url从短变成长
### 13. 统计正整数二进制1的个数
### 补充在前面
### 14. 单例模式
### 15. sleep和wait的区别
	
# 3.25 19点 腾讯视频 安卓客户端开发 一面 半个小时
### 1. 自我介绍
### 2. 问了项目，围绕数据缓存来问，怎么去淘汰，你怎么设计LRU
### 3. Java中设计类一般都涉及到哪函数，我说了setter、getter、toString、equals和HashCode
### 4. 自然会问到HashCode的作用和怎么保证相等和不等
### 5. Java反射
### 6. ArrayList、LinkedList、vector的区别
### 7. String、StringBuffer、StringBuilder的区别
### 8. 不用递归的快排

## 3.28 13:00 放弃腾讯后台面试

# 3.28 下午五六点 阿里 蚂蚁金服
### 1. 自我介绍
### 2. 问了高并发处理请求怎么实现的
#### 我突然发现，我好像不知道什么是高并发，就知道一个多线程、线程池。没有实际去操作看来还是什么都不懂。所以我打算好好看一下
### 3. 问了Hash Map的遍历方式
#### 当时打针，蒙了，就乱答了什么链表顺序，然后树中序前序后序