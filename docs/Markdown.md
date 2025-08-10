# Markdown 语法

更多语法&快速入门请参考:  
[快速入门](https://www.markdowntutorial.com/zh-cn/lesson/1/)  
[Markdown 语法参考](https://www.runoob.com/markdown/md-tutorial.html)

## 1. 标题

### 这是三级标题

#### 这是四级标题

##### 这是五级标题

###### 这是六级标题

!> 五级标题大小和六级标题的大小看起来差不多  
因为在许多 Markdown 渲染器中，五级标题和六级标题的字体大小确实非常接近，有时甚至相同  
在设计时，考虑到六级标题的使用频率较低，所以并没有为其设置特别小的字体大小

```markdown
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```

## 2. 斜体、粗体

_这是斜体_  
**这是粗体**  
**_这是斜体+粗体_**

```markdown
_这是斜体_
**这是粗体**
**_这是斜体+粗体_**
```

## 3. 超链接

局部链接:[Visit Github](https://www.github.com "Github")  
全局链接:[Visit Github][github]

```markdown
局部链接:[Visit Github](https://www.github.com "Github")
全局链接:[Visit Github][github]

(在文档底部)
[github]: https://www.github.com
```

## 4. 图片

局部链接:![Benjamin Bannekat](https://octodex.github.com/images/bannekat.png ":size=100x100")  
全局链接:![Benjamin Bannekat][Benjamin Bannekat]

```markdown
局部链接:![Benjamin Bannekat](https://octodex.github.com/images/bannekat.png ":size=100x100")
全局链接:![Benjamin Bannekat][Benjamin Bannekat]

(在文档底部)
[github]: [Benjamin Bannekat]: https://octodex.github.com/images/bannekat.png
```

## 5. 视频

<!-- <iframe src="//player.bilibili.com/player.html?aid=327623069&bvid=BV1JA411h7Gw&cid=171385214&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" height="700px" > </iframe> -->

```markdown
<iframe src="//player.bilibili.com/player.html?aid=327623069&bvid=BV1JA411h7Gw&cid=171385214&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" height="700px" > </iframe>
```

## 6. 引用块

> “无为而治的罪是所有七种罪中最致命的。有传言说，要使邪恶的人实现其目的，只需要好人无所事事。”

```markdown
> “无为而治的罪是所有七种罪中最致命的。有传言说，要使邪恶的人实现其目的，只需要好人无所事事。”
```

## 7. 代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

```markdown
    ```java
    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!");
        }
    }
    ```
```

## 8. 列表

无序列表:

- 上海
- 北京
- 重庆

- 深圳
- 四川

有序列表:

1. 标题
2. 斜体、粗体

任务列表:

- [ ] 吃饭
- [x] 睡觉

```markdown
有序列表:
* 上海
* 北京
* 重庆

- 深圳
- 四川

无序列表:
1. 标题
2. 斜体、粗体

任务列表:
- [ ] 吃饭
- [x] 睡觉
```

## 9. 段落

在每一行结尾输入一个回车没有换行的效果  
你可以通过在每一行的结尾输入俩个空格来实现这一点。  
空格是不可见的，输入的内容就像这样：

```markdown
在每一行结尾输入一个回车没有换行的效果··
你可以通过在每一行的结尾输入俩个空格来实现这一点。··
空格是不可见的，输入的内容就像这样：··
每个点（ · ）都代表一个空格。
```

## 10. 数学公式

$$
\frac{\partial f}{\partial x} = 2\sqrt{a}x
$$

$\theta=x^2$

```markdown
$$
\frac{\partial f}{\partial x} = 2\sqrt{a}x
$$

$\theta=x^2$
```

## 11. 表格

| 姓名   | 年龄 | 成绩 |
| :----- | :--: | ---: |
| 张三   |  19  |   99 |
| 李维斯 |  20  |  199 |

|     | 字段 | 类型  | 长度 | test |
| --- | ---- | ----- | ---- | ---- |
| 1   | mode | int   | 12   | 1    |
| 2   | http | array | 12   | 1    |

```markdown
| 姓名   | 年龄 | 成绩 |
| :----- | :--: | ---: |
| 张三   |  19  |   99 |
| 李维斯 |  20  |  199 |

|     | 字段 | 类型  | 长度 | test |
| --- | ---- | ----- | ---- | ---- |
| 1   | mode | int   | 12   | 1    |
| 2   | http | array | 12   | 1    |

:在左边表示左对齐，在右边表示右对齐，两边都有表示居中
```

## 12. 脚注

一键三年<sup id="a1">[三年](#f1)</sup>

```markdown
一键三年<sup id="a1">[三年](#f1)</sup>
<span id="f1">[三年](#a1)</span>:点赞、投币、收藏
```

## 13. 横线

---

```markdown
---
```

## 14. 下划线

<u>下划线</u>

```markdown
<u>下划线</u>
```

## 15. 表情

:smile: :100: 🙃 🫠  
详情参考:
<https://www.webfx.com/tools/emoji-cheat-sheet/>

```markdown
:smile: :100: 🙃
```

---

[github]: https://www.github.com
[Benjamin Bannekat]: https://octodex.github.com/images/bannekat.png

<span id="f1">[三年](#a1)</span>:点赞、投币、收藏
