# Week 1 Introduction to Python, Variables, Statements and Expressions

## 算术（Arithmetic）操作符
| 操作符 |     英文名     |        含义        |      示例      |
| :----: | :------------: | :----------------: | :------------: |
|  `+`   |    Addition    |         加         |  `3 + 2 == 5`  |
|  `-`   |  Subtraction   |         减         |  `3 - 2 == 1`  |
|  `*`   | Multiplication |         乘         |  `3 * 2 == 6`  |
|  `/`   |    Division    |  真除（浮点结果）  | `3 / 2 == 1.5` |
|  `//`  | Floor Division | 地板除（向下取整） | `7 // 3 == 2`  |
|  `%`   |    Modulus     |        取余        |  `7 % 3 == 1`  |
|  `**`  | Exponentiation |         幂         | `2 ** 3 == 8`  |

## 比较（Comparison）操作符
| 操作符 |    英文名     |   含义   |   示例   |
| :----: | :-----------: | :------: | :------: |
|  `==`  |     Equal     |   等于   | `a == b` |
|  `!=`  |   Not Equal   |  不等于  | `a != b` |
|  `>`   | Greater Than  |   大于   | `a > b`  |
|  `<`   |   Less Than   |   小于   | `a < b`  |
|  `>=`  | Greater Equal | 大于等于 | `a >= b` |
|  `<=`  |  Less Equal   | 小于等于 | `a <= b` |

## 赋值（Assignment）操作符
| 操作符   | 英文名                                  | 含义                 | 等价于 / 示例                 | 版本要求    |
| -------- | --------------------------------------- | -------------------- | ----------------------------- | ----------- |
| `=`      | Assignment                              | 直接赋值             | `x = y`                       | 所有版本    |
| `+=`     | Add AND Assignment                      | 加并赋值             | `x = x + y`                   | 所有版本    |
| `-=`     | Subtract AND Assignment                 | 减并赋值             | `x = x - y`                   | 所有版本    |
| `*=`     | Multiply AND Assignment                 | 乘并赋值             | `x = x * y`                   | 所有版本    |
| `/=`     | Divide AND Assignment                   | 除并赋值             | `x = x / y`                   | 所有版本    |
| `//=`    | Floor Divide AND Assign                 | 地板除并赋值         | `x = x // y`                  | 所有版本    |
| `%=`     | Modulus AND Assignment                  | 取余并赋值           | `x = x % y`                   | 所有版本    |
| `**=`    | Exponent AND Assignment                 | 幂运算并赋值         | `x = x ** y`                  | 所有版本    |
| `&=`     | Bitwise AND Assignment                  | 位与并赋值           | `x = x & y`                   | 所有版本    |
| `\|=`    | Bitwise OR Assignment                   | 位或并赋值           | `x = x \| y`                  | 所有版本    |
| `^=`     | Bitwise XOR Assignment                  | 位异或并赋值         | `x = x ^ y`                   | 所有版本    |
| `<<=`    | Left Shift AND Assignment               | 左移并赋值           | `x = x << y`                  | 所有版本    |
| `>>=`    | Right Shift AND Assignment              | 右移并赋值           | `x = x >> y`                  | 所有版本    |
| `:=`     | Walrus Operator / Assignment Expression | 赋值表达式           | `if (n := len(lst)) > 3: ...` | Python 3.8+ |
| 多重赋值 | Multiple Assignment                     | 一次给多个变量赋值   | `a, b = 1, 2`                 | 所有版本    |
| 解包赋值 | Unpacking Assignment                    | 拆分可迭代对象并赋值 | `a, b, *rest = [1, 2, 3, 4]`  | Python 3.x  |
| 链式赋值 | Chained Assignment                      | 多个变量赋相同值     | `a = b = c = 0`               | 所有版本    |
| 注解赋值 | Annotated Assignment                    | 带类型提示的赋值     | `count: int = 0`              | Python 3.6+ |

## 逻辑（Logical）操作符
| 操作符 |   英文名    |  含义  | 示例      |
| :----: | :---------: | :----: | :-------- |
| `and`  | Logical AND | 逻辑与 | `a and b` |
|  `or`  | Logical OR  | 逻辑或 | `a or b`  |
| `not`  | Logical NOT | 逻辑非 | `not a`   |

## 位（Bitwise）操作符
| 操作符 |   英文名    |   含义   |   示例   |
| :----: | :---------: | :------: | :------: |
|  `&`   | Bitwise AND |  按位与  | `a & b`  |
|  `\|`  | Bitwise OR  |  按位或  | `a \| b` |
|  `^`   | Bitwise XOR | 按位异或 | `a ^ b`  |
|  `~`   | Bitwise NOT | 按位取反 |   `~a`   |
|  `<<`  | Left Shift  |   左移   | `a << 2` |
|  `>>`  | Right Shift |   右移   | `a >> 2` |

## 成员（Membership）操作符
|  操作符  | 英文名 |       含义       |          示例          |
| :------: | :----: | :--------------: | :--------------------: |
|   `in`   |   in   |  在序列或集合中  | `'a' in 'abc'  # True` |
| `not in` | not in | 不在序列或集合中 |   `1 not in [2,3,4]`   |

## 身份（Identity）操作符
|  操作符  | 英文名 |     含义     |     示例     |
| :------: | :----: | :----------: | :----------: |
|   `is`   |   is   | 对象标识相同 |   `a is b`   |
| `is not` | is not | 对象标识不同 | `a is not b` |

## Python 运算符优先级（从高到低）

Python 会优先计算算术运算符，然后是关系运算符，最后才是逻辑运算符。括号可用于提升代码可读性。

---

### 运算符优先级表

| 优先级 | 描述                 | 运算符                                           |
| ------ | -------------------- | ------------------------------------------------ |
| 最高   | 指数（乘方）         | `**`                                             |
|        | 乘、除、地板除、取余 | `*`, `/`, `//`, `%`                              |
|        | 加、减               | `+`, `-`                                         |
|        | 比较与成员测试       | `==`, `!=`, `<=`, `>=`, `<`, `>`, `in`, `not in` |
|        | 布尔非（NOT）        | `not`                                            |
|        | 布尔与（AND）        | `and`                                            |
| 最低   | 布尔或（OR）         | `or`                                             |

---

Python 里没有“+= 和 + 谁优先”的问题，对于 x += expr 
  1.	先按正常运算符优先级把右侧 expr 计算出来（比如先 * 后 +），
  2.	再对左侧做增量赋值：优先调用 x.__iadd__(expr)；若不支持，就退化为 x = x + expr。

---

### 常见错误提示

**错误写法：**
```python
'x' in y or z
```

##  Python 变量名的要求和规范

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

|     名称     |           含义／场景           | 是否推荐 |
| :----------: | :----------------------------: | :------: |
|   `count`    |            计数变量            |   推荐   |
| `totalCount` | 驼峰命名（在 Python 中不常用） |  不推荐  |
| `MAX_LIMIT`  |              常量              |   推荐   |
|   `_temp`    |         私有／内部使用         |   推荐   |
|   `class`    |         Python 关键字          | **非法** |
|  `1_value`   |           以数字开头           | **非法** |

> **总结**：  
> - 语法上，变量名只能用字母、数字、下划线，且不能以数字开头，也不能是关键字；  
> - 风格上，遵循 PEP 8 建议使用小写加下划线的“snake_case”，常量则使用全大写加下划线。  

## Python 舍入与取整速查：`round()` 与 `int()`

### `round()` 知识点
- **签名**：`round(number, ndigits=None)`
- **规则**：就近取整；**遇 0.5 时取偶**（Banker’s rounding）。
- **`ndigits` 含义**  
  - `> 0`：保留到小数点后 `ndigits` 位  
  - `= 0`：到个位  
  - `< 0`：到十/百/千位（按 `10**(-ndigits)`）
- **返回类型**  
  - 省略 `ndigits`：返回 `int`  
  - 指定了 `ndigits`：**类型随输入**（`float→float`，`int→int`）
- **浮点陷阱**：二进制近似导致观感差异，如 `round(2.675, 2) == 2.67`。需十进制精确时用 `decimal.Decimal`。
- **与 Decimal**  
  - `round(Decimal('…'), ndigits)` 走十进制并**半舍到偶**  
  - 明确“**四舍五入**”请用：`Decimal('…').quantize(Decimal('0.01'), rounding=ROUND_HALF_UP)`
- **仅控制显示位数**：用格式化（不改变数值）  
  `format(x, '.2f')` / `f"{x:.2f}"`

#### 示例
```py
round(0.5)        # 0    半舍到偶
round(1.5)        # 2
round(2.5)        # 2
round(-1.5)       # -2

round(2.675, 2)   # 2.67  浮点近似
round(15, -1)     # 20    到十位
round(1499, -3)   # 1000  到千位
round(1.5, 0)     # 2.0   float 输入 → float
round(2, 0)       # 2     int 输入 → int
```

## 截断 vs 向下/向上
```python
import math
int(1.9), int(-1.9)        # (1, -1)
math.floor(-1.9)           # -2
math.ceil(-1.9)            # -1
```

## 进制解析
```python
int("42")                  # 42
int("101", 2)              # 5
int("0o17", 0)             # 15
int("0xFF", 0)             # 255
```

# Week 2 Conditionals and Iteration (while loops)

## 字符串和列表 (Strings and Lists)
- 字符串 (`str`) 和列表 (`list`) 都是 Python 的序列类型。
- 字符串是不可变的，列表是可变的。
- 切片和索引操作：`my_list[0]`, `my_str[1:3]`。
- 常用操作：拼接（`+`）、重复（`*`）、长度（`len()`）。

## Python 常用字符串与列表方法笔记

### 字符串 (`str`) 方法

#### 1. `len(s)`
- **参数**: `s`（字符串）
- **说明**: 返回字符串的长度（字符个数）
- **示例**:
```python
len("hello")  # 5
```

#### 2. `s.lower()`
- **说明**: 返回小写形式的新字符串
```python
"Hello".lower()  # "hello"
```

#### 3. `s.upper()`
- **说明**: 返回大写形式的新字符串
```python
"Hello".upper()  # "HELLO"
```

#### 4. `s.strip([chars])`
- **参数**:
  - `chars`（可选）: 要去除的字符集合（默认为空格和换行符）
- **说明**: 去掉字符串两端的指定字符
```python
"  hi  ".strip()       # "hi"
"--hi--".strip("-")    # "hi"
```

#### 5. `s.replace(old, new, count)`
- **参数**:
  - `old`: 需要替换的子串
  - `new`: 替换成的新子串
  - `count`（可选）: 限制替换次数
- **说明**: 返回替换后的新字符串
```python
"apple".replace("p", "P", 1)  # "aPple"
```

#### 6. `s.split(sep=None, maxsplit=-1)`
- **参数**:
  - `sep`（可选）: 分隔符（默认按任意空白字符）
  - `maxsplit`（可选）: 最大分割次数
- **说明**: 返回分割后的列表
```python
"a b c".split()             # ['a', 'b', 'c']
"a,b,c".split(",", 1)       # ['a', 'b,c']
```

#### 7. `sep.join(iterable)`
- **参数**:
  - `iterable`: 可迭代对象（元素需为字符串）
- **说明**: 用分隔符连接可迭代对象
```python
",".join(["a", "b"])  # "a,b"
```

#### 8. `s.find(sub, start, end])`
- **说明**: 返回子串首次出现的索引，找不到返回 -1
```python
"apple".find("p")     # 1
"apple".find("p", 2)  # 2
```

#### 9. `s.count(sub, start, end])`
- **说明**: 返回子串出现次数
```python
"apple".count("p")         # 2
"apple".count("p", 0, 2)   # 1
```

#### 10. `s.startswith(prefix, start, end])`
- **说明**: 判断是否以 `prefix` 开头
```python
"hello".startswith("he")         # True
"hello".startswith("he", 1)      # False
```

#### 11. `s.endswith(suffix, start, end])`
- **说明**: 判断是否以 `suffix` 结尾
```python
"hello".endswith("lo")           # True
"hello".endswith("lo", 0, 3)     # False
```


### 列表 (`list`) 方法

#### 1. `len(lst)`
- **说明**: 返回列表元素个数
```python
len([1, 2, 3])  # 3
```

#### 2. `lst.append(x)`
- **说明**: 在列表末尾添加一个元素
```python
nums = [1, 2]
nums.append(3)  # [1, 2, 3]
```

#### 3. `lst.insert(i, x)`
- **说明**: 在索引 `i` 处插入元素 `x`
```python
nums = [1, 3]
nums.insert(1, 2)  # [1, 2, 3]
```

#### 4. `lst.extend(iterable)`
- **说明**: 追加多个元素
```python
nums = [1, 2]
nums.extend([3, 4])  # [1, 2, 3, 4]
```

#### 5. `lst.remove(x)`
- **说明**: 删除第一个匹配的元素
```python
nums = [1, 2, 2]
nums.remove(2)  # [1, 2]
```

#### 6. `lst.pop([i])`
- **说明**: 删除并返回指定索引元素（默认最后一个）
```python
nums = [1, 2, 3]
nums.pop()    # 3
nums.pop(0)   # 1
```

#### 7. `lst.index(x, start, end])`
- **说明**: 返回第一个匹配值的索引（找不到报错）
```python
[1, 2, 3, 2].index(2)       # 1
[1, 2, 3, 2].index(2, 2)    # 3
```

#### 8. `lst.count(x)`
- **说明**: 返回元素出现次数
```python
[1, 2, 2].count(2)  # 2
```

#### 9. `lst.sort(*, key=None, reverse=False)`
- **说明**: 原地排序
- **参数**:
  - `key`: 排序函数
  - `reverse`: 是否倒序
```python
nums = [3, 1, 2]
nums.sort()                     # [1, 2, 3]
nums.sort(reverse=True)         # [3, 2, 1]
words = ["a", "ccc", "bb"]
words.sort(key=len)             # ['a', 'bb', 'ccc']
```

#### 10. `sorted(iterable, *, key=None, reverse=False)`
- **说明**: 返回排序后的新列表
```python
sorted([3, 1, 2])                      # [1, 2, 3]
sorted(["a", "ccc", "bb"], key=len)    # ['a', 'bb', 'ccc']
```

#### 11. `lst.reverse()`
- **说明**: 原地反转列表
```python
nums = [1, 2, 3]
nums.reverse()  # [3, 2, 1]
```

## 成员操作符（in 和 not in）
- 用于判断元素是否在序列中：
```python
'a' in 'apple'       # True
3 not in [1, 2, 4]   # True
```
- 返回值是布尔类型（`True` 或 `False`）。

## 条件执行：二元选择（Binary Selection）
- 二元选择：`if ... else ...` 结构。
```python
if condition:
    # 真分支
else:
    # 假分支
```

## 省略 else 子句：一元选择（Unary Selection）
- 一元选择：只有 `if`，没有 `else`。
```python
if condition:
    # 真分支
```

## 嵌套条件（Nested Conditionals）
- 条件语句的嵌套使用。
```python
if condition1:
    if condition2:
        # 两个条件都为真
```

## 链式条件（Chained Conditionals）
- 使用 `elif` 链接多个条件分支。
```python
if condition1:
    ...
elif condition2:
    ...
else:
    ...
```

## 条件语句的设置（Setting Up Conditionals）
- 设计条件判断时的步骤：
  1. 明确条件。
  2. 确定条件顺序。
  3. 合理使用 `if`、`elif`、`else`。

## while 循环简介（Introduction to While Loops）
- `while` 循环：当条件为真时重复执行。
```python
while condition:
    # 循环体
```

## while 语句（While Statement）
- 注意避免死循环（条件永远为真）。
- 循环中常用 `break` 和 `continue` 控制流程。

## 中断和继续（Break and Continue）
- `break`：立即结束当前循环。
- `continue`：跳过本次循环剩余部分，直接进入下一次循环。

# Week 3 Iteration (for loops) and Sequences

## Python 内置数据类型笔记

参考：[Python 官方文档 - Built-in Types](https://docs.python.org/3/library/stdtypes.html)

---

### 1. 数字类型（Numeric Types）
- **`int`**：整数
- **`float`**：浮点数
- **`complex`**：复数
```python
x = 10        ## int
y = 3.14      ## float
z = 2 + 3j    ## complex
```

---

### 2. 序列类型（Sequence Types）

#### 不可变序列
- `str`：字符串
- `tuple`：元组
- `range`：整数序列

#### 可变序列
- `list`：列表
- `bytearray`：可变字节序列

```python
s = "hello"          ## str
lst = [1, 2, 3]      ## list
tup = (1, 2, 3)      ## tuple
```

---

### 3. 文本序列类型（Text Sequence Type）
- `str`：专门用于存储文本（Unicode 字符）
- 其实就是 str，但官方单独提，因为它是专门存**文本（Unicode 字符）**的

```python
text = "Python"
```

---

### 4. 二进制序列类型（Binary Sequence Types）
- **不可变**：`bytes`
- **可变**：`bytearray`
- **内存视图**：`memoryview`

```python
b = b"hello"          ## bytes
ba = bytearray(b"hi") ## bytearray
mv = memoryview(b)
```

---

### 5. 集合类型（Set Types）
- `set`：可变集合
- `frozenset`：不可变集合

```python
s = {1, 2, 3}
fs = frozenset([1, 2, 3])
```

---

### 6. 映射类型（Mapping Types）
- `dict`：字典（键值对）

```python
d = {"a": 1, "b": 2}
```

---

### 7. 上下文相关类型（Context Related）
- `NoneType`：`None`
- `EllipsisType`：`...`
- `NotImplementedType`：`NotImplemented`

```python
a = None
b = ...
c = NotImplemented
```

---

### 8. 逻辑类型（Boolean Type）
- `bool`：布尔值（`True` / `False`）
- 注意：`bool` 是 `int` 的子类

```python
is_ok = True
```

---

### 9. 其他特殊类型（Other Types）
- **函数、方法、生成器**（callable types）
- **迭代器类型**（iterator types）
- **文件对象**（file objects）
- **模块类型**（module type）
- **类和实例**（class, instance）
- **类型对象**（type）

---

### 总结
- 数字、序列、集合、映射是最常用的四类
- 序列类型分可变与不可变
- `str` 既是序列类型也是文本类型
- `bool` 是数字类型的子类

## Python 序列类型（Sequence Types）笔记

参考：[Python 官方文档 - Sequence Types](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

---

### 1. 定义
序列类型（Sequence Types）是 Python 中**有序**的数据结构，能够通过索引访问元素，支持切片和迭代等操作。

---

### 2. 分类

#### 不可变序列（Immutable Sequences）
- **`str`**：字符串（文本序列类型）
- **`tuple`**：元组
- **`range`**：整数序列

#### 可变序列（Mutable Sequences）
- **`list`**：列表
- **`bytearray`**：可变字节序列

---

### 3. 共同特征

所有序列类型都支持：

1. **索引（Indexing）**
   ```python
   s = "hello"
   s[0]    ## 'h'
   s[-1]   ## 'o'
   ```

2. **切片（Slicing）**
   ```python
   lst = [1, 2, 3, 4]
   lst[1:3]    ## [2, 3]
   s = "python"
   s[:3]       ## 'pyt'
   ```

3. **迭代（Iteration）**
   ```python
   for x in [1, 2, 3]:
       print(x)
   ```

4. **长度、最值、最小值**
   ```python
   len([1, 2, 3])  ## 3
   max("abc")      ## 'c'
   min([5, 2, 9])  ## 2
   ```

5. **成员运算符**
   ```python
   3 in [1, 2, 3]       ## True
   "p" in "apple"       ## True
   ```

6. **拼接与重复**
   - 仅适用于同类型序列
   ```python
   [1, 2] + [3, 4]    ## [1, 2, 3, 4]
   "ha" * 3           ## 'hahaha'
   ```

---

### 4. 可变与不可变

| 特性           | 可变序列（list, bytearray） | 不可变序列（str, tuple, range） |
| -------------- | --------------------------- | ------------------------------- |
| 是否可修改元素 | ✅                           | ❌                               |
| 修改方式       | 直接修改元素、追加、删除    | 必须创建新对象                  |
| 示例           | `lst[0] = 99`               | 不允许 `s[0] = "H"`             |

---

### 5. 常用内置函数

| 函数            | 作用               | 示例                                |
| --------------- | ------------------ | ----------------------------------- |
| `len(seq)`      | 返回长度           | `len("abc") → 3`                    |
| `max(seq)`      | 返回最大值         | `max([1, 5, 3]) → 5`                |
| `min(seq)`      | 返回最小值         | `min("cab") → 'a'`                  |
| `sum(seq)`      | 求和（数字序列）   | `sum([1, 2, 3]) → 6`                |
| `sorted(seq)`   | 返回排序后的新列表 | `sorted("cab") → ['a','b','c']`     |
| `reversed(seq)` | 返回反向迭代器     | `list(reversed([1,2,3])) → [3,2,1]` |

---

### 6. 总结
- **序列 = 有序容器**
- 都支持索引、切片、迭代、成员运算
- 区分可变与不可变序列
- 常见序列：`list`, `tuple`, `str`, `range`, `bytes`, `bytearray`


## Python 迭代机制笔记

---

### 1. 序列类型与迭代

- **序列类型（Sequence Types）**：`list`, `tuple`, `str`, `range`, `bytes`, `bytearray` 等
- 所有序列类型都可迭代，因为它们实现了 **迭代协议（iterator protocol）**：
  - `__iter__()` 返回一个迭代器对象
  - 迭代器对象实现 `__next__()` 方法依次返回元素

---

### 2. `for in` 的工作原理

`for x in seq:` 背后的等价逻辑：
```python
it = iter(seq)   ## 获取迭代器
while True:
    try:
        x = next(it)  ## 获取下一个元素
        ## 执行循环体
    except StopIteration:
        break
```

---

### 3. 除了 `for in`，其他迭代方法

#### （1）显式使用 `iter()` 和 `next()`
```python
nums = [1, 2, 3]
it = iter(nums)
print(next(it))  ## 1
print(next(it))  ## 2
print(next(it))  ## 3
```

#### （2）`while` 循环 + `next()`
```python
nums = [10, 20, 30]
it = iter(nums)
while True:
    try:
        val = next(it)
        print(val)
    except StopIteration:
        break
```

#### （3）推导式（隐式迭代）
```python
[x**2 for x in range(5)]  ## [0, 1, 4, 9, 16]
```

#### （4）内置函数迭代
许多内置函数会自动迭代其参数：
- `sum(iterable)`
- `max(iterable)`
- `min(iterable)`
- `sorted(iterable)`
- `any(iterable)` / `all(iterable)`

```python
sum([1, 2, 3])         ## 6
max("hello")           ## 'o'
sorted((3, 1, 2))      ## [1, 2, 3]
```

---

### 4. 结论
- **序列类型**都可迭代
- `for in` 是最常用的迭代方式，但不是唯一的
- 可以用 `iter()` / `next()` 进行手动迭代
- 推导式和很多内置函数也会隐式进行迭代

## Python `range()`、`_` 变量用法与迭代机制笔记

---

### 1. `range()` 基本介绍

`range` 是一个 **类**，返回一个不可变的数字序列，通常用于生成一系列整数。

#### 语法
```python
range(stop)
range(start, stop, step)
```
- **start**：起始值（默认 0）
- **stop**：终止值（不包含该值）
- **step**：步长（默认 1，可为负）

#### 示例
```python
list(range(5))           ## [0, 1, 2, 3, 4]
list(range(2, 6))        ## [2, 3, 4, 5]
list(range(0, 11, 2))    ## [0, 2, 4, 6, 8, 10]
```

---

### 2. 直接打印 `range` 对象
如果直接打印 `range` 对象：
```python
print(range(5))
## 输出：range(0, 5)
```
这是因为 `range` 返回的是一个**惰性生成**的序列对象，而不是立即展开的列表。  
要看到所有元素，需要用 `list()` 转换：
```python
print(list(range(5)))
## 输出：[0, 1, 2, 3, 4]
```

---

### 3. `range` 的特点
- **不可变序列**（immutable）
- **惰性生成**（不会一次性生成所有数字）
- 支持 `len()`、索引、切片
```python
r = range(10)
len(r)        ## 10
r[3]          ## 3
list(r[2:5])  ## [2, 3, 4]
```

---

### 4. 常见用途
- **循环次数控制**
```python
for i in range(5):
    print(i)
```
- **生成等差数列**
```python
evens = list(range(0, 21, 2))
```
- **反向循环**
```python
for i in range(10, 0, -1):
    print(i)
```

---

### 5. `for _ in range(n)` 的用法

#### 语法
```python
for _ in range(n):
    ## 循环体
```
- `_` 是一个**约定俗成**的变量名，用于表示“忽略这个值”。
- 当循环变量不需要使用时，推荐使用 `_` 代替有意义的变量名。

#### 示例
```python
for _ in range(3):
    print("This line will execute three times")
    print("This line will also execute three times")
```
输出（共执行 3 次循环）:
```
This line will execute three times
This line will also execute three times
...（重复 3 次）
```

#### 适用场景
- 循环执行固定次数
- 不关心循环变量的值
- 让代码可读性更高

⚠️ 注意：在交互式解释器中，`_` 可能保存上一次表达式的结果，但在脚本中没有影响。

---

### 6. 总结
- `range` 是生成整数序列的高效工具，支持索引、切片、惰性生成
- 直接打印 `range` 会显示为 `range(start, stop)`，需要用 `list()` 展示所有元素
- `for _ in range(n)` 是一种 Pythonic 写法，适合固定次数循环
- Python 的迭代基于迭代协议，`for in` 是语法糖，也可用 `iter()`/`next()` 手动迭代

## Python 错误类型与调试笔记

### 1. 错误三大类

#### 1.1 语法错误（Syntax Error）
- **阶段**：解释器解析代码时  
- **表现**：程序无法运行，直接抛出错误  
- **常见错误类型**：
  - `SyntaxError`：语法不合法  
  - `IndentationError`：缩进不合法  

**示例**：
```python
## SyntaxError: missing colon
if True
    print("Hello")

## IndentationError: unexpected indent
def foo():
  print("hi")
    print("oops")
```

---

#### 1.2 运行时错误（Runtime Error）
- **阶段**：语法正确，但运行中抛出异常（Exception）  
- **表现**：执行到错误处崩溃，可通过 `try...except` 捕获  
- **常见错误类型**：
  - `ZeroDivisionError`：除数为零  
  - `NameError`：使用未定义变量  
  - `TypeError`：类型不匹配  
  - `IndexError`：索引越界  

**示例**：
```python
## ZeroDivisionError
x = 10 / 0

## NameError
print(undeclared_var)

## TypeError
result = "a" + 1

## IndexError
lst = [1, 2]
print(lst[5])
```

---

#### 1.3 语义错误（Semantic Error）
- **阶段**：代码能运行且无异常，但结果不符合预期  
- **表现**：逻辑或算法出错  

**示例**：
```python
## 本意是返回平方，但写成了乘2
def square(x):
    return x * 2

print(square(5))  ## 结果: 10（错的），期望: 25
```

- **检测方法**：单元测试、断言、代码审查

---

### 2. 调试方法
1. `print()`：快速查看变量值  
2. `pdb`：内置调试器，支持断点  
3. IDE 调试工具：PyCharm、VSCode  
4. `logging`：记录调试信息  
5. 单元测试：`unittest`、`pytest`

---

### 3. 避免 Bug 的最佳实践
- 遵循 **PEP 8** 编码规范  
- 使用 **类型注解** + `mypy` 检查  
- 输入校验 & 异常处理  ˚∑
- 编写 **测试用例**  
- 代码审查（Code Review）

# Week 4 Functions, Scoping, Namespaces and Dictionaries


# Week 5 Transforming Sequences

## List Element Deletion

### 1. 使用 `del` 关键字

#### 删除特定索引位置的元素
```python
a = [10, 20, 30, 40]
del a[1]  # 删除索引为1的元素：20

a = [0, 1, 2, 3, 4, 5, 6, 7]
del a[2:5]  # 删除索引 2~4 的元素：[2, 3, 4]

a = [0, 1, 2, 3, 4, 5]
del a[::2]  # 删除偶数索引位置的元素：a[0], a[2], a[4]
print(a)  # 输出: [1, 3, 5]

a = [1, 2, 3]
del a[:]  # 清空列表中的所有元素，但保留列表对象
print(a)  # 输出: []

a = [1, 2, 3]
del a  # 删除变量 a
print(a)  # NameError: name 'a' is not defined
```

---

### 2. 使用 `.remove(value)`

- 按**值**删除第一个匹配的元素。
- 如果值不存在会抛出 `ValueError`。

```python
a = [1, 2, 3, 2, 4]
a.remove(2)  # 删除第一个出现的 2
# a 变为 [1, 3, 2, 4]
```

---

### 3. 使用 `.pop([index])`

- 默认删除并返回**最后一个**元素。
- 可选参数 `index` 指定删除哪个位置。
- 如果索引越界会抛出 `IndexError`。

```python
a = [5, 6, 7]
x = a.pop()    # 删除并返回最后一个元素 7
y = a.pop(0)   # 删除并返回第一个元素 5
```

---

### 4. 使用列表推导式（过滤删除）

- 用于**按条件删除**一个或多个元素。

```python
a = [1, 2, 3, 4, 5, 6]
a = [x for x in a if x % 2 == 0]  # 保留偶数，删除奇数
```

---

### 5. 使用 `filter()` 函数（功能类似）

```python
a = [1, 2, 3, 4, 5]
a = list(filter(lambda x: x > 2, a))  # 删除 <=2 的元素
```

---

### 6. 使用 `clear()` 方法（清空列表）

- 删除所有元素，但保留列表对象。

```python
a = [1, 2, 3]
a.clear()  # a 变为 []
```

---

### 7. 重新赋值一个新列表（间接删除）

```python
a = [1, 2, 3, 4]
a = a[:2] + a[3:]  # 删除索引2的元素（3）
```

---

## Objects and References

### 1. 一切皆对象（Everything is an Object）
在 Python 中，**所有数据都是对象**，包括数字、字符串、函数、类、模块等。

```python
x = 42
print(type(x))  # <class 'int'>
```

- `42` 是一个 **对象**（object）。
- 变量 `x` 是一个 **引用**（reference），指向这个对象。

---

### 2. 变量是对象的引用，而不是对象本身
变量更像是给对象贴的标签，而不是“盒子”存值。

```python
x = [1, 2, 3]
y = x   # y 和 x 指向同一个对象
y.append(4)
print(x)  # [1, 2, 3, 4]
```

⚠️ 因为 `x` 和 `y` 是同一个对象的引用，所以修改一个会影响另一个。

---

### 3. `id()`：查看对象的唯一标识
Python 中每个对象都有唯一的身份标识（通常是内存地址）。

```python
a = [1, 2, 3]
b = a
print(id(a), id(b))  # 两个 id 一样
```

如果 `id` 相同，说明它们引用的是同一个对象。

---

### 4. 可变对象 vs 不可变对象

#### 不可变对象（immutable）
- 包括 `int`, `float`, `str`, `tuple`, `frozenset` 等
- 内容不可修改
- 修改变量时，其实是新建了一个对象

```python
a = 10
b = a
a = a + 5   # 创建了新对象 15
print(b)    # 10 (不受影响)
```

🔎 **补充：对象驻留**
对于某些不可变对象（如小整数、字符串），Python 会进行优化：  
如果两个变量的值相同，它们可能会引用同一个对象。

```python
a = 1
b = 1
print(id(a) == id(b))  # True
```

这意味着不可变对象的 **id 可以相同**，因为 Python 会缓存这些对象来节省内存。

#### 可变对象（mutable）
- 包括 `list`, `dict`, `set`, `bytearray` 等
- 可以原地修改对象内容

```python
a = [1, 2]
b = a
a.append(3)
print(b)  # [1, 2, 3]
```

---

## Deep and Shallow Copies

### 浅拷贝（shallow copy）
- 复制最外层对象，但内部元素仍然是引用。
- 修改内部可变对象会影响原对象。

```python
import copy

a = [[1, 2], [3, 4]]
b = copy.copy(a)   # 浅拷贝

b[0][0] = 99
print(a)  # [[99, 2], [3, 4]]
print(b)  # [[99, 2], [3, 4]]

a = [[1], [2]]
b = a[:]        # 或 list(a) / a.copy() / [*a] / a*1
b[0].append(99)
print(a)  # [[1, 99], [2]]  <- 内层对象共享
```

### 深拷贝（deep copy）
- 递归复制所有层级对象。
- 修改拷贝不会影响原对象。

```python
c = copy.deepcopy(a)  # 深拷贝

c[0][0] = 123
print(a)  # [[99, 2], [3, 4]]
print(c)  # [[123, 2], [3, 4]]
```

---

## 函数参数传递：对象引用传递

Python 的函数参数传递机制是 **对象引用传递**（call by object reference）：
- 传入函数的是对象的引用，而不是对象的副本。

### 示例 1：可变对象
```python
def modify_list(lst):
    lst.append(100)

nums = [1, 2, 3]
modify_list(nums)
print(nums)  # [1, 2, 3, 100]
```

可变对象会被函数修改。

### 示例 2：不可变对象
```python
def modify_int(x):
    x = x + 10
    return x

a = 5
result = modify_int(a)
print(a)      # 5 (不变)
print(result) # 15 (返回新对象)
```

不可变对象在函数内部修改时，其实是创建了新对象，原始变量不受影响。

---

## Mutating Methods

| Method  | Parameters     | Result     | Description                                      |
| ------- | -------------- | ---------- | ------------------------------------------------ |
| append  | item           | mutator    | Adds a new item to the end of a list             |
| insert  | position, item | mutator    | Inserts a new item at the position given         |
| pop     | none           | hybrid     | Removes and returns the last item                |
| pop     | position       | hybrid     | Removes and returns the item at position         |
| sort    | none           | mutator    | Modifies a list to be sorted                     |
| reverse | none           | mutator    | Modifies a list to be in reverse order           |
| index   | item           | return idx | Returns the position of first occurrence of item |
| count   | item           | return ct  | Returns the number of occurrences of item        |
| remove  | item           | mutator    | Removes the first occurrence of item             |

### Append versus Concatenate
append是修改原变量  
concatenate是新建一个变量

## Non-mutating Methods on Strings
| Method  | Parameters    | Description                                                                                                  |
| ------- | ------------- | ------------------------------------------------------------------------------------------------------------ |
| upper   | none          | Returns a string in all uppercase                                                                            |
| lower   | none          | Returns a string in all lowercase                                                                            |
| count   | item          | Returns the number of occurrences of item                                                                    |
| index   | item          | Returns the leftmost index where the substring item is found and causes a runtime error if item is not found |
| strip   | none          | Returns a string with the leading and trailing whitespace removed                                            |
| replace | old, new      | Replaces all occurrences of old substring with new                                                           |
| format  | substitutions | Involved! See String Format Method, below                                                                    |


# Week 6 File IO

| Mode | Description                                                           |
| ---- | --------------------------------------------------------------------- |
| r    | **Read** (default mode). Opens the file for reading. File must exist. |
| w    | **Write**. Creates a new file or overwrites an existing one.          |
| a    | **Append**. Opens file for writing, adds to the end if file exists.   |
| r+   | **Read and Write**. File must exist.                                  |
| w+   | **Write and Read**. Creates a new file or overwrites existing.        |
| a+   | **Append and Read**. Adds content to the end and allows reading.      |
| ab   | **Append in Binary Mode**. Writes data in binary form.                |


| Method Name    | Use                      | Explanation                                                                                                                                                                                       |
| -------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `write`        | `filevar.write(astring)` | Add a string to the end of the file. `filevar` must refer to a file that has been opened for writing.                                                                                             |
| `read(n)`      | `filevar.read()`         | Read and return a string of `n` characters, or the entire file as a single string if `n` is not provided.                                                                                         |
| `readline(n)`  | `filevar.readline()`     | Read and return the next line of the file up to and including the newline character. If `n` is provided, returns at most `n` characters.                                                          |
| `readlines(n)` | `filevar.readlines()`    | Returns a list of strings, each representing a single line of the file. If `n` is not provided, all lines are returned; if `n` is provided, it reads approximately `n` characters worth of lines. |


# Week 7 Modules and Libraries

## Import

## Modules and Packages

## Random module

## Re module

### 正则表达式基础（Python `re`）

#### 通配与转义
- `.`：匹配除换行符以外的任意单个字符（默认）。
- `\`：转义元字符；也引入特殊序列（如 `\d`、`\w` 等）。**在 Python 里建议用原始字符串**：`r"\d+\.\d+"`，可避免 Python 字符串本身的转义干扰。  
  > 注意：字符类 `[]` 中仍有少量字符需特殊处理：`^`（开头表示取反）、`-`（表示范围）、`]`（结束）和 `\` 本身。

#### 量词（重复）
- `*`：前一个表达式重复 **0 次或多次**
- `+`：前一个表达式重复 **1 次或多次**
- `?`：前一个表达式重复 **0 次或 1 次**
- `{m}`：前一个表达式重复 **恰好 m 次**
- `{m,n}`：前一个表达式重复 **m 到 n 次**（`{m,}` 表示至少 m 次）
- 量词**默认贪婪**；在后面加 `?` 变为惰性：`*?`、`+?`、`??`、`{m,n}?`

#### 字符类与范围
- `[ ... ]`：字符集合。例：`[Cc]at` 可匹配 `Cat` 或 `cat`。
- 范围：`[2-5]` 等价于 `2|3|4|5`；`[b-g]` 等价于 `b|c|d|e|f|g`。
- 取反：`[^ ... ]` 表示**不在集合内**。例：`[^Cc]at` 匹配 `hat`、`@at`，但不匹配 `cat`/`Cat`。

#### 分支与分组
- `A|B`：匹配 **A 或 B**。
- `()`：分组与捕获；`(?:...)` 为**非捕获**分组，便于分组而不产生捕获。
- 反向引用：`\1`、`\2`…；命名组：`(?P<name>...)` 与 `(?P=name)`。

#### 锚点（位置）
- `^`：字符串（或行）**开头**；在 `[]` 内作**取反**标记。
- `$`：字符串（或行）**结尾**。  
  > 配合 `re.MULTILINE`（或内联标志 `(?m)`）时，`^`/`$` 也匹配每一行的行首/行尾。

#### 常见元字符 / 特殊序列（Python）
| 序列           | 含义（默认 ASCII/Unicode 取决于 `re.ASCII` 标志） |
| -------------- | ------------------------------------------------- |
| `\d` / `\D`    | 数字 / 非数字                                     |
| `\w` / `\W`    | 单词字符（字母、数字、下划线）/ 非单词字符        |
| `\s` / `\S`    | 空白 / 非空白（空格、制表、换行等）               |
| `\b` / `\B`    | 单词边界 / 非单词边界                             |
| `\A` / `\Z`    | 字符串开头 / 字符串结尾（不受 `MULTILINE` 影响）  |
| `\t` `\n` `\r` | 制表、换行、回车（常见转义）                      |

#### 小示例
```text
# 1) 邮箱雏形（极简，不严谨）：
r"[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}"

# 2) 提取重复的词（忽略大小写）：
r"(?i)\b(\w+)\b\s+\1\b"

# 3) 惰性匹配 HTML 标签内容：
r"<tag>.*?</tag>"

# 4) 行首数字（逐行）：
r"(?m)^\d+"
```

## Numpy module

## Pandas module

## Matplotlib module

# Week 8 Object-Oriented Programming 1

## Class

```python
# 类名首字母大写
class Classname:

  # 初始化方法，返回值必须为None
  # 该方法在对象创建之后被调用
  # 它的职责是初始化对象的状态
  # 参数self是必须的
  def __init__(self, x, y) -> None:
    self.x = x
    self.y = y
    self.z = 0
```

## Instance
```python
class Object:
  # Object中的new方法
  # 如果不定义，默认用的就是Object的new方法
  # 该方法的职责是创建一个新的实例
  def __new__(cls, *args, **kwargs):
      # 分配一块内存来保存 cls 类型的新实例
      instance = allocate_memory_for(cls)
      return instance
```

## Insatance method & Class method & Static method
```python
class User:
    # ---- 类级数据（所有实例共享）----
    _count = 0

    # ---- 实例创建与初始化 ----
    def __init__(self, username: str, email: str):
        # 使用静态方法做工具处理
        norm_name = self.normalize_username(username)
        if not self.is_valid_username(norm_name):
            raise ValueError(f"Invalid username: {username!r}")

        norm_email = self.normalize_email(email)
        if not self.is_valid_email(norm_email):
            raise ValueError(f"Invalid email: {email!r}")

        self.username = norm_name
        self.email = norm_email

        # 统计实例数量（类级数据）
        type(self)._count += 1

    # ---- 类方法（操作类级状态/充当工厂方法）----
    @classmethod
    def instances(cls) -> int:
        """返回当前已创建的实例数量"""
        return cls._count

    @classmethod
    def from_dict(cls, data: dict) -> "User":
        """工厂：从字典创建 User"""
        return cls(username=data["username"], email=data["email"])

    # ---- 静态方法（工具函数，不依赖类/实例状态）----
    @staticmethod
    def normalize_username(s: str) -> str:
        # 去空格、转小写、空格改下划线
        return s.strip().lower().replace(" ", "_")

    @staticmethod
    def is_valid_username(s: str) -> bool:
        # 只允许 a-z、0-9、下划线，且长度 3~20
        if not (3 <= len(s) <= 20):
            return False
        return all(c.islower() or c.isdigit() or c == "_" for c in s)

    @staticmethod
    def normalize_email(s: str) -> str:
        return s.strip().lower()

    @staticmethod
    def is_valid_email(s: str) -> bool:
        # 简化校验：包含一个 @ 且左右都非空
        parts = s.split("@")
        return len(parts) == 2 and all(parts)

    # ---- 实例方法（操作具体对象）----
    def greet(self) -> str:
        """实例方法：使用实例数据进行行为"""
        return f"Hi, I'm {self.username} ({self.email})"

    def rename(self, new_username: str) -> None:
        """实例方法：修改实例状态"""
        norm = self.normalize_username(new_username)
        if not self.is_valid_username(norm):
            raise ValueError(f"Invalid new username: {new_username!r}")
        self.username = norm


# ---------------- 演示 ----------------
# 1) 用构造函数直接创建
u1 = User("  Alice Zhang  ", "Alice@Example.COM")
print(u1.greet())
# -> Hi, I'm alice_zhang (alice@example.com)

# 2) 用类方法工厂 from_dict 创建
u2 = User.from_dict({"username": "Bob", "email": "bob@example.com"})
print(u2.greet())
# -> Hi, I'm bob (bob@example.com)

# 3) 实例方法修改对象
u2.rename("Bob_the_builder")
print(u2.greet())
# -> Hi, I'm bob_the_builder (bob@example.com)

# 4) 类方法统计实例数量
print(User.instances())
# -> 2

# 5) 静态方法可单独作为工具使用
print(User.is_valid_username("bad name!"))  # -> False
```

| 方法类型 | 英文名称            | 定义方式                | 第一个参数 | 调用者   | 自动传入的参数    | 是否可访问实例属性 | 是否可访问类属性     | 典型用途                 |
| -------- | ------------------- | ----------------------- | ---------- | -------- | ----------------- | ------------------ | -------------------- | ------------------------ |
| 实例方法 | **Instance Method** | 普通 `def`              | `self`     | 实例对象 | 当前实例 (`self`) | ✅ 是               | ✅ 是                 | 操作具体对象数据         |
| 类方法   | **Class Method**    | `@classmethod` + `def`  | `cls`      | 类或实例 | 当前类 (`cls`)    | ❌ 否（除非传实例） | ✅ 是                 | 操作类级别数据、工厂方法 |
| 静态方法 | **Static Method**   | `@staticmethod` + `def` | 无         | 类或实例 | ❌ 无自动传参      | ❌ 否               | ❌ 否（除非显式传入） | 辅助逻辑、工具函数       |


## Class variables vs. instance variables
类变量和实例变量
```python
class Dog:
    species = "Canis familiaris"  # 类变量（所有狗都一样）
    def __init__(self, name):
        self.name = name  # 实例变量
```

访问顺序
```python
# 当访问一个变量的时候
# 先在当前实例中寻找
# 然后再去类上找
# 如果有父类，再去父类上找
# 最后找不到，抛出AttributeError
# 也就是说实例变量会遮蔽同名类变量
class Cat:
    sound = "meow"  # 类变量
    def __init__(self, name):
        self.name = name # 实例变量

c = Cat("Kitty")
print(c.sound)  # meow  -> 来自类变量
c.sound = "purr"  # 新建实例变量，遮蔽类变量
print(c.sound)  # purr  -> 来自实例变量
print(Cat.sound)  # 仍然是 meow
```

## dunder methods
```python
class User:
    def __init__(self, name, age): self.name, self.age = name, age
    def __repr__(self):  # 调试/交互式解释器
        return f"User(name={self.name!r}, age={self.age!r})"
    def __str__(self):   # 面向用户的展示
        return f"{self.name} ({self.age})"
```
想系统查阅，官方文档关键词：Python Data Model（数据模型）

# Week 9 Object-Oriented Programming 2

## Class Inheritance
单继承
```python
class SuperClass:
    # Super class attributes and methods

class SubClass(SuperClass):
    # Sub class attributes and methods
```

单继承链
```python
class SuperClass:
    # ...

class SubClass1(SuperClass):
    # ...

class SubClass2(SubClass1):
    # ...
```

多继承
```python
class Root:
    def __init__(self, *args, **kwargs):
        print("Root.__init__")
        super().__init__(*args, **kwargs)

class A(Root):
    def __init__(self, *args, **kwargs):
        print("A.__init__")
        super().__init__(*args, **kwargs)

class B(Root):
    def __init__(self, *args, **kwargs):
        print("B.__init__")
        super().__init__(*args, **kwargs)

class C(A, B):  # 菱形：C -> A -> B -> Root -> object
    def __init__(self, *args, **kwargs):
        print("C.__init__")
        super().__init__(*args, **kwargs)

C()
# 输出顺序：
# C.__init__
# A.__init__
# B.__init__
# Root.__init__

# 要点：所有类的 __init__ 都调用了 super().__init__，并且签名兼容 *args, **kwargs，
# 这样就能按 MRO 链式调用，避免某个父类被调用多次或漏掉。
```

关键点：MRO（方法解析顺序）
1. Python 采用 C3 线性化 来确定查找顺序（Method Resolution Order）。
2. 多继承时，属性/方法查找从左到右，沿着 MRO 走。
3. 用 Class.mro() 或 help(Class) 可以查看 MRO。

常见坑与建议
1. 父类顺序很重要：class C(A, B) 与 class C(B, A) 的行为可能不同（查找顺序不同）。
2. 一致使用 super()：所有参与多继承的类都应调用 super()，且保持签名兼容（*args, **kwargs）。
3. 避免同名属性冲突：不同父类若定义了同名属性/方法，最终采用 MRO 的最前者。
4. Mixin 要轻薄：只提供小而清晰的功能片段，不要有重的状态或依赖。

## Overriding Methods
```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):
    def speak(self):  # 这个就是 override
        print("Dog barks")

a = Animal()
a.speak()  # 输出: Animal speaks

d = Dog()
d.speak()  # 输出: Dog barks
```

## super & super()
- super是一个类
- super()是super类的一个实例，是一个代理对象
  - 这个对象会根据当前类的 MRO（方法解析顺序）来查找下一个类的方法（通常就是父类，但不仅限于“直接父类”， 参考上面多继承中print的顺序）

## Abstract Classes
```python
from abc import ABC, abstractmethod
from math import pi

class Shape(ABC):
    
    def __init__(self, name, shape_data):
        self.name = name
        self.shape_data = shape_data

    def get_name(self):
        return self.name

    @abstractmethod
    def get_area(self):
        pass

    @abstractmethod
    def get_perimeter(self):
        pass
```

## Inheritance with Abstract Classes
```python
# Shape类在上面
class Square(Shape):

    def get_area(self):
        return self.shape_data**2

    def get_perimeter(self):
        return self.shape_data*4

class Circle(Shape):

    def get_area(self):
        return pi*(self.shape_data**2)

    def get_perimeter(self):
        return 2*pi*self.shape_data

# 抽象方法必须被实现，否则无法实例化，会报错
my_circle = Circle('my circle', 3)
print("The area of " + my_circle.get_name() + " is: " + str(my_circle.get_area()))
print("The perimeter of " + my_circle.get_name() + " is: " + str(my_circle.get_perimeter()))

my_square = Square('my square', 3)
print("The area of " + my_square.get_name() + " is: " + str(my_square.get_area()))
print("The perimeter of " + my_square.get_name() + " is: " + str(my_square.get_perimeter()))
```
## Name Mangling & Convention

Python 中没有真正的“私有变量”，但有几种命名约定用来表示变量应该被视为“私有”或“受保护”。  
1. _var（单下划线开头） 
    - 表示“受保护的变量”，是一种约定（convention），不是强制隐藏。
    - 其他地方仍然可以访问 _var，只是表明“你不该动它”。
    ```python
      class MyClass:
          _class_var = 42  # 类变量，受保护的

          def __init__(self):
              self._x = 10   # 实例变量，受保护的

      obj = MyClass()
      print(obj._x)         # ✅ 可以访问
      print(MyClass._class_var)  # ✅ 也可以访问
    ```
2. __var（双下划线开头）
    - 触发“名称改写”（name mangling）机制，会将变量变为 _类名__变量名，从而“避免子类覆盖”或误用。
    - 这是一种“有限的封装”，但仍然不是绝对私有（只是更难访问）。
    ```python
      class MyClass:
          __class_var = 99  # 类变量，名称改写
          def __init__(self):
              self.__x = 10  # 实例变量，名称改写

      obj = MyClass()

      # print(obj.__x)              # ❌ 报错：AttributeError
      print(obj._MyClass__x)        # ✅ 可以访问
      print(MyClass._MyClass__class_var)  # ✅ 可以访问
    ```

总结

| 写法      | 是否隐藏       | 能否访问    | 推荐用途                            |
| --------- | -------------- | ----------- | ----------------------------------- |
| `var`     | 否             | ✅           | 公有变量                            |
| `_var`    | 否（仅约定）   | ✅           | 受保护变量                          |
| `__var`   | 是（名称改写） | ✅（可绕过） | 私有变量                            |
| `__var__` | 否             | ✅           | 特殊方法或魔法方法（如 `__init__`） |

   
# Week 10 Assertions, Exceptions and Unit Testing

## Raise exception
```python
raise ExceptionType("错误信息")
```

## Try/except
```python
try:
    # 主体代码：可能会抛出异常的操作
    risky_operation()
    
except SpecificError as e:
    # 处理特定异常（优先放具体的）
    print(f"Handled SpecificError: {e}")
    
except AnotherError as e:
    # 处理另一种异常
    print(f"Handled AnotherError: {e}")
    
except Exception as e:
    # 通用兜底（放最后）
    print(f"Unexpected error: {e}")
    
else:
    # 没有发生异常时才会执行
    print("Everything went fine!")
    
finally:
    # 无论是否发生异常，都会执行（清理资源等）
    print("Cleanup done.")
```

## Assert
```python
# python原生，不要导入任何模块
assert condition, "错误信息"

def set_age(age):
    assert age >= 0, "Age cannot be negative"
    print(f"Age set to {age}")

set_age(20)   # ✅
set_age(-1)   # ❌ AssertionError: Age cannot be negative
```

## Unit test
```python
# 被测试的类
class Calculator:
    def add(self, x, y):
        return x + y

    def divide(self, x, y):
        return x / y

# 测试代码
# 使用unittest的时候需要导入这个模块
# 如果使用assert，则不需要导入任何模块
import unittest

# 一定继承自unittest.TestCase
class TestCalculator(unittest.TestCase):

    def setUp(self):
        # 在每个 test_ 方法运行前执行
        self.calc = Calculator()  # 统一创建对象

    # 测试方法（test case） 必须以 test_ 开头，才能被自动识别和执行
    def test_add(self):
        result = self.calc.add(2, 3)
        self.assertEqual(result, 5)

    def test_divide(self):
        result = self.calc.divide(10, 2)
        self.assertEqual(result, 5)

    def test_divide_by_zero(self):
        # 这段代码的意思是：我希望 divide(1, 0) 这一句代码在运行时抛出 ZeroDivisionError 异常，
        # 如果没有抛出，测试就失败。
        with self.assertRaises(ZeroDivisionError):
            self.calc.divide(1, 0)

if __name__ == '__main__':
    unittest.main()
```

常用断言方法  

| 断言方法                    | 说明                        |
| --------------------------- | --------------------------- |
| `assertEqual(a, b)`         | 判断 `a == b`               |
| `assertNotEqual(a, b)`      | 判断 `a != b`               |
| `assertTrue(x)`             | 判断 `bool(x) is True`      |
| `assertFalse(x)`            | 判断 `bool(x) is False`     |
| `assertIs(a, b)`            | 判断 `a is b`（对象标识）   |
| `assertIsNot(a, b)`         | 判断 `a is not b`           |
| `assertIsNone(x)`           | 判断 `x is None`            |
| `assertIsNotNone(x)`        | 判断 `x is not None`        |
| `assertIn(a, b)`            | 判断 `a in b`               |
| `assertNotIn(a, b)`         | 判断 `a not in b`           |
| `assertIsInstance(a, b)`    | 判断 `isinstance(a, b)`     |
| `assertNotIsInstance(a, b)` | 判断 `not isinstance(a, b)` |

特殊断言方法

| 方法                                             | 说明                                        |
| ------------------------------------------------ | ------------------------------------------- |
| `assertAlmostEqual(a, b[, places])`              | 判断 `a` 和 `b` 近似相等，默认小数点后 7 位 |
| `assertNotAlmostEqual(a, b[, places])`           | 判断 `a` 和 `b` 不近似                      |
| `assertGreater(a, b)`                            | 判断 `a > b`                                |
| `assertGreaterEqual(a, b)`                       | 判断 `a >= b`                               |
| `assertLess(a, b)`                               | 判断 `a < b`                                |
| `assertLessEqual(a, b)`                          | 判断 `a <= b`                               |
| `assertRaises(exception, func, *args, **kwargs)` | 断言某异常被抛出                            |
| `assertRaisesRegex(exception, regex, ...)`       | 异常中包含匹配的错误信息                    |
| `assertWarns(warning, func, ...)`                | 判断是否产生指定 warning                    |
| `assertLogs(logger, level)`                      | 捕获 logging 输出                           |


## Test strategy
### Test cases

| 类型               | 含义                               |
| ------------------ | ---------------------------------- |
| **Valid cases**    | 正常输入                           |
| **Invalid cases**  | 非法输入（应抛异常或报错）         |
| **Boundary cases** | 接近边界的值（例如 0, 空, 极大值） |

### Test Cases for Functions
- return value test
- Side Effect Tests
- defending programming


### Testing Conditionals  
Edge cases are unusual or extreme values that push the limits of what your code can handle.   
Testing these ensures your program behaves correctly even in rare situations.
  - Negative numbers
  - Empty strings or lists
  - Zero
  - Equal boundary values (e.g., x == y)
  - Maximum or minimum allowed input

# Week 11 Recursion

## What is a recursion
递归是一种编程技巧，在这种技巧中，函数会调用自身来解决同类问题的更小实例。
每次递归调用都会处理一个更简单的子问题，直到达到基本情况（base case），从而停止递归。
它常用于可分解为相似子问题的结构，例如树、图或数学序列。

**Key ideas:**
- 递归函数必须有一个基本情况（base case），防止无限调用  
- 每次调用都应朝向基本情况（base case）推进
- 对于层级结构或分治类问题，递归通常比循环更容易理解

## Three laws of recursion
1. **Base Case Law**（基本情况定律 – 每个递归函数必须至少有一个可以不用递归就能解决的基本情况。
2. **Progress Law**（推进定律）– 每次递归调用都必须让问题更接近基本情况。 
3. **Design Law** （设计定律）– 设计递归函数时，要假设所有更小的子问题都能正确解。（也有说是必须调用自身）

## Examples of recursion
```python
# Sum of numbers
def sum_to_n(n):
    if n == 0:
        return 0
    return n + sum_to_n(n - 1)

# Reverse a string
def reverse(s):
    if len(s) <= 1:
        return s
    return reverse(s[1:]) + s[0]

# Implementations of the Fibonacci sequence
def fib(n):
    if n == 1 or n == 2:
        return 1
    return fib(n-1) + fib(n-2)
```

# Week 12 Advanced Python

## Optional parameters/Default arguments

## Lambda, filter and map

## List comprehensions

## zip