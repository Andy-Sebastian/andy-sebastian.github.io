# Week 1

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
| 操作符 |           英文名           |     含义     |    等价于    |
| :----: | :------------------------: | :----------: | :----------: |
|  `=`   |         Assignment         |   直接赋值   |      —       |
|  `+=`  |     Add AND Assignment     |   加并赋值   | `x = x + y`  |
|  `-=`  |  Subtract AND Assignment   |   减并赋值   | `x = x - y`  |
|  `*=`  |  Multiply AND Assignment   |   乘并赋值   | `x = x * y`  |
|  `/=`  |   Divide AND Assignment    |   除并赋值   | `x = x / y`  |
| `//=`  |  Floor Divide AND Assign   | 地板除并赋值 | `x = x // y` |
|  `%=`  |   Modulus AND Assignment   |  取余并赋值  | `x = x % y`  |
| `**=`  |  Exponent AND Assignment   | 幂运算并赋值 | `x = x ** y` |
|  `&=`  |   Bitwise AND Assignment   |  位与并赋值  | `x = x & y`  |
| `\|=`  |   Bitwise OR Assignment    |  位或并赋值  | `x = x \| y` |
|  `^=`  |   Bitwise XOR Assignment   | 位异或并赋值 | `x = x ^ y`  |
| `<<=`  | Left Shift AND Assignment  |  左移并赋值  | `x = x << y` |
| `>>=`  | Right Shift AND Assignment |  右移并赋值  | `x = x >> y` |

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

### 🔢 运算符优先级表

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

### ⚠️ 常见错误提示

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

# Week 2

## 字符串和列表 (Strings and Lists)
- 字符串 (`str`) 和列表 (`list`) 都是 Python 的序列类型。
- 字符串是不可变的，列表是可变的。
- 切片和索引操作：`my_list[0]`, `my_str[1:3]`。
- 常用操作：拼接（`+`）、重复（`*`）、长度（`len()`）。

## Python 常用字符串与列表方法笔记

### 📜 字符串 (`str`) 方法

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


### 📜 列表 (`list`) 方法

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

## The 'in' and 'not in' operators
- 用于判断元素是否在序列中：
```python
'a' in 'apple'       # True
3 not in [1, 2, 4]   # True
```
- 返回值是布尔类型（`True` 或 `False`）。

## Conditional Execution: Binary Selection
- 二元选择：`if ... else ...` 结构。
```python
if condition:
    # 真分支
else:
    # 假分支
```

## Omitting the 'else' Clause: Unary Selection
- 一元选择：只有 `if`，没有 `else`。
```python
if condition:
    # 真分支
```

## Nested Conditionals
- 条件语句的嵌套使用。
```python
if condition1:
    if condition2:
        # 两个条件都为真
```

## Chained Conditionals
- 使用 `elif` 链接多个条件分支。
```python
if condition1:
    ...
elif condition2:
    ...
else:
    ...
```

## Setting Up Conditionals
- 设计条件判断时的步骤：
  1. 明确条件。
  2. 确定条件顺序。
  3. 合理使用 `if`、`elif`、`else`。

## Introduction to 'While' Loops
- `while` 循环：当条件为真时重复执行。
```python
while condition:
    # 循环体
```

## The 'While' Statement
- 注意避免死循环（条件永远为真）。
- 循环中常用 `break` 和 `continue` 控制流程。

## Break and Continue
- `break`：立即结束当前循环。
- `continue`：跳过本次循环剩余部分，直接进入下一次循环。

# Week 3

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

| 特性 | 可变序列（list, bytearray） | 不可变序列（str, tuple, range） |
|------|----------------------------|--------------------------------|
| 是否可修改元素 | ✅ | ❌ |
| 修改方式 | 直接修改元素、追加、删除 | 必须创建新对象 |
| 示例 | `lst[0] = 99` | 不允许 `s[0] = "H"` |

---

### 5. 常用内置函数

| 函数 | 作用 | 示例 |
|------|------|------|
| `len(seq)` | 返回长度 | `len("abc") → 3` |
| `max(seq)` | 返回最大值 | `max([1, 5, 3]) → 5` |
| `min(seq)` | 返回最小值 | `min("cab") → 'a'` |
| `sum(seq)` | 求和（数字序列） | `sum([1, 2, 3]) → 6` |
| `sorted(seq)` | 返回排序后的新列表 | `sorted("cab") → ['a','b','c']` |
| `reversed(seq)` | 返回反向迭代器 | `list(reversed([1,2,3])) → [3,2,1]` |

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
