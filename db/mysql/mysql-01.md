### 《MySQL 实战 45 讲》学习笔记 Day 01

开篇词 | 这一次，让我们一起来搞懂MySQL

#### 这个专栏的意义

能够帮助这样的一些开发者：他们正在使用 MySQL，知道如何写出逻辑正确的 SQL 语句来实现业务目标，却不确定这个语句是不是最优的；他们听说了一些使用数据库的最佳实践，但是更想了解为什么这么做；他们使用的数据库偶尔会出问题，亟需了解如何更快速、更准确地定位问题，甚至自己解决问题……

能够激发开发者对数据库原理的探索欲，从而更好地理解工作中遇到的问题，更能知道背后的为什么。会选那些平时使用数据库时高频出现的知识，如事务、索引、锁等内容构成专栏的主线。

#### 课程大纲

开篇词｜这一次，让我们一起来搞懂 MysaL

**基础篇**

1. 基础架构：一条 SQL 查询语句是如何执行的？
2. 日志系统：一条 SQL 更新语句是如何执行的？
3. 事务隔离：为什么你改了我还看不见？
4. 深入浅出素引（上）
5. 深入浅出素引（下)
6. 全局锁和表锁：给表加个字段怎么有这么多阻碍？
7. 行锁功过：怎么减少行锁对性能的影响？
8. 事务到底是隔离的还是不隔离的？

**实践篇**

1. 普通索号l和唯一索引l，应该怎么选择？
2. MysQL为什么有时候会选错索引？
3. 怎么给字符串字段加索引？
4. 为什么我的MySQL会“抖”一下？
5. 为什么表数据删掉一半，表文件大小不变？
6. count(*)这么慢，我该怎么办
7. 答疑文章（一）：日志和索引相关问题
8. “order by”是怎么工作的？
9. 如何正确地显示随机消息？
10. 为什么这些 SQL 语句逻辑相同，性能却差异巨大？
11. 为什么我只查一行的语句，也执行这么慢？
12. 幻读是什么，幻读有什么问题？
13. 为什么我只查一行的语句，锁这么多？
14. MySQL 有哪些“饮鸩止渴”提高性能的方法？
15. MySQL是怎么保证数据不丢的？
16. MySQL是怎么保证主备一致的？
17. MysQL 是怎么保证高可用的？
18. 备库为什么会延迟好几个小时？
19. 主库出问题了，从库怎么办？
20. 读写分离有哪些坑？
21. 如何判断一个数据库是不是出问题了？
22. 答疑文章（二）：用动态的观点看加锁
23. 误删数据后除了跑路，还能怎么办？
24. 为什么还有kil 不掉的语句？
25. 我查这么多数据，会不会把数据库内存打爆？
26. 到底可不可以使用 join？
27. join 语句怎么优化？
28. 为什么临时表可以重名？
29. 什么时候会使用内部临时表？
30. 都说 InnoDB 好，那还要不要使用 Memory 引擎？
31. 自增主键为什么不是连续的？
32. insert 语句的锁为什么这么多？
33. grant 之后要跟着 flush privileges 吗？
34. 怎么最快地复制一张表？
35. 要不要使用分区表？
36. 答疑文章（三）
37. 递增 id 用完了怎么办？

**结束语**

* 结束语｜点线网面，一起构建 MysQL 知识网络
* 结课测试|这些MySQL 知识你都掌握了吗？

> 感悟：MySQL用了十几年了，还是一知半解，只有遇到问题才会看官方文档，这一次争取搞懂MySQL！

学习来源： 极客时间 https://time.geekbang.org/column/intro/100020801

