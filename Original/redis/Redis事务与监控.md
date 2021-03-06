# Redis事务与监控



## 事务

​		Redis事务本质：一组命令的集合。事务中每条命令都会被序列化，执行过程中按顺序执行，不允许其他命令进行干扰。

1. Redis事务没有隔离级别的概念
2. Redis单条命令是保证原子性的，但是事务不保证原子性！

3. 一次性，顺序性，排他性



### Redis事务操作过程

- 开启事务（`multi`）
- 命令入队
- 执行事务（`exec`）

​    事务在添加命令的阶段可以执行 discard命令，从而取消事务。



### 事务错误

​		命令语法错误（编译时异常），所有的命令都不执行。

​		命令逻辑错误（运行时异常），错误的命令不执行，**其他命令可以正常执行 **，所以不保证事务原子性。



## 监控

### 锁

- **悲观锁：**

  认为所有操作都会出现问题，不管执行什么操作都会加锁

- **乐观锁：**

  认为所有操作都不会出现问题，所以不会主动上锁，只有在更新数据时采用 CAS的方式进行更新。



### 监控命令

- **watch key**：根据 key监控一个值，相当于保存一个 key当前的值。

- **unwatch key**：根据 key取消监控一个值。



### Redis的乐观锁

​		当前线程监控一个 key对应的值后，若另一个线程修改了这个值，当前线程若修改这个值，就会出错。因为 watch命令相当于保存这个值修改前的值，当当前线程运行修改此值之前会比较 watch保存的值是否与此时的值相同（CAS），但另一个线程修改了此值，所以拒绝执行，最终出错。

​		当遇到这种情况后，当前线程可以再次执行 watch命令更新保存的值，然后再修改。









