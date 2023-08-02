595. 大的国家

World 表：

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |
+-------------+---------+
在 SQL 中，name 是这张表的主键。
这张表的每一行提供：国家名称、所属大陆、面积、人口和 GDP 值。
 

如果一个国家满足下述两个条件之一，则认为该国是 大国 ：

面积至少为 300 万平方公里（即，3000000 km2），或者
人口至少为 2500 万（即 25000000）
查询并报告 大国 的国家名称、人口和面积。

按 任意顺序 返回结果表。

查询结果格式如下例所示。

示例：

输入：
World 表：
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
输出：
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+

# Write your MySQL query statement below
# 方法一：使用 WHERE 子句和 OR
# select t.name, t.population, t.area from world t
#     where t.area >= 3000000 or t.population >= 25000000

# 方法二：使用 WHERE 子句和 UNION
# 使用 or 会使索引会失效，在数据量较大的时候查找效率较低，通常建议使用 union 代替 or
select t.name, t.population, t.area from world t
    where t.area >= 3000000
    union
select t.name, t.population, t.area from world t
    where t.population >= 25000000
