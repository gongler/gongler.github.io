---
layout: default
title: "在Jekyll网页显示数学表达式"
date: 2021-10-14 22:00:00 +0800
published: 2021-10-14 22:00:00 +0800
comments: true
categories: development
tags: [MathJax, jekyll]
github: "https://github.com/gongler/"
noimage: true
---
在Jekyll博客中如何显示数学表达式？这里我做了一个尝试。
<!--more-->

## 如何在Jekyll网页显示数学表达式

现在GitHub已经成了世界上最大的Git托管网站，集中了世界众多的开源项目。GitHub也可以托管博客。目前默认采用Jekyll处理博客，因此基于jekyll的网页很多。

能否在基于Jekyll的博客中显示数学表达式呢？在官网查找，并没能找到答案。查找更重资料，多次尝试，最终显示成功。在此把自己的配置方式分享给大家，希望有所帮助。

### 添加JavaScript代码块

在`_includes/head.html`尾部，</head>前，添加以下代码块。

```javascript
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      skipTags: ['script', 'noscript', 'style', 'textarea', 'pre']
    }
  });

  MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i=0; i < all.length; i += 1) {
      all[i].SourceElement().parentNode.className += ' has-jax';
    }
  });
</script>      
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"> </script>

```
### 添加css代码块

在assets/css/main.css的文件头部以下代码块：

``` css
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
```
数学公式插入格式为：

段间公式：

### 效果展示

```
$$
x=−a±b2−4ac
$$
```

$$
x=−a±b2−4ac
$$

```
$$
3x^2+4xy+5y^2+6=0
$$
```

$$
3x^2+4xy+5y^2+6=0
$$


```
$$
[x = {-b \pm \sqrt{b^2-4ac} \over 2a}]
$$
```


$$
[x = {-b \pm \sqrt{b^2-4ac} \over 2a}]
$$

数学符号A
```
$$
y = cos(\alpha)+sin(\beta)+abs(\lambda)+\delta +2\pi +\gamma+\epsilon+\theta +\kappa+ \mu + \xi+\rho+\sigma +\varsigma +\upsilon+\phi+\psi+\omega
$$
```

$$
y = cos(\alpha)+sin(\beta)+abs(\lambda)+\delta +2\pi +\gamma+\epsilon+\theta +\kappa+ \mu + \xi+\rho+\sigma +\varsigma +\upsilon+\phi+\psi+\omega
$$

数学符号B
```
$$
\mid \cdot \leq \geq \neg \approx \equiv \bigodot \bigotimes \bigoplus \pm \times \div \sum \prod \coprod
$$
```

$$
\mid \cdot \leq \geq \neg \approx \equiv \bigodot \bigotimes \bigoplus \pm \times \div \sum \prod \coprod
$$


```
$$
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{bmatrix}
$$
```


$$
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{bmatrix}
$$


```
$$
\begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{pmatrix}
$$
```

$$
\begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{pmatrix}
$$

```
$$
\begin{Bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{Bmatrix}
$$
```

$$
\begin{Bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{Bmatrix}
$$

```
$$
\begin{vmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{vmatrix}
$$
```

$$
\begin{vmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9 \end{vmatrix}
$$

```
$$
\begin{cases}
3x + 5y + z \\
7x - 2y + 4z \\
-6x + 3y + 2z
\tag{1} \end{cases}
$$
```

$$
\begin{cases}
3x + 5y + z \\
7x - 2y + 4z \\
-6x + 3y + 2z
\tag{1} \end{cases}
$$

```
$$
 \sigma(z) = \begin{cases}
1, & \text{if } z > 0 \\
0, & \text{if } z \le 0 \tag{2} \end{cases} 
$$
```

$$
 \sigma(z) = \begin{cases}
1, & \text{if } z > 0 \\
0, & \text{if } z \le 0 \tag{2} \end{cases} 
$$

```
$$
\begin{align}
f(x)&=(m+n)^{2}\\
&=m^{2}+2mn+n^{2}\\
\tag{3} \end{align}
$$
```

$$
\begin{align}
f(x)&=(m+n)^{2}\\
&=m^{2}+2mn+n^{2}\\
\tag{3} \end{align}
$$


### 更多例子

```
$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\]  另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\)  Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\]  另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)\,dx $$

\\[ f(x,y,z) = 3y^2 z \left( 3 + \frac{7x+5}{1 + y^2} \right). \\]


```

$$ \int_a^b f(x)\,dx $$ #Inline公式

\\[\int_0^{+\infty} x^n e^{-x} \,dx = n! \\]  另起一行居中公式

\\( p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\)  Inline公式

\\[ p\{X=x\}=f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}} \\]  另起一行居中公式

$$ F(x) = P\{ X <= x \} = \int_{-\infty}^x f(x)\,dx $$

\\[ f(x,y,z) = 3y^2 z \left( 3 + \frac{7x+5}{1 + y^2} \right). \\]



### 我的软件版本：

- node.js:  v14.17.5
- ruby:       v2.5.9
- gem:       v2.7.6.3
- jekyll:      v4.2.1 (gem list jekyll)
- CentOS:  v8 (cat /proc/version)

### 结尾

如果你没有成功，可以到我的GitHub看看源码：[gongler/gongler.github.io](https://github.com/gongler/gongler.github.io)，确认有什么差异。



