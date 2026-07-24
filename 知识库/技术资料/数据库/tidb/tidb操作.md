# tidb操作
```sql
## 绑定索引
CREATE GLOBAL BINDING for SELECT * FROM t WHERE a IN (?) USING SELECT /*+ use_index(t, idx) */ * FROM t WHERE a in (?);
## 查看绑定
SHOW BINDINGS;
SELECT @@LAST_PLAN_FROM_BINDING;
```
