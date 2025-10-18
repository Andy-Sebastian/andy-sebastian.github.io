# Week 1

relation sheet
relationship
relation: set of sets

# Week 2 Entity

| 类别     | 术语                                             | 定义                                         |
| -------- | ------------------------------------------------ | -------------------------------------------- |
| **实体** | 强实体 (strong entity)                           | 独立存在、有自身主键的实体                   |
|          | 弱实体 (weak entity)                             | 依赖强实体主键才能唯一标识的实体             |
|          | 正则实体 (regular entity)                        | 与强实体同义，强调独立存在                   |
|          | 存在依赖 (existence-dependent)                   | 实体存在依赖于另一个实体                     |
|          | 存在独立 (existence-independent)                 | 实体可独立存在，不依赖其他实体               |
| **属性** | 简单属性 (simple attribute)                      | 原子不可再分，如“性别”                       |
|          | 派生属性 (derived attribute)                     | 可由其它属性计算，如“年龄”                   |
|          | 复合属性 (composite attribute)                   | 由多个子属性组成，如“地址”＝〈省、市、街道〉 |
|          | 多值属性 (multivalued attribute)                 | 同一实体可有多个值，如“电话号码”             |
|          | 单值属性 (single-valued attribute)               | 每个实体实例仅一个值，如“身份证号”           |
|          | 必需属性 (required attribute)                    | 不可为空的属性                               |
|          | 可选属性 (optional attribute)                    | 可取空值的属性                               |
|          | 域 (domain)                                      | 属性取值范围，如性别域={男, 女}              |
| **关系** | 二元关系 (binary relationship)                   | 两个实体间关联，如“员工-所属-部门”           |
|          | 三元关系 (ternary relationship)                  | 三个实体同时参与的关联                       |
|          | 一元关系/递归关系 (unary/recursive relationship) | 同一实体的自引用关系                         |
|          | 强（标识）关系 (identifying)                     | 用于标识弱实体主键的关系                     |
|          | 弱（非标识）关系 (non-identifying)               | 普通主外键关系，不参与弱实体标识             |
|          | 连通性/基数 (connectivity/cardinality)           | 描述关联的 1:1、1:N、M:N 类型                |
|          | 参与度 (participation)                           | 实体在关系中是否必需：强制/可选              |
| **建模** | 标识符 (identifiers)                             | 实体主键，分简单标识符、复合标识符           |
|          | 关系模式 (relational schema)                     | ER 模型映射到关系模型后的表结构定义          |
|          | 迭代过程 (iterative process)                     | ER 建模的反复完善流程                        |

# Week 6 Considering Personal Data in Database Design | Creating & Altering the Database

## Considering Personal Data in Database Design

## Creating & Altering the Database

### Components of SQL language

- DDL(Data Definition Language)
- DML(Data Manipulation Language)
- DCL(Data Conrtol Language)

### Oracle Data Type

### DDL

#### Common ORACLE Data Types
| Code | Data Type                                                      | 参数信息说明                                                |
| ---- | -------------------------------------------------------------- | ----------------------------------------------------------- |
| 1    | VARCHAR2(size [BYTE｜CHAR])                                    | `size`：最大长度；BYTE/CHAR：按字节或字符计数               |
| 1    | NVARCHAR2(size)                                                | `size`：最大字符数（以字符为单位，支持Unicode）             |
| 2    | NUMBER([precision [, scale]])                                  | `precision`：总位数；`scale`：小数位数                      |
| 8    | LONG                                                           | 最多存储 2GB 字符数据（已过时，不推荐使用）                 |
| 12   | DATE                                                           | 存储日期和时间（精确到秒），基于 **Gregorian** 历法         |
| 21   | BINARY_FLOAT                                                   | 单精度浮点数（32位）                                        |
| 22   | BINARY_DOUBLE                                                  | 双精度浮点数（64位）                                        |
| 23   | RAW(size)                                                      | `size`：最大字节数（存储二进制数据）                        |
| 24   | LONG RAW                                                       | 最多存储 2GB 二进制数据（已过时，不推荐使用）               |
| 69   | ROWID                                                          | 存储行的唯一物理地址                                        |
| 96   | CHAR [(size [BYTE｜CHAR])]                                     | `size`：固定长度字符串；BYTE/CHAR：按字节或字符计数         |
| 96   | NCHAR[(size)]                                                  | `size`：固定长度 Unicode 字符串                             |
| 112  | CLOB                                                           | 存储大对象，最大 4GB 字符数据                               |
| 112  | NCLOB                                                          | 存储大对象，最大 4GB Unicode 字符数据                       |
| 113  | BLOB                                                           | 存储二进制大对象，最大 4GB                                  |
| 114  | BFILE                                                          | 存储外部文件的二进制数据（只读，数据库外部）                |
| 180  | TIMESTAMP [(fractional_seconds)]                               | `fractional_seconds`：小数秒位数（0–9）                     |
| 181  | TIMESTAMP [(fractional_seconds)] WITH TIME ZONE                | 带时区的时间戳                                              |
| 182  | INTERVAL YEAR [(year_precision)] TO MONTH                      | `year_precision`：年位数（默认2，最大9）                    |
| 183  | INTERVAL DAY [(day_precision)] TO SECOND[(fractional_seconds)] | `day_precision`：天位数；`fractional_seconds`：秒的小数位数 |
| 208  | UROWID [(size)]                                                | `size`：最大存储长度，用于存储索引组织表行地址              |
| 231  | TIMESTAMP [(fractional_seconds)] WITH LOCAL TIMEZONE           | 带本地时区的时间戳                                          |

#### Create Syntax
```sql
CREATE TABLE table_name (
  column_name data_type [DEFAULT expr] [constraint],
  ...
  [table_constraints]
);

```

#### Column VS Table Level Constraints
| 约束类型        | 列级可定义 | 表级可定义 | 说明                                                 |
| --------------- | ---------- | ---------- | ---------------------------------------------------- |
| **NOT NULL**    | ✅          | ❌          | **只能列级**，因为它只针对单一列。                   |
| **PRIMARY KEY** | ✅          | ✅          | 表级可以定义 **复合主键**（多列），列级只能单列。    |
| **UNIQUE**      | ✅          | ✅          | 表级可以定义 **多列唯一性**，列级只能单列唯一。      |
| **FOREIGN KEY** | ✅          | ✅          | 列级：单列外键；表级：可以定义复合外键（涉及多列）。 |
| **CHECK**       | ✅          | ✅          | 表级：可以跨多列检查；列级：仅针对该列。             |

**All constraints other than the not null constraints must have a name.**

#### Alter Syntax

- use alter add constraint
    ```sql
    -- 1) 主键（可多列）
    ALTER TABLE emp
    ADD CONSTRAINT pk_emp PRIMARY KEY (emp_id)
    USING INDEX;              -- 可选：索引选项/表空间等

    -- 2) 唯一约束（可多列）
    ALTER TABLE emp
    ADD CONSTRAINT uq_emp_name UNIQUE (emp_name);

    -- 3) 外键（支持级联/可延迟检查）
    ALTER TABLE emp
    ADD CONSTRAINT fk_emp_dept
    FOREIGN KEY (dept_no)
    REFERENCES department(dept_no)
    ON DELETE SET NULL        -- 或 ON DELETE CASCADE
    DEFERRABLE INITIALLY DEFERRED;  -- 可选：事务提交时再检查

    -- 4) 检查约束（可跨列）
    ALTER TABLE emp
    ADD CONSTRAINT ck_salary CHECK (salary > 0);

    -- 5) NOT NULL（只能走 MODIFY 语法，见下节）

    -- 约束状态管理
    -- 启用/禁用
    ALTER TABLE emp ENABLE  CONSTRAINT fk_emp_dept;
    ALTER TABLE emp DISABLE CONSTRAINT fk_emp_dept;

    -- 是否立即校验历史数据
    ALTER TABLE emp ENABLE  VALIDATE   CONSTRAINT fk_emp_dept;  -- 立即检查现有数据
    ALTER TABLE emp ENABLE  NOVALIDATE CONSTRAINT fk_emp_dept;  -- 仅对新数据生效
    ```
- use alter modify attributes
    ```sql
    -- 1) 改数据类型/长度/精度
    ALTER TABLE emp MODIFY (emp_name VARCHAR2(200 CHAR));
    ALTER TABLE emp MODIFY (salary   NUMBER(10,2));

    -- 2) 设置/移除默认值
    ALTER TABLE emp MODIFY (salary DEFAULT 0);
    ALTER TABLE emp MODIFY (salary DEFAULT NULL);

    -- 3) 设置 NOT NULL（可命名约束）
    ALTER TABLE emp MODIFY (emp_name CONSTRAINT nn_emp_name NOT NULL);

    -- 4) 允许 NULL
    ALTER TABLE emp MODIFY (emp_name NULL);
    ```
- use alter for mulitple change
    ```sql
    ALTER TABLE employees
      ADD CONSTRAINT pk_emp PRIMARY KEY (emp_id)
      ADD CONSTRAINT ck_salary CHECK (salary > 0)
      MODIFY (emp_name VARCHAR2(100) NOT NULL)
      MODIFY (salary DEFAULT 0);
    ```

---

Oracle ALTER 对已有数据的影响

在 **Oracle** 里，`ALTER TABLE` 修改列定义或增加约束时，是否立即作用于已有数据，取决于操作类型：


1. `MODIFY` 修改列定义

* **加长列长度**

  * 立即生效，不影响已有数据。

  ```sql
  ALTER TABLE emp MODIFY (ename VARCHAR2(200));
  ```

* **缩短列长度 / 改精度**

  * Oracle 会立刻检查已有数据是否能容纳。
  * 如果有数据超出范围 → 报错，DDL 不会成功。
  * 需要手动清理/转换数据后再执行。

* **DEFAULT 值**

  * 对已有行 **不改变**，只对 **之后插入/更新时缺省值** 生效。

* **NOT NULL**

  * Oracle 会立刻检查已有数据是否存在 `NULL`，如果有 → 报错。

---

2. `ADD CONSTRAINT`

* **PRIMARY KEY / UNIQUE / CHECK**

  * 默认 `ENABLE VALIDATE` → Oracle 会立刻检查全表数据是否符合。
  * 如果数据不符合 → 报错，DDL 失败。
  * 可以用 `ENABLE NOVALIDATE` 跳过已有数据检查，仅对新数据生效。

  ```sql
  ALTER TABLE emp ADD CONSTRAINT ck_salary CHECK (salary > 0) ENABLE NOVALIDATE;
  ```

* **FOREIGN KEY**

  * 默认同样会检查已有数据；
  * 可用 `ENABLE NOVALIDATE` 跳过检查，仅对新数据生效。

---

- 总结

* **大部分 ALTER** → 默认立即作用并校验现有数据。
* **DEFAULT** → 仅影响新插入行，不会修改已有数据。
* **约束** → 默认检查全表数据，可用 `ENABLE NOVALIDATE` 只对新数据生效。

#### Referential Integrity
当 **父表的主键记录被删除**时，子表的外键引用可能会有不同的处理方式。Oracle 支持以下几种策略：

---

1. RESTRICT （Oracle 默认：NO ACTION）

* **含义**：如果某个主键在子表中还有外键引用，则 **不允许删除** 该主键行。
* **例子**：

  * `DEPARTMENT.dept_no = 10`
  * `EMPLOYEE` 表里还有多行员工的 `dept_no=10`
  * 删除 `DEPARTMENT` 表的 `dept_no=10` → **报错，拒绝删除**。

---

2. CASCADE （级联删除，Oracle 语法：`ON DELETE CASCADE`）

* **含义**：删除父表（主键表）的行时，自动删除子表中对应的外键行。
* **例子**：

  * 删除 `DEPARTMENT.dept_no=10` → 自动把 `EMPLOYEE` 表中所有 `dept_no=10` 的行一并删除。

---

3. NULLIFY （置空，Oracle 语法：`ON DELETE SET NULL`）

* **含义**：删除父表的主键行时，子表中对应的外键字段会 **更新为 NULL**。
* **例子**：

  * 删除 `DEPARTMENT.dept_no=10` → `EMPLOYEE` 表中所有 `dept_no=10` 的行会变成 `dept_no=NULL`。

#### Referential Integrity 中的删除策略
| 策略                   | 使用场景                                              | 示例                                                                                            | 优点                               |
| ---------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------------- |
| **ON DELETE CASCADE**  | 子表记录 **完全依赖父表**，父表不存在时子表也应被删除 | - 订单主表（orders） ↔ 订单明细表（order_items）<br>- 学生表（students） ↔ 成绩表（scores）     | 保证数据一致性，不会留下“孤儿记录” |
| **ON DELETE SET NULL** | 子表记录 **可独立存在**，但外键关系失效时需要解除关联 | - 员工表（employees） 的 `manager_id` ↔ 经理表<br>- 客户表（customers） 的推荐人字段 ↔ 推荐人表 | 保留子表数据，仅解除外键依赖       |


#### Drop syntax
```sql
DROP TABLE table_name [CASCADE CONSTRAINTS] [PURGE];
-- CASCADE CONSTRAINTS：删除该表的同时，自动删除依赖它的外键约束。
-- PURGE：跳过回收站，彻底删除表，无法闪回恢复。
DROP INDEX index_name;
DROP VIEW view_name;
DROP USER user_name [CASCADE];
-- CASCADE：删除用户的同时，连同该用户下的所有对象一起删除。
```
# Week 7 DML and Transaction Management

## DML

### COMMIT and ROLLBACK

- COMMIT: makes the changes to the database permanent
- ROLLBACK: will undo/remove the changes

| 类型                                    | 典型语句                              | 是否会提交事务       | 说明                                          |
| --------------------------------------- | ------------------------------------- | -------------------- | --------------------------------------------- |
| **DML（Data Manipulation Language）**   | `INSERT`, `UPDATE`, `DELETE`, `MERGE` | ❌ 不会自动提交       | 修改表中数据，需显式 `COMMIT` 或 `ROLLBACK`。 |
| **DDL（Data Definition Language）**     | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | ✅ 自动提交           | 修改对象结构，会隐式提交前后事务。            |
| **DCL（Data Control Language）**        | `GRANT`, `REVOKE`                     | ✅ 自动提交           | 改变权限控制，同样会隐式提交。                |
| **TCL（Transaction Control Language）** | `COMMIT`, `ROLLBACK`, `SAVEPOINT`     | ✅ 控制事务提交与回滚 | 控制事务边界。                                |


### Insert
```sql
-- insert single row
INSERT INTO table_name (column_list)
VALUES( value_list);

INSERT INTO table_name
VALUES (value_list);

-- insert multiple rows
INSERT INTO table_name (column_list)
VALUES 
   ( value_list_1),
   ( value_list_2),
   ( value_list_3);

COMMIT/ROLLBACK
```

If you exclude one or more columns from the Oracle `INSERT` statement, then you must specify the column list because Oracle needs it to match with values in the value list.

The column that you omit in the `INSERT` statement will use the default value if available or `NULL` if the column accepts NULL.

#### Inserting DATES into a table
```sql
INSERT INTO t_orders (id, order_dt)
VALUES (1, TO_DATE('2025-09-30 14:35:00', 'YYYY-MM-DD HH24:MI:SS'));
COMMIT/ROLLBACK

-- convert a date
TO_DATE('10 Dec 2022','dd Mon yyyy')
-- convert a datetime
TO_DATE('10/12/2022 17:00','dd/mm/yyyy hh24:mi')
-- convert a time
TO_DATE('17:00','hh24:mi')
```

常用的格式元素:
- year
    - YYYY -> 4 位年（最常用）
    - YY → 2 位年
- month
    - MM → 月份数字（别和 MI 分钟混）
    - MON → 英文缩写月（Jan, Feb… 受 NLS_DATE_LANGUAGE 影响）
    - MONTH → 英文全名（January…）
- day
    - DD → 月内第几天（01–31）
    - DDD → 年内第几天（001–366）
- time
    - HH24 → 24小时制小时（00–23）
    - HH → 12小时制小时（01–12）
    - MI → 分钟（00–59）
    - SS → 秒（00–59）
- am/pm
    - AM / PM → 配合 HH 使用（12小时制）
  
---

大小写不敏感
在 Oracle 中，**TO_DATE 的格式掩码（format model）是大小写不敏感（case-insensitive）**的。
也就是说：
```sql
YYYY == yyyy == Yyyy == yYyY
```
虽然功能上没区别，但在实际开发/考试/作业中  
统一写成 大写（YYYY-MM-DD HH24:MI:SS） 

---

连接符与文字  
格式中可以写字面量（如 -、/、空格、固定单词），需与字符串逐字符对应。
```sql
TO_DATE('2025-10-18','YYYY-MM-DD')
TO_DATE('18 of Oct 2025','DD "of" MON YYYY')
TO_DATE('2025/10/18', 'YYYY-MM-DD');  -- 也 OK（分隔符不同也能匹配）
```
使用 FX（Exact match）时，所有字面量、空格、大小写必须完全匹配：
```sql
TO_DATE('2025-10-18','FXYYYY-MM-DD') ✅
TO_DATE('2025/10/18','FXYYYY-MM-DD') ❌ （分隔符不同）
```

#### Using a SEQUENCE
```sql
CREATE SEQUENCE schema_name.sequence_name
[INCREMENT BY interval]
[START WITH first_number]
[MAXVALUE max_value | NOMAXVALUE]
[MINVALUE min_value | NOMINVALUE]
[CYCLE | NOCYCLE]
[CACHE cache_size | NOCACHE]
[ORDER | NOORDER];

sequence_name.nextval
sequence_name.currval

-- NEXTVAL 第一次返回的就是 START WITH
-- CURRVAL 仅在当前会话且已调用过 NEXTVAL 后可用；否则报 ORA-08002
-- CURRVAL 拿到的是本会话最近一次 NEXTVAL 的值，不是“全库最新”

-- 例子：
-- 序列：主键自增来源
CREATE SEQUENCE seq_emp_id
  START WITH 1
  INCREMENT BY 1
  CACHE 100;

-- 主表：EMP
CREATE TABLE emp (
  id       NUMBER PRIMARY KEY,
  name     VARCHAR2(50) NOT NULL,
  hiredate DATE NOT NULL
);

-- 从表举例1：员工详情（外键指向 EMP.ID）
CREATE TABLE emp_detail (
  emp_id    NUMBER NOT NULL,
  address   VARCHAR2(200),
  phone     VARCHAR2(30),
  CONSTRAINT fk_emp_detail_emp
    FOREIGN KEY (emp_id) REFERENCES emp(id)
);

-- 从表举例2：员工日志（外键指向 EMP.ID）
CREATE TABLE emp_log (
  emp_id    NUMBER NOT NULL,
  action    VARCHAR2(30) NOT NULL,
  action_ts TIMESTAMP DEFAULT SYSTIMESTAMP NOT NULL,
  CONSTRAINT fk_emp_log_emp
    FOREIGN KEY (emp_id) REFERENCES emp(id)
);

-- 插入主表：用 NEXTVAL 生成新主键
INSERT INTO emp (id, name, hiredate)
VALUES (seq_emp_id.NEXTVAL,
        'Alice',
        TO_DATE('2025-10-18 14:30:00','YYYY-MM-DD HH24:MI:SS'));

-- 复用刚刚那次的主键：同一会话内使用 CURRVAL
INSERT INTO emp_detail (emp_id, address, phone)
VALUES (seq_emp_id.CURRVAL, 'Melbourne, VIC', '0400-000-000');

INSERT INTO emp_log (emp_id, action)
VALUES (seq_emp_id.CURRVAL, 'CREATE');

COMMIT;
```

### Update
```sql
UPDATE
    table_name
SET
    column1 = value1,
    column2 = value2,
    column3 = value3,
    ...
WHERE
    condition;

-- subquery
UPDATE 
    target_table
SET 
    column1 = (
      SELECT value_column
        FROM source_table
      WHERE source_table.id = target_table.id
    )
WHERE EXISTS (
      SELECT value_column
        FROM source_table
      WHERE source_table.id = target_table.id
    );
```

### LOWER() and UPPER()
Since we cannot "know" the case of our data, SQL has two functions UPPER
and LOWER used to modify case:
```sql
SELECT * FROM table_name WHERE LOWER(column) = LOWER(value);
SELECT * FROM table_name WHERE UPPER(column) = UPPER(value);
```

### Delete
```sql
DELETE
FROM
    table_name
WHERE
    condition;

-- Deleting all rows from a table
DELETE FROM table_name;
```

## Transaction Management

### Transaction Properties
📌 Transaction Properties (事务特性)

在数据库系统中，一个事务必须具备以下四个属性（ACID）：

1. Atomicity（原子性）

所有数据库操作（SQL请求）必须 全部完成或全部不做。

如果事务中的任何一个操作失败，则之前的所有操作都必须回滚（撤销）。

2. Consistency（一致性）

事务必须使数据库从一个一致状态变换到另一个一致状态。

保证事务前后数据的完整性约束不被破坏。

3. Isolation（隔离性）

事务在执行过程中不应受到其他并发事务的干扰。

某个事务在执行时所使用的数据在其完成前不应被其他事务访问。

4. Durability（持久性）

一旦事务提交，所做的修改就是永久性的。

即使系统发生故障，已提交的数据也不会丢失。

### Transaction Management

- Follows the ACID properties
- Transaction boundaries
    - Start
        - first SQL statement is executed (eg. Oracle)
        - Some systems have a BEGIN WORK type command
    - End
        - COMMIT or ROLLBACK
- Concurrency Management
- Restart and Recovery

### Concurrency Management

- Locking mechanism
    - Shared lock
    - Exclusive lock

### Deadlock

- Dealing with deadlock
    - Deadlock prevention
    - Deadlock avoidance
    - Deadlock detection and recovery

### Database Recovery

- Transaction Log
    - Record for beginning of transaction
    - Type of operation being performed (update, delete, insert)
    - Names of objects affected by the transaction (the name of the table)
    - “Before” and “after” values for updated fields
    - Pointers to previous and next transaction log entries for the same transaction
    - The ending (COMMIT) of the transaction
- Checkpoint
    - Accepting new transactions is temporarily halted, and current transactions are suspended.
    - Results of committed transactions are made permanent (force-written to the disk).
    - A checkpoint record is written in the log.
    - Execution of transactions is resumed.

- Software Crash Recovery
    - Write Through
        1. 构建 REDO 和 UNDO 列表

            - 根据日志，从**最近的检查点（Checkpoint）**开始向前读取，构建两个列表：
                - **REDO list**：包含所有 **已提交事务** 的 Transaction ID。
                - **UNDO list**：包含所有 **未完成（未提交或已回滚）事务** 的 Transaction ID。

        2. UNDO 未完成事务（从最近开始）

            - 对 `UNDO list` 中的事务按**逆序（从新到旧）**处理；
            - 使用 **before image（变更前数据）** 进行 **ROLLBACK**；
            - 目的是撤销未提交事务对数据库的影响。

        3. REDO 已提交事务（从最早开始）

            - 对 `REDO list` 中的事务按**顺序（从旧到新）**处理；
            - 使用 **after image（变更后数据）** 进行 **ROLLFORWARD**；
            - 目的是重做已提交事务的操作，确保持久化完成。

    - Deferred Write
        1. 数据库只在事务提交（COMMIT）之后才写入磁盘
            - 所有更改首先保存在内存中（如 redo log buffer）；
            - 只有在事务真正提交之后，才将更改数据写入数据库的数据文件；
            - 在崩溃前未提交的事务更改 **根本不会写入磁盘**。

        2. 只需 **Redo（重做）已提交事务**
            - 崩溃恢复时只需要将已提交事务的更改重新应用（roll forward）；
            - **无需回滚未提交事务**，因为它们根本未写入磁盘（不存在“脏写”）；
            - 相比 Write Through 策略，此策略的恢复更简单快速。

# Week 8 SQL Part I

##  SQL statement, clause, predicate

**Anatomy**

```sql
SELECT <select_list>
FROM   <table_or_joins>
WHERE  <predicate>
[ORDER BY <expr> [ASC|DESC] [NULLS FIRST|LAST]]
```

* A **predicate** is any Boolean expression in `WHERE` (also in `JOIN ... ON`, `HAVING`, `CASE WHEN`, etc.).
* Oracle evaluates the predicate **per row** using **three‑valued logic**: `TRUE`, `FALSE`, `UNKNOWN` (NULL involved).
* Only rows where the predicate evaluates to **TRUE** are returned.

---

## Writing SQL predicates

### Comparison operators

`>`, `<`, `=`, `<>` (preferred), `!=`, `>=`, `<=`

**Notes**

* Any comparison with `NULL` is `UNKNOWN` (except `IS NULL` / `IS NOT NULL`).
* Character comparisons use session collation rules; for safe case‑insensitive search, use `UPPER(col) = UPPER(:val)` or `REGEXP_LIKE(col, :val, 'i')`.

**Examples**

```sql
WHERE salary >= 120000
WHERE last_name <> 'Smith'
WHERE start_dt < DATE '2025-01-01'
```

### Range: `BETWEEN`

* Syntax: `expr BETWEEN low AND high`
* **Inclusive** of both ends.

```sql
WHERE order_total BETWEEN 100 AND 200  -- 100 ≤ order_total ≤ 200
```

**Date tip**: For full‑day ranges prefer **half‑open** windows to avoid time parts:

```sql
WHERE order_dt >= DATE '2025-10-01'
  AND order_dt <  DATE '2025-11-01'
```

### Set membership: `IN`

```sql
WHERE status IN ('NEW','PENDING','HOLD')
```

**Pitfall**: `NOT IN` with a list containing `NULL` yields **no rows** (predicate becomes `UNKNOWN`). Prefer `NOT EXISTS` or filter out NULLs in the subquery.

### Pattern matching: `LIKE` and `REGEXP_LIKE`

* `LIKE` wildcards: `%` (0+ chars), `_` (single char).
* Use `ESCAPE '\'` to treat wildcard chars literally.

```sql
WHERE name LIKE 'SMI%'
WHERE code LIKE 'A\_%' ESCAPE '\'  -- matches A_*
-- Case‑insensitive, flexible patterns:
WHERE REGEXP_LIKE(email, '\\.(edu|org)$', 'i')
```

### NULL checks: `IS NULL`

```sql
WHERE cancelled_dt IS NULL
WHERE cancelled_dt IS NOT NULL
```

### Subquery predicates: `ANY`, `ALL`, `EXISTS`

* `> ANY (subq)`: greater than **at least one** value (i.e., `> MIN(...)`).
* `> ALL (subq)`: greater than **every** value (i.e., `> MAX(...)`).
* `EXISTS (correlated_subq)`: true if subquery returns **any** row; **ignores NULLs** inside.

```sql
-- Price higher than at least one competitor
WHERE price > ANY (SELECT competitor_price FROM price_survey)

-- Price higher than all competitors
WHERE price > ALL (SELECT competitor_price FROM price_survey)

-- Has at least one active rental
WHERE EXISTS (
  SELECT 1
  FROM   drone.rental r
  WHERE  r.drone_id = d.drone_id
  AND    r.rent_in_dt IS NULL
)
```

---

## Combining predicates

### Logical operators & precedence

* Operators: `NOT` > `AND` > `OR` (use parentheses to be explicit).

### Truth tables (three‑valued logic)

**AND**

| A \ B | **T** | **U** | **F** |
| :---- | :---: | :---: | :---: |
| **T** |   T   |   U   |   F   |
| **U** |   U   |   U   |   F   |
| **F** |   F   |   F   |   F   |

**OR**

| A \ B | **T** | **U** | **F** |
| :---- | :---: | :---: | :---: |
| **T** |   T   |   T   |   T   |
| **U** |   T   |   U   |   U   |
| **F** |   T   |   U   |   F   |

**NOT**

|  A  | NOT A |
| :-: | :---: |
|  T  |   F   |
|  U  |   U   |
|  F  |   T   |

---

## Arithmetic in SQL

* Operators: `+`, `-`, `*`, `/`.
* **Any arithmetic with `NULL` → `NULL`** (use `NVL`/`COALESCE` if needed).
* Division by zero raises `ORA-01476`.
* Date arithmetic: `DATE + n` adds **n days**; subtracting two `DATE`s returns **number of days** (`NUMBER`).

```sql
SELECT (salary + NVL(bonus,0)) AS total_pay
FROM   employees;

SELECT SYSDATE + 7 AS one_week_from_now FROM dual;    -- +7 days
SELECT (DATE '2025-10-31' - DATE '2025-10-01') AS days_span FROM dual;  -- 30
```

---

## Handling NULLs — `NVL` and friends

### `NVL(expr1, expr2)`

Replaces `NULL` with a value. **Both arguments must be the same datatype** or implicitly convertible.

> 规则：两个参数（`expr1` 与 `expr2`）必须是相同数据类型，或者 Oracle 能够隐式转换成同一类型。

```sql
NVL(enrolmark, 0)
NVL(enrolgrade, 'WH')
```

### Related functions (know when to prefer)

* `NVL2(expr, value_if_not_null, value_if_null)`
* `COALESCE(a,b,c,...)` — returns first non‑NULL; **ANSI** and variadic; often preferable in portable SQL.
* `CASE WHEN expr IS NULL THEN ... ELSE ... END` — for complex logic.

```sql
SELECT COALESCE(nick_name, first_name, 'N/A') AS display_name FROM users;
```

---

## Column aliases

* Syntax: `expr AS alias` (keyword `AS` is optional in Oracle).
* Aliases are usable in `ORDER BY`, **not** in `WHERE` of the same SELECT.

```sql
SELECT salary * 12 AS annual_salary
FROM   employees
ORDER BY annual_salary DESC;  -- valid
```

---

## Ordering (sorting) results

* `ORDER BY <expr> [ASC|DESC]` (default **ASC**).
* Control placement of NULLs: `NULLS FIRST` | `NULLS LAST`.
* Oracle defaults: in **ASC**, NULLs sort **LAST**; in **DESC**, NULLs sort **FIRST**.

```sql
ORDER BY last_name ASC NULLS LAST,
         hire_date DESC NULLS FIRST;
```

---

## Removing duplicate rows

* `SELECT DISTINCT ...` removes **duplicate rows across the entire select list**.
* Be deliberate—`DISTINCT` can be expensive; consider `GROUP BY` when aggregating.

```sql
SELECT DISTINCT department_id FROM employees;
```

---

## Joining tables (ANSI JOINs — required)

> For assessment: **do not** place joins in the `WHERE` clause; use ANSI join syntax.

### Join types & patterns

```sql
-- Inner join
SELECT e.emp_id, d.dept_name
FROM   employees e
JOIN   departments d
  ON   d.dept_id = e.dept_id;

-- Left outer join
SELECT e.emp_id, d.dept_name
FROM   employees e
LEFT JOIN departments d
  ON   d.dept_id = e.dept_id;

-- Full outer join
SELECT e.emp_id, d.dept_name
FROM   employees e
FULL OUTER JOIN departments d
  ON   d.dept_id = e.dept_id;

-- Cross join (Cartesian)
SELECT e.emp_id, p.perm
FROM   employees e
CROSS JOIN perms p;
```

### `USING` vs `ON`

* `USING(col)` auto‑matches same‑named columns and **returns one copy** of the column.
* `ON` allows arbitrary join expressions and keeps both columns (qualify names).

```sql
SELECT *
FROM   orders o
JOIN   customers c
USING (customer_id);
```

### `NATURAL` JOIN (use sparingly)

* Automatically joins on **all columns with matching names**. Can break if schema changes. Prefer `USING`/`ON` for clarity.

---

## Oracle date & time

### Types

* `DATE` — stores **date + time to seconds**.
* `TIMESTAMP` — higher precision; `TIMESTAMP WITH TIME ZONE` / `WITH LOCAL TIME ZONE` add TZ semantics.

### Current date/time

* `SYSDATE` (type `DATE`) — DB server clock.
* `CURRENT_DATE` (type `DATE`) — session time zone.
* `SYSTIMESTAMP` / `CURRENT_TIMESTAMP` — timestamp variants.
* `USER` — current schema name; also `SESSIONTIMEZONE`, `DBTIMEZONE` if needed.

### Formatting & parsing

* Display with `TO_CHAR(expr, 'fmt')`; parse with `TO_DATE(text, 'fmt')` or ANSI literals.
* Prefer **ANSI literals** to avoid NLS issues:

  * `DATE 'YYYY-MM-DD'`
  * `TIMESTAMP 'YYYY-MM-DD HH24:MI:SS'`

```sql
SELECT rent_no,
       drone_id,
       TO_CHAR(rent_out_dt, 'DD-Mon-YYYY') AS date_out,
       NVL(TO_CHAR(rent_in_dt, 'DD-Mon-YYYY'), 'Still out') AS date_in
FROM   drone.rental;
```

### Date arithmetic helpers

* Truncate time: `TRUNC(dt)` (to day) or `TRUNC(dt, 'MM')` (to month).
* Add months: `ADD_MONTHS(dt, n)`; month diff: `MONTHS_BETWEEN(a,b)`.
* Intervals: `NUMTODSINTERVAL(n,'DAY'|'HOUR'|...)`, `NUMTOYMINTERVAL`.

---

## Worked subquery patterns

### `EXISTS` vs `IN`

```sql
-- Customers who have at least one rental
SELECT c.customer_id, c.name
FROM   customers c
WHERE  EXISTS (
  SELECT 1 FROM drone.rental r
  WHERE  r.customer_id = c.customer_id
);

-- Customers with a rental on specific day (using half‑open range)
SELECT c.customer_id, c.name
FROM   customers c
WHERE  EXISTS (
  SELECT 1 FROM drone.rental r
  WHERE  r.customer_id = c.customer_id
  AND    r.rent_out_dt >= DATE '2025-10-01'
  AND    r.rent_out_dt <  DATE '2025-10-02'
);
```

### `ANY` / `ALL`

```sql
-- Drones heavier than all drones in model X
SELECT d.drone_id
FROM   drone.inventory d
WHERE  d.weight_kg > ALL (
  SELECT weight_kg FROM drone.inventory WHERE model = 'X'
);
```

---

## Common pitfalls & best practices

* ✅ Use **ANSI JOIN** syntax; avoid old `WHERE` join style.
* ✅ Write **half‑open** date ranges (`>= start AND < next_day`) to avoid time‑component bugs.
* ✅ Be explicit with parentheses around complex `AND/OR` logic.
* ✅ Prefer `COALESCE` for portability; use `NVL` when you need Oracle‑specific semantics.
* ⚠️ `NOT IN (subq)` where subq returns `NULL` causes no rows; use `NOT EXISTS`.
* ⚠️ Comparisons with `NULL` are `UNKNOWN`; use `IS NULL` / `IS NOT NULL`.
* ⚠️ Don’t rely on implicit type conversions; use proper literals (`DATE 'YYYY-MM-DD'`).
* ⚠️ `DISTINCT` de‑dupes across the **whole** select list; can mask data issues and impact performance.
* ⚠️ Alias visibility: usable in `ORDER BY`, not in `WHERE`.

---

## Quick reference (copy‑ready)

```sql
-- Inclusive between
col BETWEEN :low AND :high

-- Half‑open date window
col >= DATE '2025-10-01' AND col < DATE '2025-11-01'

-- LIKE with escape
col LIKE 'A\_%' ESCAPE '\'

-- Null‑safe arithmetic
NVL(col, 0)

-- EXISTS (ignores NULLs inside)
EXISTS (SELECT 1 FROM t WHERE t.k = s.k)

-- ANY / ALL
x > ANY (SELECT y FROM t)  -- x > MIN(y)
x > ALL  (SELECT y FROM t) -- x > MAX(y)

-- Sort with explicit NULL placement
ORDER BY score DESC NULLS LAST
```

# Week 9 SQL Intermediate

## Aggregate Functions

- COUNT
- MAX
- MIN
- SUM
- AVG

```sql
SELECT
MAX(drone_flight_time)
FROM
drone.drone;

SELECT
MIN(drone_flight_time)
FROM
drone.drone;

SELECT
AVG(drone_flight_time)
FROM
drone.drone;

SELECT COUNT(*)
FROM drone.drone
WHERE drone_flight_time > 100;
```

---

> count(\*) and count(column_name)  
> count(\*)统计的是所有的记录，不受任何列是否为 NULL 影响  
> 在oracle中count(1)等价于count(*)  
> count(column_name)只统计该列非 NULL 的行数

## GROUP BY

```sql
SELECT
  *
FROM table_name
GROUP BY column_name
```

当group by和聚合函数一起使用的时候  
- group by决定了如何进行分组
- 聚合函数在每个分组内进行计算

---

group by中列的顺序可以随意调换，最后分组的结果是一样的
order by中列的顺序不能随意调换，最后的排序结果会不一样

---

group by中不能使用alias  
order by中可以使用alias  

oracle中SQL的执行顺序:  
1. FROM/JOIN
2. WHERE
3. GROUP BY
4. Aggregate Functions
5. HAVING
6. SELECT
7. ORDER BY

到第六步的select才会应用alias  
到第七步的order by才可以使用alias

---

GROUP BY 子句中的列不一定必须出现在 SELECT 里  
但是，SELECT 里的非聚合列必须出现在 GROUP BY 中  

非聚合列指的是 SELECT 中直接出现的普通列（没有放进聚合函数里的列） 

```sql
SELECT deptno, COUNT(*)
FROM emp
GROUP BY deptno;   -- ✅ 正确

SELECT deptno, job, COUNT(*)
FROM emp
GROUP BY deptno;   -- ❌ 错误，job 不是聚合列，也不在 GROUP BY里
```

## HAVING

```sql
SELECT group_by_column, aggregate_function(column)
FROM table_name
[WHERE condition]         -- 分组前过滤（行级过滤）
GROUP BY group_by_column
HAVING aggregate_condition -- 分组后过滤（组级过滤）
[ORDER BY ...];
```

## Subqueries

1. where子句里的子查询（最常见）

    ```sql
    -- 标量子查询（返回单个值）
    SELECT ename, sal
    FROM emp
    WHERE sal > (SELECT AVG(sal) FROM emp);   

    -- 多行子查询（配合 IN/EXISTS/ANY/ALL）
    SELECT ename, deptno
    FROM emp
    WHERE deptno IN (SELECT deptno FROM dept WHERE loc = 'NEW YORK');
    ```
2. from子句里的子查询

    ```sql
    -- 子查询结果作为一张 临时表。
    SELECT d.dname, t.avg_sal
    FROM (SELECT deptno, AVG(sal) AS avg_sal
          FROM emp
          GROUP BY deptno) t
    JOIN dept d ON t.deptno = d.deptno;
    ```
3. select子句里的子查询

    ```sql
    -- 子查询返回一个值，作为结果集中的一列。
    SELECT e.ename,
         (SELECT d.dname 
          FROM dept d 
          WHERE d.deptno = e.deptno) AS dept_name
    FROM emp e;
    ```

### Types of Subqueries

1. 单值子查询
2. 多行子查询
3. 多列子查询

### Comparison Operators for Subquery

- Operator for single value comperation
    =, <, >
- Operator for multiple rows or a list comperation
  IN
  ALL, ANY combined with <, >

---

1. ANY
  - \> ANY 等价于大于最小值
  - < ANY 等价于小于最大值
2. ALL
  - \> ALL 等价于大于最大值
  - < ALL 等价于小于最小值

# Week 10 SQL Advanced

## CASE

## Subquery – nested, inline, correlated

## Views

## Joins - self join, outer join

## Set Operators

## Oracle Functions

# Week 11 Non Relational Databases

## Big Data Characteristics
## NoSQL Data Models
## NoSQL Databases
## MongonDB
### Create
### RETRIEVE
### UPDATE
### DELETE

# Week 12 BI, Data Warehousing and Legal/Ethical Issues
workshop used for test  
no recording  
pass