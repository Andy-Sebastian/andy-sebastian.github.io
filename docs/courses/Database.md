# Week 1

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

