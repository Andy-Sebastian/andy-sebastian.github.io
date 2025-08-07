# Week 1

## 1. 算术（Arithmetic）操作符
| 操作符 | 英文名          | 含义               | 示例             |
|:------:|:---------------:|:------------------:|:----------------:|
| `+`    | Addition        | 加                 | `3 + 2 == 5`     |
| `-`    | Subtraction     | 减                 | `3 - 2 == 1`     |
| `*`    | Multiplication  | 乘                 | `3 * 2 == 6`     |
| `/`    | Division        | 真除（浮点结果）    | `3 / 2 == 1.5`   |
| `//`   | Floor Division  | 地板除（向下取整）  | `7 // 3 == 2`    |
| `%`    | Modulus         | 取余               | `7 % 3 == 1`     |
| `**`   | Exponentiation  | 幂                 | `2 ** 3 == 8`    |

## 2. 比较（Comparison）操作符
| 操作符 | 英文名         | 含义     | 示例      |
|:------:|:--------------:|:--------:|:---------:|
| `==`   | Equal          | 等于     | `a == b`  |
| `!=`   | Not Equal      | 不等于   | `a != b`  |
| `>`    | Greater Than   | 大于     | `a > b`   |
| `<`    | Less Than      | 小于     | `a < b`   |
| `>=`   | Greater Equal  | 大于等于 | `a >= b`  |
| `<=`   | Less Equal     | 小于等于 | `a <= b`  |

## 3. 赋值（Assignment）操作符
| 操作符 | 英文名                    | 含义                 | 等价于            |
|:------:|:-------------------------:|:--------------------:|:-----------------:|
| `=`    | Assignment                | 直接赋值             | —                 |
| `+=`   | Add AND Assignment        | 加并赋值             | `x = x + y`       |
| `-=`   | Subtract AND Assignment   | 减并赋值             | `x = x - y`       |
| `*=`   | Multiply AND Assignment   | 乘并赋值             | `x = x * y`       |
| `/=`   | Divide AND Assignment     | 除并赋值             | `x = x / y`       |
| `//=`  | Floor Divide AND Assign   | 地板除并赋值         | `x = x // y`      |
| `%=`   | Modulus AND Assignment    | 取余并赋值           | `x = x % y`       |
| `**=`  | Exponent AND Assignment   | 幂运算并赋值         | `x = x ** y`      |
| `&=`   | Bitwise AND Assignment    | 位与并赋值           | `x = x & y`       |
| `\|=`  | Bitwise OR Assignment     | 位或并赋值           | `x = x \| y`      |
| `^=`   | Bitwise XOR Assignment    | 位异或并赋值         | `x = x ^ y`       |
| `<<=`  | Left Shift AND Assignment | 左移并赋值           | `x = x << y`      |
| `>>=`  | Right Shift AND Assignment| 右移并赋值           | `x = x >> y`      |

## 4. 逻辑（Logical）操作符
| 操作符 | 英文名      | 含义     | 示例           |
|:------:|:-----------:|:--------:|:---------------|
| `and`  | Logical AND | 逻辑与   | `a and b`      |
| `or`   | Logical OR  | 逻辑或   | `a or b`       |
| `not`  | Logical NOT | 逻辑非   | `not a`        |

## 5. 位（Bitwise）操作符
| 操作符 | 英文名         | 含义       | 示例         |
|:------:|:--------------:|:----------:|:------------:|
| `&`    | Bitwise AND    | 按位与     | `a & b`      |
| `\|`   | Bitwise OR     | 按位或     | `a \| b`     |
| `^`    | Bitwise XOR    | 按位异或   | `a ^ b`      |
| `~`    | Bitwise NOT    | 按位取反   | `~a`         |
| `<<`   | Left Shift     | 左移       | `a << 2`     |
| `>>`   | Right Shift    | 右移       | `a >> 2`     |

## 6. 成员（Membership）操作符
| 操作符   | 英文名   | 含义               | 示例                    |
|:--------:|:--------:|:------------------:|:-----------------------:|
| `in`     | in       | 在序列或集合中     | `'a' in 'abc'  # True`  |
| `not in` | not in   | 不在序列或集合中   | `1 not in [2,3,4]`      |

## 7. 身份（Identity）操作符
| 操作符   | 英文名  | 含义             | 示例          |
|:--------:|:-------:|:----------------:|:-------------:|
| `is`     | is      | 对象标识相同     | `a is b`      |
| `is not` | is not  | 对象标识不同     | `a is not b`  |

## 8. Python 变量名的要求和规范

### 一、语法层面要求
1. **合法字符**  
   - 只能包含：  
     - 字母（A–Z，a–z）  
     - 数字（0–9）  
     - 下划线（`_`）  
2. **首字符限制**  
   - 变量名**必须**以字母或下划线开头，**不能**以数字开头  
   - 合法示例：  
     ```python
     _count = 0
     total_sum = 100
     a1 = "hello"
     ```  
   - 非法示例：  
     ```python
     1st = 10      # 以数字开头
     my-var = 5    # 包含非法字符 “-”
     ```  
3. **关键字冲突**  
   - 不能使用 Python 保留字（关键字）作为变量名  
   - 如：`if`, `for`, `while`, `class`, `import` 等  
   - 可通过 `import keyword; keyword.kwlist` 查看完整列表  

4. **大小写敏感**  
   - `myVar`、`myvar`、`MYVAR` 都是**不同**的名字  

5. **长度不限**  
   - 理论上没有硬性长度限制，但过长会影响可读性  

### 二、风格（PEP 8）推荐
1. **小写加下划线**  
   - 例如：`total_count`, `user_name`, `file_path`  
2. **常量大写**  
   - 模块级别不变的变量建议用全大写加下划线：  
     ```python
     MAX_RETRIES = 5
     DEFAULT_TIMEOUT = 30
     ```  
3. **避免单字符**  
   - 除非在非常局部或循环计数中，用 `i, j, k`；其他场景尽量用描述性名称  
4. **下划线前缀/后缀意义**  
   - `_name`：模块或类的“私有”成员（非强制，只是约定）  
   - `__name`：类中触发名称改写（name-mangling）  
   - `name_`：避免与关键字冲突（如 `class_` 避免与 `class` 冲突）

### 三、示例对比

| 名称            | 含义／场景                  | 是否推荐   |
|:---------------:|:---------------------------:|:---------:|
| `count`         | 计数变量                    | 推荐       |
| `totalCount`    | 驼峰命名（在 Python 中不常用）| 不推荐     |
| `MAX_LIMIT`     | 常量                        | 推荐       |
| `_temp`         | 私有／内部使用               | 推荐       |
| `class`         | Python 关键字                | **非法**   |
| `1_value`       | 以数字开头                  | **非法**   |

> **总结**：  
> - 语法上，变量名只能用字母、数字、下划线，且不能以数字开头，也不能是关键字；  
> - 风格上，遵循 PEP 8 建议使用小写加下划线的“snake_case”，常量则使用全大写加下划线。  