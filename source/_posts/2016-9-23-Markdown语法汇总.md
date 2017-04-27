title: "Markdown语法汇总"
date:   2016-09-23 15:19 +0800
comments: true
categories: Blog
tags: Blog
---

Markdown语法汇总
<!-- more -->


# 表格

```
标题1|标题2|标题3
---:|:-----:|:--
abc|上面的虚线可用多个减号代替|efg
123|英文冒号可以调节居左、中、右|456
```

效果：

标题1|标题2|标题3
---:|:-----:|:--
abc|上面的虚线可用多个减号代替|efg
123|英文冒号可以调节居左、中、右|456

## 数学符号：

运算符|说明|实例|代码
---|---|---|---|---
+|加|$ x + y $|`$ x + y $`
-|减|$ x - y $|`$ x - y $`
\times|乘|$ x \times y $|`$ x \times y $`
\cdot|乘|$ x \cdot y $|`$ x \cdot y $`
\ast|乘|$ x \ast y $|`$ x \ast y $`
\div|除|$ x \div y $|`$ x \div y $`
\frac|分数|$ \frac{x}{y} $|`$ \frac{x}{y} $`
^|上标|$ x ^ y $|`$ x ^ y $`
_ |下标|$ x _ y $|`$ x _ y $`
\sqrt|开二次方|$ \sqrt x $|`$ \sqrt x $`
\sqrt|开方|$ \sqrt[x]{y^4+3y-1} $|`$ \sqrt[x]{y^4+3y-1} $`
\lceil和\rceil|上取整|$ \lceil\frac12\rceil $|`$ \lceil\frac12\rceil $`
\lfloor和\rfloor|下取整|$ \lfloor\frac12\rfloor $|`$ \lfloor\frac12\rfloor $`
\pm|加减|$ x \pm y $|`$ x \pm y $`
\mp|减加|$ x \mp y $|`$ x \mp y $`
=|等于|$ x = y $|`$ x = y $`
\leq|小于等于|$ x \leq y $|`$ x \leq y $`
\geq|大于等于|$ x \geq y $|`$ x \geq y $`
\ngeq|不大于等于|$ x \ngeq y $|`$ x \ngeq y $`
\not\geq|不大于等于|$ x \not\geq y $|`$ x \not\geq y $`
\neq|不等于|$ x \neq y $|`$ x \neq y $`
\approx|约等于|$ x \approx y $|`$ x \approx y $`
\equiv|恒等于|$ x \equiv y $|`$ x \equiv y $`
\bigodot|定义运算符|$ x \bigodot y=x+y^2 $|`$ x \bigodot y=x+y^2 $`
\bigotimes|定义运算符|$ x \bigotimes y=x+y^2 $|`$ x \bigotimes y=x+y^2 $`
\in|属于|$ x \in y $|`$ x \in y $`
\notin|不属于|$ x \notin y $|`$ x \notin y $`
\subset|子集|$ x \subset y $|`$ x \subset y $`
\not\subset|非子集|$ x \not\subset y $|`$ x \not\subset y $`
\subseteq|子集|$ x \subseteq y $|`$ x \subseteq y $`
\supset|超集|$ x \supset y $|`$ x \supset y $`
\supseteq|超集|$ x \supseteq y $|`$ x \supseteq y $`
\cup|并|$ x \cup y $|`$ x \supseteq y $`
\cap|交|$ x \cap y $|`$ x \cap y $`
\log|对数|$ \log(x) $|`$ \log(x) $`
\overline|平均数|$ \overline{x} $|`$ \overline{x} $`
\overline|连线符号|$ \overline{a+b+c+d} $|`$ \overline{a+b+c+d} $`
\underline|下划线|$ \underline{a+b+c+d} $|`$ \underline{a+b+c+d} $`
\overbrace|上大括号|$\overbrace{a+\underbrace{b+c}_{1.0}+d}^{2.0}$|`$\overbrace{a+\underbrace{b+c}_{1.0}+d}^{2.0}$`
\underbrace|下大括号|$ \underbrace{a+d}_3 $|`$ \underbrace{a+d}_3 $`
\partial|部分|$ \frac{\partial x}{\partial y} $|`$ \frac{\partial x}{\partial y} $`
\lim|极限|$ \lim_{x\to\infty} $|`$ \lim_{x\to\infty} $`
\displaystyle|块公式格式|$ \displaystyle \lim_{x\to\infty} $|`$ \displaystyle \lim_{x\to\infty} $`
\sum|求和|$ \sum_{i=1}^n $|`$ \sum_{i=1}^n $`
\infty|极限|$ \sum_{i=0}^\infty i^2 $|`$ \sum_{i=0}^\infty i^2 $`
\int|积分|$ \int_0^1 x^2 {\rm d}x $|`$ \int_0^1 x^2 {\rm d}x $`
\iint|二重积分|$ \iint_D f(x,y)d\sigma $|`$ \iint_D f(x,y)d\sigma $`
\oint|曲面积分|$ \oint e^{x+y} ds $|`$ \oint e^{x+y} ds $`
\ldots|底端对齐的省略号|$ 1,2,\ldots,n $|`$ 1,2,\ldots,n $`
\cdots|中线对齐的省略号|$ x_1^2 + x_2^2 + \cdots + x_n^2 $|`$ x_1^2 + x_2^2 + \cdots + x_n^2 $`
\uparrow|上箭头|$ \uparrow $|`$ \uparrow $`
\Uparrow|上箭头|$ \Uparrow $|`$ \Uparrow $`
\vec|向量|$ \vec{a} $|`$ \vec{a} $`
\hat|拟合值|$\hat Y = \hat \beta_0 + \hat \beta_1X $|`$\hat Y = \hat \beta_0 + \hat \beta_1X $`
\bot|垂直|$ A \bot B $|`$ A \bot B $`
\circ|度|$ 45^\circ $|`$ 45^\circ $`

## 使用方法

> 在`$…$`中插入MathJax语法(只能在行内输入，不能换行）：

```
$S = \pi r^2$
```

$S = \pi r^2$

> 在`$$…$$`中插入MathJax语法（可以换行）：

```
$$
\Gamma(z) = \int_0^\infty t^{z-1} e^{-t} dt  
$$
```

$$
\Gamma(z) = \int_0^\infty t^{z-1} e^{-t} dt  
$$

## 附加内容

1. `$\sideset{^1_2}{^3_4}\bigotimes$` --> $\sideset{^1_2}{^3_4}\bigotimes$
2. 加空格：可以加 \空格，\quad 与 \qquad 的空格更大。
  * `$a\ bcd\quad efghij\qquad k$` --> $a\ bcd\quad efghij\qquad k$
3. `换行：\\`
  * `$1234\\567$` --> $ 1234\\\567 $
4. 括号自适应大小：
  * `$(\frac12)$` --> $(\frac12)$
  * `$ \left(\frac12\right)$` --> $ \left(\frac12\right)$
5. 方程组：
  * `$$\left\{\begin{array}{c}a_1x+b_1y+c_1z=d_1\\a_2x+b_2y+c_2z=d_2\\a_3x+b_3y+c_3z=d_3\end{array}\right.$$`
  $$\\left\\{\\begin{array}{c}a_1x+b_1y+c_1z=d_1\\\\a_2x+b_2y+c_2z=d_2\\\\a_3x+b_3y+c_3z=d_3\\end{array}\\right.$$


# 字体

语法|字体|例子|效果
---|---|---|---
\rm|罗马体</td style="border-style: solid; border-width: 0px 1px 1px 0px; border-color: rgb(221, 221, 221);padding: 5px 10px;">|`{$\rm 你好，World，123$}`|{$\rm 你好，World，123$}
\bf|黑体|`{$\bf 你好，World，123$}`|{$\bf 你好，World，123$}
\Bbb|黑板粗体字|`{$\Bbb 你好，World，123$}`|{$\Bbb 你好，World，123$}
\mit|数学斜体|`{$\mit 你好，World，123$}`|{$\mit 你好，World，123$}
\scr|小体大写字母|`{$\scr 你好，World，123$}`|{$\mit 你好，World，123$}
\it|意大利体|`{$\it 你好，World，123$}`|{$\mit 你好，World，123$}
\cal|花体|`{$\cal 你好，World，123$}`|{$\cal 你好，World，123$}
\sf|等线体|`{$\sf 你好，World，123$}`|{$\sf 你好，World，123$}
\tt|打字机字体|`{$\tt 你好，World，123$}`|{$\tt 你好，World，123$}
\frak|Fraktur字母（一种德国字体）|`{$\frak 你好，World，123$}`|{$\frak 你好，World，123$}

# 颜色

代码|效果
---|---
`$\color{black}{Hello World!}$`|$\color{black}{Hello World!}$
`$\color{gray}{Hello World!}$`|$\color{gray}{Hello World!}$
`$\color{silver}{Hello World!}$`|$\color{silver}{Hello World!}$
`$\color{white}{Hello World!}$`|$\color{white}{Hello World!}$
`$\color{maroon}{Hello World!}$`|$\color{maroon}{Hello World!}$
`$\color{red}{Hello World!}$`|$\color{red}{Hello World!}$
`$\color{yellow}{Hello World!}$`|$\color{yellow}{Hello World!}$
`$\color{lime}{Hello World!}$`|$\color{lime}{Hello World!}$
`$\color{olive}{Hello World!}$`|$\color{olive}{Hello World!}$
`$\color{green}{Hello World!}$`|$\color{green}{Hello World!}$
`$\color{teal}{Hello World!}$`|$\color{teal}{Hello World!}$
`$\color{aqua}{Hello World!}$`|$\color{aqua}{Hello World!}$
`$\color{blue}{Hello World!}$`|$\color{blue}{Hello World!}$
`$\color{navy}{Hello World!}$`|$\color{navy}{Hello World!}$
`$\color{purple}{Hello World!}$`|$\color{purple}{Hello World!}$
`$\color{fuchsia}{Hello World!}$`|$\color{fuchsia}{Hello World!}$
