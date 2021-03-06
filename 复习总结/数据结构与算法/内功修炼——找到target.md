提示：本文较短
# 一、什么是找到Target？
我们在解决算法问题的时候，可能常常会遇到让我们从一个数组里找和为Target的元素类似的题。
例如：leetcode 1 两数和。

# 二、 解决思路
所以我们如何解决这个问题呢？当遇到问题时，我们应该也必须先想到的是**暴力的方法**去解决问题。
毕竟我们的目标是解决问题，能够将问题解决后，我们再去想如何去更快更准的解决问题。
<br />
那么，暴力的方法解决了，我们要如何优化呢？
这个时候，针对这一类题，我们需要引入的是**哈希表**，为找到目标，每个元素自己可以在哈希表中查看和登记到
**哈希表**中，当查到哈希表中有元素**（Target - curr）**可以和自己组合为目标就可以返回。
<br />
打个比方，就好比找对象，你到婚姻介绍所**（哈希表）**登记想找一个满足自己的另一个人**（target - curr）**
，当你在登记表上看到有那个你想到的人，你的目标就找到啦。

### 写在最后
如果觉得本文对你有帮助的话，可以为我点个赞哈，你的关注和支持是我坚持下去最大的鼓励。
新手上路，对文章有什么建议和意见，也欢迎留言告诉我，期待你的回馈。