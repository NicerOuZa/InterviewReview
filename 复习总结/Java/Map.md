## 0. hash是什么？
- Hash，一般翻译做散列、杂凑，或音译为哈希，是把任意长度的输入通过散列算法变换成固定长度的输出，该输出就是散列值。
- 常见的hash算法：
 - MD4、MD5，md5比MD4更复杂，速度要慢，但更安全，在抗分析和抗差分方面表现更好
- hash表常用构造方法：
 - 直接寻址法：取关键字或关键字的某个线性函数值为散列地址。
 - 平方取中法：取关键字平方后的中间几位为哈希地址。
 - 随机数法： 选择一个随机函数，取关键字的随机函数值为它的哈希地址。
 - 除留余数法：取关键字被某个不大于哈希表表长m的数p除后所得余数为哈希地址。
## 1. HashMap的底层原理
## 2. 说一下map的分类和常见情况
   - java为数据结构中的映射定义了一个接口 java.util.Map;它有四个实现类，分别是**HashMap**、**Hashtable**、**LinkedHashMap**和**TreeMap**.
   - Map主要用于存储健值对，根据键得到值，因此不允许键重复(重复了覆盖了），但允许值重复。
   1. Hashmap是一个最常用的Map，它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的。HashMap最多只允许一条记录的键为Null;允许多条记录的值为Null;HashMap不支持线程的同步，即任一时刻可以有多个线程同时写HashMap;可能会导致数据的不一致。如果需要同步，可以用Collections的synchronizedMap方法使HashMap具有同步的能力，或者使用ConcurrentHashMap。
   2. Hashtable与HashMap类似，它继承自Dictionary类，不同的是:它不允许记录的键或者值为空;它支持线程的同步，即任一时刻只有一个线程能写Hashtable,因此也导致了 Hashtable在写入时会比较慢。
   3. LinkedHashMap是HashMap的一个子类，保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的.也可以在构造时用带参数，按照应用次数排序。在遍历的时候会比HashMap慢，不过有种情况例外，当HashMap容量很大，实际数据较少时，遍历起来可能会比LinkedHashMap慢，因为LinkedHashMap的遍历速度只和实际数据有关，和容量无关，而HashMap的遍历速度和他的容量有关。
   4. TreeMap实现SortMap接口，能够把它保存的记录根据键排序,默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator遍历TreeMap时，得到的记录是排过序的。
   - **常见情况** </br>
	一般情况下，我们用的最多的是HashMap,在Map中插入、删除和定位元素，HashMap是最好的选择。但如果您要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。如果需要输出的顺序和输入的相同,那么用LinkedHashMap可以实现，它还可以按读取顺序来排列。
		- **HashMap**是一个最常用的Map，它根据键的hashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度。HashMap最多只允许一条记录的键为NULL，允许多条记录的值为NULL。HashMap不支持线程同步，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致性。如果需要同步，可以用Collections的synchronizedMap方法使HashMap具有同步的能力。
		- **Hashtable与HashMap类似**，不同的是：它不允许记录的键或者值为空；它支持线程的同步，即任一时刻只有一个线程能写Hashtable,因此也导致了 Hashtable在写入时会比较慢。
		- **LinkedHashMap**保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的。
		- 在遍历的时候会比HashMap慢**TreeMap**能够把它保存的记录根据键排序，默认是按升序排序，也可以指定排序的比较器。当用Iterator遍历TreeMap时，得到的记录是排过序的。