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
| 类别          | 数据类型                   | 示例                         | 说明                                           |
| ------------- | -------------------------- | ---------------------------- | ---------------------------------------------- |
| **Text**      | `CHAR(size)`               | `CHAR(10)`                   | 定长字符，'apple' = 'apple     '（自动补空格） |
|               | `VARCHAR2(size)`           | `VARCHAR2(10)`               | 变长字符，'apple' ≠ 'apple     '               |
| **Numbers**   | `NUMBER(precision, scale)` | `NUMBER(7)` 或 `NUMBER(7,0)` | 精度 7，无小数，例如 `7456124`                 |
|               |                            | `NUMBER(9,2)`                | 总 9 位，2 位小数，例如 `7456123.89`           |
|               |                            | `NUMBER(8,1)`                | 总 8 位，1 位小数，例如 `7456123.9`            |
| **Date/Time** | `DATE`                     |                              | 存储日期+时间（到秒），内部为公历日期          |
|               | `TIMESTAMP`                |                              | 存储日期+时间（可到小数秒），本单元未使用      |
|               | `TIMESTAMP WITH TIME ZONE` |                              | 存储日期+时间+时区                             |


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

2. CASCADE （级联删除）

* **含义**：删除父表（主键表）的行时，自动删除子表中对应的外键行。
* **例子**：

  * 删除 `DEPARTMENT.dept_no=10` → 自动把 `EMPLOYEE` 表中所有 `dept_no=10` 的行一并删除。

---

3. NULLIFY （置空，Oracle 语法：`ON DELETE SET NULL`）

* **含义**：删除父表的主键行时，子表中对应的外键字段会 **更新为 NULL**。
* **例子**：

  * 删除 `DEPARTMENT.dept_no=10` → `EMPLOYEE` 表中所有 `dept_no=10` 的行会变成 `dept_no=NULL`。

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