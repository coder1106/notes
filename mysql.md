mysql distinct和order by一起用时，order by的字段必须在select中。
首先，在mysql中distinct 的执行顺序高于order by。
第二，distinct执行时会对查询的记录进行去重，产生一张虚拟的临时表；
第三，order by执行时对查询的虚拟临时表进行排序，产生新的虚拟临时表。


# 数据恢复
https://blog.csdn.net/weixin_41004350/article/details/78547005
https://zhuanlan.zhihu.com/p/265005574
https://blog.51cto.com/u_12592884/2697522
https://www.cnblogs.com/michael9/p/11923483.html

http://zhongmingmao.me/2019/03/04/mysql-data-recovery/


show variables like "max_connections";
set global max_connections = 500;