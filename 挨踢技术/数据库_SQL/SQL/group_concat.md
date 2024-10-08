[目录](./)

# group_concat

> GROUP_CONCAT() 是一个非常实用的聚合函数，主要用于将属于一组的相关行的数据项进行合并并以字符串的形式返回。

## 实例

假设我们有一个 orders 表，包含 order_id 和 product 字段，每个订单可能包含多个产品。

```
+---------+-----------+
| order_id|   product |
+---------+-----------+
|    1    |   apple   |
|    1    |   banana  |
|    2    |   orange  |
|    2    |   apple   |
+---------+-----------+
```

要把 product 输出为一个字段，就可以使用 group_concat 。

```

SELECT order_id, GROUP_CONCAT(product SEPARATOR ', ') AS products
FROM orders
GROUP BY order_id;
```

最终输出

```
+---------+----------------+
| order_id|     products    |
+---------+----------------+
|    1    | apple, banana   |
|    2    | orange, apple   |
+---------+----------------+
```