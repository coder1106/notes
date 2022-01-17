mysql distinct和order by一起用时，order by的字段必须在select中。
首先，在mysql中distinct 的执行顺序高于order by。
第二，distinct执行时会对查询的记录进行去重，产生一张虚拟的临时表；
第三，order by执行时对查询的虚拟临时表进行排序，产生新的虚拟临时表。