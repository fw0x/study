### 《MySQL 实战 45 讲》学习笔记 Day 12

11 | 怎么给字符串字段加索引？

几乎所有的系统都支持邮箱登录，如何在邮箱这样的字段上建立合理的索引？

#### 前缀索引

```
mysql> create table SUser(
ID bigint unsigned primary key,
email varchar(64), 
... 
)engine=innodb; 
```

```
mysql> select f1, f2 from SUser where email='xxx';
```

```
mysql> alter table SUser add index index1(email);
或
mysql> alter table SUser add index index2(email(6));
```

优点：定义好长度，就可以做到既节省空间，又不用额外增加太多的查询成本

缺点：可能会增加额外的记录扫描次数，回表查询完整字段值的开销

用区分度来判断前缀长度：

```
mysql> select 
  count(distinct left(email,4)）as L4,
  count(distinct left(email,5)）as L5,
  count(distinct left(email,6)）as L6,
  count(distinct left(email,7)）as L7,
from SUser;
```

#### 优化方式

身份证号 18 位，前 6 位是地址码，同县的人前 6 位一般会是相同的。可能需要创建长度为 12 以上的前缀索引。

**倒序存储**

倒过来存，索引最后 6 位。

```
mysql> select field_list from t where id_card = reverse('input_id_card_string');
```

**hash 字段**

索引生成的整数校验码。

```
mysql> alter table t add id_card_crc int unsigned, add index(id_card_crc);
```

校验码可能重复，where要精确判断原字段。

```
mysql> select field_list from t where id_card_crc=crc32('input_id_card_string') and id_card='input_id_card_string'
```

**倒序和 hash 异同**

相同点：都不支持 range 查询。

区别：

1. 占用空间：倒序方式在主键索引上，不消耗额外存储空间，而 hash 字段需要增加字段。另外，倒序方式使用 4 个字节的前缀长度一般是不够的，如果再长一点，这个消耗跟额外这个 hash 字段也差不多抵消了
2. CPU 消耗：倒序方式每次写和读的时候，都需要额外调用一次 reverse 函数，而 hash 字段方式需要额外调用一次 crc32() 函数。如果只从这两个函数的计算复杂度来看的话，reverse 函数额外消耗的 CPU 资源会更小些
3. 查询效率：hash 字段方式的查询性能更稳定。因为 crc32 算出来的值虽然有冲突的概率，但是概率非常小，可以认为每次查询的平均扫描行数接近 1。而倒序方式毕竟还是用的前缀索引的方式，也就是说会增加扫描行数

> 感悟：还有一个思路，截取字段的一部分作为适合全部索引的新的冗余字段。

学习来源： 极客时间 https://time.geekbang.org/column/intro/100020801


