#### 数据库事务
事务是一个不可分割的数据库操作序列，也是数据库并发控制的基本单位，其执行的结果必须使数据库从一种一致性状态变为另一种一致性状态。事务中的操作要不全部执行，要不全部不执行。

##### 事务特性
事务遵循ACID四种特性

1. 原子性(Atomicity)：事务中的一系列操作要不全部执行，要不全部不执行
2. 一致性(Consistency)：事务的执行结果必须使数据库从一个一致性状态到另一个一致性状态
3. 隔离性(Isolation)：并发执行的事务之间不能相互影响
4. 持久性(Durability)：事务一旦提交，对数据库中数据的改变是永久性的

##### 事务带来的问题
1. 脏读：一个事务读取了另一个事务未提交的数据
2. 不可重复读：读取的数据可以被其他事务修改，相同条件下读取的结果不同，重点是修改
3. 幻读：读取的数据可以被其他事务添加或删除，相同条件下读取的结果不同，重点是添加或删除

##### 事务隔离级别
隔离级别决定了一个事务对另一个事务的影响。ANSI定义了四种隔离级别：
1. READ_UNCOMMITTED，读未提交：允许一个事务读取另一个事务未提交的数据，可能导致脏读问题，是最低级别的隔离
2. READ_COMMITTED，读已提交：在一个事务中只允许对其他事务已经提交的数据可见，不能避免不可重复读问题
3. REPEATABLE_READ，重复读：在一个事务开始后，其他事务对数据库的修改在本事务中不可见，直到本事务提交或回滚，但是其他事务的insert/delete操作对本事务是可见的，这样，该隔离级别不能避免幻读问题。在一个事务中重复select的结果一样，除非本事务中update数据库
4. SERIALIZABLE，序列化：最高隔离级别，只允许事务串行执行

MySQL默认隔离级别是REPEATABLE READ
