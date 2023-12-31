# 高等数学（微积分视角）

<center>Karry Ren</center>

> 由于大学并未对高等数学进行系统的学习，所以也没有做什么像样的笔记，所以从 2023 年 8 月份开始，整理此笔记。本部分内容参考的是考研复习（《武老师高数强化精讲》），从微积分的视角出发构建起来整个高等数学的框架，既有核心概念，又有常见的问题出发点，还有系统的思考方式。
>
> 之所以还要再次系统地学习，是因为高数是一个极为基础、精准、有力的工具。只有将这些基础概念弄明白，才有可能在以后的科研和工作中进行规范化、系统化的理解数学原理，并进行补足和扩充，而不是东敲一锤子，西打一榔头。再然后才有可能实现理论上的突破。因而此次从微积分视角学习的核心也绝不在做题（作者并不是为了考研而学），而是在于完整的架构起来高数的`逻辑`，搞清楚整体的`框架`与具体的`理论`，进而在思考问题时有迹可循，出现新的理论时有空间去填充。
>
> ```c++
> 从微积分的视角出发，高等数学可分为五大部分：
> 
> 一、函数基础 // 函数的概念与性质
> 	1. 基本概念
> 	2. 极限
>   3. 连续
> 	
> 二、一元函数 // 在明确 “极限” 的概念后，就可以对一元函数的相关概念进行拓展
> 	1. 一元函数的微分
> 	2. 一元函数的积分
> 	
> 三、多元函数 // 从一元函数出发，引申出多元函数的微分和积分计算方式
> 	1. 多元函数的微分
> 	2. 多元函数的积分（尤其是二重积分）
> 	
> 四、微分方程 // 对微分概念的扩充（换一个方向理解微分）
> 
> 五、无穷级数 // 离散化无穷性
> ```



## 一、函数基础

### 第一节 基本概念

#### 1.1 函数的概念及常见函数

**==函数==**：本质在于定义域和对应关系

```
常见对定义域的判断，比如给出一个 f(x + 1) 的定义域，问 f(x) 的定义域
```

**==复合函数==**：内层函数的值域和外层函数的定义域相交

**==反函数==**：$x$ 和 $f(x)$ 一一对应，才有反函数

==**初等函数**==：由基础函数通过有限次加、减、乘、除、复合得到的函数

#### 1.2 函数的四大基本性态

#####  a. 单调性

**==定义==**：单调增、单调不减

**==应用==**：判断根的个数、不等式的证明（是否有等号）

**==判定==**：可以用定义判别（只适用于简单的函数）、求导进行判别（基本上所有题目都是这种方式）

```c++
导数在一个【区间】内大于零，确实可以判断函数在该区间内单调增。但如果只是在一个【点】上大于零（而无法推出一阶导数是连续的）则无法判断函数在该该点的临域内单调增（无论区间有多小），但如果再加上一个二阶导数存在就可以判断了，因为这样就能推出一阶导是连续的。
```

##### b. 奇偶性

**==定义==**：偶函数 $f(x) = f(-x)$，奇函数 $f(x) = -f(x)$

**==判定==**：

1. 直接用定义进行判定

2. 使用微分进行判定：奇函数的导函数是偶函数，偶函数的导函数是奇函数

3. 使用积分进行判定：连续奇函数的原函数都是偶函数，连续偶函数的原函数***<u>之一</u>***是奇函数

   > 只要涉及到原函数性质的判定，就需要使用变上限积分进行证明。
   >
   > 因为奇函数如果在原点有定义，其值一定是 0，所以对所加的常数有要求。

##### c. 周期性

**==定义==**：$f(x + T) = f(x)$

**==判定==**：

1. 直接用周期函数进行判定

2. 使用微分进行判定：可导周期函数的导函数是周期函数

3. 使用积分进行判定：周期函数原函数不一定是周期函数（需要再补一个条件，在一个周期上的积分是否为 0 ）

   > 只要涉及到原函数性质的判定，就要考虑变上限积分函数。因此要想保证周期函数的原函数还是周期函数就需要使用下面的这条性质（展开证明，注意证充要需要双向证明）。
   >
   > 设 $f(x)$ 连续，且以 $T$ 为周期，则 $F(x) = \int_0^xf(t)dt$ 是以 $T$ 为周期的周期函数 $\iff$ $\int_0^Tf(x)dx = 0$ 

##### d. 有界性

**==定义==**：若 $\exist M>0, \forall x\in I, |f(x)| \le M$ ；则称 $f(x)$ 在 $I$ 上有界

**==判定==**：

1. $f(x)$ 在闭区间上连续，那么在该闭区间上一定有界

2. $f(x)$ 在开区间上连续，并且其左端点的右极限和右端点的左极限存在，那么在该开区间上有界

3. 导数在某个**<u>*有限区间*</u>**上有界，那么对应函数在该区间上有界

   > 涉及到导数和其对应函数就要考虑中值定义（如果只涉及到单一函数，那就优先考虑拉格朗日中值定理）
   >
   > $|f(x)| = |f(x) - f(x_0) + f(x_0)| \le |f(x) - f(x_0)| + |f(x_0)| = |f^\prime(\zeta)(x - x_0)| + |f(x_0)| = ML +|f(x_0)|$

```c++
1. 证明有界
2. 已知有界，问原函数满足什么性质
	- 使用判定理论 2（开区间两边的端点上极限存在）
```

### 第二节 极限

#### 2.1 极限的概念

#### 2.2 极限的性质

#### 2.3 极限存在准则

#### 2.4 无穷小

#### 2.5 无穷大









#### 1.1 函数极限的定义及相关性质

==**定义**==：通过引入任意一个正数 $\epsilon$，以及$x \to ·$ 这两大概念构建起来函数的极限。其中 $x \to ·$ 可以是趋近于任何点的左右两边以及该点，或者正无穷、负无穷以及无穷。

==**性质**==：

1. 趋近于某个点存在极限的情况下，该点的左极限等于其右极限

#### 1.2 函数极限的计算

> 计算某个函数的极限是常见的问题，出现 $\frac{0}{0}$ 或 $\frac{∞}{∞}$ 的时候无法直接通过代入进行求解。
>
> 计算的核心思路其实就是一个：将原式变换为可以通过代入进行求解的形式，变换的思路有三种：
>
> 1. 通过各种等价公式进行变换（常见的公式变形）
> 2. 通过等价无穷小 / 大进行变换（本质是泰勒公式）
> 3. 通过洛必达法则进行变换（本质是套定义）

##### a. 泰勒公式

> - 同济大学上册（p137）
> - [公式汇总](https://zhuanlan.zhihu.com/p/323446382)

**==原理==**：对于一些较为复杂的函数，为了便于研究，往往希望用一些简单的函数来近似表达。由于多项式表示的函数，只需要对自变量进行有限次加、减、乘三种算术运算就可以求出它的函数值来，因此可以采用多项式来近似表达函数。泰勒公式的出发点就在于此，希望通过不断提高多项式的次数以尽可能提高多项式函数对原函数的逼近程度（通过图像就可以理解，不断提高次数的同时，多项式函数图像的性质与原函数愈发接近）。

**==方法==**：通过将原函数在某个点 $x_0$ 处进行展开，形成多项式函数。希望该多项式<u>该点处的值与原函数相同</u>，在<u>其周围范围内的点误差可控</u>。根据性质不同可以得到两种不同的泰勒展开：*<u>**泰勒中值定理 1.（带佩亚诺余项）**</u>*以及**<u>*泰勒中值定理 2.（带拉格朗日余项）*</u>**。这两种展开的区别是和原函数的误差大小，佩亚诺余项的大小是通过高阶无穷小表示的，拉格朗日余项（通过柯西中值定理推出）的大小则是通过具体的数值表示的。

**==应用==**：可以从上述方法中发现，泰勒公式可以在原函数的任意一点 $x_0$ 进行展开，且展开点的值与原函数肯定相同。我们把在 $x_0 = 0$ 处的展开成为**<u>*麦克劳林公式*</u>**。

1. 结合泰勒中值定理1.，可以得到**<u>*带佩亚诺余项的麦克劳林公式*</u>**，对函数进行近似化处理，用于函数极限的求解（等价无穷小替换）。
2. 结合泰勒中值定理2.，可以得到**<u>*带拉格朗日余项的麦克劳林公式*</u>**，对函数进行近似化处理，同时还能估计误差。

##### b.洛必达法则

> - 同济大学上册（p133）
> - [公式证明](https://zhuanlan.zhihu.com/p/109612952)（本质仍然是由柯西中值定理推出）

**==方法==**：对以分式形式出现的函数极限来说，如果出现 $\frac{0}{0}$ 或 $\frac{∞}{∞}$ ，并满足相应的条件，可以对分子分母同时求导后再做判断。

### 第三节 连续



