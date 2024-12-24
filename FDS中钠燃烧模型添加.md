---
typora-root-url: ./FDS中钠燃烧模型添加.assets
---

[TOC]

# 钠物性

| Quantity                                                     | Value      | Units       | Method | Reference                                                    | Comment                                                      |
| ------------------------------------------------------------ | ---------- | ----------- | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $T_{boil}$                                                   | **1156.**  | K           | N/A    | [Honig and Kramer, 1969](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=4#ref-1) | Uncertainty assigned by TRC = 1. K; *TRC*                    |
| Quantity                                                     | Value      | Units       | Method | Reference                                                    | Comment                                                      |
| $T_{fus}$                                                    | **370.96** | K           | N/A    | [Marsh, 1987](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=4#ref-2) | Uncertainty assigned by TRC = 0.01 K; recommended as fixed point for thermometry; *TRC* |
| Quantity                                                     | Value      | Units       | Method | Reference                                                    | Comment                                                      |
| $T_{triple}$                                                 | 370.98     | K           | N/A    | [Honig and Kramer, 1969](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=4#ref-1) | Uncertainty assigned by TRC = 0.03 K; *TRC*                  |
| Heat Capacity (298.15K) ![heat capacity](https://cccbdb.nist.gov/gifs/logocp.gif) | 20.79      | J K-1 mol-1 |        | [JANAF](https://cccbdb.nist.gov/exp2.asp#JANAF)              |                                                              |

## Liquid Phase Heat Capacity (Shomate Equation)

$Cp° = A + B*t + C*t^2 + Dt^3 + E/t^2$
$H° − H°_{298.15}= At + Bt^2/2 + Ct^3/3 + Dt^4/4 − E/t + F − H$
$S° = Aln(t) + B*t + C*t^2/2 + D*t^3/3 − E/(2*t^2) + G$
  Cp = heat capacity (J/(molK)
  H° = standard enthalpy (kJ/mol)
  S° = standard entropy (J/(mol*K)
  t = temperature (K) / 1000.

| Temperature (K) | 370.98 to 1170.525                                           |
| :-------------- | ------------------------------------------------------------ |
| A               | 40.25707                                                     |
| B               | -28.23849                                                    |
| C               | 20.69402                                                     |
| D               | -3.641872                                                    |
| E               | -0.079874                                                    |
| F               | -8.782300                                                    |
| G               | 113.6646                                                     |
| H               | 2.406001                                                     |
| Reference       | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-1) |
| Comment         | Data last reviewed in June, 1962                             |

| Quantity            | Value        | Units   | Method                                                       | Reference                                                    | Comment                          |
| ------------------- | ------------ | ------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------- |
| $Δ_fH°_{liquid}$    | **2.41**     | kJ/mol  | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-1) | Data last reviewed in June, 1962 |
| Quantity            | Value        | Units   | Method                                                       | Reference                                                    | Comment                          |
| $S°_{liquid,1 bar}$ | 57.86        | J/mol*K | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-1) | Data last reviewed in June, 1962 |
| Quantity            | Value        | Units   | Method                                                       | Reference                                                    | Comment                          |
| $S°_{solid,1 bar}$  | 51.30 ± 0.20 | J/mol*K | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Cox, Wagman, et al., 1984](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-2) | CODATA Review value              |
| Quantity            | Value        | Units   | Method                                                       | Reference                                                    | Comment                          |
| $S°_{solid}$        | 51.46        | J/mol*K | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-1) | Data last reviewed in June, 1962 |

> $S°_{liquid,1 bar}$ Entropy of liquid at standard conditions (1 bar)
>
> $S°_{solid}$ Entropy of solid at standard conditions
>
> $S°_{solid,1 bar}$ Entropy of solid at standard conditions (1 bar)
>
> $Δ_fH°_{liquid}$ Enthalpy of formation of liquid at standard conditions



## Gas Phase Heat Capacity (Shomate Equation)

$Cp° = A + B*t + C*t^2 + Dt^3 + E/t^2$
$H° − H°_{298.15}= At + Bt^2/2 + Ct^3/3 + Dt^4/4 − E/t + F − H$
$S° = A*ln(t) + B*t + C*t^2/2 + D*t^3/3 − E/(2*t^2) + G$
  Cp = heat capacity (J/mol*K)
  H° = standard enthalpy (kJ/mol)
  S° = standard entropy (J/mol*K)
  t = temperature (K) / 1000.

| Temperature (K) | 1170.525 to 6000.                                            |
| :-------------- | ------------------------------------------------------------ |
| A               | 20.80573                                                     |
| B               | 0.277206                                                     |
| C               | -0.392086                                                    |
| D               | 0.119634                                                     |
| E               | -0.008879                                                    |
| F               | 101.0386                                                     |
| G               | 178.7095                                                     |
| H               | 107.2999                                                     |
| Reference       | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=1#ref-2) |
| Comment         | Data last reviewed in June, 1962                             |

| Quantity         | Value           | Units     | Method                                                       | Reference                                                    | Comment                          |
| ---------------- | --------------- | --------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------- |
| $Δ_fH°_{gas}$    | 107.5 ± 0.7     | kJ/mol    | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Cox, Wagman, et al., 1984](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=1#ref-1) | CODATA Review value              |
| $Δ_fH°_{gas}$    | **107.30**      | kJ/mol    | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=1#ref-2) | Data last reviewed in June, 1962 |
| **Quantity**     | **Value**       | **Units** | **Method**                                                   | **Reference**                                                | **Comment**                      |
| $S°_{gas,1 bar}$ | 153.718 ± 0.003 | J/mol*K   | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Cox, Wagman, et al., 1984](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=1#ref-1) | CODATA Review value              |
| $S°_{gas,1 bar}$ | 153.65          | J/mol*K   | [Review](https://webbook.nist.gov/chemistry/enthalpy.html#Review) | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=1#ref-2) | Data last reviewed in June, 1962 |

> $S°_{gas,1 bar}$ Entropy of gas at standard conditions (1 bar)
>
> $Δ_fH°_{gas}$ Enthalpy of formation of gas at standard conditions



## Solid Phase Heat Capacity (Shomate Equation)

$Cp° = A + Bt + Ct^2 + Dt^3 + E/t^2$
$H° − H°_{298.15}= At + B^t2/2 + Ct^3/3 + Dt^4/4 − E/t + F − H$
$S° = A*ln(t) + B*t + C*t^2/2 + D*t^3/3 − E/(2*t^2) + G$
  Cp = heat capacity (J/mol*K)
  H° = standard enthalpy (kJ/mol)
  S° = standard entropy (J/mol*K)
  t = temperature (K) / 1000.

| Temperature (K) | 298. to 370.                                                 |
| :-------------- | ------------------------------------------------------------ |
| A               | 72.63675                                                     |
| B               | -9.491572                                                    |
| C               | -730.9322                                                    |
| D               | 1414.518                                                     |
| E               | -1.259377                                                    |
| F               | -21.79467                                                    |
| G               | 155.0963                                                     |
| H               | 0.000000                                                     |
| Reference       | [Chase, 1998](https://webbook.nist.gov/cgi/cbook.cgi?ID=C7440235&Mask=2#ref-1) |
| Comment         | Data last reviewed in June, 1962                             |

（气体状态下）钠及其氧化物的leonard-jones参数[^11]：

| 组分种类  | $\epsilon/k(K)$ | $\sigma(\times 10^{-10}m)$ |
| :-------- | --------------- | -------------------------- |
| $O_2$     | 106.7           | 3.467                      |
| $N_2$     | 71.4            | 3.798                      |
| $Na$      | 712.28          | 1.192                      |
| $Na_2O$   | 2697.98         | 1.606                      |
| $Na_2O_2$ | 1820.16         | 1.682                      |

以下参考[^3][^4]:P22

（1）液态钠的密度
$$
{{\rho }_{l}}={{\rho }_{c}}+f\left( 1-\frac{T}{{{T}_{c}}} \right)+g{{\left( 1-\frac{T}{{{T}_{c}}} \right)}^{0.5}}
$$
适用范围：$371K\le T\le 2503.7K$

式中，${{\rho }_{c}}$——临界密度，$219kg/{{m}^{3}}$；

   ${{T}_{c}}$——临界温度，2503.7K；

   $f$——常数，275.32；

   $g$——常数，511.8。

（2）液态钠的汽化潜热
$$
{{H}_{fg}}=393.37\left( 1-\frac{T}{{{T}_{c}}} \right)+4398.6{{\left( 1-\frac{T}{{{T}_{c}}} \right)}^{0.29302}}
$$
适用范围：$371K\le T\le 2503.7K$

（3）液态钠的定压比热
$$
{{c}_{p}}=38.121-0.069\times {{10}^{6}}{{T}^{-2}}-19.493\times {{10}^{-3}}T+10.240\times {{10}^{-6}}{{T}^{2}}
$$

适用范围：$371K\le T\le 2300K$

王式保：$kJ/kg/K$
$$
{{c}_{p}}=1.5919-6.6637\times {{10}^{-4}}{{T}}+2.6883\times {{10}^{-7}}T^2-5.8546\times {{10}^{-11}}{{T}^{3}}
$$
适用范围：$371𝐾≤𝑇≤1900𝐾$

（4）液态钠的动力粘度
$$
ln \eta =-6.4406-0.3958\ln T+\frac{556.835}{T}
$$


适用范围：$371K\le T\le 2300K$

（5）液态钠的导热系数$W/m/K$
$$
K=124.67-0.11381T+5.522610\times {{10}^{-5}}{{T}^{2}}-1.184210\times {{10}^{-8}}{{T}^{3}}
$$
适用范围：$371K\le T\le 2300K$

（6）钠蒸气的比热容
$$
{{c}_{p,Na,gas}}=1.6582-8.479\times {{10}^{-4}}T+4.4541\times {{10}^{-7}}{{T}^{2}}-2992.6{{T}^{-2}}
$$
（7）液态金属钠的定压比热计算采用的是洪顺章推荐的拟合公式
$$
c_p=38.121-0.069\times 10^6T^{-2}-19.493\times 10^{-3}T+10.240\times 10^{-6}T^2
$$
适用范围：$371K\le T\le 2300K$

（8）液态金属钠的表面张力(N/m)[^5]:interrobang:
$$
\sigma=202-0.091(T-371)
$$
适用范围：$370K\le T\le 1200K$

## 钠的物性参数

*参考401资料*

借助JANAF 表[1]里面的物质属性的参数以及其他相关文献，找到了钠、氧化钠和过氧化钠在固体、液体、气体状态下的物性参数，如下表所示：

| 名称         | Na    | Na2O    | Na2O2   | 单位            | 文献          |
| ------------ | ----- | ------- | ------- | --------------- | ------------- |
| 熔点         | 370   | 1405    | 785     | K               | ref[^p1]      |
| 汽化温度     | 1155  | 2220    | 930     | K               | ref[^p1]      |
| 汽化放热     | Eq.1  |         |         | $kJ/kg$         | ref[^p2]      |
| 液体比热     | Eq.2  | 1688    | 1457    | $J/(kg\cdot K)$ | ref[^p1][^p3] |
| 液体密度     | Eq.3  | 2270    | 2805    | $kg/m^3$        | ref[^p3]      |
| 热焓？       | 2.406 | -417.98 | -513.21 | $kJ/mol$        | ref[^p1]      |
| 吉布斯自由能 | 107.5 | -377.1  | -446.9  | $kJ/mol$        | ref[^p1]      |

Eq.3液体钠密度，在熔化温度和汽化温度之间时，是关于温度的方程：
$$
\rho=1014-0.235\mathrm{T}
$$
Eq.2液体钠的比热也是关于温度的方程：
$$
\mathrm{C_p(T)=-~3.001\times10^6T^{-2}+1658-0.8479T+4.454\times10^{-4}T^2}
$$
Eq.1液钠蒸发放热关于温度的方程为(汽化潜热)：
$$
\mathrm{H_v=393.37(1-T/T_c)+4398.6(1-T/T_c)^{0.29302}}
$$
其中，$371\mathrm{K}<T<2503.7K$且$T_c=2503.7K$。

****

[^p1]:
[^p2]:
[^p3]:

****



# 钠的燃烧反应

在[^1]空气中，特别是同时有水蒸气存在，金属钠非常容易产生燃烧，产生多种产物。 但在所有的产物中，只有两种氧化物较为丰富，分别是氧化钠和过氧化钠。氧化钠的熔点为1132℃，当温度到达1950℃时会被分解，氧化钠的相关反应如下：
$$
2Na+{1\over2}O_2\rightarrow Na_2O
$$
该反应为放热反应，**释热量为9187.9 J/g（燃烧热）**，**当在氧气比例较大时，氧化钠会近一步 氧化成为过氧化钠**，过氧化钠的熔点为674℃，并且会在1627℃时分解，反应过程中， 会有**10464.6J/g**的热量释放，生成过氧化钠的反应如下：
$$
2Na+O_2\rightarrow Na_2O_2
$$
液态金属钠还可能会与水蒸气反应，化学反应方程如下：
$$
2Na+2H_2O(liquid)\rightarrow 2NaOH+H_2\uparrow
$$
钠是质软银白色金属，在98℃时熔化。钠在含有氧气的环境中会着火，着火时形成各种各样氧化物。但主要生成两种氧化物，即$Na_2O$和$Na_2O_2$。钠着火伴随如下化学反应[^2]：  
$$
2Na+{1\over2}O_2\rightarrow Na_2O\quad \Delta H=-418.1kJ/mol \\
2Na+O_2\rightarrow Na_2O_2\quad \Delta H=-513kJ/mol
$$
在氧气过量的情况下$Na_2O_2$是主要反应产物；在钠过量的情况下$Na_2O$是主要反应产物。  

$$
2Na+H_2O(vapor)\rightarrow Na_2O+H_2\uparrow
$$

$$
Na_2O_2+2Na\rightarrow 2Na_2O
$$

$$
Na_2O+H_2O\rightarrow 2NaOH
$$

$$
Na_2O_2+H_2O\rightarrow 2NaOH+{1\over2}O_2\uparrow
$$

钠火的特征为火焰和**白色浓密烟雾**。燃烧的钠一部分形成**烟雾**，另一部分是**钠氧化物形式的沉积物**。沉积物和烟雾中的反应产物都包括$Na_2O$和$Na_2O_2$。 在氧气过量时，$Na_2O_2$是主要的反应产物；在钠过量时，$Na_2O$是主要的；在这两者之间时，两种氧化物都可能大量形成。



## 钠的燃烧机理

钠的燃点温度与很多因素有关，如钠的纯度、燃烧气体温度、表面条件和氧化率等等。

钠的点燃与其表面的氧化物层的性质和直接相关。一般地，随着温度的变化，钠表面氧化物层的形成遵循不同的规律。**钠温度较低时**其氧化速率与时间呈对数关系，表面氧化物层起保护作用，防止钠的进一步氧化；随着**钠温度的升高**，其氧化速率与时间呈抛物线关系，表面氧化物层不再是保护层，但它阻止钠与氧气直接反应，氧气通过扩散穿过氧化层与钠反应；**钠温度较高时**参与钠氧化反应的氧气消耗量是时间的线性函数，其表面氧化物层的多孔度己经足以使氧气通过并维持钠氧化反应。**钠氧化规律从抛物线变化为线性规律时的温度称为钠的转换温度**。转变温度的值取决于影响钠氧化物的各种物理和化学变形。物理变形包括氧化物的升华、熔化，相变造成的收缩，以及由于钠和氧化物的热膨胀系数不同造成的氧化层的破裂等。化学变形指氧化层化学成分的改变。如果钠氧化反应产生的热量多于系统内丧失的热量，在达到其转换温度时会点燃钠。
钠的点燃和钠的存在形式有关。在钠池中钠与氧气接触后形成的氧化层会阻止钠的燃烧。但钠池的运动会使氧化层破碎。因此在相同的条件下搅动的钠池比未受干扰的钠池更容易发生燃烧。钠以微滴的形式存在时更容易点燃。同时**钠的燃点在一定范围内随着氧气的摩尔份额的降低而升高**。钠点燃需要的最小氧气的摩尔份额约为3%。实验表明，**不受干扰的钠池在干燥的空气其燃点约为205℃，氧气摩尔份额为5%时约为344℃。**

**钠点燃之后，将以气态形式继续燃烧**。燃烧时燃烧热从火焰传到钠表面， 为钠提供汽化潜热。在距钠表面一定距离内存在火焰区并形成烟雾。这些烟雾由非常细小的氧化物微粒组成。火焰区内液态或者固体氧化物微粒、气态分子或原子的同时存在，造成钠燃烧各向异性的特点。
:interrobang:**钠氧化物分子在气态条件下不能存在。它们会很快分解为钠蒸汽和氧气**。 <font color=red>**钠氧化物颗粒的这种热不稳定性形成了火焰温度的上限**</font>。通常**认为钠氧化物的分解温度是它的沸点**。其**火焰温度位于钠表面温度和钠氧化物沸点之间**。

房间内气体的辐射传热能力极小。通过辐射进行热交换并不是在空气和墙壁之间发生，而是在房间气体中的气溶胶和墙壁之间发生。研究表明，火灾时所产生的气溶胶和房间内气体的温度将很快一致。因此，**可以认为气溶胶和气体温度相同**。

**钠燃烧反应的阈值**：反应阈值与温度/组分浓度等反应条件相关，由实验数据或化学反应动力学仿真结果确定阈值曲线。

![image-20240624094810061](..\FDS中钠燃烧模型添加.assets\image-20240624094810061.png)



## 钠火分类

当钠流本身只是部分燃烧或不燃烧，主要能量由形成的钠池释放时，发生池式钠火（比较典型的工况为管道大破口或者双端断裂）。钠池的燃烧速率是能量释放的主要参数，它和**钠池表面积、钠池厚度、钠的温度、大气中的氧气浓度以及大气湿度等参数直接相关**。实验表明，钠池的燃烧速率随钠池表面积而增大，在达到某一个值(约为$12m^2$)后停止增长，一般不高于$36kg/(m^2∙h)$。比较典型的情况是管道断裂或者大泄漏。这时管道保温层被迅速破坏，钠可以不受干扰地迅速流至地面形成钠池并发生池式钠火。

典型的池式钠火有三个阶段：

1.在最初的数分钟内，周围空气剧烈受热，直到接近燃烧过程中的最高温度。钠的受热取决于钠容器的条件(如材料、保温层等)和钠池的厚度。

2.第二阶段温度接近稳定水平，其温度取决于钠池的尺寸、钠容器的容积和通过墙壁的热传递。

3.在第三阶段，钠池内的热残留物逐渐冷却。

钠池式燃烧过程是图所示的双线现象。一方面，氧气通过火焰区扩散与液钠反应并形成氧化层；另一方面，钠蒸汽汽化扩散至火焰区。在不同的氧气的压力、温度和浓度条件下，钠形成气态燃烧或在表面燃烧。气态钠火在火焰区形成*Na*2*O*并在火焰区尾部转变为*Na*2*O*2。表面钠火燃烧形成*Na*2*O*2。<font color=red>**在通常的钠火条件下，即周围环境为空气，钠温在200℃~500℃时，只发生气态燃烧。气溶胶由*Na*2*O*2组成。容器中钠燃烧的残余物基本上由Na2O组成，包括少量的Na2O2**</font>。钠燃烧结束时，气溶胶中钠的含量，最高为燃烧的钠质量的45%， Na2O2占钠燃烧产物的平均百分数约为52%。

![image-20240521160000461](..\FDS中钠燃烧模型添加.assets\image-20240521160000461.png)



喷雾钠火的特点是钠以微滴的形式在空气中立即燃烧。在**破口散开或被障碍物散开的喷雾钠流可能形成喷雾钠火**（比较典型的工况为高压力管道上发生不规则的小破口泄漏）。其能量释放与钠流量直接相关。与表面积为12*m*2，燃烧速率为36*kg*/(*m*2∙*h*)的大型池式钠火相比，即使是小泄漏(约为0.1*m*2的孔)，喷雾钠火的燃烧速率可能也可以达到这个值。

钠泄漏的流量和钠的泄漏总量是影响喷雾钠火后果的最重要的因素。其它因素还有钠喷流的几何条件和形状。**钠燃烧速率取决于液态钠滴表面的钠汽化速度。钠汽化速度由向钠滴的热传递的速度决定**。[一文看懂：单颗粒在流体中的受力 - CFD-Tyro - 博客园 (cnblogs.com)](https://www.cnblogs.com/cfd-tyro/articles/15989193.html)

**钠滴的预燃阶段**：在预燃阶段，表面氧化过程会在钠滴表面形成一层粗糙的氧化物膜。氧化过程产生的热量返回到钠滴表面而不是传递给气态环境。这导致钠滴温度的快速上升。当达到钠滴的燃点温度时，钠滴被点燃。

实验表明， 在气相燃烧期间的绝大部分时间内钠滴处于沸点温度。



一般而言，喷雾钠火在事故早期将产生一个压力峰值，而池式钠火在事故的长时间内形成温度峰值。混合钠火类似池式钠火和燃烧的钠流的组合。其行为主要取决于位于破口和钠池表面之间的钠流的特性。如果钠流在下落过程中没有以喷雾形式完全燃烧，剩余部分在地面形成钠池并以钠池形式燃烧，则造成混合钠火。如果钠流不被干扰，仅仅依靠水力学效应散开并在地面形成钠池，则钠流释放的能量较小，能量主要由钠池释放。这时混合钠火的后果与池式钠火相当。如果钠流被干扰后在下落过程中燃烧较充分，而落在地面形成钠池的部分较少，能量释放主要由钠流释放，则混合钠火的后果与喷雾钠火相当。

<font color=red>参见能动学院ppt《燃烧学讲义2019-第六章》</font>

![image-20241115095754956](./image-20241115095754956.png)

![image-20241115095904870](./image-20241115095904870.png)

![image-20241115100007713](./image-20241115100007713.png)

![image-20241115100307052](./image-20241115100307052.png)

# 钠的其他反应

气溶胶最初由$Na_2O_2$组成，与水反应生成腐蚀性极强的$NaOH$，使得气溶胶具有很强的氧化能力。同时反应中形成了$H_2O_2$，它在反应热和$NaOH$的影响下分解，容易产生特别活跃的新鲜氧气。房间中的有机元素，尤其是油漆容易燃烧。当氧化物沉积超过500g/m2钠时，容易发生**钠的二次燃烧**。沉积物是钠、$Na_2O_2$和$Na_2O$的混合物。它们也可能变成氢氧化物和碳酸盐。这些高活性的产物，尤其是$Na_2O_2$和$NaOH$的释放，对人和环境均有害。

## 程序对比

文献[^1]

| 计算方法               | 程序名称             | 钠火类型   | 是否借助于 第三方CFD 软件平台 | 特点比较                                                     |
| ---------------------- | -------------------- | ---------- | ----------------------------- | ------------------------------------------------------------ |
| 集总参数法             | **PYROSI**           | 池式钠火   | 否                            | 不需要划分网格，计算量相对最少，方程求解速度快，只能得到整个房间内平均温度，压力和氧气浓度等参数 |
|                        | SPOOL                | 池式钠火   | 否                            | 同上                                                         |
|                        | FEUMIX               | 池式钠火   | 否                            | 同上                                                         |
|                        | NACOM                | 喷雾钠火   | 否                            | 同上                                                         |
|                        | SOFIRE-M3            | 柱状流钠火 | 否                            | 同上                                                         |
| 双单元模型             | SOFIRE               | 池式钠火   | 否                            | 需要划分单元，但单元数目较少,计算量较小，燃烧区域以外的区域只能得到总的平均参数，燃烧区域内只能得到一个方向上参数分布 |
|                        | SPRAY                | 喷雾钠火   | 否                            | 同上                                                         |
|                        | SSPRAY               | 喷雾钠火   | 否                            | 同上                                                         |
| 三维的欧拉- 拉格朗日法 | AQUA-SF              | 喷雾钠火   | 是                            | 需要划分详细的网格，计算量较大,通过求解复杂的流场方程得到较为详细的三维温度场和流场 |
|                        | 国内仿真计算(未命名) | 柱状流钠火 | 是                            | 同上                                                         |

其中采用集总参数法的程序最 多，该方法求解最为简单，但只能得到整个求解区域的压力、温度等参数的平均值，无 法得到更加细致的分布。双单元模型是将整个计算区域分为燃烧区内部和非燃烧区域两 个大的单元，整个非燃烧区域为一个单元，燃烧区域内根据计算需要沿着一个方向进一 步划分更小的单元，该方法是对集总参数法的一种改进，相对集总参数法可以区分燃烧 区域与非燃烧区域的状态，但无法获得各个区域内更加细致的温度场、速度场等参量变 化情况。采用三维的欧拉-拉格朗日法的仿真计算，需要划分更为细致的计算网格，求 解复杂的控制方程，因此采用该方法的仿真程序均借助于通用的第三方热工水利求解平 台，对气相区域进行网格划分和求解相应的三维控制方程，金属钠流动和燃烧部分根据 相应情况建立恰当的物理模型进行计算，最后进行整合，这种方法可以获得整个计算区 域内三维温度场和流场分布等物理参量分布。 



# 灭火

自带液封装置地自灭火接纳盘，膨胀石墨灭火剂

# 钠火事故

1. 西班牙ALMERIAN钠火事故：1986年8月，发生于西班牙南部ALmeria附近小 型太阳能系统的中央接受系统。事故原因为阀门失效，导致了系统内钠泄露，泄露速度为14kg/s，总计钠泄露量为14t[^6]。火灾过程中形成了喷雾钠火以及池式钠火，对建筑物造成严重破坏，由于屋顶没有不锈钢保护壳，将屋顶烧穿，形成了一个$12m^2$的空洞。不过由于事故为非核设施事故，虽然钠火事故比较严重，但是没有发生放射性物质的泄露，影响不是广泛[^7]。
2. 德国ILONA钠火事故：1992年9月，德国Bensberg的ILONA钠试验装置发生事故，事故由于卸压阀失效引起。钠泄漏速度很小，仅为0.2kg/s，但是由于泄露时间长，泄露总量达4t。由于建筑内部地面没有不锈钢保护壳，大量的金属钠堆积在地面，与混凝土发生反应，形成钠池，钠以池火的形式燃烧持续了14个小时。 
3. 日本文殊核电站钠泄露事故：1995年日本文殊核电站发生二回路钠泄露，泄露量较少，总计泄露640kg。在发现泄露之后，反应堆停止运行，并未造成辐射性影响[^8][^9][^10]。
4. 法国Super Phoenix钠火事故：1987年，法国Super Phoenix反应堆乏燃料储罐发生泄漏，大约$20m^3$金属钠泄漏出来。由于堆容器外部有保护容器，而二者之间充满了惰性气体，因此泄漏的钠并未发生燃烧，没有造成很严重的后果。
5. 迄今为止，全世界范围内总共发生一百余次钠泄露事故，大部分快堆都发生过钠泄漏事故，但幸运的是都没有对堆芯造成严重损坏。



# 思路

设置了与试验面积相同的池火作为火源。这些**池火的热输出是根据 FDS 中的单位面积热释放率（HRRPUA）设定**的。根据这些池火的测量值，通过FDS中的“**RAMP**”命令设置池火的热释放率历史。

**热辐射**：The fraction of energy released from the fire as thermal radiation, usually referred to as the radiative fraction, is by default 0.35 for a LES in FDS. However, in some cases, one may vary this parameter for a specific fuel.

**计算域建立的注意事项**：a sophisticated FDS user should choose to establish the domain of the computation away from the physical exit to avoid this possible error  ;  The width of the domain ensures minimal influence of the open boundary conditions (at the sides) on the air entrainment near the fire. The height of the domain is set to be almost three times the expected flame height to allow a fully developed fire plume by defining an open boundary condition. 

湍流分辨率：

![image-20240507144150169](..\FDS中钠燃烧模型添加.assets\image-20240507144150169.png)

不同湍流模型的对比

用户输入的燃烧速率 可以按照 单位面积的质量损失率(MLRPUA)或单位面积的放热率(HRRPUA)给出，这样设置将会没有燃料燃尽，可以通过设置`RAMP_Q`在指定时间停止燃烧。预估燃尽时间的方法如下：$\Delta H$为燃烧热，材料密度$\rho_s$，材料厚度$\delta_s$，HRRPUA：$\dot{q}_\mathrm{f}^{\prime\prime}$
$$
t_\mathrm{b}=\frac{\rho_\mathrm{s}\delta_\mathrm{s}\Delta H}{\dot{q}_\mathrm{f}^{\prime\prime}}
$$
液体燃料的燃尽时间是根据液体层厚度THICKNESS、液体密度DENSITY和计算出的燃尽速度自动计算出来的。:interrobang:燃烧速率是怎么计算出来的？$\dot{m}^{\prime\prime}\approx\frac{\dot{q}^{\prime\prime}}{h_\mathrm{g}}\quad;\quad h_\mathrm{g}=c(T_\mathrm{b}-T_\infty)+h_\mathrm{v}$这样吗？

FDS设置输入的第一种方法是设置MLRPUA或HRRPUA；第二种选择是通过设置燃料特性并使用**液体热解模型(LPM)**来模拟液体燃料的蒸发。

$\spadesuit$ The inclusion of BOILING_TEMPERATURE on the MATL line tells FDS to use its liquid pyrolysis model.  

FUG：If the species is not known, then you must furnish additional information.   

**固体或液体燃料的热特性决定了它可以燃烧的时间长度**。总的来说， 燃尽时间是质量损失率$\dot m^{”}$、密度$ρ_s$和层厚$δ_s$的函数:
$$
t_\mathrm{b}=\frac{\rho_\mathrm{s}\delta_\mathrm{s}}{\dot{m}^{\prime\prime}}
$$

open-cv用直线逼近任意形状的轮廓。

利用fds2FEM将热边界传递给有限元分析软件。

fluent中dpm模型模拟钠滴燃烧

是否需要设置两步反应，将氧化钠向过氧化钠的转变过程表示出来？（只有当您对近火焰现象感兴趣时，才应该调用两步简单化学选项，其中CO和Soot浓度的增加在火焰化学和辐射发射中起重要作用。）

设置自动点燃温度AUTO_IGNITION_TEMPERATURE on the REAC line

**钠滴场景**

**当钠滴温度低于沸点时，发生表面氧化+蒸发**

**当钠滴温度不低于沸点时，仅发生蒸发+气相燃烧**

![image-20241104111924452](/C:/Users/Li/AppData/Roaming/Typora/typora-user-images/image-20241104111924452.png)

钠池、钠雾的表面反应对蒸发的影响，采用类似的方式，系数取值不同。



# FDS软件使用指南

Fire Dynamics Simulator (FDS)软件是由美国国家标准与技术研究所(NIST)、UL研究所和消防安全研究所共同开发的一款火灾模拟器，主要用于低速流动的LES模拟，第一版于2000年2月发行。FDS软件主要包含了火灾驱动流体流动的计算流体动力学(CFD)模型，在数值上解决了一种形式的Navier-Stokes方程，适用于低速(Ma < 0.3)，热驱动流，重点是来自火灾的烟雾和热量传输过程。此外，FDS软件可以借助现有三维软件的建模和网格处理功能，从而解决较为复杂场景下的三维模拟。

开源包下载：https://github.com/firemodels/fds?tab=readme-ov-file

发行版本：https://github.com/firemodels/fds/releases/tag/FDS-6.8.0

## 发行版本的安装及使用

### 安装

1. 双击下载好的发行版；![image-20240530092819031](..\FDS中钠燃烧模型添加.assets\image-20240530092819031.png)
2. 等待出现如下提示，按需要选择安装路径；![image-20240530092830559](..\FDS中钠燃烧模型添加.assets\image-20240530092830559.png)
3. 显示如下信息，即安装完毕，按任意键退出；![image-20240530092845619](..\FDS中钠燃烧模型添加.assets\image-20240530092845619.png)
4. 在安装路径中即可看到安装好的文件。![image-20240530092857514](..\FDS中钠燃烧模型添加.assets\image-20240530092857514.png)

### 使用

1. 打开文件夹`…\firemodels\FDS6\Examples\Fires`；
2. 复制上述Fires文件夹下任意文件到任意位置（除软件安装路径及其子路径下，因为在计算过程中会产生较多结果文件）；
3. 打开CMDfds命令提示符（若桌面没有，可在电脑中搜索）；

![img](..\FDS中钠燃烧模型添加.assets\clip_image002.jpg)

4. 将路径切换到步骤2中的文件存放路径（如下所示的firemodel_test）；

![img](..\FDS中钠燃烧模型添加.assets\clip_image004.jpg)

5. 运行算例->`fds_local simple_test.fds`（其中local表示在单个电脑运行）；
6. 运行结果如下所示；

![img](..\FDS中钠燃烧模型添加.assets\clip_image006.jpg)

7. 返回步骤2所在路径，在smv文件中查看运行结果（用[安装](#安装)中步骤4安装好的`SMV6\smokeview.exe`打开）；



![img](..\FDS中钠燃烧模型添加.assets\clip_image008.jpg)![img](..\FDS中钠燃烧模型添加.assets\clip_image010.jpg)

8. 初步运行结束。

### MPI环境变量添加

在FDS6\bin目录下还有一个mpi文件夹，其表示并行运算，将其添加到PATH中，可以简化前述操作。可以看到，在前期安装FDS的过程中，已自动将SMV6和FDS6\bin添加到环境变量中。

![img](..\FDS中钠燃烧模型添加.assets\clip_image002-1717033214037-6.jpg)

同样，以[使用](#使用)节中的案例为例，运行`simple_test.fds`，步骤如下：

1. 在`simple_test.fds`所在目录下打开cmd；
2. 运行`fds simple_test.fds`，开始计算；

![img](..\FDS中钠燃烧模型添加.assets\clip_image004-1717033214037-7.jpg)

3. 运行结束。

### FDS结果转Tecplot

大多数时候，需要将FDS的计算结果用云图表示，以便直观地展示，一种常用的方法是将FDS的数据以ascii的形式表示，再转换为tecplot形式。

1. 将[安装](#安装)目录下的`bin`文件中的`fds2ascii.exe`程序拷贝至[使用](#使用)步骤2中的算例文件；
2. 双击运行`fds2ascii.exe`；![image-20240530094349521](..\FDS中钠燃烧模型添加.assets\image-20240530094349521.png)![](..\FDS中钠燃烧模型添加.assets\image-20240530094435733.png)
3. 用记事本打开输出文件，例如xxx，删除红框中的内容，并替换为如下；![image-20240530094527822](..\FDS中钠燃烧模型添加.assets\image-20240530094527822.png)
4. 保存，将xxx文件后缀改为plt，即可用tecplot打开。![image-20240530094555853](..\FDS中钠燃烧模型添加.assets\image-20240530094555853.png)
5. [FDS软件使用记录 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/685636063)

### 网格设置方法

1) 不同输出变量对网格的要求不同；
2) 由粗到细逐步加密网格，直至两次结果变化不大（无关性验证）；
3) 网格大小具体设置方法为：

$$
{{D}^{*}}={{\left( \frac{{\dot{Q}}}{{{\rho }_{\infty }}{{c}_{p}}{{T}_{\infty }}\sqrt{g}} \right)}^{\frac{2}{5}}},\frac{{{D}^{*}}}{{{\delta }_{x}}}\approx 4\sim16(建议取8\sim10)
$$

其中，$\dot{Q}$为热释放速率（MW，kW），${{\rho }_{\infty }}$为空气的密度，${{c}_{p}}$为空气的比热，${{T}_{\infty }}$为周围环境温度，$g$为重力加速度，${{D}^{*}}$为火焰的特征直径，${{\delta }_{x}}$为初始网格大小。

多个网格区域相接触的面程序识别为连通状态。

y轴和z轴网格的数值应为$2^l3^m5^n$，（素数）具体如下[^f1]：

2 3 4 5 6 8 9 10 12 15 16 18 20 24 25 27 30 32 36 40 45 48 50 54 60 64 72 75 80 81 90 96 100 108 120 125 128 135 144 150 160 162 180 192 200 216 225 240 243 250 256 270 288 300 320 324 360 375 384 400 405 432 450 480 486 500 512 540 576 600 625 640 648 675 720 729 750 768 800 810 864 900 960 972 1000 1024

------

[^f1]: 见《火灾FDS数值模拟》，详见老版本FDS Users’ Guide 6.5第6.3节。

### FDS源码

![image-20240530100533497](..\FDS中钠燃烧模型添加.assets\image-20240530100533497.png)

**Van Driest damping** was the default wall model in FDS Version 6。

## 几何

### 非结构几何参数（FUG7.3.2）

定义一个简单的非结构固体几何参数：

```fortran
&GEOM ID='My Solid'
	SURF_ID='FIRE','INERT'
	VERTS= -1.0, -1.0, 1.0, -1.0, -1.0, 0.0,0.0, 1.0, 0.0,0.0, 0.0, 1.0,
	FACES= 1,3,2, 2,
			1,4,3, 1,
			3,4,2, 1,
			2,4,1, 0 /
```

ID指定名称——' My Solid '， VERTS指定每个顶点的坐标(x1,y1,z1;x2,y2,z2，…)， FACES定义每个三角形面-三个顶点的索引和一个边界条件索引:(v1,v2,v3,b)。 顶点索引的范围从1到在vert中列出的顶点数。三个顶点的顺序定义：从几何体外部观察，每个三角形的顶点应该按照右手定则的惯例逆时针排列。

边界条件索引b的取值范围是0 ~ SURF_ID表项个数。b = 0应用默认边界条件。在上面的例子中，第一个面有一个索引b = 2，对应于 ' INERT '，第二个和第三个面有b = 1对应于' FIRE '，第四个面对应于默认值。

### 几何变形（FUG7.3.8）

几何图形可以平移、旋转和缩放。例如，在下面的`GEOM`命名列表中，

```fortran
&MOVE ID='ChairMove', AXIS=...,...,..., ROTATION_ANGLE=..., DX=, /
&GEOM ID='chair'
SURF_ID='woodSID','apholsterySID', VERTS=X1,Y1,Z1,...,XM,YM,ZM, FACES=F1_1,F1_2,F1_3,F1_SID,...,FN_1,FN_2,FN_3,FN_SID MOVE_ID='ChairMove'
/
```

椅子对象使用对MOVE名称列表的引用进行变换和旋转，该列表在`FUG11.4`节中进行了定义和解释。

例如[^f2]：

```fortran
&MOVE ID='spin', ROTATION_ANGLE=45., X0=2., Y0=3., Z0=4., AXIS=1,0,0 /
```

![image-20240530100951462](..\FDS中钠燃烧模型添加.assets\image-20240530100951462.png)![image-20240530100954954](..\FDS中钠燃烧模型添加.assets\image-20240530100954954.png)

------

[^f2]: 旋转的方向存疑——FUG 11.4，经过多次测试验证，应该是顺时针。

**表示使一个物体沿着从（x0,y0,z0）发出的方向向量AXIS旋转45°**。此外，可以相对于(x0;y0;z0)在原始未旋转的轴上缩放对象，方法是定义因子SCALE > 0使其在每个方向缩放，或者定义因子SCALEX, SCALEY, SCALEZ使其在指定方向缩放；同时，可以用参数DX, DY, DZ在三个坐标方向上平移物体，每一个都以米为单位。

欲同时对物体进行旋转、缩放和平移，可以使用变换矩阵，描述坐标为x,y,z的点p的变换方程为：
$$
\begin{Bmatrix}x^{'}\\y^{'}\\z^{'}\end{Bmatrix}=\begin{bmatrix}i_1j_1k_1a_1\\i_2j_2k_2a_2\\i_3j_3k_3a_3\end{bmatrix}\begin{bmatrix}x\\y\\z\\1\end{bmatrix}
$$
在FDS中的命令表示为：

```fortran
&MOVE ID='My Move', T34 = i1,i2,i3, j1,j2,j3, k1,k2,k3, a1,a2,a3 /
```

式中(i1;i2;i3)， (j1;j2;J3)和(k1;k2;k3)为旋转和缩放操作的正交基向量，(a1;a2;a3)为平移向量。注意，如果定义了T34，它优先于所有其他转换参数。

## 进程监测

特定计算的诊断结果会写入一个名为 CHID.out 的文件。当前的模拟时间和时间步长会被写入该文件，以便查看程序的进展情况。默认情况下，在前 100 个时间步之后，每 100 个时间步写出一次诊断。用户可以指定不同的时间间隔：

```fortran
&DUMP DIAGNOSTICS_INTERVAL=100 /
```

计算过程中，Smokeview都可以运行并且查看进程。

默认情况下，CHID.out 文件中的诊断信息是详细的。默认情况下，对于涉及 32 个网格或更少的作业，其值为 F；对于更大的网格，其值为 T。在运行大型 MPI 作业时，将仅由 MPI 进程 0 写入的输出静音可能会有好处。为此，添加：

```fortran
&DUMP SUPPRESS_DIAGNOSTICS=T /
```

请注意，在这种情况下，输出文件不会监测网格边界速度错误；它将只显示模拟时间和时间步长。如有必要，仍可输出 QUANTITY='VELOCITY ERROR' 的 BNDF。

要在预定时间之前停止计算，请在输出文件的同一目录下创建一个名为 CHID.stop 的文件。该文件的存在将优雅地停止程序，使其转储出最新的流量变量，以便在 Smokeview 中查看。

:exclamation:由于计算时间可长达数小时或数天，因此 FDS 具有**重新启动功能**。关于如何使用该功能的详细信息，请参阅第 5.6 节。简而言之，在计算开始时指定保存 "重启 "文件的频率。如果发生停电等中断计算的情况，可以从上次保存重启文件的时间重新开始计算。

还可以使用第 18.5 节所述的控制功能来控制停止时间和重新启动文件的转储时间。

#### Stopping and Restarting Calculations (.restart)

**一个重要的 MISC 参数叫做 "重启"（RESTART）**。通常情况下，模拟由一系列从环境条件开始的事件组成。不过，**有时您可能需要停止计算，进行一些有限的调整，然后从该时间点重新开始计算**。为此，首先要在输出文件所在目录下创建一个名为 CHID.stop 的文件，使计算平稳停止。请记住，FDS 是区分大小写的。文件名必须与 CHID 完全相同，"stop "应为小写。FDS 会在每个时间步检查该文件是否存在，如果发现该文件，则会先创建一个名为 CHID.restart （或 CHID_nn.restart）的文件（如果是多网格作业，则创建多个文件），然后优雅地关闭计算。**要重新启动作业，工作目录中应存在 CHID.restart 文件，输入数据文件的 MISC 行需要添加 RESTART=T 短语**。例如，假设 CHID 为 "plume "的任务停止，方法是在创建所有输出文件的目录下创建一个名为 plume.stop 的虚拟文件。**要从中断处重新启动该作业，您需要删除 CHID.stop 文件，以便 FDS 不会立即停止计算**，并在输入文件 plume.fds 的 **MISC 行添加 RESTART=T**，或者您选择的输入文件名。如果存在与原始作业 CHID 相同的重启文件，FDS 就会继续将新数据保存在与旧数据相同的文件中[^a]。如果在 MISC 行也指定了 RESTART_CHID，则 FDS 将查找使用此字符串标记的旧输出文件，而不是使用 HEAD 行上指定的 CHID。在这种情况下，新的输出文件将使用 CHID 标记，而旧的输出文件不会被更改。运行重启的任务时，重启任务的诊断输出将附加到原始任务的输出文件中。

**有时您可能希望在运行过程中定期保存重启文件，以防断电或系统崩溃**。如果是这种情况，可在原始运行开始时在 **DUMP 行设置 DT_RESTART=50.**，例如每 50 秒保存一次重启文件。DT_RESTART 的默认值是 1000000，这意味着不会创建重启文件，除非通过创建名为 CHID.stop 的虚拟文件来优雅地停止作业。控制功能（见第 18.5 节）可用于在计算达到某些可测量条件（如首次启动喷洒器）时停止计算或转储重启文件。

****

[^a]:默认情况下，重新启动作业时，电子表格输出文件将在作业重新启动时而不是作业停止时添加。:exclamation:如果希望在不剪切任何现有数据的情况下附加输出文件，即使会留下一些重复输出，那么请在 DUMP 行中将 CLIP_RESTART_FILES 设置为 F。

****

:exclamation:在工作停止和重新启动之间，不能对计算进行重大更改，如添加或删除通风口和障碍物。更改仅限于那些不会立即改变现有流场的参数。例如，**更改发送到热释放率（*_hrr.csv）或设备（*_devc.csv）文件的数据输出频率，甚至切片文件输出。**新频率在 DUMP 行中设置（输出频率完整列表见表 23.8）。如果没有在新运行中设置频率，则会保留上一次运行的频率。但 DT_RESTART 并非如此；如果新运行中没有 DT_RESTART，则不会写入重启文件（这可防止覆盖旧的重启文件）。

由于开发人员很少使用重启功能，因此应将其视为一种脆弱的结构。检查输出结果，确保在停止和重启过程中不会发生突然或意外事件。

:exclamation:【繁琐】基本流程：运行->在某一时刻结束运行->工作目录下创建CHID.stop文件->输入卡中输入`&MISC RESTART=T`，并删除工作目录下的CHID.stop文件->重启计算。（一般的操作是，创建两个输入文件，其中一个规定DT_RESTART，另一个用来重启。）<font color=red>**pyrosim可以实现，在设计前后处理器时可以参考。**</font>



## 可用压力求解器概要

![image-20240619105550961](..\FDS中钠燃烧模型添加.assets\image-20240619105550961.png)

*******

1. “Refinement”是指允许改变相邻网格的网格分辨率。
2. “Add/Remove”是指求解器在模拟过程中处理几何体变化的能力，可以通过 CTRL 功能添加或删除 OBST 或 GEOM。
3. “Velocity @ Mesh”是指网格边界（即 FDS 中所谓的 "内插 "边界）处速度法向分量的误差。对于非精确求解器，可以使用参数 VELOCITY_TOLERANCE 控制这一误差。质量守恒误差与速度容差成正比。列为 "精确 "的求解器为全局求解器。"全局 "指的是全局矩阵求解，即整个域只有一个矩阵，而不是每个网格只有一个矩阵。因此，**这种求解器没有网格边界误差**。
4. “Velocity @ Solid”是指固体边界处速度法向分量的误差，即所谓的 "穿透 "误差，这种误差存在于浸没边界法中，并导致质量守恒误差。对于严密密封的压力区，控制这些误差尤为重要。对于非精确求解器，可以使用参数 VELOCITY_TOLERANCE 控制这一误差。质量守恒误差与速度容差成正比。**列为 "精确 "的求解器为非结构化求解器**。"非结构化 "意味着固体边界（如 OBST 边界）被视为压力泊松方程的域边界。非结构求解器与浸没边界法正好相反。
5. “Inseparability”是指与不可分割泊松方程的解法相比，由于压力在气压项中滞后而产生的误差。可以使用参数 PRESSURE_TOLERANCE 来控制这一误差。

****



## 常用命令

```fortran
&VENT XB = 1.0 2.2 0 0 0 2.1		门的坐标
	SURF_ID = 'OPEN'/			定义surface_id
HRRPUA：heat release rate per unit area，单位面积的热释放速率（kw/m2）。
&MESH XB = 0 6 0 4.5 0 2.8
IJK = 60 45 28 /
&TIME T_END = 60/
&VENT XB = 1.0 2.2 0 0 0 2.1	暂以VENT表示门，surf_id为开；vent只能用于mesh形成的边界上（若整个外表面要打开，可采用MB参数），而hole表示在物体上挖洞，只能用于内部物体，不能用于MESH命令形成的外部边界。
	SURF_ID = 'OPEN'/
&OBST XB =  3.0 3.2 0 4.5 0 2.8			表示房间内的障碍物，具有厚度
	COLOR = 'GRAY'/	
&HOLE XB = 3.0 3.2 0.6 1.6 0 1.8/		障碍物上开孔
边界条件
&SURF ID = 'FIRE' HRRPUA = 1000/		定义火焰的id和热释放率
&OBST XB = 4 4.1 3 3.1 1.5 1.6			定义火焰燃烧的位置；SURF_IDS可依次定义顶、侧、底面
	SURF_ID = 'FIRE'
	 RGB = 255 128 0/
&REAC FUEL = 'PROPANE'				定义化学反应，soot_yield为产烟率
	SOOT_YIELD = 0.05/

多个物体（需配合OBST使用）
&MULT ID=’S’ DX=0.3 DZ=0.1 N_UPPER=11/    DX：偏移量；N_UPPER:个数
&OBST XB=1 1.3 1 2 0 0.1 MULT_ID=’S’ RGB=128 0 128/
测点：测点要取在网格内
&DEVC XYZ=4.05 3.5 0.15 QUANTITY='TEMPERATURE' ID= 'T1'/
&DEVC XYZ=4.05 3.05 0.15 QUANTITY='VOLUME FRACTION' SPEC_ID= 'CARBON DIOXIDE' ID= 'CO2'/
TEMPERATURE:温度
VOLUME FRACTION:气体体积份额

切片动画：
&SLCF PBY = 3.05 QUANTITY='TEMPERATURE'/	PBY：垂直于Y轴
等值面动画：
&ISOF QUANTITY = 'TEMPERATURE' VALUE = 45/	VALUE最多可以输出三个值
材料热物性：
&MATL 命令设置热物性系数
```



### Advanced Control Functions: The CTRL Namelist Group



#### Control Function: RESTART and KILL

有时，您可能只想运行一次模拟，直到达到某个目标，或者您可能想创建某个基线条件，然后运行该基线的多种排列组合。例如，您可能想运行一系列模拟，一旦探测器报警，就测试不同的缓解策略。使用重启控制功能，您可以在满足所需条件后创建重启文件。仿真可以继续进行，重启文件可以复制，以便拥有各种排列组合的作业识别字符串 CHID（当然，前提是遵守使用重启文件的常规限制）。一旦满足所需的条件，使用 KILL 控制功能即可停止 FDS。**如果既要写入重启文件，又要停止 FDS，则需要在使用这两个函数时使用相同的 INPUT_ID**。例如：

```fortran
&DEVC ID='temp', QUANTITY='TEMPERATURE', SETPOINT=1000., XYZ=4.5,6.7,3.6 /
&DEVC ID='velo', QUANTITY='VELOCITY', SETPOINT=10., XYZ=4.5,6.7,3.6 /
&CTRL ID='kill', FUNCTION_TYPE='KILL', INPUT_ID='temp' /
&CTRL ID='restart', FUNCTION_TYPE='RESTART', INPUT_ID='velo' /
```

当给定点的温度上升超过 1000 ℃ 时，将终止工作；或者当给定点的速度超过 10 米/秒时，只强制输出重启文件。行：

```fortran
&DEVC ID='temp', QUANTITY='TEMPERATURE', SETPOINT=1000., XYZ=4.5,6.7,3.6 /
&CTRL ID='kill', FUNCTION_TYPE='KILL', INPUT_ID='temp' /
&CTRL ID='restart', FUNCTION_TYPE='RESTART', INPUT_ID='temp' /
```

会在给定点的温度上升到 1000 ℃ 以上时杀死任务，并写入重启文件。

很多系统的功能都无法用一个简单的 "设定点 "设备来描述。例如，一个典型的供热HVAC系统。该系统由一个恒温器控制，恒温器上有一个温度设定点。当温度低于设定值一定程度时，系统开启；当温度高于设定值一定程度时，系统关闭。**这种行为不能仅通过指定一个设定点来定义**。您还必须定义设定点周围的范围或 "死区"，以及温度升高或降低是否会激活系统。在HVAC示例中，越过死区的下边缘会激活加热；越过上边缘则会停用加热。这些更为复杂的行为可通过 CTRL 在 FDS 中建模。以下参数决定了控制功能的行为方式：

`ID`控制函数的名称，在所有控制函数中是唯一的。

`FUNCTION_TYPE`控制功能的类型。可能的类型如表18.2所示。

`INPUT_ID`控制功能输入的 DEVC 或 CTRL ID 列表。最多可指定 40 个输入。如果 DEVC 或 CTRL 被用作控制功能的 INPUT_ID，那么它必须在设备和控制功能中都具有唯一的 ID。此外，控制功能本身不能用作输入。

`SETPOINT`控制函数状态发生变化时的值。这只适用于返回数值的函数。

`TRIP_DIRECTION`:exclamation:正整数表示当控制功能的值上升超过设定点时，控制功能将改变状态；负整数表示当控制功能的值下降超过设定点时，控制功能将改变状态。默认值为 +1。

`LATCH`如果该逻辑值设为 T，则控制功能只改变一次状态。默认为 LATCH=T。

`INITIAL_STATE`控制功能的初始状态。例如，如果与控制功能相关的障碍物要消失，则在 DEVC 行设置 INITIAL_STATE=T。

**对于可以指定 DEVC_ID 的任何对象（如 OBST 或 VENT），可以指定 CTRL_ID 代替**。

:exclamation:如果要设计一个涉及多次状态变化的控制和设备系统，请在相关的 DEVC 或 CTRL 行中加入属性 LATCH=F。默认情况下，设备和控制只能改变一次状态，如自动喷水灭火器启动或烟雾探测器报警。默认情况下，设备和控制器都使用 LATCH=T。

如果希望 DEVC 根据 CTRL 的逻辑状态运行，请设置 QUANTITY='CONTROL'，并将 CTRL_ID 设为控制功能的 ID。

数值控制功能的输出值由 QUANTITY='CONTROL VALUE' 的 DEVC 行定义，CTRL_ID 设置为控制功能的 ID。然后，可以使用 SETPOINT 使 DEVC 操作控制功能的特定输出值。该输出值不能用于纯逻辑控制功能，其唯一输出是 ANY 或 DEADBAND 等逻辑状态。对于 CUSTOM，输出值将是 RAMP 函数的值，而对于 TIME_DELAY，输出值将是已评估的延迟。

控制函数的每个状态变化都记录到日志文件中，参见第27.5节。

![image-20240621101639935](..\FDS中钠燃烧模型添加.assets\image-20240621101639935.png)

#### Control Functions: ANY, ALL, ONLY, and AT_LEAST

假设您希望在房间中的四个烟雾探测器激活后移除障碍物(例如打开一扇门)。使用如下格式的输入行:

```fortran
&OBST XB=..., SURF_ID='...', CTRL_ID='SD' /
&DEVC XYZ=1,1,3, PROP_ID='Acme Smoker', ID='SD_1' /
&DEVC XYZ=1,4,3, PROP_ID='Acme Smoker', ID='SD_2' /
&DEVC XYZ=4,1,3, PROP_ID='Acme Smoker', ID='SD_3' /
&DEVC XYZ=4,4,3, PROP_ID='Acme Smoker', ID='SD_4' /
&CTRL ID='SD', FUNCTION_TYPE='ANY', INPUT_ID='SD_1','SD_2','SD_3','SD_4',
    INITIAL_STATE=T /
```

控制功能 SD 的 INITIAL_STATE 为 T，表示最初存在障碍物。状态改变 "表示当**任一**烟雾探测器报警时，障碍物将被移除。默认情况下，控制功能 SD 的 INITIAL_STATE 为 F，即最初不存在障碍物。

假设您现在希望在房间内的四个烟雾探测器都启动后才创建障碍物（例如，门被关闭）。请使用以下形式的控制线

```fortran
&CTRL ID='SD', FUNCTION_TYPE='ALL', INPUT_ID='SD_1','SD_2','SD_3','SD_4' /
```

控制函数 AT_LEAST 和 ONLY 是 ANY 和 ALL 的概括。例如

```fortran
&CTRL ID='SD', FUNCTION_TYPE='AT_LEAST', N=3, INPUT_ID='SD_1','SD_2','SD_3','SD_4' /
```

当至少有 3 个探测器启动时，状态就会从 F 变为 T。请注意，在本示例和下面的示例中，参数 N 用于指定满足控制功能条件所需的激活设备数量。控制功能:

```fortran
&CTRL ID='SD', FUNCTION_TYPE='ONLY', N=3, INPUT_ID='SD_1','SD_2','SD_3','SD_4' /
```

当 3 个且仅有 3 个探测器启动时，状态会从 F 变为 T。

#### Control Function: TIME_DELAY

当 TIME_DELAY 控制函数的输入状态发生变化时，它将启动一个长度为 DELAY 的定时器。当定时器到期时，TIME_DELAY 控制函数将改变状态。请注意，**每次输入状态发生变化时，定时器都会启动**；因此，如果在第一个定时器结束前输入状态发生第二次变化，定时器将被重置。**通过该功能，FDS 可以模拟设备激活与其他动作发生之间的时间延迟，如干式管道喷淋灭火系统**。

```fortran
&DEVC XYZ=2,2,3, PROP_ID='Acme Sprinkler_link', QUANTITY='LINK TEMPERATURE',
    ID='Spk_29_link' /
&DEVC XYZ=2,2,3, PROP_ID='Acme Sprinkler', QUANTITY='CONTROL', ID='Spk_29',
    CTRL_ID='dry pipe' /
&CTRL ID='dry pipe', FUNCTION_TYPE='TIME_DELAY', INPUT_ID='Spk_29_link', DELAY=30. /
```

自动喷水灭火系统与管道之间的这种关系意味着自动喷水灭火系统的喷水是由 "dry pipe "控制的（在本例中是延迟的），在水从喷头流出之前，Spk_29 的激活时间（由 Spk_29_link 测得）增加了 30 秒。

#### Control Function: DEADBAND

该控制功能的作用类似于HVAC恒温器。它可以在类似于加热或制冷的两种模式下运行。该函数有一个 INPUT_ID（即函数使用的 DEVC 值）、一个上限和下限 SETPOINT 以及 ON_BOUND 指定的运行模式。如果 ON_BOUND="LOWER"，当 INPUT_ID 的值低于 SETPOINT 的下限值时，函数将从初始状态（INITIAL_STATE）开始改变状态；当 INPUT_ID 的值超过 SETPOINT 的上限值时，函数将恢复初始状态，即类似于加热系统。如果 ON_BOUND='UPPER'，则会出现相反的情况，即冷却系统。

对HVAC系统来说，以下几行输入可以设置一个简单的恒温器：

```fortran
&SURF ID='FAN', TMP_FRONT=40., VOLUME_FLOW=-1. /
&VENT XB=-0.3,0.3,-0.3,0.3,0.0,0.0, SURF_ID='FAN', CTRL_ID='thermostat' /
&DEVC ID='TC', XYZ=2.4,5.7,3.6, QUANTITY='TEMPERATURE' /
&CTRL ID='thermostat', FUNCTION_TYPE='DEADBAND', INPUT_ID='TC',
    ON_BOUND='LOWER', SETPOINT=23.,27., LATCH=F/
```

在这里，我们要控制的是模拟FAN的VENT，它将热空气吹入房间。一个名为 TC 的 DEVC 位于房间内，用于测量温度。当温度低于 23 ℃（ON_BOUND='LOWER'）时，恒温器使用 SETPOINT 打开风扇；当温度高于 27 ℃ 时，恒温器关闭风扇。

:exclamation:注意，DEADBAND控制器需要将LATCH设置为F

#### Control Function: CUSTOM

对于大多数控制功能类型，设备和控制功能的逻辑（真/假）输出以及它们上次改变状态的时间都被用作输入。CUSTOM 功能使用 DEVC 的数值输出和 RAMP 来确定功能的输出。当 DEVC 值的 RAMP 输出为负值时，CTRL 将具有其初始状态的值。当 DEVC 值的 RAMP 输出为正值时，CTRL 将具有与其初始状态相反的值。在下面的例子中，CUSTOM 控制函数使用定时器设备的数字输出作为输入。当 RAMP_ID 指定的斜坡中的 F 参数为正值时，函数返回 true（INITIAL_STATE 的默认值为 F）；当 RAMP F 值为负值时，函数返回 false。在这种情况下，控制将从 false 开始，并在计时器计时到 60 秒时切换为 true。

请注意，在使用控制功能时，分配给 CTRL 和 DEVC 输入的 ID 在两组输入中必须是唯一的，也就是说，**不能对控制功能和设备使用相同的 ID**。通过使用基于时间的自定义控制功能，您可以使风扇以固定的周期运行：

```fortran
&SURF ID='FAN', TMP_FRONT=40., VOLUME_FLOW=-1. /
&VENT XB=-0.3,0.3,-0.3,0.3,0.0,0.0, SURF_ID='FAN', CTRL_ID='cycling timer' /
&DEVC ID='TIMER', XYZ=2.4,5.7,3.6, QUANTITY='TIME' /
&CTRL ID='cycling timer', FUNCTION_TYPE='CUSTOM', INPUT_ID='TIMER', RAMP_ID='cycle' /
&RAMP ID='cycle', T= 59, F=-1 /
&RAMP ID='cycle', T= 61, F= 1 /
&RAMP ID='cycle', T=119, F= 1 /
&RAMP ID='cycle', T=121, F=-1 /
```

在上述示例中，风扇最初将处于关闭状态，在 60 秒时打开，然后在 120 秒时关闭。

您可以通过以下几行让障碍物多次出现和消失

```fortran
&OBST XB=..., SURF_ID='whatever', CTRL_ID='cycling timer' /
&DEVC ID='TIMER', XYZ=..., QUANTITY='TIME' /
&CTRL ID='cycling timer', FUNCTION_TYPE='CUSTOM', INPUT_ID='TIMER', RAMP_ID='cycle' /
&RAMP ID='cycle', T= 0, F=-1 /
&RAMP ID='cycle', T= 59, F=-1 /
&RAMP ID='cycle', T= 61, F= 1 /
&RAMP ID='cycle', T=119, F= 1 /
&RAMP ID='cycle', T=121, F=-1 /
```

在上述过程中，最初会移除障碍物，然后在 60 秒时添加障碍物，并在 120 秒时再次移除障碍物。

在尝试一个案例之前，先用一个简单的案例对这些组合进行试验，以确保 FDS 确实达到了预期的效果。

#### Control Function: Math Operations

执行简单数学运算（SUM、SUBTRACT、MULTIPLY、DIVIDE、POWER 等）的控制函数可以指定一个常量值作为其输入之一。具体方法是将其中一个 INPUT_ID 指定为 "CONSTANT"，并使用输入 CONSTANT 提供数值。例如，下面的输入代表一个控制函数，当速度的平方超过 10 时，该函数的状态将发生变化（有关 TRIP_DIRECTION 的解释，请参见第 18.4 节）。

```fortran
&DEVC ID='SPEED SENSOR', XYZ=..., QUANTITY='VELOCITY' /
&CTRL ID='multiplier', FUNCTION_TYPE='POWER',
    INPUT_ID='SPEED SENSOR','CONSTANT', CONSTANT=2., SETPOINT=10.,
    TRIP_DIRECTION=1 /
```

#### Control Function: PID Control Function

PID（比例积分微分）控制功能是一种常用的反馈控制器，用于控制电气和机械系统。该功能计算过程变量与期望设定点之间的误差。PID 功能的目标是将误差最小化。PID 控制函数的计算公式为
$$
u(t)=K_{\mathfrak{p}}e(t)+K_{\mathfrak{i}}\int_0^te(t)\mathrm{d}t+K_{\mathrm{d}}\frac{\mathrm{d}e(t)}{\mathrm{d}t}
$$
其中，Kp、Ki 和 Kd 分别是PROPORTIONAL_GAIN、INTEGRAL_GAIN和DIFFERENTIAL_GAIN；e(t) 是INPUT_ID减去TARGET_VALUE后得到的误差；u(t) 是输出值。

**Example Case: using PID for time integration of mass loss rate**

PID 控制器可用于对热解表面的质量损失进行时间积分。首先，使用 SPATIAL_STATISTIC='SURFACE INTEGRAL' 的 DEVC 作为 PID 控制器的输入。省略 TARGET_VALUE（默认为 0），输入变为误差函数 e(t)。将 INTEGRAL_GAIN 设为 1，其他增益设为 0。下面是语法示例：

```fortran
&DEVC ID='MY MLR', XB=..., QUANTITY='BURNING RATE', SURF_ID='s1',
    SPATIAL_STATISTIC='SURFACE INTEGRAL'/
&CTRL ID='MY PID', FUNCTION_TYPE='PID', INPUT_ID='MY MLR',
    PROPORTIONAL_GAIN=0, DIFFERENTIAL_GAIN=0, INTEGRAL_GAIN=1/
&DEVC ID='PYROLYZATE', XYZ=..., QUANTITY='CONTROL VALUE', CTRL_ID='MY PID'/
```

这里，_devc.csv 文件中 "PYROLYZATE "列的单位是千克。

**Special Case: using PID for controlling momentum**

PID 控制器可用于调节平均动量源项，以实现与动量相关的各种输出目标。一个简单的例子是控制通道中的体积流量。在下文中，我们将监控平均流速，并设置 CONTROL_FORCE(1)=T，为 x 动量方程添加一个源项（y 和 z 分别使用 2 和 3）。其结果类似于手动调节 FORCE_VECTOR(1)，以达到所需的流速。在下面的例子中，PID 控制器将使平均体积流量保持在 10 m/s 的 TARGET_VALUE 值附近。

```fortran
&DEVC ID='Ub', XB=..., QUANTITY='U-VELOCITY', SPATIAL_STATISTIC='MEAN'/
&CTRL ID='MY PID', FUNCTION_TYPE='PID', TARGET_VALUE=10, INPUT_ID='Ub',
    PROPORTIONAL_GAIN=0.1, CONTROL_FORCE(1)=T/
&DEVC ID='FORCE X', XYZ=..., QUANTITY='CONTROL VALUE', CTRL_ID='MY PID'/
```

#### Control Function: PERCENTILE

考虑累积分布函数,$F(x)$
$$
F(x)=\int_{-\infty}^xf(x^{\prime})\mathrm{~d}x^{\prime}/\int_{-\infty}^\infty f(x^{\prime})\mathrm{~d}x^{\prime}
$$
PERCENTILE 控制函数返回 F(x) = p 的 x 值，其中 p 是介于 0 和 1 之间的值。 在离散形式中，函数 f (x) 由 1 ≤ i ≤ N 的成对 (xi, fi) 表示。第 p 个百分位数的计算公式为:
$$
x(p)=\bar{x}_{k-1}+(\bar{x}_k-\bar{x}_{k-1})\frac{pF_N-F_{k-1}}{F_k-F_{k-1}}
$$
其中，
$$
F_k=\sum_{i=1}^kf_i\delta\bar{x}_i\quad;\quad\bar{x}_i=\frac{x_{i+1}+x_i}2\quad;\quad\delta\bar{x}_i=\bar{x}_i-\bar{x}_{i-1}\quad;\quad k=\min_n\left(F_n>pF_N\right)
$$
假设值 $x_i$ 是离散函数的中点；也就是说，$f_i$是函数在区间$(\bar{x}_{i-1}-\bar{x}_i)$上的平均值。
PERCENTILE 函数可用于计算火焰高度。请考虑以下输入行：

```fortran
&DEVC XB=0,0,0,0,0.05,4.95, QUANTITY='HRRPUL', POINTS=50, Z_ID='z', ID='qdot' /
&CTRL ID='pct', FUNCTION_TYPE='PERCENTILE', INPUT_ID='qdot', PERCENTILE=0.95 /
&DEVC ID='L_F', XYZ=0,0,0, QUANTITY='CONTROL VALUE', CTRL_ID='pct', UNITS='m' /
```

第一条 DEVC 线表示 "HRRPUL "或单位长度热释放率（千瓦/米）的垂直剖面。这 50 个数值是对两个水平方向上的单位体积热释放率进行积分后得出的。CTRL 功能在 0.05 米到 4.95 米之间的 50 个均匀分布的高度上提取这 50 个值，并计算出火灾能量释放到 95% 的高度。请注意，对于 10 厘米网格，垂直阵列点位于单元中心，这也是上述离散积分的原因。第二行 DEVC 只是将控制函数计算出的值打印到时间历史文件 CHID_devc.csv。HRRPUL "的 50 个值被时间平均化并写入文件 CHID_line.csv。请注意，写入 CHID_devc.csv 的火焰高度是打印输出之间时间间隔的时间平均值。**如果将 DT_DEVC 设为很小的值（即小于时间步长），则将获得瞬时火焰高度的时间历史记录**。

#### Combining Control Functions: A Deluge System

对于淹没式自动喷水灭火系统，当检测事件发生时，通常干燥的自动喷水灭火管道会被淹没。在本例中，检测事件是四个烟雾探测器中的两个报警。淹没管网需要 30 秒。喷嘴是一个名为 "NOZZLE 1 "的 DEVC，由名为 "nozzle trigger "的 CTRL 控制。当检测和延时都发生时，喷嘴才会启动。请注意，DEVC 是以 QUANTITY='CONTROL' 指定的。

```fortran
&DEVC XYZ=1,1,3, PROP_ID='Acme Smoker', ID='SD_1' /
&DEVC XYZ=1,4,3, PROP_ID='Acme Smoker', ID='SD_2' /
&DEVC XYZ=4,1,3, PROP_ID='Acme Smoker', ID='SD_3' /
&DEVC XYZ=4,4,3, PROP_ID='Acme Smoker', ID='SD_4' /
&DEVC XYZ=2,2,3, PROP_ID='Acme Nozzle', QUANTITY='CONTROL',
    ID='NOZZLE 1', CTRL_ID='nozzle trigger' /
&CTRL ID='nozzle trigger', FUNCTION_TYPE='ALL', INPUT_ID='smokey','delay' /
&CTRL ID='delay', FUNCTION_TYPE='TIME_DELAY', INPUT_ID='smokey', DELAY=30. /
&CTRL ID='smokey', FUNCTION_TYPE='AT_LEAST', N=2,
    INPUT_ID='SD_1','SD_2','SD_3','SD_4' /
```

**Example Case: control_test_2**

control_test_2 示例演示了数学和 PID 控制功能的使用。定义了两个隔间，左侧隔间初始化为 20℃，右侧隔间初始化为 10℃。控制功能定义为

- 将两个隔间的温度相加
- 用左侧隔间温度减去右侧隔间温度
- 左侧温度乘以0.5
- 左侧温度除以右侧温度
- 取右侧温度的平方根
- 将时间作为目标值为 5 的 PID 函数的输入，$Kp=-0.5$，$Ki=0.001$，$Kd=1$

```fortran
&CTRL ID='Add',FUNCTION_TYPE='SUM',INPUT_ID='LHS Temp','RHS Temp'/
&CTRL ID='Subtract',FUNCTION_TYPE='SUBTRACT',INPUT_ID='RHS Temp','LHS Temp'/
&CTRL ID='Multiply',FUNCTION_TYPE='MULTIPLY',INPUT_ID='LHS
    Temp','CONSTANT',CONSTANT=0.5/
&CTRL ID='Divide',FUNCTION_TYPE='DIVIDE',INPUT_ID='LHS Temp','RHS Temp'/
&CTRL ID='Power',FUNCTION_TYPE='POWER',INPUT_ID='RHS Temp','CONSTANT',CONSTANT=0.5/
&CTRL ID='PID',FUNCTION_TYPE='PID',INPUT_ID='Time',TARGET_VALUE=5.,
    PROPORTIONAL_GAIN=-0.5,INTEGRAL_GAIN=0.001,DIFFERENTIAL_GAIN=1./
```

结果如图18.7所示

![image-20240621110242183](..\FDS中钠燃烧模型添加.assets\image-20240621110242183.png)

#### Combining Control Functions: A Dry Pipe Sprinkler System

对于干管水喷淋管道系统，通常是用气体对干燥的水喷淋管道加压。当自动喷水灭火系统中的一个喷头启动时，压降会让水流入管网。在此示例中，一旦喷淋器链接启动，需要 30 秒钟才能使管网进水。运行所需的事件顺序是：首先必须启动ANY链接，从而启动 30 秒的时间延迟（TIME_DELAY）。30 秒延时结束后，每个具有激活链接的喷嘴、ALL控制功能都将开始喷水。

```fortran
&DEVC XYZ=2,2,3, PROP_ID='Acme Sprinkler Link', ID='LINK 1' /
&DEVC XYZ=2,3,3, PROP_ID='Acme Sprinkler Link', ID='LINK 2' /
&PROP ID='Acme Sprinkler Link', QUANTITY='LINK TEMPERATURE',
    ACTIVATION_TEMPERATURE=74., RTI=30./
&DEVC XYZ=2,2,3, PROP_ID='Acme Nozzle', QUANTITY='CONTROL',
    ID='NOZZLE 1', CTRL_ID='nozzle 1 trigger' /
&DEVC XYZ=2,3,3, PROP_ID='Acme Nozzle', QUANTITY='CONTROL',
    ID='NOZZLE 2', CTRL_ID='nozzle 2 trigger' /
&CTRL ID='check links', FUNCTION_TYPE='ANY', INPUT_ID='LINK 1','LINK 2'/
&CTRL ID='delay', FUNCTION_TYPE='TIME_DELAY', INPUT_ID='check links', DELAY=30. /
&CTRL ID='nozzle 1 trigger', FUNCTION_TYPE='ALL', INPUT_ID='delay','LINK 1'/
&CTRL ID='nozzle 2 trigger', FUNCTION_TYPE='ALL', INPUT_ID='delay','LINK 2'/
```

#### Example Case: activate_vents

名为 activate_vents 的简单测试用例演示了几个控制功能。图 18.8 显示了七个不同颜色的通风口，它们会根据特定的定时或控制功能在不同的时间激活。

![image-20240621110601955](..\FDS中钠燃烧模型添加.assets\image-20240621110601955.png)



### DEVC (Device Parameters)

| 可输入参数         | 类型           | 描述                       | 单位 | 默认         |
| ------------------ | -------------- | -------------------------- | ---- | ------------ |
| ABSOLUTE_VALUE     | Logical        | Section 18.2               |      | F            |
| BYPASS_FLOWRATE    | Real           | Section 18.3.7             | kg/s | 0            |
| CELL_L             | Real           | Section 22.16              | m    |              |
| CONVERSION_ADDEND  | Real           | Section 18.2               |      | 0            |
| CONVERSION_FACTOR  | Real           | Section 18.2               |      | 1            |
| COORD_FACTOR       | Real           | Section 22.2.5             |      | 1            |
| CTRL_ID            | Character      | Section 18.6.1             |      |              |
| DB                 | Character      | Section 22.2.3             |      |              |
| DELAY              | Real           | Section 18.3.7             | s    | 0            |
| DEPTH              | Real           | Section 22.10.17           | m    | 0            |
| DEVC_ID            | Character      | Sections 18.3.7 and 18.6.1 |      |              |
| D_ID               | Character      | Section 22.2.5             |      |              |
| DRY                | Logical        | Section 22.10.22           |      | F            |
| DUCT_ID            | Character      | Section 10.2               |      |              |
| DX                 | Real           | Section 22.2.5             | m    | 0            |
| DY                 | Real           | Section 22.2.5             | m    | 0            |
| DZ                 | Real           | Section 22.2.5             | m    | 0            |
| FLOWRATE           | Real           | Section 18.3.7             | kg/s | 0            |
| FORCE_DIRECTION    | Real(3)        | Section 22.10.21           |      |              |
| HIDE_COORDINATES   | Logical        | Section 22.2.5             |      | F            |
| ID                 | Character      | Section 18.1               |      |              |
| INITIAL_STATE      | Logical        | Section 18.4               |      | F            |
| INIT_ID            | Character      | Section 15.4               |      |              |
| IOR                | Integer        | Section 18.1               |      |              |
| LATCH              | Logical        | Section 18.4               |      | T            |
| MATL_ID            | Character      | Section 22.10.17           |      |              |
| MOVE_ID            | Character      | Section 22.2.5             |      |              |
| N_INTERVALS        | Integer        | Section 22.2.4             |      | 10           |
| NODE_ID            | Character(2)   | Section 10.2               |      |              |
| NO_UPDATE_CTRL_ID  | Character      | Section 18.6.3             |      |              |
| NO_UPDATE_DEVC_ID  | Character      | Section 18.6.3             |      |              |
| ORIENTATION        | Real Triplet   | Section 18.1               |      | 0,0,-1       |
| OUTPUT             | Logical        | Section 18.2               |      | T            |
| PART_ID            | Character      | Section 22.15              |      |              |
| PIPE_INDEX         | Integer        | Section 18.3.1             |      | 1            |
| POINTS             | Integer        | Section 22.2.5             |      | 1            |
| POINTS_ARRAY_X     | Real Array     | Section 22.2.5             | m    |              |
| POINTS_ARRAY_Y     | Real Array     | Section 22.2.5             | m    |              |
| POINTS_ARRAY_Z     | Real Array     | Section 22.2.5             | m    |              |
| PROP_ID            | Character      | Section 18.1               |      |              |
| QUANTITY           | Character      | Section 18.1               |      |              |
| QUANTITY2          | Character      | Section 22.2.5             |      |              |
| QUANTITY_RANGE     | Real(2)        | Section 22.2.3             |      | -1.E50,1.E50 |
| REAC_ID            | Character      | Section 22.12              |      |              |
| RELATIVE           | Logical        | Section 18.2               |      | F            |
| R_ID               | Character      | Section 22.2.5             |      |              |
| ROTATION           | Real           | Section 18.1               | deg. | 0            |
| **SETPOINT**       | Real           | Section 18.4               |      |              |
| SMOOTHING_FACTOR   | Real           | Section 18.4               |      | 0            |
| SPATIAL_STATISTIC  | Character      | Section 22.2.3             |      |              |
| SPEC_ID            | Character      | Section 22.12              |      |              |
| STATISTICS_END     | Real           | Section 22.2.4             | s    | T_BEGIN      |
| STATISTICS_START   | Real           | Section 22.2.4             | s    | T_BEGIN      |
| SURF_ID            | Character      | Section 22.2.3             |      |              |
| TEMPORAL_STATISTIC | Character      | Section 22.2.3             |      |              |
| TIME_AVERAGED      | Logical        | Section 18.2               |      |              |
| TIME_HISTORY       | Logical        | Section 22.2.5             |      |              |
| TIME_PERIOD        | Real           | Section 22.2.4             | s    |              |
| TRIP_DIRECTION     | Integer        | Section 18.4               |      | 1            |
| UNITS              | Character      | Section 18.2               |      |              |
| VELO_INDEX         | Integer        | Section 22.10.24           |      | 0            |
| XB(6)              | Real Sextuplet | Section 22.2.3             | m    |              |
| XBP(6)             | Real Sextuplet | Section 22.2.5             | m    |              |
| XYZ(3)             | Real Triplet   | Section 18.1               | m    |              |
| X_ID               | Character      | Section 22.2.5             |      | ID-x         |
| Y_ID               | Character      | Section 22.2.5             |      | ID-y         |
| Z_ID               | Character      | Section 22.2.5             |      | ID-z         |
| XYZ_UNITS          | Character      | Section 22.2.5             |      | ’m’          |

设备可用于控制各种操作，如创建和移除障碍物，**或激活和关闭风扇和通风口**。每个设备都有一个相关的数量（QUANTITY），无论是直接包含在 DEVC 线路中，还是间接包含在可选的 PROP 线路中。使用 DEVC 参数 SETPOINT，可以在 QUANTITY 值超过或低于给定的 SETPOINT 时触发动作。以下参数决定了设备的控制方式：

`SETPOINT`设备状态发生变化时的数值。**对于检测类型的设备（如热或烟雾），该值取自设备的 PROP 输入**，无需在 DEVC 线上指定。

`TRIP_DIRECTION`正整数表示，当设备值大于设定点时，设备将从初始状态（INITIAL_STATE）开始变化，而当设备值小于设定点时，设备将等于初始状态（INITIAL_STATE）。负整数的行为正好相反。当设备值小于 SETPOINT 时，设备将从 INITIAL_STATE 开始变化，而当设备值大于 SETPOINT 时，设备将等于 INITIAL_STATE。默认值为 +1。

`LATCH`如果该逻辑值设置为 T，设备将只改变一次状态。默认值为 T。

`INITIAL_STATE`该逻辑值是设备的初始状态。例如，<font color=red>**如果与设备相关的障碍物要消失，则设置 INITIAL_STATE=T**</font>。

`QUANTITY2`

如果希望使用比单个设备及其设定点更复杂的逻辑来控制 FDS，则可使用 CTRL 输入指定控制功能。有关 CTRL 功能的更多信息，请参见第 18.5 节。最简单的设备示例就是计时器：

```fortran
&DEVC XYZ=1.2,3.4,5.6, ID='my clock', QUANTITY='TIME', SETPOINT=30. /
```

通过参数 DEVC_ID="my clock "与设备相关的任何内容都将在 30 秒后改变其状态。例如，如果将文本添加到 OBST 行，30 秒后该障碍物的初始状态将从 F 变为 T。**这就是打开一扇门或一扇窗的简单方法**。

使用 DEVC 输出控制 FDS 时，使用 DEVC 的瞬时值。对于某些类型QUANTITY（如TEMPERATURE），该输出可能会产生很大的噪声。为防止虚假尖峰导致 DEVC 状态改变，**可以指定参数 SMOOTHING_FACTOR。它对 DEVC 输出进行指数平滑处理**，具体如下：
$$
\bar{x}^n=\bar{x}^{n-1}\text{ SMOOTHING{\_}FACTOR}+x^n\mathrm{~(1-SMOOTHING{\_}FACTOR)}
$$
其中，n 为时间步长，x 为瞬时设备输出，$\bar x$为平滑输出。SMOOTHING_FACTOR 的默认值为 0，表示不执行平滑处理。:question:请注意，SMOOTHING_FACTOR 只改变传递给控制函数的值，对写入 CHID_devc.csv 文件的 DEVC 值没有影响。

设备的每次状态变化都会记录到日志文件中，参见第 27.5 节。

#### Creating and Removing Obstructions

:exclamation:在许多火灾现场，打开或关闭一扇门或一扇窗都会导致火势的急剧变化。有时这些动作是有意为之，有时则是火灾的结果。在火灾数据系统的计算框架内，这些动作表现为设置或移除固体障碍物，或打开或关闭外部通风口。

通过指定字符串 DEVC_ID（DEVC_ID 表示 OBST 行中要创建或移除的 DEVC ID 名称）来移除或创建实体障碍物。这将指示 FDS 在设备状态变为 F 或 T 时分别删除或创建障碍物。例如：

```fortran
&OBST XB=..., DEVC_ID='det2' /
&DEVC XYZ=..., ID='det2', INITIAL_STATE=T /
```

会在指定的 DEVC 改变状态时移除给定的障碍物。

使用以时间为测量量的 DEVC，可以在预定时间创建或移除障碍物。例如，以下指令将使指定的孔洞（HOLE）和障碍物（OBSTructions）在不同的指定时间出现/消失。这几行是名为 create_remove.fds 的简单测试用例的一部分

```fortran
&OBST XB=0.3,0.4,0.1,0.9,0.1,0.9, COLOR='PURPLE' /
&HOLE XB=0.2,0.4,0.2,0.3,0.2,0.3, COLOR='RED', DEVC_ID='timer1' /
&HOLE XB=0.2,0.4,0.7,0.8,0.7,0.8, COLOR='GREEN', DEVC_ID='timer2' /
&OBST XB=0.7,0.8,0.2,0.3,0.2,0.3, COLOR='BLUE', DEVC_ID='timer3' /
&OBST XB=0.7,0.8,0.6,0.7,0.6,0.7, COLOR='PINK', DEVC_ID='timer4' /
&OBST XB=0.5,1.0,0.0,1.0,0.0,0.1, COLOR='YELLOW', DEVC_ID='timer5' /
&HOLE XB=0.7,0.8,0.7,0.8,0.0,0.1, COLOR='BLACK', DEVC_ID='timer6' /
&HOLE XB=0.7,0.8,0.2,0.3,0.0,0.1, COLOR='GRAY 50', DEVC_ID='timer7' /

&DEVC XYZ=..., ID='timer1', SETPOINT=1., QUANTITY='TIME', INITIAL_STATE=F /
&DEVC XYZ=..., ID='timer2', SETPOINT=2., QUANTITY='TIME', INITIAL_STATE=T /
&DEVC XYZ=..., ID='timer3', SETPOINT=3., QUANTITY='TIME', INITIAL_STATE=F /
&DEVC XYZ=..., ID='timer4', SETPOINT=4., QUANTITY='TIME', INITIAL_STATE=T /
&DEVC XYZ=..., ID='timer5', SETPOINT=5., QUANTITY='TIME', INITIAL_STATE=F /
&DEVC XYZ=..., ID='timer6', SETPOINT=6., QUANTITY='TIME', INITIAL_STATE=T /
&DEVC XYZ=..., ID='timer7', SETPOINT=6., QUANTITY='TIME', INITIAL_STATE=F /
```

模拟开始时，紫色的障碍物上嵌有一个红色块。这个红色块实际上是一个洞，其初始状态为 F，即洞已被填满。同样在模拟开始时，可以看到一个粉红色的障碍物。1 秒后，红块消失。2 秒后，紫色障碍物上的空洞被绿色块填满。这个孔最初是真实的，即是空的。蓝色障碍物在 3 秒时出现，因为它的初始状态是假的，也就是说它最初并不存在。粉色障碍物在 4 秒时消失，因为它的初始状态为 "真"，而这一状态在 4 秒时发生了变化。6 秒时，灰色块消失，因为它是一个最初为假的洞，因此在其父障碍物（黄色）创建时被灰色块填满。同样，在 6 秒时，黄色障碍物中原本存在的孔被黑色块填满，因为它是一个最初为空的孔，在其 DEVC 状态改变后被填满。在对障碍物和孔洞进行复杂的创建/删除方案之前，您应该先尝试一个简单的示例。

要多次创建和移除障碍物，可以将 LATCH=F 设置为循环数学函数（见第 18.5.1 节），如下图所示，或者使用 "自定义 "控制功能（见第 18.5.5 节）。下面使用时间作为 SIN 数学函数的输入。DEVC 值的符号会切换 OBST 的状态。

```fortran
&DEVC ID='t1', XYZ=..., QUANTITY='TIME', TIME_AVERAGED=F/
&CTRL ID='s1', FUNCTION_TYPE='SIN', INPUT_ID='t1'/
&DEVC ID='timer', XYZ=..., QUANTITY='CONTROL VALUE', CTRL_ID='s1', SETPOINT=0,
LATCH=F/
&OBST XB=..., DEVC_ID='timer'/
```

#### Activating and Deactivating Vents

当设备或控制功能应用于VENT时，其目的是通过 DEVC_ID 激活或停用与VENT相关联的任何时间斜坡。例如，要控制风扇，请执行以下操作：

```fortran
&SURF ID='FAN', VOLUME_FLOW=5. /
&VENT XB=..., SURF_ID='FAN', DEVC_ID='det2' /
&DEVC ID='det2', XYZ=..., QUANTITY='TIME', SETPOINT=30., INITIAL_STATE=F /
```

请注意，在 30 秒时，"FAN "的 "状态 "从 F 变为 T，或者更简单地说，"FAN "开启。由于没有与 "FAN "相关联的明确时间函数，默认的 1 秒斜坡上升将从 30 秒开始，而不是从 0 秒开始。如果 INITIAL_STATE=T，则风扇应在 30 秒后关闭。从本质上讲，"激活 "VENT会导致所有相关的时间功能延迟，直到达到设备SETPOINT。**VENT的 "停用 "会关闭所有时间功能。这通常意味着 SURF 线路上的参数全部失效，因此最好通过一个简单的示例来检查其功能**。

MIRROR "或 "OPEN "VENT不应被激活或关闭。<font color=red>不过，您可以在 "OPEN "VENT前放置障碍物，然后创建或移除障碍物，以模拟门窗的关闭或打开</font>。

在某些情况下，您可能需要创建或移除附有VENT的障碍物。如果这些障碍物重叠在一起，就可能会混淆哪个VENT与哪个 OBST 相连。如果遇到这种情况，请给 OBST 一个 ID，并将此 OBST_ID 分配到通风口线路上。

#### Device Output: The DEVC Namelist Group

每个设备(DEVC)记录一个特定的数量。通常这个QUANTITY会被写入一个带有`_dev .csv`后缀的电子表格文件中。<font color=red>QUANTITY列于表22.4至22.8。</font>

表 22.4 列出了气相输出量，共分几页。文件类型 "一栏内列出了允许的量输出文件： D "表示设备 (DEVC)，"I "表示等表面 (ISOF)，"P "表示 Plot3D，"S "表示切片 (SLCF)。

对于需要通过 SPEC_ID 提供物种名称的输出量，使用简单化学燃烧模型时隐含定义的物种为 "OXYGEN"、"NITROGEN"、"WATER VAPOR "和 "CARBON DIOXIDE"。如果在 REAC 行中指定了 CO_YIELD、SOOT_YIELD 和/或 HCN_YIELD，则 "CARBON MONOXIDE"、"SOOT "和/或 "HYDROGEN CYANIDE"将作为输出物质。燃料种类可通过 REAC 行中指定的 FUEL 输出。举例说明如何使用物种名称，假设您要计算一氧化碳通过水平面的综合质量通量，如火灾羽流中夹带的总量。使用 "设备 "如下

```fortran
&DEVC ID='CO_flow', XB=-5,5,-5,5,2,2, QUANTITY='MASS FLUX Z',
    SPEC_ID='CARBON MONOXIDE', SPATIAL_STATISTIC='AREA INTEGRAL' /
```

ID 只是输出文件中的一个标签。当输出量与特定气体种类或粒子类型相关时，必须在同一输入行中指定相应的 SPEC_ID 或 PART_ID。所有输出量名称都应使用单引号。

<center>Table 22.4: Gas phase output quantities.</center>

| QUANTITY                        | Explanation                                                  | Units                                    | File Type |
| ------------------------------- | ------------------------------------------------------------ | ---------------------------------------- | --------- |
| ABSOLUTE PRESSURE               | Absolute pressure,$p=\overline{p}+\tilde{p}$                 | Pa                                       | D,I,P,S   |
| ABSORPTION COEFFICIENT          | Section 14.3                                                 | 1/m                                      | D,I,P,S   |
| ADVECTIVE MASS FLUX X[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| ADVECTIVE MASS FLUX Y[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| ADVECTIVE MASS FLUX Z[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| AEROSOL VOLUME FRACTION[^224-1] | Section 22.10.23                                             | mol/mol                                  | D,I,P,S   |
| BACKGROUND PRESSURE             | Background pressure,$\overline{p}$                           | Pa                                       | D,I,P,S   |
| CELL REYNOLDS NUMBER            | Section 22.10.28                                             |                                          | D,I,P,S   |
| CELL U                          | $(u_{i,j,k}+u_{i-1,j,k})/2$                                  | m/s                                      | D,I,P,S   |
| CELL V                          | $(\nu_{i,j,k}+\nu_{i,j-1,k})/2$                              | m/s                                      | D,I,P,S   |
| CELL W                          | $(w_{i,j,k}+w_{i,j,k-1})/2$                                  | m/s                                      | D,I,P,S   |
| CFL                             | Section 22.10.26                                             |                                          | D,I,P,S   |
| CFL MAX                         | Section 22.10.26                                             |                                          | D         |
| CHEMISTRY SUBITERATIONS         | Section 13.3.5                                               |                                          | D,S       |
| CHI_R                           | Section 14.1                                                 |                                          | D,I,S     |
| COMBUSTION EFFICIENCY           | $\delta t/\tau_{\mathrm{mix}}$                               |                                          | D,I,P,S   |
| CONDUCTIVITY                    | Thermal conductivity                                         | W/(mK)                                   | D,I,P,S   |
| C_SMAG                          | Smagorinsky coefficient                                      |                                          | D,I,P,S   |
| DENSITY[^224-1]                 | Total or species density                                     | $kg/m^3$                                 | D,I,P,S   |
| DIFFUSIVE MASS FLUX X[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| DIFFUSIVE MASS FLUX Y[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| DIFFUSIVE MASS FLUX Z[^224-1]   | Section 22.10.10                                             | $\mathrm{kg/s/m^{2}}$                    | D,I,P,S   |
| DIFFUSIVITY[^224-1]             | Section 12.1.3                                               | $\mathrm{m^{2}/s}$                       | D,I,P,S   |
| DISSIPATION RATE                | $\mu/\rho\times\text{ STRAIN RATE}$                          | $\mathrm{m}^{2}/\mathrm{s}^{3}$          | D,I,P,S   |
| DIVERGENCE                      | $\nabla\cdot\mathbf{u}$                                      | 1/s                                      | D,I,P,S   |
| EFFECTIVE FLAME TEMPERATURE     | Section 22.10.15                                             | ℃                                        | D,I,P,S   |
| ENTHALPY                        | Section 12.1.3                                               | $\mathrm{kJ/m^{3}}$                      |           |
| ENTHALPY FLUX X                 | Section 22.10.11                                             | $\mathrm{kW/m^{2}}$                      | D,I,P,S   |
| ENTHALPY FLUX Y                 | Section 22.10.11                                             | $\mathrm{kW/m^{2}}$                      | D,I,P,S   |
| ENTHALPY FLUX Z                 | Section 22.10.11                                             | $\mathrm{kW/m^{2}}$                      | D,I,P,S   |
| EXTINCTION                      | Section 22.10.29                                             |                                          | D,S       |
| EXTINCTION COEFFICIENT          | Section 22.10.5                                              | 1/m                                      | D,I,P,S   |
| F_X, F_Y, F_Z                   | Momentum terms,$F_x,F_y,F_z$                                 | $\mathrm{m/s}^{2}$                       | D,I,P,S   |
| H                               | ${H=|\mathbf{u}|^{2}/2+\tilde{p}/\rho}$                      | $(\mathrm{m/s})^{2}$                     | D,I,P,S   |
| HRRPUL                          | $\int\dot{q}^{\prime\prime\prime}\mathrm{d}x\mathrm{d}y$     | kW/m                                     | D         |
| HRRPUV                          | $\dot{q}^{\prime\prime\prime}$                               | $\mathrm{kW/m^{3}}$                      | D,I,P,S   |
| HRRPUV REAC[^224-6]             | $\dot{q}^{\prime\prime\prime}$for REAC_ID                    | $\mathrm{kW/m^{3}}$                      | D,S       |
| IDEAL GAS PRESSURE              | $\bar{p}=\rho RT/\overline{W}$                               | $Pa$                                     | D,I,P,S   |
| INTEGRATED INTENSITY            | $U=\int I\mathrm{ds}$                                        | $\mathrm{kW/m^{2}}$                      | D,I,P,S   |
| INTERNAL ENERGY                 | $\rho h-\bar{p}$                                             | $\mathrm{kJ/m^{3}}$                      | D,I,P,S   |
| KINETIC ENERGY                  | Staggered$(u^{2}+v^{2}+w^{2})/2$                             | $(\mathrm{m/s})^{2}$                     | D,I,P,S   |
| KOLMOGOROV LENGTH SCALE         | Section 22.10.28                                             | m                                        | D,I,P,S   |
| MACH NUMBER                     | ${|\mathbf{u}|/\sqrt{(R/\overline{W})T\gamma}}$              |                                          | S,D       |
| MASS FLUX X[^224-1]             | Section 22.10.10                                             | $\mathrm{kg}/(\mathrm{m}^{2}\mathrm{s})$ | D,I,P,S   |
| MASS FLUX Y[^224-1]             | Section 22.10.10                                             | $\mathrm{kg}/(\mathrm{m}^{2}\mathrm{s})$ | D,I,P,S   |
| MASS FLUX Z[^224-1]             | Section 22.10.10                                             | $\mathrm{kg}/(\mathrm{m}^{2}\mathrm{s})$ | D,I,P,S   |
| MASS FRACTION[^224-1]           | $Y_{\alpha}$                                                 | $kg/kg$                                  | D,I,P,S   |
| MAXIMUM VELOCITY ERROR          | Section 21                                                   | m/s                                      | D         |
| MIXING TIME                     | Combustion mixing time,$\tau_{\mathrm{mix}}$                 | s                                        | D,I,P,S   |
| MIXTURE FRACTION                | $Z$                                                          | $kg/kg$                                  | D,I,P,S   |
| MOLECULAR VISCOSITY             | Molecular viscosity,$(u,v,w)\cdot(n_x,n_y,n_z)$              | $\mathrm{kg/(ms)}$                       | D,I,P,S   |
| OPTICAL DENSITY                 | Section 22.10.5                                              | 1/m                                      | D,I,P,S   |
| ORIENTED VELOCITY[^224-5]       | $(u,v,w) \cdot(n_x,n_y,n_z)$                                 | m/s                                      | D         |
| PRESSURE                        | Perturbation pressure,$\tilde{p}$                            | Pa                                       | D,I,P,S   |
| PRESSURE ITERATIONS             | Number of pressure iterations                                |                                          | D         |
| PRESSURE ZONE                   | Section 10.3                                                 |                                          | D,S       |
| Q CRITERION                     | $\frac{1}{2}[\mathrm{trace}(\nabla\mathbf{u})^{2}-\mathrm{trace}((\nabla\mathbf{u})^{2})]$ | $1/\mathrm{s}^{2}$                       | D,I,P,S   |
| RADIAL VELOCITY                 | $(u,v)\cdot(x,y)/\sqrt{x^{2}+y^{2}}$                         | m/s                                      | D,I,P,S   |
| RADIATION LOSS                  | $\nabla\cdot\mathbf{q}_r^{\prime\prime}$                     | $\mathrm{kW/m^{3}}$                      | D,I,P,S   |
| RADIATIVE HEAT FLUX GAS         | Section 22.10.12                                             | $\mathrm{kW/m^{2}}$                      | D         |
| REAC SOURCE TERM[^224-1]        | $\dot{m}_\alpha^{\prime\prime\prime}$                        | $kg/m^{3}$                               | D,I,P,S   |
| RELATIVE HUMIDITY               | Section 13.1.1                                               | %                                        | D,I,P,S   |
| RESOLVED KINETIC ENERGY         | $k_{res}=(\bar{u}^{2}+\bar{v}^{2}+\bar{w}^{2})/2$            | $(\mathrm{m/s})^{2}$                     | D,I,P,S   |
| RTE SOURCE CORRECTION FACTOR    | Section 14.1.3                                               |                                          | D         |
| SENSIBLE ENTHALPY               | Section 22.10.25                                             | $kJ/m^3$                                 | D,I,P,S   |
| SPECIFIC ENTHALPY               | Section 22.10.25                                             | $\text{kJ/kg}$                           | D,I,P,S   |
| SPECIFIC HEAT                   | $c_{p}$                                                      | ${\mathrm{kJ}/(\mathrm{kgK})}$           | D,I,P,S   |
| SPECIFIC INTERNAL ENERGY        | $h-\bar{p}/\rho $                                            | $\text{kJ/kg}$                           | D,I,P,S   |
| SPECIFIC SENSIBLE ENTHALPY      | Section 22.10.25                                             | $\text{kJ/kg}$                           | D,I,P,S   |
| STRAIN RATE                     | $2(S_{ij}S_{ij}-1/3(\nabla\cdot\mathbf{u})^{2})$             | 1/s                                      | D,I,P,S   |
| STRAIN RATE X                   | $\partial w/\partial y+\partial\nu/\partial z$               | 1/s                                      | D,I,P,S   |
| STRAIN RATE Y                   | $\partial u/\partial z+\partial w/\partial x$                | 1/s                                      | D,I,P,S   |
| STRAIN RATE Z                   | $\partial\nu/\partial x+\partial u/\partial y$               | 1/s                                      | D,I,P,S   |
| SUBGRID KINETIC ENERGY          | Section 22.10.28                                             | $\mathrm{m^{2}/s^{2}}$                   | D,S       |
| SUM LUMPED MASS FRACTIONS       | $\sum_{i}Z_{i}$(should be 1)                                 |                                          | D,S       |
| SUM PRIMITIVE MASS FRACTIONS    | $\sum_\alpha Y_\alpha $(should be 1)                         |                                          | D,S       |
| TEMPERATURE                     | Section 22.10.8                                              | ℃                                        | D,I,P,S   |
| TOTAL MASS FLUX X[^224-1]       | Section 22.10.10 kg/                                         | $kg/s/m^{2}$                             | D,I,P,S   |
| TOTAL MASS FLUX Y[^224-1]       | Section 22.10.10 kg/                                         | $kg/s/m^{2}$                             | D,I,P,S   |
| TOTAL MASS FLUX Z[^224-1]       | Section 22.10.10 kg/                                         | $kg/s/m^{2}$                             | D,I,P,S   |
| U-VELOCITY                      | Gas velocity component,$u$                                   | m/s                                      | D,I,P,S   |
| V-VELOCITY                      | Gas velocity component,$v$                                   | m/s                                      | D,I,P,S   |
| W-VELOCITY                      | Gas velocity component,$w$                                   | m/s                                      | D,I,P,S   |
| VELOCITY[^224-3]                | Gas velocity                                                 | m/s                                      | D,I,P,S   |
| VISCOSITY                       | Effective viscosity,$\mu+\mu_{\mathrm{t}}$                   | ${\mathrm{kg/(ms)}}$                     | D,I,P,S   |
| VISIBILITY                      | Section 22.10.5                                              | m                                        | D,I,P,S   |
| VN                              | Section 22.10.26                                             |                                          | D,I,P,S   |
| VN MAX                          | Section 22.10.26                                             |                                          | D         |
| VORTICITY X                     | $\partial w/\partial y-\partial\nu/\partial z$               | 1/s                                      | D,I,P,S   |
| VORTICITY Y                     | $\partial u/\partial z-\partial w/\partial x$                | 1/s                                      | D,I,P,S   |
| VORTICITY Z                     | $\partial\nu/\partial x-\partial u/\partial y$               | 1/s                                      | D,I,P,S   |
| VOLUME FRACTION[^224-1]         | $X_\alpha$                                                   | mol/mol                                  | D,I,P,S   |
| WAVELET ERROR                   | Section 22.10.28                                             |                                          | S         |

****

[^224-1]:需要使用SPEC_ID指定气体种类。忽略SPEC_ID的总通量。不要用于MIXTURE FRACTION。
[^224-2]:需要使用PART_ID指定粒子名称。
[^224-3]:如果您希望将速度乘以u的符号，则将VELO_INDEX=1添加到输入行。分别用指标2和3表示v和w。
[^224-4]:允许可选的MATL_ID。
[^224-5]:在DEVC线上需要一个ORIENTATION。
[^224-6]:需要REAC_ID。

****



下表 22.5 列出了固相输出量。表中引用了适当的章节。数学符号的定义见《FDS 技术参考指南》第 1 卷。文件类型 "B "指边界文件，"D "指设备文件 CHID_devc.csv，"pr "指剖面文件 CHID_prof.csv。

<center>Table 22.5: Solid phase output quantities.</center>

| QUANTITY                          | Explanation                           | Units                                   | File Type |
| --------------------------------- | ------------------------------------- | --------------------------------------- | --------- |
| ADIABATIC SURFACE TEMPERATURE     | Section 22.10.13                      | ℃                                       | B,D       |
| AMPUA[^225-2]                     | Section 22.9.1                        | $\mathrm{kg/m^2}$                       | B,D       |
| AMPUA_Z[^225-1]                   | Section 22.9.1                        | $\mathrm{kg/m^2}$                       | B,D       |
| BACK WALL TEMPERATURE             | Section 22.2.2                        | ℃                                       | B,D       |
| BURNING RATE                      | Mass loss rate of fuel                | $\mathrm{kg/(m^{2}s)}$                  | B,D       |
| CONDENSATION HEAT FLUX            | Section 13.7                          | $\mathrm{kW/m^{2}}$                     | B,D       |
| CONVECTIVE HEAT FLUX              | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| CONVECTIVE HEAT FLUX GAUGE        | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| CONVECTIVE HEAT TRANSFER REGIME   | Section 8.2.2                         |                                         | B,D       |
| CPUA[^225-2]                      | Section 22.9.1                        | $\mathrm{kW/m^{2}}$                     | B,D       |
| CPUA_Z[^225-1]                    | Section 22.9.1                        | $\mathrm{kW/m^{2}}$                     | B,D       |
| DEPOSITION VELOCITY               | Section 13.4                          | m/s                                     | B,D       |
| FRICTION VELOCITY                 | Section 22.10.28                      | m/s                                     | B,D       |
| GAUGE HEAT FLUX                   | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| ENTHALPY FLUX WALL                | Section 22.10.11                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| TOTAL HEAT FLUX                   | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| EMISSIVITY                        | Surface emissivity (usually constant) |                                         | B,D       |
| GAS DENSITY                       | Gas Density near wall                 | $\mathrm{kg/m^{3}}$                     | B,D       |
| GAS TEMPERATURE                   | Gas Temperature near wall             | ℃                                       | B,D       |
| HEAT TRANSFER COEFFICIENT         | Section 8.2.2                         | $\mathrm{W}/(\mathrm{m}^{2}\mathrm{K})$ | B,D       |
| HRRPUA                            | $\dot{q}^{\prime\prime}$              | $\mathrm{kW/m^{2}}$                     | B,D       |
| INCIDENT HEAT FLUX                | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| INSIDE WALL TEMPERATURE           | Section 22.2.2                        | ℃                                       | D,Pr      |
| INSIDE WALL DEPTH                 | Section 22.2.2                        | m                                       | D,Pr      |
| MASS FLUX[^225-1][^225-4]         | Section 22.10.10                      | $\mathrm{kg/(m^{2}s)}$                  | B,D       |
| MASS FLUX WALL[^225-1]            | Section 22.10.10                      | $\mathrm{kg/(m^{2}s)}$                  | B,D       |
| MPUA[^225-2]                      | Section 22.9.1                        | $kg/m^{2}$                              | B,D       |
| MPUA_Z[^225-1]                    | Section 22.9.1                        | $kg/m^{2}$                              | B,D       |
| NORMAL VELOCITY                   | Wall normal velocity                  | m/s                                     | B,D       |
| NORMALIZED HEATING RATE           | Section 22.10.17                      | W/g                                     | D         |
| NORMALIZED HEAT RELEASE RATE      | Section 22.10.17                      | W/g                                     | D         |
| NORMALIZED MASS[^225-4]           | Section 22.10.17                      |                                         | D         |
| NORMALIZED MASS LOSS RATE[^225-4] | Section 22.10.21                      | 1/s                                     | D         |
| PRESSURE COEFFICIENT              | Section 22.10.12                      |                                         | B,D       |
| RADIATIVE HEAT FLUX               | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| RADIOMETER                        | Section 22.10.12                      | $\mathrm{kW/m^{2}}$                     | B,D       |
| REFERENCE_HEAT_FLUX               | Section 9.1.4                         | $\mathrm{kW/m^{2}}$                     | B,D       |
| SOLID CONDUCTIVITY[^225-4]        | Section 22.2.2                        | $\mathrm{W}/(\mathrm{m}\mathrm{K})$     | D,Pr      |
| SOLID DENSITY[^225-4]             | Section 22.2.2                        | $kg/m^{3}$                              | D,Pr      |
| SOLID ENTHALPY[^225-4]            | Section 22.2.2                        | $\mathrm{kJ/m^{3}}$                     | D,Pr      |
| SOLID MASS FRACTION[^225-5]       | Section 22.2.2                        | kg/kg                                   | D,Pr      |
| SOLID SPECIFIC HEAT[^225-4]       | Section 22.2.2                        | $\mathrm{kJ}/(\mathrm{kg}\mathrm{K})$   | D,Pr      |
| SUBSTEPS                          | Section 8.3.8                         |                                         | B,D       |
| SURFACE DENSITY[^225-4]           | Section 22.10.17                      | $kg/m^{2}$                              | B,D       |
| SURFACE DEPOSITION[^225-1]        | Section 13.4                          | $kg/m^{2}$                              | B,D       |
| TOTAL MASS FLUX WALL[^225-1]      | Section 22.10.10                      | $kg/s/m^{2}$                            | B,D       |
| VELOCITY ERROR                    | Section 21                            | m/s                                     | B,D       |
| VISCOUS STRESS WALL               | Section 22.10.21                      | Pa                                      | B,D       |
| VISCOUS WALL UNITS                | Section 22.10.28                      |                                         | B,D       |
| WALL ENTHALPY                     | $\int\rho_{s}c_{s}T\mathrm{d}V_{s}$   | kJ                                      | B,D       |
| WALL PRESSURE                     | Section 22.10.21                      | Pa                                      | B,D       |
| WALL TEMPERATURE                  | Surface temperature                   | ℃                                       | B,D       |
| WALL THICKNESS                    | Section 22.10.17                      | m                                       | B,D       |
| WALL VISCOSITY                    | Near-wall viscosity,$\mu_{w}$         | $\mathrm{kg}/(\mathrm{ms})$             | B,D       |

****

[^225-1]:需要使用SPEC_ID指定气体种类。
[^225-2]:需要使用PART_ID指定粒子名称。
[^225-3]:需要使用QUANTITY2指定一个额外的标量
[^225-4]:允许可选的MATL_ID。
[^225-5]:需要一个MATL_ID。

****



下表 22.6 列出了与设备和控制相关的输出量以及其他杂项输出量。文件类型 "D "指的是设备输出文件 CHID_devc.csv。文件类型 "S "指轮廓或 "切片 "文件。

<center>Table 22.6: Output quantities for devices, controls, and miscellaneous functions.</center>

| QUANTITY                   | Explanation                        | Units | File Type |
| -------------------------- | ---------------------------------- | ----- | --------- |
| ACTUATED SPRINKLERS        | Section 22.10.26                   |       | D         |
| ASPIRATION                 | Section 18.3.7                     | %/m   | D         |
| CHAMBER OBSCURATION        | Section 18.3.5                     | %/m   | D         |
| CELL INDEX I               | Mesh cell index in x               |       | D,S       |
| CELL INDEX J               | Mesh cell index in y               |       | D,S       |
| CELL INDEX K               | Mesh cell index in z               |       | D,S       |
| CONTROL                    | Section 18.5                       |       | D         |
| CONTROL VALUE              | Section 18.5                       |       | D         |
| CPU TIME                   | Section 22.10.26                   | s     | D         |
| FED                        | Section 22.10.18                   |       | D         |
| FIC                        | Section 22.10.18                   |       | D,S       |
| FIRE DEPTH                 | Section 18.3.8                     | m     | D         |
| ITERATION                  | Section 22.10.26                   |       | D         |
| LAYER HEIGHT               | Section 22.10.7                    | m     | D         |
| LINK TEMPERATURE           | Section 18.3.4                     | ℃     | D         |
| LOWER TEMPERATURE          | Section 22.10.7                    | ℃     | D         |
| NUMBER OF PARTICLES        | Section 22.10.26                   |       | D         |
| OPEN NOZZLES               | Section 22.10.26                   |       | D         |
| PATH OBSCURATION           | Section 18.3.6                     | %     | D         |
| RAM                        | Section 22.10.26                   | MB    | D         |
| RANDOM NUMBER              | Uniform random variable over [0,1] |       | D         |
| SPRINKLER LINK TEMPERATURE | Section 18.3.1                     | ℃     | D         |
| THERMOCOUPLE               | Section 22.10.8                    | ℃     | D         |
| TIME                       | Section 22.2                       | s     | D         |
| TIME STEP                  | Section 22.10.26                   | s     | D         |
| TRANSMISSION               | Section 18.3.6                     | %/m   | D         |
| UPPER TEMPERATURE          | Section 22.10.7                    | ℃     | D         |
| WALL CLOCK TIME            | Section 22.10.26                   | s     | D         |
| WALL CLOCK TIME ITERATIONS | Section 22.10.26                   | s     | D         |



下表 22.7 列出了一些不常用的输出量。这些量主要用于诊断目的。大多数输出量的解释见《FDS 技术参考指南》第 1 卷。

<center>Table 22.7: Particle and droplet output quantities.</center>

| QUANTITY                                   | Explanation                          | Units                  | File Type |
| ------------------------------------------ | ------------------------------------ | ---------------------- | --------- |
| ADA[^227-2]                                | Avg. Droplet (cross sectional) Area  | $\mathrm{m^{2}/m^{3}}$ | D,I,P,S   |
| ADA_Z[^227-1]                              | Avg. Droplet (cross sectional) Area  | $\mathrm{m^{2}/m^{3}}$ | D,I,P,S   |
| ADD[^227-2]                                | Avg. Droplet Diameter                | $\mu m$                | D,I,P,S   |
| ADD_Z[^227-1]                              | Avg. Droplet Diameter                | $\mu m$                | D,I,P,S   |
| ADT[^227-2]                                | Avg. Droplet Temperature             | ℃                      | D,I,P,S   |
| ADT_Z[^227-1]                              | Avg. Droplet Temperature             | ℃                      | D,I,P,S   |
| DROPLET VOLUME FRACTION[^227-2]            | Section 22.9.3                       |                        | D,P,S     |
| MPUV[^227-2]                               | Section 22.9.3                       | $kg/m^{3}$             | D,P,S     |
| MPUV_Z[^227-1]                             | Section 22.9.3                       | $kg/m^{3}$             | D,P,S     |
| PARTICLE ACCEL X[^227-2]                   | Section 22.9.4                       | $\mathrm{m/s^{2}}$     | PA        |
| PARTICLE ACCEL Y[^227-2]                   | Section 22.9.4                       | $\mathrm{m/s^{2}}$     | PA        |
| PARTICLE ACCEL Z[^227-2]                   | Section 22.9.4                       | $\mathrm{m/s^{2}}$     | PA        |
| PARTICLE AGE                               | Section 22.9.4                       | s                      | PA        |
| PARTICLE BULK DENSITY                      | Section 22.9.4                       | $\mathrm{kg/(m^{3})}$  | PA        |
| PARTICLE DIAMETER                          | Section 22.9.4                       | $\mu m$                | PA        |
| PARTICLE DRAG COEFFICIENT[^227-2]          | Section 22.9.4                       |                        | PA        |
| PARTICLE DRAG FORCE X[^227-2]              | Section 22.9.4                       | N                      | PA        |
| PARTICLE DRAG FORCE Y[^227-2]              | Section 22.9.4                       | N                      | PA        |
| PARTICLE DRAG FORCE Z[^227-2]              | Section 22.9.4                       | N                      | PA        |
| PARTICLE FLUX X[^227-2]                    | Section 22.9.3                       | $\mathrm{kg/(m^{2}s)}$ | P,S       |
| PARTICLE FLUX Y[^227-2]                    | Section 22.9.3                       | $\mathrm{kg/(m^{2}s)}$ | P,S       |
| PARTICLE FLUX Z[^227-2]                    | Section 22.9.3                       | $\mathrm{kg/(m^{2}s)}$ | P,S       |
| PARTICLE HEAT TRANSFER COEFFICIENT[^227-2] | Section 22.9.4                       | $\mathrm{W/m^2/K}$     | PA        |
| PARTICLE MASS                              | Section 22.9.4                       | kg                     | PA        |
| PARTICLE PHASE                             | Section 22.9.4                       |                        | PA        |
| PARTICLE RADIATION LOSS                    | Section 22.9.3                       | $\mathrm{kW/m^{3}}$    | D,I,P,S   |
| PARTICLE TEMPERATURE                       | Section 22.9.4                       | ℃                      | PA        |
| PARTICLE U                                 | Section 22.9.4                       | m/s                    | PA        |
| PARTICLE V                                 | Section 22.9.4                       | m/s                    | PA        |
| PARTICLE VELOCITY                          | Section 22.9.4                       | m/s                    | PA        |
| PARTICLE W                                 | Section 22.9.4                       | m/s                    | PA        |
| PARTICLE WEIGHTING FACTOR                  | Section 22.9.4                       |                        | PA        |
| PARTICLE X                                 | Section 22.9.4                       | m                      | PA        |
| PARTICLE Y                                 | Section 22.9.4                       | m                      | PA        |
| PARTICLE Z                                 | Section 22.9.4                       | m                      | PA        |
| PDPA                                       | Droplet statistics, Section 22.10.16 |                        | D         |
| QABS[^227-2]                               | Absorption efficiency of droplets    |                        | D,I,P,S   |
| QABS_Z[^227-1]                             | Absorption efficiency of droplets    |                        | D,I,P,S   |
| QSCA[^227-2]                               | Scattering efficiency of droplets    |                        | D,I,P,S   |
| QSCA_Z[^227-1]                             | Scattering efficiency of droplets    |                        | D,I,P,S   |

****

[^227-1]:需要使用SPEC_ID指定气体种类。
[^227-2]:需要使用PART_ID指定粒子名称。

****



表 22.8 汇总了暖通空调系统的各种输出量。在文件类型一栏中，D 表示用 DEVC 输入指定的设备输出，H 表示用 HVAC 输入指定的 Smokeview 输出。

所有暖通空调输出量均可通过 DEVC 输入选择。请勿为暖通空调输出指定 XYZ 或 XB。使用 DEVC 时，管道的量需要指定 DUCT_ID，节点的量需要指定 NODE_ID，管道单元的量（当指定 HVAC_MASS_TRANSPORT_CELL_L 或 ct N_CELLS 时）需要同时指定 DUCT_ID 和 CELL_L（从所需单元所在的第一个节点算起沿管道的距离，以米为单位）。**质量和体积分数输出也需要指定 SPEC_ID**。风扇和盘管输出需要其所在管道的 DUCT_ID。过滤器输出需要其所在节点的 NODE_ID。DUCT ENTHALPY FLOW（管道入口流量）量将公式 22.32 应用于管道中的流量。要使节点输出 NODE ENTHALPY 反映 DUCT ENTHALPY FLOW 的管道量，请为节点输出设置 RELATIVE=.TRUE。节点压力差量 NODE PRESSSURE DIFFERENCE（节点压力差）要求指定数组 NODE_ID 的两个元素，并通过从第二个节点减去第一个节点来计算压力差。

以 DUCT 开头的暖通空调输出量（非风管单元量）和以 NODE 开头的输出量（NODE 压力差除外）也可以输出到 CHID.hvac 文件，Smokeview 使用该文件将风管量可视化（文件格式说明请参见第 27.21 节）。这些文件在表 22.8 中的文件类型为 H。Smokeview 输出使用 HVAC 命名列表指定。要选择管道输出，请创建一个 TYPE_ID='DUCT QUANTITY LIST' 的单个 HVAC 输入；要选择节点输出，请创建一个 TYPE_ID='NODE QUANTITY LIST' 的单个 HVAC 输入。使用 QUANTITY（数量）指定一个最多包含 20 个输出的列表，如果任何数量需要一个种类，还需为该数量指定 QUANTITY_SPEC_ID。对于风道输出，如果风道被划分为多个单元，则会为每个单元写入 Smokeview 输出。可以使用 DUMP 上的 DT_HVAC 设置输出间隔。例如:

```fortran
&HVAC TYPE_ID='DUCT QUANTITY LIST',
    QUANTITY='DUCT VELOCITY','DUCT LOSS','DUCT VOLUME FRACTION','DUCT VOLUME
    FRACTION',
    QUANTITY_SPEC_ID(3)='OXYGEN',QUANTITY_SPEC_ID(4)='SOOT'/
```

会输出速度，流动损失，以及所有管道中氧气和烟灰的体积分数。

<center>Table 22.8: HVAC output quantities.</center>

| QUANTITY                  | Explanation                                 | Units                       | File Type |
| ------------------------- | ------------------------------------------- | --------------------------- | --------- |
| AIRCOIL HEAT EXCHANGE     | Heat exchange rate for an aircoil           | $kW$                        | D         |
| DUCT DENSITY              | Density of the flow in a duct               | $kg/m^{3}$                  | D,H       |
| DUCT CELL DENSITY         | Gas density in a duct cell                  | $kg/m^{3}$                  | D         |
| DUCT CELL MASS FRACTION   | Mass fraction of a species in a duct cell   | $kg/kg$                     | D         |
| DUCT CELL TEMPERATURE     | Gas temperature in a duct cell              | ℃                           | D         |
| DUCT CELL VOLUME FRACTION | Volume fraction of a species in a duct cell | $mol/mol$                   | D         |
| DUCT ENTHALPY FLOW        | Enthalpy flow in a duct                     | $kW$                        | D,H       |
| DUCT LOSS                 | Total flow loss coefficient for a duct      |                             | D,H       |
| DUCT MASS FLOW            | Mass flow in a duct                         | kg/s                        | D,H       |
| DUCT MASS FRACTION        | Mass fraction of a species in a duct        | $kg/kg$                     | D,H       |
| DUCT TEMPERATURE          | Temperature of the flow in a duct           | ℃                           | D,H       |
| DUCT VELOCITY             | Velocity of a duct                          | m/s                         | D,H       |
| DUCT VOLUME FLOW          | Volumetric flow in a duct                   | $\mathrm{m}^{3}/\mathrm{s}$ | D,H       |
| DUCT VOLUME FRACTION      | Volume fraction of a species in a duct      | $mol/mol$                   | D,H       |
| FAN PRESSURE              | Pressure output of a fan in a duct          | Pa                          | D         |
| FILTER LOADING            | Loading of a species in a filter            | kg                          | D         |
| FILTER LOSS               | Flow loss through a filter                  |                             | D         |
| NODE DENSITY              | Density of the flow through a node          | $kg/m^{3}$                  | D,H       |
| NODE ENTHALPY             | Enthalpy of a node                          | $kJ/kg$                     | D,H       |
| NODE SENSIBLE ENTHALPY    | Sensible Enthalpy of a node                 | $kJ/kg$                     | D,H       |
| NODE MASS FRACTION        | Mass fraction of a species in a node        | $kg/kg$                     | D,H       |
| NODE PRESSURE             | Pressure of a node                          | Pa                          | D,H       |
| NODE PRESSURE DIFFERENCE  | Pressure difference between two nodes       | Pa                          | D         |
| NODE TEMPERATURE          | Temperature of the flow though a node       | ℃                           | D,H       |
| NODE VOLUME FRACTION      | Volume fraction of a species in a node      | $mol/mol$                   | D,H       |

DEVC有两种输出方式。第一个是模拟过程中给定QUANTITY的时间历史。第二种是由point devices的线性阵列组成的时间平均剖面。下面逐一解释。

**1.Gas Phase Quantity at a Single Point**

如果你只是想记录时间历史，比如说，气体中某一点的温度，如下：

```fortran
&DEVC XYZ=6.7,2.9,2.1, QUANTITY='TEMPERATURE', ID='T-1' /
```

然后在输出文件`CHID_dev.csv`中会出现一列，标签为' T-1 '。

FDS报告包含点XYZ的单元格中的QUANTITY值。大多数标量(如TEMPERATURE)都是在**单元中心**定义的，并表示该值在整个单元中的平均值。:exclamation:如果你指定坐标xyz将设备放置在单元边界，两个单元中心中间，**FDS会选择具有较大坐标值的那个**。FDS不会对最近的8个网格中心进行加权平均。原因是其中一些网格中心可能位于薄障碍物的另一侧。

如果QUANTITY是在单元面上定义的，比如“U-VELOCITY”，**FDS选择最近的单元面并报告相应的值**。

**2.Solid Phase Quantity at a Single Point**

<font color=red>**在描述固相量时，一定要将设备置于固体表面**</font>。实体表面的位置并不总是很明显，因为网格并不总是与输入障碍物位置对齐。为了帮助定位合适的表面，在指定固相量时**必须包括IOR参数**，除非使用第3节中描述的空间统计选项之一，在这种情况下，输出量不与表面上的单个点相关联。如果固体表面的方向在x正方向，则设IOR=1。如果它在负x方向，则设置IOR=-1, y和z方向也是如此。例如，下面表示负y方向墙的表面温度。

```fortran
&DEVC XYZ=0.7,0.9,2.1, QUANTITY='WALL TEMPERATURE', IOR=-2, ID='...' /
```

**Solid Phase Quantity In-Depth**

:exclamation:要记录表面内部的温度，可以使用以下设备：

```fortran
&DEVC XYZ=..., QUANTITY='INSIDE WALL TEMPERATURE', DEPTH=0.005, ID='Temp_1', IOR=3 /
```

DEPTH (m)表示实体表面内部的距离。如果DEPTH为正，FDS输出由表面正面移动DEPTH得到的壁面节点的温度。如果为负，则从背面测量(例如，由当前固体表面厚度给出的从正面的位置+深度)。请注意，如果由于固相反应，壁厚随着时间的推移而减少，并且从当前的前表面测量距离，测量点将向固体的背面移动。最终，测量点可能从固体中出现，在这种情况下，它开始显示环境温度。**测量与后表面的距离可以更好地适应这一目的**。

:question:请注意，DEPTH可能与“INSIDE WALL temperature”输出的固体单元温度对应的中心离散空间位置不完全对齐。考虑到固相例程所做的拉伸和重新网格划分，手工计算局部离散单元的位置比较困难。如果需要离散的实体单元中心位置，则可以使用

```fortran
&DEVC XYZ=..., QUANTITY='INSIDE WALL DEPTH', DEPTH=0.005, ID='XC_1', IOR=3 /
```

输出应该位于指定DEPTH距离的半个实体网格单元格距离内。

为了记录材料成分的**密度随时间的变化**，使用“SOLID DENSITY”输出量如下：

```fortran
&DEVC ID='...', XYZ=..., IOR=3, QUANTITY='SOLID DENSITY', MATL_ID='wood', DEPTH=0.001/
```

这产生了在MATL线上称为“木材”的材料密度的时间历史。密度记录在表面下1mm处，方向为正z方向。请注意，如果“木材”是混合物的一部分，则密度表示每单位体积混合物中“木材”的质量。没有指定MATL_ID，则给出总密度。

要记录固体热导率(W/(mK))，使用QUANTITY= 'SOLID CONDUCTIVITY '。要记录固体比热(kJ/(kgK))，使用QUANTITY= ' SOLID SPECIFIC HEAT '。来记录固体焓(kJ/m3)，使用QUANTITY= ' SOLID ENTHALPY'。这些量可以采用可选的MATL_ID关键字。要记录固体中材料的质量分数，使用QUANTITY= ' SOLID MASS FRACTION '，需要一个MATL_ID。

:exclamation:请注意，这些数量只允许作为DEVC或PROF输出，而不允许作为BNDF输出。

**Back Surface Temperature**

如果你只是想知道“墙”背面的温度，那就用如下命令：

```fortran
&DEVC XYZ=..., QUANTITY='BACK WALL TEMPERATURE', ID='Temp_b', IOR=3 /
```

请注意，只有当“墙”的正面或暴露的表面具有该属性时，这个量才有意义，在定义它的SURF行上的BACKING= ' EXPOSED '。

**3.Spatially-Integrated Outputs**

设备(DEVC)的一个有用特性是指定输出量以及所需的统计量。例如：

```fortran
&DEVC XB=..., QUANTITY='TEMPERATURE', ID='maxT', SPATIAL_STATISTIC='MAX' /
```

使FDS写出**以XB为界的体积上的最大气相温度**。有些适用于气相输出量，有些适用于固相输出量，有些适用于两者。注意，如果XB用于没有SPATIAL_STATISTIC的点设备，那么FDS将把XYZ定义为XB定义的体积中心。SPATIAL_STATISTIC只能用于表22.12中文件类型列中同时包含D和S的气相QUANTITY或表22.13中文件类型列中同时包含D和B的固相QUANTITY。

对于固相输出量，如热通量和表面温度，SURF_ID的规定和适当的统计数据将计算限制在这些表面上。通过使用坐标XB的六元组来强制FDS只计算给定体积内表面单元的统计信息，可以进一步限制搜索。注意，**在使用空间统计量时，不能(也不应该)通过参数IOR指定方向**。IOR只需要在固体表面上找到一个特定的点。

**Linearly Interpolated Value**

**4.Temporally-Integrated Outputs**

除了空间统计外，时间统计还可以通过参数TEMPORAL_STATISTIC应用于DEVC输出。**可以在DEVC行上同时指定SPATIAL_STATISTIC和TEMPORAL_STATISTIC**，假设组合是有意义的。首先应用SPATIAL_STATISTIC，比如对给定体积XB上的QUANTITY进行积分，然后是TEMPORAL_STATISTIC，就像时间积分一样。

**Time Average**

默认情况下，通常应用TEMPORAL_STATISTIC= ' TIME AVERAGE '，除非它不适合所选的QUANTITY。有了这个统计信息，FDS输出在输出时间之前的DT_DEVC时间段内QUANTITY的平均值。DT_DEVC参数是在DUMP行指定的。



**5.Linear Array of Point Devices**

您可以使用单个DEVC线来指定设备的线性阵列。<font color=red>**通过添加参数POINTS并使用六元坐标数组`XBP`，您可以指示FDS创建从(x1,y1, z1)到(x2, y2, z2)的线段**</font>。

**Steady-State Profile**

有时计算稳态剖面很方便。例如，沿门道中心线的垂直速度剖面可以用以下输入线记录：

```fortran
&DEVC XBP=X1,X2,Y1,Y2,Z1,Z2, QUANTITY='U-VELOCITY', ID='vel', POINTS=20,
    STATISTICS_START=20., STATISTICS_END=40. /
```

在一个名为CHID_line.csv的文件中，将有1到4列与此DEVC线相关联的数据。如果X1不同于X2，则会有一列x坐标与点的线性数组相关联。对于yz坐标也一样。最后一列包含在STATISTICS_START和STATISTICS_END之间的间隔内的20个温度点的时间平均值。**后者的默认值是T_END，前者是总模拟时间的一半**。注意，输出到_line.csv文件的统计数据**在T=STATISTICS_START时开始平均。在此之前，值为零**。这可以防止初始瞬态对最终平均值或其他时间统计数据产生偏差。默认情况下，**点在(x1,y1, z1)和(x2,y2, z2)之间均匀间隔**。要改变这种情况，您可以添加坐标值POINTS_ARRAY_X、POINTS_ARRAY_Y和/或POINTS_ARRAY_Z的数组。例如，

```fortran
&DEVC XBP=0,0,0,0,0,1, QUANTITY='TEMPERATURE', ID='T', POINTS=4,
    POINTS_ARRAY_Z=0.1,0.2,0.3,0.7 /
```

在垂直方向上创建一个由四个点组成的数组，这些点的间距不均匀。数组XBP中的原始值0和1将被忽略。使用所有三个POINTS_ARRAYs，您可以创建点的曲线。**这些数组的上维数是100（100个点？）**。

:smile:**数据的存储**：单个“line”文件可以保存多行数据。默认情况下，坐标列使用DEVC的ID加上-x、-y或-z进行标记。要更改这些标签，请使用X_ID，Y_ID，和/或Z_ID。**还可以不显示这些标签，参见手册P348**。如果您希望将数据绘制为与原点距离的函数，$r = \sqrt {x^2+y^2+z^2}$，则提供标签R_ID。如果希望将数据绘制为与直线上第一个点(X1,Y1,Z1)之间距离的函数，则提供标签D_ID。同时，可以设置COORD_FACTOR转换稳态的空间坐标尺度。（m，cm）

**Time-Varying Profile**

:exclamation:如果您不想要一个稳态配置文件，而只是想要指定一个均匀间隔的设备数组，那么您可以使用类似的输入行，除了使用额外的属性TIME_HISTORY。

```fortran
&DEVC XBP=X1,X2,Y1,Y2,Z1,Z2, QUANTITY='U-VELOCITY', ID='vel', POINTS=20,
    TIME_HISTORY=T /
```

这将引导FDS将20个设备添加到正在进行的列表中，从而使您不必编写20行DEVC。每个设备的ID将是' vel-01 '， ' vel-02 '，等等。

**Other Statistics for a Linear Array of Devices**

默认情况下，当您在DEVC线路上指定多个点并且不指定TIME_HISTORY=T时，指定的QUANTITY的运行平均值将使用在STATISTICS_END. csv时间的累积值保存在每个点位置并以后缀_line.csv写入文件。但是，您可以应用任何其他TEMPORAL_STATISTIC。例如，计算指定时间间隔内的均方根(' RMS ')、最小值(' MIN ')或最大值(' MAX ')值。

你也可以为每一个设备指定一个SPATIAL_STATISTIC，如下所示：

```fortran
&DEVC XBP=1,10,5,5,8,8, QUANTITY='TEMPERATURE', ID='Tmean', POINTS=20,
    STATISTICS_START=20., STATISTICS_END=40.
    SPATIAL_STATISTIC='MEAN', DX=0.1, DY=5.0, DZ=3.0 /
```

**Moving a Linear Array of Devices**

可以使用MOVE线上的参数平移和/或旋转器件的线性阵列(参见11.4节)。在DEVC行中使用MOVE_ID字符串来指定这些参数。注意，如果指定了SPATIAL_STATISTIC，则不会转换空间边界DX、DY和/或DZ。



### DUMP (Output Parameters)

| 可输入参数           | 类型        | 描述             | 单位 | 默认       |
| -------------------- | ----------- | ---------------- | ---- | ---------- |
| CFL_FILE             | Logical     | Section 6.2.2    |      | F          |
| CLIP_RESTART_FILES   | Logical     | Section 5.6      |      | T          |
| COLUMN_DUMP_LIMIT    | Logical     | Section 18.2     |      | F          |
| CTRL_COLUMN_LIMIT    | Integer     | Section 18.2     |      | 254        |
| DEVC_COLUMN_LIMIT    | Integer     | Section 18.2     |      | 254        |
| DIAGNOSTICS_INTERVAL | Integer     | Section 3.4      |      | 100        |
| DT_BNDF              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_CPU               | Real        | Section 27.6     | s    | 2Δt        |
| DT_CTRL              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_DEVC              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_FLUSH             | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_HRR               | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_HVAC              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_ISOF              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_MASS              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_PART              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_PL3D              | Real        | Section 22.1     | s    | 2Δt        |
| DT_PROF              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_RADF              | Real        | Section 22.10.14 | s    | 2Δt        |
| DT_RESTART           | Real        | Section 22.1     | s    | 2Δt        |
| DT_SL3D              | Real        | Section 22.1     | s    | 2Δt        |
| DT_SLCF              | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_SMOKE3D           | Real        | Section 22.1     | s    | Δt/NFRAMES |
| DT_SPEC              | Real        | Section 20.6     | s    |            |
| DT_TMP               | Real        | Section 20.6     | s    |            |
| DT_UVW               | Real        | Section 20.6     | s    |            |
| FLUSH_FILE_BUFFERS   | Logical     | Section 22       |      | T          |
| HRR_GAS_ONLY         | Logical     | Section 22.10.1  |      | F          |
| MASS_FILE            | Logical     | Section 22       |      | F          |
| MAXIMUM_PARTICLES    | Integer     | Section 15.5     |      | 1000000    |
| NFRAMES              | Integer     | Section 22       |      | 1000       |
| PLOT3D_PART_ID(5)    | Char. Quint | Section 22.7     |      |            |
| PLOT3D_QUANTITY(5)   | Char. Quint | Section 22.7     |      |            |
| PLOT3D_SPEC_ID(5)    | Char. Quint | Section 22.7     |      |            |
| PLOT3D_VELO_INDEX    | Int. Quint  | Section 22.10.24 |      | 0          |
| RAMP_BNDF            | Character   | Section 22.1     |      |            |
| RAMP_CPU             | Character   | Section 27.6     |      |            |
| RAMP_CTRL            | Character   | Section 22.1     |      |            |
| RAMP_DEVC            | Character   | Section 22.1     |      |            |
| RAMP_FLUSH           | Character   | Section 22.1     |      |            |
| RAMP_HRR             | Character   | Section 22.1     |      |            |
| RAMP_HVAC            | Character   | Section 22.1     |      |            |
| RAMP_ISOF            | Character   | Section 22.1     |      |            |
| RAMP_MASS            | Character   | Section 22.1     |      |            |
| RAMP_PART            | Character   | Section 22.1     |      |            |
| RAMP_PL3D            | Character   | Section 22.1     |      |            |
| RAMP_PROF            | Character   | Section 22.1     |      |            |
| RAMP_RADF            | Character   | Section 22.10.14 |      |            |
| RAMP_RESTART         | Character   | Section 22.1     |      |            |
| RAMP_SL3D            | Character   | Section 22.1     |      |            |
| RAMP_SLCF            | Character   | Section 22.1     |      |            |
| RAMP_SMOKE3D         | Character   | Section 22.1     |      |            |
| RAMP_SPEC            | Character   | Section 22.1     |      |            |
| RAMP_TMP             | Character   | Section 22.1     |      |            |
| RAMP_UVW             | Character   | Section 22.1     |      |            |
| RENDER_FILE          | Character   | Reference [^17]  |      |            |
| RESULTS_DIR          | Character   | Section 22       |      |            |
| SIG_FIGS             | Integer     | Section 22.10.27 |      | 8          |
| SIG_FIGS_EXP         | Integer     | Section 22.10.27 |      | 3          |
| SMOKE3D              | Logical     | Section 22.8     |      | T          |
| STATUS_FILES         | Logical     | Section 22       |      | F          |
| SUPPRESS_DIAGNOSTICS | Logical     | Section 3.4      |      | F          |
| VELOCITY_ERROR_FILE  | Logical     | Section 22.10.26 |      | F          |
| WRITE_XYZ            | Logical     | Section 22.7     |      | F          |

$\Delta t=T_{END}-T_{BEGIN}$

:exclamation:<font color=red>输入文件中只能有一个DUMP行。</font>

FDS默认将结果文件输出到当前工作目录。用户可以通过在DUMP行设置RESULTS_DIR来**指定二进制文件的单独输出目录**。

#### Controlling the Frequency of Output

点设备数据、切片(轮廓)数据、粒子数据、等值面数据、三维烟雾数据、边界数据、固相轮廓数据和控制函数数据每隔`(T_END-T_BEGIN)/NFRAMES`秒写入一次文件，除非使用表22.1中列出的参数另有规定。这些参数将写入 DUMP 行。您也可以将 NFRAMES 设置为默认值 1000 以外的值。名为 DT_XXXX 的参数指定了数据转储之间的统一时间间隔。

:exclamation:<font color=red>参数RAMP_XXXX允许您精确地指定写入的时间。</font>

例如，如果您想在10,20和60s时写入边界文件，可以像如下定义：

```fortran
&DUMP ..., RAMP_BNDF='b-ramp' /
&RAMP ID='b-ramp', T=10 /
&RAMP ID='b-ramp', T=20 /
&RAMP ID='b-ramp', T=60 /
```

1. 如果模拟涉及燃烧，FDS会自动写入烟灰密度、单位体积热量释放率和温度的Smoke3D文件。这些数量在烟雾视图中呈现为逼真的烟雾和火焰。要关闭此功能，请在DUMP行设置SMOKE3D=F。
2. `DT_PL3D`：Plot3D文件输出间隔时间。请注意，6之前的FDS版本默认输出Plot3D文件。现在，您必须使用该参数指定输出间隔。**它的默认值是1000000s，这意味着除非指定，否则没有Plot3D输出**。
3. `FLUSH_FILE_BUFFERS`：FDS定期清理输出文件缓冲区，并强制将数据写入相应的输出文件。这样做是为了在运行时更容易在烟雾视图中查看案例。在Windows计算机上已经注意到，由于与缓冲区刷新相关的文件访问问题，偶尔会发生运行时错误。**如果发生这种情况，将此参数设置为F**，但要注意，在计算完成之前，可能无法查看烟雾视图中的输出。您还可以设置DT_FLUSH来控制文件刷新的频率。它的默认值是模拟的持续时间除以NFRAMES。
4. `STATUS_FILES`：如果为T，则生成一个输出文件CHID.notready。如果模拟成功完成，则删除。这个文件可以用作错误指示器。默认值是F。

<center>表22.1 控制输出频率的参数</center>

| 均匀输出   | 非均匀输出   | 目的                     |
| ---------- | ------------ | ------------------------ |
| DT_BNDF    | RAMP_BNDF    | Boundary files           |
| DT_CPU     | RAMP_CPU     | CPU timings              |
| DT_CTRL    | RAMP_CTRL    | Control output           |
| DT_DEVC    | RAMP_DEVC    | Device output            |
| DT_FLUSH   | RAMP_FLUSH   | File flushing times      |
| DT_HRR     | RAMP_HRR     | HRR output               |
| DT_HVAC    | RAMP_HVAC    | HVAC output              |
| DT_ISOF    | RAMP_ISOF    | Isosurface output        |
| DT_MASS    | RAMP_MASS    | Species mass output      |
| DT_PART    | RAMP_PART    | Particle output          |
| DT_PL3D    | RAMP_PL3D    | Plot3D output            |
| DT_PROF    | RAMP_PROF    | In-depth profile output  |
| DT_RADF    | RAMP_RADF    | Radiation output         |
| DT_RESTART | RAMP_RESTART | Restart times            |
| DT_SLCF    | RAMP_SLCF    | Slice files              |
| DT_SL3D    | RAMP_SL3D    | Slice 3D files           |
| DT_SMOKE3D | RAMP_SMOKE3D | Smoke 3D files           |
| DT_SPEC    | RAMP_SPEC    | Species field output     |
| DT_TMP     | RAMP_TMP     | Temperature field output |
| DT_UVW     | RAMP_UVW     | Velocity field output    |





#### In-Depth Profiles within Solids: The PROF Namelist Group

FDS在每个边界单元上使用精细的一维网格来计算固体内部的热传导和反应。固体可以是壁面单元或拉格朗日粒子。在任何一种情况下，使用PROF输出以离散的时间间隔记录固体的深度属性。PROF可以使用任何采用DEPTH的固相输出QUANTITY。它们在22.13节中用文件类型“Pr”标识。

<center>Solid phase output quantities</center>

| 量                              | 说明                                  | 单位        | 文件类型 |
| ------------------------------- | ------------------------------------- | ----------- | -------- |
| ADIABATIC SURFACE TEMPERATURE   | Section 22.10.13                      | ℃           | B,D      |
| AMPUA[^fb]                      | Section 22.9.1                        | $kg/m^2$    | B,D      |
| AMPUA_Z[^fa]                    | Section 22.9.1                        | $kg/m^2$    | B,D      |
| BACK WALL TEMPERATURE           | Section 22.2.2                        | ℃           | B,D      |
| BURNING RATE                    | Mass loss rate of fuel                | $kg/(m^2s)$ | B,D      |
| CONDENSATION HEAT FLUX          | Section 13.7                          | $kW/m^2$    | B,D      |
| CONVECTIVE HEAT FLUX            | Section 22.10.12                      | $kW/m^2$    | B,D      |
| CONVECTIVE HEAT FLUX GAUGE      | Section 22.10.12                      | $kW/m^2$    | B,D      |
| CONVECTIVE HEAT TRANSFER REGIME | Section 8.2.2                         |             | B,D      |
| CPUA[^fb]                       | Section 22.9.1                        | $kW/m^2$    | B,D      |
| CPUA_Z[^fa]                     | Section 22.9.1                        | $kW/m^2$    | B,D      |
| DEPOSITION VELOCITY             | Section 13.4                          | m/s         | B,D      |
| FRICTION VELOCITY               | Section 22.10.28                      | m/s         | B,D      |
| GAUGE HEAT FLUX                 | Section 22.10.12                      | $kW/m^2$    | B,D      |
| ENTHALPY FLUX WALL              | Section 22.10.11                      | $kW/m^2$    | B,D      |
| TOTAL HEAT FLUX                 | Section 22.10.12                      | $kW/m^2$    | B,D      |
| EMISSIVITY                      | Surface emissivity (usually constant) |             | B,D      |
| GAS DENSITY                     | Gas Density near wall                 | $kg/m^3$    | B,D      |
| GAS TEMPERATURE                 | Gas Temperature near wall             | ℃           | B,D      |
| HEAT TRANSFER COEFFICIENT       | Section 8.2.2                         | $W/(m^2K)$  | B,D      |
| HRRPUA                          | $\dot{q}^{\prime\prime}$              | $kW/m^2$    | B,D      |
| INCIDENT HEAT FLUX              | Section 22.10.12                      | $kW/m^2$    | B,D      |
| INSIDE WALL TEMPERATURE         | Section 22.2.2                        | ℃           | D,**Pr** |
| INSIDE WALL DEPTH               | Section 22.2.2                        | m           | D,**Pr** |
| MASS FLUX[^fa][^fd]             | Section 22.10.10                      | $kg/(m^2s)$ | B,D      |
| MASS FLUX WALL[^fa]             | Section 22.10.10                      | $kg/(m^2s)$ | B,D      |
| MPUA[^fb]                       | Section 22.9.1                        | $kW/m^2$    | B,D      |
| MPUA_Z[^fa]                     | Section 22.9.1                        | $kW/m^2$    | B,D      |
| NORMAL VELOCITY                 | Wall normal velocity                  | m/s         | B,D      |
| NORMALIZED HEATING RATE         | Section 22.10.17                      | W/g         | D        |
| NORMALIZED HEAT RELEASE RATE    | Section 22.10.17                      | W/g         | D        |
| NORMALIZED MASS[^fd]            | Section 22.10.17                      |             | D        |
| NORMALIZED MASS LOSS RATE[^fd]  | Section 22.10.17                      | 1/s         | D        |
| PRESSURE COEFFICIENT            | Section 22.10.21                      |             | B,D      |
| RADIATIVE HEAT FLUX             | Section 22.10.12                      | $kW/m^2$    | B,D      |
| RADIOMETER                      | Section 22.10.12                      | $kW/m^2$    | B,D      |
| REFERENCE_HEAT_FLUX             | Section 9.1.4                         | $kW/m^2$    | B,D      |
| SOLID CONDUCTIVITY[^fd]         | Section 22.2.2                        | $W/(mK)$    | D,**Pr** |
| SOLID DENSITY[^fd]              | Section 22.2.2                        | $kg/m^3$    | D,**Pr** |
| SOLID ENTHALPY[^fd]             | Section 22.2.2                        | $kJ/m^3$    | D,**Pr** |
| SOLID MASS FRACTION[^fe]        | Section 22.2.2                        | $kg/kg$     | D,**Pr** |
| SOLID SPECIFIC HEAT[^fd]        | Section 22.2.2                        | $kJ/(kgK)$  | D,**Pr** |
| SUBSTEPS                        | Section 8.3.8                         |             | B,D      |
| SURFACE DENSITY[^fd]            | Section 22.10.17                      | $kg/m^2$    | B,D      |
| SURFACE DEPOSITION[^fa]         | Section 13.4                          | $kg/m^2$    | B,D      |
| TOTAL MASS FLUX WALL[^fa]       | Section 22.10.10                      | $kg/s/m^2$  | B,D      |
| VELOCITY ERROR                  | Section 21                            | m/s         | B,D      |
| VISCOUS STRESS WALL             | Section 22.10.21                      | Pa          | B,D      |
| VISCOUS WALL UNITS              | Section 22.10.28                      |             | B,D      |
| WALL ENTHALPY                   | $\int\rho_{s}c_{s}T\mathrm{d}V_{s}$   | kJ          | B,D      |
| WALL PRESSURE                   | Section 22.10.21                      | Pa          | B,D      |
| WALL TEMPERATURE                | Surface temperature                   | ℃           | B,D      |
| WALL THICKNESS                  | Section 22.10.17                      | m           | B,D      |
| WALL VISCOSITY                  | Near-wall viscosity, $μ_w$            | $kg/(ms)$   | B,D      |

*******

[^fa]:Requires the specification of a gas species using SPEC_ID.
[^fb]:Requires the specification of a particle name using PART_ID.
[^fc]:Requires specification of an additional scalar using QUANTITY2.
[^fd]:Allows for an optional MATL_ID.
[^fe]:Requires a MATL_ID.

*************

参数说明如表23.23所示。对于壁面单元，参数类似于DEVC组中指定表面量的参数。XYZ指定坐标三元组，IOR指定方向，ID指定标识字符串。

<center>表23.23 PROF (Wall Profile Parameters)</center>

| 可输入参数    | 类型         | 描述         | 单位 | 默认 |
| ------------- | ------------ | ------------ | ---- | ---- |
| CELL_CENTERED | Logical      | Section 22.3 |      | F    |
| FORMAT_INDEX  | Integer      | Section 22.3 |      | 1    |
| ID            | Character    | Section 22.3 |      |      |
| INIT_ID       | Character    | Section 22.3 |      |      |
| IOR           | Real         | Section 22.3 |      |      |
| MATL_ID       | Character    | Section 22.3 |      |      |
| QUANTITY      | Character    | Section 22.3 |      |      |
| XYZ           | Real Triplet | Section 22.3 | m    |      |



下面是一个如何使用此功能来获取壁面单元内温度曲线的时间历史的示例：

```fortran
&PROF ID='T-1', XYZ=..., QUANTITY='INSIDE WALL TEMPERATURE', IOR=3 /
```

:exclamation:对于一个粒子，你必须引用一个INIT行，用来将粒子放置在域中：

```fortran
&INIT ID='my particle', XYZ=..., N_PARTICLES=1, PART_ID='...' /
&PROF ID='T-2', INIT_ID='my particle', QUANTITY='INSIDE WALL TEMPERATURE' /
```

对于粒子，不要在PROF行上指定XYZ或IOR。

QUANTITY是要记录的物理量。每个PROF行创建一个单独的文件。每行中的第一个数字是提取概要文件的时间。第二个数字是“节点”的数量n，也就是固相单元的数量加1。接下来的n个值是节点坐标，从表面的0到最后的整个厚度。接下来的n个数字是节点上QUANTITY的值。第一个值位于表面。如果指定CELL_CENTERED=T，则QUANTITY值将记录在n个内部单元格中心，而不是单元格边界。ID是一个可选的输入，如果提供了，将在文件头中使用。

还有第二种可选格式。如果您在PROF行指定FORMAT_INDEX=2，则结果文件将包括仅包含最终节点坐标和数量值集的列。<font color=red>**这对于显示稳态温度曲线很方便**</font>。

#### CPU Usage Data（DT_CPU）

名为 CHID_cpu.csv 的文件记录了每个 MPI 进程的 CPU 占用时间。

Rank,MAIN,DIVG, ... , Total T_USED (s)
0, 2.052E+00, 1.058E+01, ... , 5.143+01
1, 2.432E+00, 1.062E+01, ... , 5.123+01
.
.

其中，"Rank "是 MPI 进程的编号（从 0 开始），"MAIN"、"DIVG "等是主要例程，"Total T_USED (s) "是特定 MPI 进程消耗的 CPU 总时间。通常情况下，总时间是相似的。**在 MAIN 中花费的时间实质上是开销--没有用于计算的时间**。如果想知道工作负载是否平衡，可以看看在 MAIN 中花费的时间。所有 MPI 进程花费的时间应该差不多。<font color=red>如果其中一个 MPI 进程的 MAIN 值明显较小，则说明该进程正在执行核心例程，而其他进程在 MAIN 中处于闲置状态</font>。

CHID_cpu.csv 文件将在模拟结束时打印出来。要强制在仿真期间定期打印，可在 DUMP 行设置 DT_CPU 或 RAMP_CPU。后一个参数允许您在指定时间写出文件。:question:（这个的作用是什么呢？尝试之后未按DT_CPU间隔输出文件）

### Ventilation

本章介绍如何对通风系统进行建模。有两种方法可以做到。首先，是明确指定进出隔室的空气流速，见第10.1节对简单速度边界条件的描述。第二，是使用暖通空调系统对气流速率进行建模，参见第10.2节对暖通空调系统建模的描述。

#### Simple Vents, Fans and Heaters

描述送风机或排气扇的最简单方法是在固体表面指定一个VENT，并指定一个具有某种形式的指定速度或体积流量的 SURF_ID。**速度的法向分量通常通过参数 VEL 直接指定。如果 VEL 为负值，则流向计算域，即供气通风口。如果 VEL 为正值，则气流流出计算域，即排气口**。例如：

```fortran
&SURF ID='SUPPLY', VEL=-1.2, COLOR='BLUE' /
&VENT XB=5.0,5.0,1.0,1.4,2.0,2.4, SURF_ID='SUPPLY' /
```

创建一个通风口，以 1.2 米/秒的速度向名义面积为 0.16 平方米的区域供气，具体取决于将通风口重新调整到 FDS 网格上。无论平面x = 5的方向如何，由于VEL的标志，气流将被引导进入房间。在这个例子中，VENT的面积可能不是精确的0.16 $m^2$，因为它可能与计算网格不完全对齐。**如果是这种情况，则可以指定VOLUME_FLOW而不是VEL**，单位为$m^3/s$。**如果气流正在进入计算域，VOLUME_FLOW 应为负数，这与 VEL 的约定相同**。需要注意的是，规定了 VOLUME_FLOW 的 SURF 可以由 VENT 或 OBST 调用，但要注意的是，在后一种情况下，障碍面上的速度将由指定的 VOLUME_FLOW 除以该特定面的面积得出。例如，

```fortran
&SURF ID='SUPPLY', VOLUME_FLOW=-5.0, COLOR='GREEN' /
&OBST XB=..., SURF_ID6='BRICK','SUPPLY','BRICK','BRICK','BRICK','BRICK' /
```

表明流向计算域的障碍物前 x 向表面的速度等于 5 立方米/秒除以面的面积（在 FDS 中近似）。

注意VEL和VOLUME_FLOW不应该在同一SURF行上指定。**选择取决于在给定的通风口是否需要精确的速度，或者是否需要给定的体积流量**。

还需注意的是，如果VENT或 OBST 穿过网格边界，则将在每个网格中重新计算指定的 VOLUME_FLOW，以获得所需的体积流量。在 FDS 6.3 及更早版本中，情况并非如此。Flowfields 文件夹中名为 `volume_flow_1.fds` 和 `volume_flow_2.fds` 的示例演示了可以将VENT或 OBST 划分到多个网格中。在这两个案例中，空气以 0.01 立方米/秒的速度从一个 1 米乘 1 米乘 1 米的方框中吸入。这些情况也确保了VENT或 OBST 无需与网格对齐即可产生所需的流速。图 10.1 显示了在指定体积流量的情况下，通过箱体相对面上的OPEN边界与VENT（左侧）或 OBST（右侧）所产生的体积流量。

![image-20240617194120512](..\FDS中钠燃烧模型添加.assets\image-20240617194120512.png)

#### Total Mass Flux

通常情况下，**通过设置固体表面的法向流速或体积流量来指定简单的供气或排气通风口**。不过，也可以通过参数 MASS_FLUX_TOTAL（总质量流量）来指定单位面积的总质量流量（$kg/(m^2 s)$）。**该参数使用与上述 VEL 相同的符号约定**。事实上，**输入的 MASS_FLUX_TOTAL 值会在内部转换成速度边界条件**，**其流出量的值会根据当地密度进行调整**。请注意，<font color=red>**MASS_FLUX_TOTAL 只能用于流出边界条件；对于流入边界条件，请使用 MASS_FLUX**</font>，这将在第 10.1.6 节中讨论。

#### Heaters

你可以通过改变进入空气的温度来创建一个简单的加热通风口：

```fortran
&SURF ID='BLOWER', VEL=-1.2, TMP_FRONT=50. /
```

SURF_ID='BLOWER'的VENT会以 1.2 米/秒的速度将 50 ℃ 的空气吹入流域。将 VEL 设置为正值会将空气吸出，在这种情况下就不需要 TMP_FRONT。

注意，**如果指定HRRPUA或固相反应参数，则不应规定速度**。可燃气体以FDS计算的速度喷射。

#### Louvered Vents

大多数实际的送风口都有某种格栅或百叶，它们的作用是改变或扩散进入的气流。通过规定气流的法向和切向分量，可以在一定程度上模拟这种效果。如上所述，**法向分量是通过 VEL 指定的**。**切向分量是通过一对实数 VEL_T 来指定的**，这对实数代表其他两个坐标方向（x 或 y 应在 y 或 z 之前）上所需的切向速度分量。例如，`Flowfields/tangential_velocity.fds` 示例中的行：

```fortran
&SURF ID='LOUVER', VEL=-2.0, VEL_T=3.0,0.0, TAU_V=5., COLOR='GREEN' /
```

是一个百叶通风口的边界条件，该通风口以 2 米/秒的法向速度和 3 米/秒的切向速度将空气推入空间。请注意，速度法向分量的负号表示流体注入计算域。切向速度为 3 米/秒，表示流体在正 y 方向流动。如图 10.2 所示，**使用 TAU_V 或 RAMP_V 对法线和切线速度分量进行加速**。

![image-20240617200903221](..\FDS中钠燃烧模型添加.assets\image-20240617200903221.png)

在网格分辨率有限的情况下，可能没有足够的网格单元跨越开口，VEL_T 无法正常工作。在这种情况下，您可以考虑在VENT前简单地指定一个偏移一个网格单元的平板障碍物。平板将简单地将气流转向所有横向方向。

#### Specified Normal Velocity Gradient

有时需要为边界法线方向的速度指定一个 Neumann 边界条件（指定梯度）。例如，下面的条件允许沿域顶流入和流出，但是$\partial w/\partial z=0$。**注意FREE_SLIP=T**只设置$\partial u/\partial z=0$和$\partial v/\partial z=0$：

```fortran
&SURF ID = 'sky', COLOR = 'INVISIBLE', VEL_GRAD=0., FREE_SLIP=T /
&VENT MB='ZMAX', SURF_ID='sky' /
```

#### Species and Species Mass Flux Boundary Conditions

有两种气体种类边界条件（有关气体种类的一般性讨论，请参见第 12 章）。默认情况下，气体种类不会穿透固体表面，如果只需要穿透固体表面，则无需指定任何条件。如果在强迫流动边界（指定了 VEL、VOLUME_FLOW 或 MASS_FLUX_TOTAL）处物种的质量分数为某一数值，则将 MASS_FRACTION(:)设为相应 SURF 行上所需的物种质量分数。如果需要物种的质量通量，请设置 MASS_FLUX(:)，而不是 MASS_FRACTION(:)。如果设置了 MASS_FLUX(:)，请勿指定 VEL、VOLUME_FLOW 或 MASS_FLUX_TOTAL。这些参数将根据指定的质量通量自动计算。输入 MASS_FLUX(:)和通常的 MASS_FRACTION(:)**只能用于流入边界条件**。MASS_FLUX(:) 应为正数，单位为$ kg/（m^2 s）$。另外请注意，**使用 MASS_FRACTION 时不能指定背景物质**。背景物种的质量分数将被设置为其他物种未指定的质量分数。

下面是一个如何指定以$0.025 kg/(m^2 s)$的速率产生甲烷的表面的例子：

```fortran
&SPEC ID='METHANE' /
&SURF ID='METHANE BURNER', SPEC_ID(1)='METHANE', MASS_FLUX(1)=0.025 /
&VENT XB=..., SURF_ID='METHANE BURNER' /
```

下面是如何指定以0.1米/秒的速度吹出甲烷的表面的例子：

```fortran
&SPEC ID='METHANE' /
&SURF ID='METHANE BLOWER', MASS_FRACTION(1)=1.0, SPEC_ID(1)='METHANE', VEL=-0.1 /
&VENT XB=..., SURF_ID='METHANE BLOWER' /
```

请注意，如果指定的速度较小，则指定 VEL 和 MASS_FRACTION 的组合可能导致结果不准确，**因为扩散将主导质量输运**。要获得边界处准确的物种质量通量，请使用 MASS_FLUX。

或者，为速度边界（VEL、VOLUME_FLOW 或 MASS_FLUX_TOTAL）添加 CONVERT_VOLUME_TO_MASS=T，根据指定的边界成分（MASS_FRACTION）和温度（TMP_FRONT）将体积流量转换为质量流量：
$$
\dot{m}_{\alpha}^{\prime\prime}=\rho Z_{\alpha}u=\frac{p_{\infty}\overline{W}}{RT}Z_{\alpha}\frac{\dot{Q}}{A}
$$
其中，ρ 是密度，Zα 是 α 的质量分数，u 是表面法线速度，$p_∞$ 是环境压力，$\overline{W}$ 是混合物分子量，R 是理想气体常数，T 是表面温度，$\dot{Q}$ 是体积流量，A 是通风口面积。请注意，使用 CONVERT_VOLUME_TO_MASS=T 将 SURF 转换为质量通量边界条件，因此可能无法应用速度曲线。

#### Tangential Velocity Boundary Conditions at Solid Surfaces

无滑移条件意味着表面的连续气体切向速度为零。在湍流中，速度通过厚度只有几毫米的边界层迅速增加到 "自由流 "值。在大多数实际模拟中，不可能直接解决边界层问题；因此，需要使用经验模型来表示边界层对整个流场的影响。对于 DNS（直接数值模拟），壁面处的速度梯度是直接根据壁面附近的解析速度计算出来的（默认情况下 NO_SLIP=T）。对于 LES（大涡模拟），采用的是 "对数定律 "壁面模型。"砂粒 "表面粗糙度1 （以米为单位）由 SURF 上的 ROUGHNESS 设置。要强制固体边界具有自由滑条件，请在 SURF 行上设置 FREE_SLIP=T。**在 LES 中，要覆盖壁模型并强制使用无滑动边界条件，请在 SURF 行上设置 NO_SLIP=T**。

#### Synthetic Turbulence Inflow Boundary Conditions

空气等低粘度流体的实际流动很少在时间上完全静止或在空间上完全均匀--它们（在某种程度上）是湍流。当然，流动的湍流特性可能会对混合和其他行为产生重大影响，因此仅规定名义上恒定和均匀的边界条件可能是不够的。为了解决这个问题，FDS 采用了合成涡流法 (SEM)(不能用于HVAC通风口，这是严格的质量通量边界)。详细介绍参见 Jarrin [^19]。简而言之，"涡流 "在边界上的随机位置注入流动，并在边界附近相当于最大涡流长度尺度的短距离内随平均流平移。一旦涡流通过该区域，它就会在边界入口处以新的随机位置和长度尺度重新循环。漩涡被理想化为空间球形区域上的速度扰动，其直径（漩涡长度尺度）从均匀随机分布中选择。选择程序保证满足规定的一阶和二阶统计量（包括雷诺应力）。

通过在VENT行设置湍流数量 N_EDDY、特征湍流长度尺度 L_EDDY、均方根速度波动 VEL_RMS 或雷诺应力张量分量 REYNOLDS_STRESS(3,3)，可以调用合成湍流。图 10.3 展示了使用 SEM 处理平剖面、抛物线剖面、大气剖面和湍流强度为 10%的斜坡剖面的示例（见湍流验证子目录中的 sem_* 测试系列）。大气剖面的输入线为：（有关剖面参数的进一步讨论，请参见第 16.5 节）。

```fortran
&SURF ID='inlet', VEL=-1, PROFILE='ATMOSPHERIC', Z0=0.5, PLE=0.3 /
&VENT MB='XMIN', SURF_ID='inlet', N_EDDY=100, L_EDDY=0.2, VEL_RMS=.1 /
```

![image-20240617205211679](..\FDS中钠燃烧模型添加.assets\image-20240617205211679.png)

请注意，雷诺应力是对称的，只需指定下三角部分。均方根速度波动是各向同性的（每个分量都等效）。因此，$\mathrm{VEL{\_}RMS}\equiv\sqrt{2k/3}$，其中$k\equiv\langle\frac12u_i^{\prime}u_i^{\prime}\rangle $ 是单位质量的湍流动能。下面的示例说明了速度波动有效值与雷诺应力对角线分量之间的等效关系。请注意，如果指定了 VEL_RMS，则相当于

```fortran
REYNOLDS_STRESS(1,1) = VEL_RMS**2
REYNOLDS_STRESS(2,2) = VEL_RMS**2
REYNOLDS_STRESS(3,3) = VEL_RMS**2
```

REYNOLDS_STRESS的其他分量均为零。如果波动不是各向同性的，那么雷诺应力必须按组件方式指定。

在 Jarrin 的论文[^19]第 7 章中，他介绍了修正合成涡流法，其中涡流长度尺度是各向异性的。这样可以更真实地描述湍流边界层中的流向涡。要指定与 Jarrin 公式 (7.1) 中 $\sigma_{ij}$值相对应的长度尺度，请使用 L_EDDY_IJ(3,3)。下面是一个涡长尺度和雷诺应力分量随机值的示例：

```fortran
&VENT XB=... , SURF_ID='WIND', N_EDDY=500,
    L_EDDY_IJ(1,1)=21., L_EDDY_IJ(1,2)=6.22, L_EDDY_IJ(1,3)=4.23
    L_EDDY_IJ(2,1)=2.35, L_EDDY_IJ(2,2)=5.66, L_EDDY_IJ(2,3)=2.50
    L_EDDY_IJ(3,1)=5.42, L_EDDY_IJ(3,2)=0.78, L_EDDY_IJ(3,3)=1.01
    REYNOLDS_STRESS(1,1)=2.16, REYNOLDS_STRESS(1,2)=0., REYNOLDS_STRESS(1,3)=-0.47
    REYNOLDS_STRESS(2,1)=0., REYNOLDS_STRESS(2,2)=1.53, REYNOLDS_STRESS(2,3)=0.
    REYNOLDS_STRESS(3,1)=-0.47, REYNOLDS_STRESS(3,2)=0., REYNOLDS_STRESS(3,3)=4.259 /
```

**Synthetic Turbulence at OPEN Boundaries**

对于风模拟（见第 16.2 节），可能有必要增加一定程度的流入湍流，以便在不大幅增加计算域大小的情况下与大气条件相匹配。可以在 "OPEN "边界的 VENT 线上调用 Jarrin 的合成涡流法[^19]。该方法应与 WIND 线结合使用，以指定平均风场。例如：

```fortran
&WIND SPEED=10, DIRECTION=270, ... /
&VENT DB='XMIN', SURF_ID='OPEN', N_EDDY=500, L_EDDY=3, VEL_RMS=1 /
```

图 10.4 显示了一个示范案例（`sem_open_wind.fds`）的结果。根据莫宁-奥布霍夫曲线，地面温度设置为 20 ℃，环境温度设置为 19.18℃。入口处的均方根速度波动设为 1 m/s。横向边界为 "PERIODIC"。流入、流出和顶部边界条件设置为 "OPEN"。请注意，针对 WIND 开发了一种特殊的 OPEN 边界条件，FDS 技术指南对此进行了讨论。

![image-20240617210212591](..\FDS中钠燃烧模型添加.assets\image-20240617210212591.png)

#### Random Mass Flux Variation

目前合成涡流法的实施不允许在 SURF 线上定义质量通量的变化。例如，参数 HRRPUA 和 MASS_FLUX 遵循用户指定的时间历史，不包括随机波动。不过，您可以使用参数 MASS_FLUX_VAR 指定质量通量变化。例如，如果您希望单位面积 100 kW/m2 的热释放率变化率为 10%，则使用：

```fortran'
&SURF ID='burner', HRRPUA=100., MASS_FLUX_VAR=0.1 /
```

使用边界文件输出量“MASS FLUX”可能有助于可视化变化。例如,

```fortran
&BNDF QUANTITY='MASS FLUX', CELL_CENTERED=T /
```



### GEOM (Unstructured Geometry Parameters)

| 可输入参数             | 类型                      | 描述           | 单位 | 默认          |
| ---------------------- | ------------------------- | -------------- | ---- | ------------- |
| BINARY_FILE            | Character                 | Section 7.3.9  |      | ’null’        |
| BNDF_GEOM              | Logical                   | Section 22.5   |      | T             |
| CELL_BLOCK_IOR         | Integer                   | Section 7.3.10 |      | 0             |
| CELL_BLOCK_ORIENTATION | Real Triplet              | Section 7.3.10 |      | 0.0,0.0,0.0   |
| COLOR                  | Character                 | Section 7.5    |      | ’null’        |
| CYLINDER_LENGTH        | Real                      | Section 7.3.6  | m    |               |
| CYLINDER_RADIUS        | Real                      | Section 7.3.6  | m    |               |
| CYLINDER_ORIGIN        | Real Triplet              | Section 7.3.6  | m    |               |
| CYLINDER_AXIS          | Real Triplet              | Section 7.3.6  |      |               |
| CYLINDER_NSEG_AXIS     | Integer                   | Section 7.3.6  |      |               |
| CYLINDER_NSEG_THETA    | Integer                   | Section 7.3.6  |      |               |
| EXTEND_TERRAIN         | Logical                   | Section 7.3.6  |      | F             |
| EXTRUDE                | Real                      | Section 7.3.6  | m    |               |
| FACES                  | Array of Integer Triplets | Section 7.3    |      |               |
| ID                     | Character                 | Section 7.3    |      | ’geom’_#      |
| IJK                    | Integer Triplet           | Section 7.3.6  |      | 0,0,0         |
| IS_TERRAIN             | Logical                   | Section 7.3.6  |      | F             |
| MOVE_ID                | Character                 | Section 7.3.8  |      | ’null’        |
| N_LAT                  | Integer                   | Section 7.3.6  |      | 0             |
| N_LEVELS               | Integer                   | Section 7.3.6  |      | 0             |
| N_LONG                 | Integer                   | Section 7.3.6  |      | 0             |
| POLY                   | Integer Array             | Section 7.3.6  |      |               |
| RGB(3)                 | Integer Triplet           | Section 7.5    |      |               |
| SPHERE_ORIGIN          | Real Triplet              | Section 7.3.6  | m    |               |
| SPHERE_RADIUS          | Real                      | Section 7.3.6  | m    |               |
| SPHERE_TYPE            | Integer                   | Section 7.3.6  |      |               |
| SURF_ID                | Character                 | Section 7.3    |      | ’INERT’       |
| SURF_ID6(6)            | Character Sextuplet       | Section 7.2.1  |      |               |
| SURF_IDS(3)            | Character Triplet         | Section 7.2.1  |      |               |
| TEXTURE_MAPPING        | Character                 | Section 7.5.2  |      | ’RECTANGULAR’ |
| TEXTURE_ORIGIN         | Real Triplet              | Section 7.5.2  | m    | 0.0,0.0,0.0   |
| TEXTURE_SCALE          | Real                      | Section 7.5.2  |      | 1.0           |
| TRANSPARENCY           | Real                      | Section 7.5    |      | 1.0           |
| VERTS                  | Array of Real Triplets    | Section 7.3    | m    |               |
| XB(6)                  | Real Array                | Section 7.3.6  | m    |               |
| ZMIN                   | Real                      | Section 7.3.6  | m    |               |
| ZVALS                  | Real Array                | Section 7.3.6  | m    |               |
| ZVAL_HORIZON           | Real                      | Section 7.3.6  | m    |               |

命名表 GEOM 描述了一个或多个**非结构化封闭几何曲面**，这些曲面包围了流体域的实体部分。这些曲面由一系列三角形面组成，其中每个三角形面由三个顶点组成。**用户可以为每个面指定特定的边界条件**。

#### My First Geometry

为了让您熟悉新的几何特征，我们允许将 OBST 命名列表的某些参数应用于 GEOM。因此，根据本节末尾列出的限制（请参阅第 7.3.11 节），您应该可以使用 OBST 建立的案例，只需将其替换为 GEOM 即可开始使用非结构化几何体。例如，如果您的燃烧器是这样创建的：

```fortran
&OBST XB=-1,1,-1,1,0,0.5, SURF_IDS='FIRE','INERT','INERT' /
```

可以替换为：

```fortran
&GEOM XB=-1,1,-1,1,0,0.5, SURF_IDS='FIRE','INERT','INERT' /
```

此外，GEOM可以使用第7.3.8节中讨论的MOVE线进行转换。

#### Unstructured Geometry Basics

给出了一个简单的非结构化固体的例子：

```fortran
&GEOM ID='My Solid'
	SURF_ID='FIRE','INERT'
    VERTS= -1.0, -1.0, 0.0,
        1.0, -1.0, 0.0,
        0.0, 1.0, 0.0,
        0.0, 0.0, 1.0,
    FACES= 1,3,2, 2,
        1,4,3, 1,
        3,4,2, 1,
        2,4,1, 0 /
```

ID 指定名称 "My Solid"，VERTS 指定每个顶点的坐标（x1,y1,z1; x2,y2,z2, ...），FACES 定义每个三角形面--三个顶点和一个边界条件索引： (v1,v2,v3,b). <font color=red>**顶点索引的范围从 1 到 VERTS 中列出的顶点数量。三个顶点的顺序决定了三角形的哪一面朝外**。从外部观察，**每个三角形的顶点应按照右手定则惯例逆时针排序**</font>。

**边界条件索引 b 的范围从 0 到 SURF_ID 中的条目数。**b = 0 应用默认边界条件。在上面的示例中，第一个面的索引 b = 2 对应于 "INERT"，第二个和第三个面的索引 b = 1 对应于 "FIRE"，第四个面对应于默认值。

#### Triangulated Surfaces Quality

为了使 FDS 能够从流体域的其他部分正确检测出体积的实体部分，在开始时要对三角化曲面的质量进行一些测试。FDS 对每个 GEOM namelist 的顶点和面集合执行以下条件：

1. 每个顶点必须是唯一的，由边共享，是唯一成型曲面的一部分，因此其相邻的面环理论上可以连续变形为圆盘：符合这些条件的顶点称为非退化顶点和流形顶点。好顶点和坏顶点的例子见**图 7.3**。
2. 连接顶点的每条边的长度必须不为零，而且必须始终由恰好两个面共享。符合这些条件的边称为**非退化边和流形边**。请参见**图 7.4** 中好边和坏边的示例。
3. 每个面不能与其他面相交，且面积必须不为零；这样的面称为非相交面和非退化面。
4. 如**图 7.1** 所示，面的顶点排序应使相邻面的法线向外一致。
5. 每个 GEOM 命名列表可定义一个或多个不同的体块（非连接体块），**这些体块不应 相交或自相交**。请参见**图 7.7** 中的不良相交几何体示例。

如果遵守了前面的条件，就可以得到一个成型的 GEOM 命名列表，它代表了一个或多个封闭的、流形的、可定向的、不相交的三角形曲面，这些曲面包围着定义明确的体量。**图 7.2** 展示了一个成形良好的三角形曲面。

每当对这些条件的其中一项检查失败时，FDS 就会输出一条错误信息，说明问题及其在域中的位置。例如：

```fortran
ERROR: GEOM ID='Cube': Non manifold geometry at edge: ...
```



![image-20240618142336379](..\FDS中钠燃烧模型添加.assets\image-20240618142336379.png)

![image-20240618142356314](..\FDS中钠燃烧模型添加.assets\image-20240618142356314.png)

![image-20240618142410891](..\FDS中钠燃烧模型添加.assets\image-20240618142410891.png)

![image-20240618142422343](..\FDS中钠燃烧模型添加.assets\image-20240618142422343.png)

#### Intersections

GEOM 之间以及 GEOM 与其他 namelists 之间可能会发生几种类型的交叉：

- GEOM - GEOM 和 GEOM - OBST：每当发生这些类型的相交时，**FDS 都会尝试执行布尔运算，在尊重曲面边界条件的前提下将对象合并**。当一个几何体与另一个几何体相交时，用户尚未输入定义该交点的顶点和边。在一般情况下，**要辨别确切的交点可能非常复杂，因此我们采用了线性化方法**，通过在单元的笛卡尔面上定义的边来生成单元内的近似边界面。两个相交球体的示例如下**图 7.8** 所示。如果几何形状过于复杂，这一操作可能会失败。在这种情况下，单元格将是空的。建议用户尽可能在自己选择的预处理器中应用几何联合。
- GEOM - HOLE：目前没有交叉。

![image-20240618143501256](..\FDS中钠燃烧模型添加.assets\image-20240618143501256.png)

#### Coloring and Texture Maps

GEOM 对象的着色和纹理贴图的指定方法与 OBST 相同（见第 7.5 节）。

#### Self-Generated Geometries

GEOM 命名列表允许快速定义特定类型的几何对象，如使用 XB 的块体、使用 SPHERE_ORIGIN 和 SPHERE_RADIUS 的球体以及使用 ZVALS 的二维地形高程。FDS 会生成顶点和面，以表示这些对象，相当于使用 VERTS 和 FACES 所定义的对象。

**Blocks**

定义块的GEOM名称列表为：

```fortran
&GEOM ID='block'
    SURF_ID='S1'
    XB=0.0,1.0,0.0,1.0,0.0,1.0
/
```

其中，XB=xmin,xmax,ymin,ymax,zmin,zmax 定义了区块的最小和最大边界。XB 参数的使用方法与 OBST 或 VENT 行相同。通过指定 IJK 参数，可以将区块细化为多个部分。例如，IJK=8,6,4 将把图块沿 x 维分成 8 个部分，沿 y 维分成 6 个部分，沿 z 维分成 4 个部分。SURF_ID 参数将指定的边界条件分配给所有生成的面。与 OBST 类似，您也可以使用 SURF_IDS 和 SURF_ID6 列表指定曲面条件（见第 7.2.1 节）。

**Spheres**

一个定义了以 (0,0,0) 为中心、半径为 1 的球体的 GEOM 命名列表是这样指定的：

```fortran
&GEOM ID='sphere'
    SURF_ID='S1'
    SPHERE_ORIGIN=0.0,0.0,0.0, SPHERE_RADIUS=1.0
/
```

默认情况下，球体被离散化，因此每个面的大小与网格分辨率一致。我们可以指定一个 N_LEVELS 参数来定义球体被分割的次数。

**Cylinders**

GEOM 命名列表定义了一个圆柱体几何体，圆心位于 CYLINDER_ORIGIN=(0,0,0)，轴线 CYLINDER_AXIS = (1.,0,0)，长度 CYLINDER_LENGTH = 2.，半径 CYLINDER_RADIUS = 0.5。

```fortran
&GEOM ID='cylinder', SURF_ID='S1',
        CYLINDER_LENGTH=2.,
        CYLINDER_RADIUS=.5,
        CYLINDER_ORIGIN=0.,0.,0.,
        CYLINDER_AXIS=1.,0.,0.,
        CYLINDER_NSEG_AXIS=6,
        CYLINDER_NSEG_THETA=48 /
```

其中，圆柱体沿轴线分为 6 段，周长分为 48 段。关键字 SURF_ID 可用 SURF_IDS='S1'、'S2'、'S3'代替，其中字符串'S1'、'S2'、'S3'分别对应顶面、侧面和底面的表面 ID。

**2D Terrain Elevations**

定义2D地形高程的GEOM名称列表由：

```fortran
&GEOM ID='terrain'
    SURF_ID='S1'
    IJK=ivals,jvals, XB=xmin,xmax,ymin,ymax,
    EXTEND_TERRAIN=etlog, ZVAL_HORIZON=zvhr,
    ZVALS=...
/
```

其中 XB 定义了以（xmin,ymin）和（xmax,ymax）为边界的矩形区域，ZVALS 定义了该区域的高程数据。IJK 指定了该区域内每个维度的顶点数量。在本例中，ivals 值出现在 x 维度上，jval 值出现在 y 维度上。ZVALS 关键字用于指定每个 (x,y) 位置的标高。在 ZVALS 关键字后指定的高程数据按行主次顺序排列。第一行包含从 xmin 到 xmax 的 ymin 位置上的 ivals 高程值。同样，最后一行包含 ymax 位置从 xmin 到 xmax 的 ivals 高程值。海拔数据有 jvals 行和 ivals 列。可选字段 EXTEND_TERRAIN 和 ZVAL_HORIZON 的使用形式如下。如果计算域的设置大于 XB 定义的地形补丁，从而完全包含地形，则设置 EXTEND_TERRAIN=T 可以将地形扩展到域边界。这对于减少计算中的边界效应很有帮助。此外，如果在 GEOM 行上设置了实数 ZVAL_HORIZON，那么在扩展域时，域边界将使用该标高。与块体和球体一样，FDS 使用这些关键字提供的信息来构造顶点和三角形面。几何体的底面标高（仅用于 Smokeview 可视化目的）可通过参数 ZMIN 设置。

此外，还可以指定地形几何图形，定义一个从顶部看具有凸形规则边界的三角剖面图。该三角剖面将代表所关注的地形，并定义地形 GEOM 的顶部边界。地形表面由 VERTS 和 FACES 指定，如同基本几何体（第 7.3.2 节），字段 IS_TERRAIN 需设置为 T，以便 FDS 知道这是一个地形非结构化表面。每个面的曲面类型的指定方式与基本几何体相同。此外，还可以使用 EXTEND_TERRAIN 逻辑。

**Geometries Extruded From Simple Planar Polygons**

在这种情况下，可以定义一个几何体，指定 VERTS、连接性 POLY 和挤出距离 EXTRUDE。例如：

```fortran
&GEOM ID='ExtPoly', SURF_ID='Poly1',
VERTS =
    -1.0, -1.0, 1.0,
    0.5, -1.0, 1.75,
    1.0, -1.0, 2.0,
    0.0, 0.0, 1.5,
    1.0, 1.0, 2.0,
    -1.0, 1.0, 1.0,
POLY = 1, 2, 4, 3, 5, 6,
EXTRUDE=0.5 /
```

POLY 所定义的多边形必须简单、非退化（无线段交叉、无重复顶点），且所有线段必须位于三维空间的同一平面上。它最多可以有 1000 个顶点。EXTRUDE 的值可以是正或负的实数，但不能为零。可以通过 SURF_IDS 字段提供单一曲面 ID 或顶面、侧面和底面 ID，方法与第 7.3.6 节中的圆柱体相同。请注意，SURF_IDS 中的底面总是指在 POLY 中定义的多边形，挤出操作就是从这里开始的。

#### Generating Complex Geometries

生成格式良好的复杂几何图形是一个耗时且容易出错的过程。FDS-SMV 社区提供了多个第三方预处理工具，**用于将 CAD 文件自动转换为 GEOM 命名列表**。

这些工具应始终对三角化曲面进行质量检查，并生成格式良好的 GEOM 命名列表。<font color=red>这些工具的链接可在项目主页 https://pages.nist.gov/fds-smv/ 的 "**Third-Party Tools and Training** "下找到</font>（不过很多都没用了:sob:）。

#### Transforming Objects

几何图形可以平移、旋转和缩放。例如，在下面的GEOM命名列表中，

```fortran
&MOVE ID='ChairMove', AXIS=...,...,..., ROTATION_ANGLE=..., DX=, /
&GEOM ID='chair'
    SURF_ID='woodSID','apholsterySID',
    VERTS=X1,Y1,Z1,...,XM,YM,ZM,
    FACES=F1_1,F1_2,F1_3,F1_SID,...,FN_1,FN_2,FN_3,FN_SID
    MOVE_ID='ChairMove'
/
```

椅子对象的平移和旋转是通过引用 MOVE 命名列表进行的，其定义和解释见第 11.4 节。

#### Reading Geometry Node Locations And Connectivity Data From Binary

如果几何图形有大量节点和曲面三角形，则可以通过从 FDS 生成的二进制文件中读取这些数据来提高设置效率。该二进制文件可在仅设置模式（T_END=0.0）下运行情况下获得。请看上一节中定义的椅子几何图形。当 FDS 读取几何体时，XYZ 和面连接数据 FACES 会自动写入运行目录下名称为 CHID_GEOM_ID.bingeom 的二进制文件（此处 GEOM_ID="chair"）。如果没有提供 ID，二进制文件的名称将是 CHID_N_GEOM.beingom，其中 N_GEOM 是定义 FDS 输入文件中几何线出现顺序的数字。

然后，假设案例 ID 为 CHID="DiningRoom"，下次运行案例时，几何体行可以修改为：

```fortran
&GEOM ID='chair',
    SURF_ID='woodSID','apholsterySID',
    BINARY_FILE='DiningRoom_chair.bingeom',
    MOVE_ID='ChairMove' /
```

其中的 BINARY_FILE 指示 FDS 从二进制几何体文件中读取节点和面。请注意，我们删除了输入行中的 VERTS 和 FACES 阵列。这种加载大型几何体的方式避免了测试和读取 FDS 输入文件中与这些数组相关的所有行。<font color=red>**这种方法在使用并行文件系统的大型并行计算中特别有效**</font>。有关几何图形 I/O 二进制格式的更多信息，请参见第 27.19 节。如果使用与默认名称不同的名称，可以在 BINARY_FILE 字段中指定。也可以在 BINARY_FILE 字符串中添加位置目录。

地形也可以二进制格式读取和写入，在这种情况下，只记录其顶面三角测量。二进制文件包含其几何信息和地形类型，但如上图所示，必须在几何行中提供 SURF_ID 数组。如果需要扩展地形，EXTEND_TERRAIN 也需要同样的要求。二进制文件连接性中定义的曲面 ID 数量必须与 SURF_ID 中定义的曲面数量一致。

#### Handling Split Cells and Thin Geometries

非结构化几何算法目前的一个限制是，笛卡尔单元不能被薄几何体或角分割，这样就有可能在一个笛卡尔单元内产生两个背景压力区。默认情况下，如果单元被薄几何体分割，FDS 将填充两个不相连的体积中较小的一个。但是，您可能希望让一侧完全平滑，而让另一侧吸收几何体的变化。例如，您希望隧道或天花板的内壁光滑，但对问题的外部部分并不太在意。在这种情况下，您可以通过在 GEOM 行中设置 CELL_BLOCK_IOR 或 CELL_BLOCK_ORIENTATION 来控制几何体的哪一边被填充。前者是一个表示笛卡尔轴的整数，后者允许指定任何方向的矢量。图 7.9 举例说明了这一功能的工作原理。目前，这一功能仅限于 IOR 可以定义方向的几何图形。例如，这对空心球体无效。对于地形几何图形，默认值为 CELL_BLOCK_IOR=-3。

![image-20240618184136928](..\FDS中钠燃烧模型添加.assets\image-20240618184136928.png)

#### GEOM Limitations

- 目前，GEOM namelists 没有控制逻辑。也就是说，无法添加或删除 GEOM。
- MULT 结构目前无法应用于几何图形。
- 薄几何图形和边角不能分割单元，必须封住一边。参见第 7.3.10 节。
- 仅允许在单个网面上使用外部衬底。如果背面在另一个网格上，背衬将被设置为 VOID（静音）。
- **VENT 不能应用于 GEOM**。表面属性必须通过 SURF_ID 逐个面应用。
- 无VENT意味着HVAC不能应用于 GEOM 表面。这已列入我们的优先事项，并将在未来推出。
- 无法在几何图形中施加切向速度。NO_SLIP 条件假定切向速度为零。允许这一功能也是开发工作的重点。
- **GEOM 中没有三维传热和 BURN_AWAY**。
- HOLE 命名列表不适用于 GEOM。
- 不建议使用子网格几何图形（小于一个网格单元）。它们目前不包括在动量方程的处理中。同样，间隙也应定义为一个单元格大小的厚度。
- 不建议使用比笛卡尔网格单元小得多的三角形面。与笛卡尔网格单元相比，每个面的边界条件分配分辨率过低。
- 粒子会与几何体相互作用，但由于表面张力的作用，粒子不会在几何体下方流动。也就是说，如果粒子落在球体顶部，一旦到达赤道，就会直接落到地面上。它们将表现为颗粒，而不是液滴。
- 小心烟尘沉积。虽然几何图形具有沉积功能，但尚未经过全面测试。

#### The Big Picture, Run Time, and Accuracy

**Big picture** FDS 中复杂几何图形的长期目标是实现与建筑信息管理 (BIM) 模型和复杂 CAD 几何图形相对无缝的工作流程。然而，过去几年中，我们一直在开发一种保守而稳定的公式。为此，我们不得不暂时放弃浸没边界法，转而采用需要非结构化压力求解器（ULMAT；见第 21.1 节）的切割单元方案。

**Run time** 在使用复杂几何体时，您可能会发现运行时间变慢，原因有两个。首先，设置时间会明显变慢，尤其是在未从二进制文件导入几何体的情况下（见第 7.3.9 节）。这是不可避免的，因为识别和处理切割单元非常耗时。其次，使用 ULMAT 虽然在实体边界处更为精确，但比 FFT 压力求解器（每次迭代）更慢。此外，随着网格大小的增加，ULMAT 的速度也会逐渐变慢。因此，在较大的情况下使用 ULMAT 时，必须将域分解为小于 150,000 个单元（约 $53^3$ 个）的网格。

**Accuracy** 使用曲线几何图形的理由应该是笛卡尔几何图形的精度不够。例如，您可能有一个倾斜的天花板或房间的某些细节需要更高的逼真度。如果需要更高的精度，通常也意味着需要更好的网格分辨率。几何图形和笛卡尔网格的保真度要保持一致。如果笛卡尔网格过粗，就不要指望高度精细的几何图形会带来更好的结果。

### HVAC (HVAC System Definition)

| 可输入参数              | 类型          | 描述                            | 单位       | 默认      |
| ----------------------- | ------------- | ------------------------------- | ---------- | --------- |
| AIRCOIL_ID              | Character     | Section 10.2.1                  |            |           |
| AMBIENT                 | Logical       | Section 10.2.3                  |            | F         |
| AREA                    | Real          | Section 10.2.1                  | $m^2$      |           |
| CLEAN_LOSS              | Real          | Section 10.2.5                  |            |           |
| COOLANT_MASS_FLOW       | Real          | Section 10.2.6                  | kg/s       |           |
| COOLANT_SPECIFIC_HEAT   | Real          | Section 10.2.6                  | $kJ/(kgK)$ |           |
| COOLANT_TEMPERATURE     | Real          | Section 10.2.6                  | ℃          |           |
| CTRL_ID                 | Character     | Sections 10.2.1, 10.2.4, 10.2.5 |            |           |
| DAMPER                  | Logical       | Sections 10.2.1, 10.2.2         |            | F         |
| DEVC_ID                 | Character     | Sections 10.2.1, 10.2.4, 10.2.5 |            |           |
| DIAMETER                | Real          | Section 10.2.1                  | m          |           |
| DISCHARGE_COEFFICIENT   | Real          | Section 10.3.2                  |            | 1.        |
| DUCT_ID                 | Char. Array   | Section 10.2.3                  |            |           |
| EFFICIENCY              | Real Array    | Sections 10.2.5, 10.2.6         |            | 1.0       |
| FAN_ID                  | Character     | Section 10.2.1                  |            |           |
| FILTER_ID               | Character     | Section 10.2.3                  |            |           |
| FIXED_Q                 | Real          | Section 10.2.6                  | kW         |           |
| ID                      | Character     | Section 10.2                    |            |           |
| LEAK_ENTHALPY           | Logical       | Section 10.3.2                  |            | F         |
| LEAK_PRESSURE_EXPONENT  | Real          | Section 10.3.2                  |            | 0.5       |
| LEAK_REFERENCE_PRESSURE | Real          | Section 10.3.2                  | Pa         | 4         |
| LENGTH                  | Real          | Section 10.2.1                  | m          |           |
| LOADING                 | Real Array    | Section 10.2.5                  | kg         | 0.0       |
| LOADING_MULTIPLIER      | Real Array    | Section 10.2.5                  | 1/kg       | 1.0       |
| LOSS                    | Real Array    | Sections 10.2.1 – 10.2.5        |            | 0.0       |
| MASS_FLOW               | Real          | Section 10.2.1                  | kg/s       |           |
| MAX_FLOW                | Real          | Section 10.2.4                  | $m^3/s$    |           |
| MAX_PRESSURE            | Real          | Section 10.2.4                  | Pa         |           |
| N_CELLS                 | Integer       | Section 10.2.8                  |            | 10×LENGTH |
| NETWORK_ID              | Character     | Section 10.2                    |            |           |
| NODE_ID                 | Char. Doublet | Section 10.2.1                  |            |           |
| PERIMETER               | Real          | Section 10.2.1                  | m          |           |
| QUANTITY                | Char. Array   | Sections 22.16                  |            |           |
| QUANTITY_SPEC_ID        | Char. Array   | Sections 22.16                  |            |           |
| RAMP_ID                 | Character     | Sections 10.2.1, 10.2.5, 10.2.4 |            |           |
| RAMP_LOSS               | Character     | Sections 10.2.1, 10.2.2         |            |           |
| REVERSE                 | Logical       | Section 10.2.1                  |            | F         |
| ROUND                   | Logical       | Section 10.2.1                  |            | T         |
| ROUGHNESS               | Real          | Section 10.2.1                  | m          | 0.0       |
| SPEC_ID                 | Char. Array   | Section 10.2.5                  |            |           |
| SQUARE                  | Logical       | Section 10.2.1                  |            | T         |
| TAU_AC                  | Real          | Section 10.2.6                  | s          | 1.0       |
| TAU_FAN                 | Real          | Section 10.2.4                  | s          | 1.0       |
| TAU_VF                  | Real          | Section 10.2.1                  | s          | 1.0       |
| TRANSPORT_PARTICLES     | Logical       | Section 10.3.2                  | s          | F         |
| TYPE_ID                 | Character     | Section 10.2                    |            |           |
| VENT_ID                 | Character     | Section 10.2.3                  |            |           |
| VENT2_ID                | Character     | Section 10.3.2                  |            |           |
| VOLUME_FLOW             | Real          | Section 10.2.1, 10.2.4          | $m^3/s$    |           |
| WAYPOINTS               | Real Array    | Section 10.2.1                  | m          |           |
| XYZ                     | Real Triplet  | Section 10.2.3                  | m          | 0.0       |

在某些情况下，简单地定义固定流量和固定物种边界条件不足以模拟HVAC(采暖、通风和空调)系统的行为。如果需要通过管道网络传输热量和燃烧产物，或者需要充分考虑火灾导致的隔间增压对管道网络流量的影响，则可以使用耦合HVAC网络求解器。该求解器计算流经管道网络的流量，该网络被描述为管道段和节点的映射，其中节点是两个或多个管道的连接处（例如三通），或者是管道段与 FDS 计算域的连接处。有关消防安全工程中耦合混合建模的更多信息，感兴趣的读者可参考 Ralph 等人[^18]的文献综述。

默认情况下，HVAC求解器不允许管道网络中的大量存储(即，在一个时间步长期间进入的内容，在一个时间步长期间流出)。但是，如果为HVAC管道设置N_CELLS，则HVAC求解器将考虑大量存储，并将计算通过管道的瞬态物种和能量传输。

HVAC组件，如风扇和二元阻尼器(全开或全关)可以包括在HVAC网络和FDS控制功能都耦合在一起。风扇有三种型号可供使用。

如果输入文件中存在HVAC名称列表组，则调用HVAC求解器。HVAC网络通过为管道提供输入、管节点、以及系统中存在的任何风扇，阻尼器，过滤器或加热和卷曲线圈来定义。此外，您**必须定义HVAC网络加入计算域的位置**。HVAC组件的基本语法是：

```fortran
&HVAC TYPE_ID='componenttype', ID='componentname', ... /
```

TYPE_ID是一个字符串，表示名称列表组正在定义的组件类型。可以是DUCT, NODE, FAN, FILTER, AIRCOIL, or LEAK（参考10.3.2节）

ID是一个字符串，为组件提供一个名称。**名称在该类型的所有其他组件中必须是唯一的**；但是，不同类型的组件可以使用相同的名称(例如，一个管道和一个节点可以具有相同的名称，但两个管道不能)。

在样本案例的HVAC文件夹中给出了一些简单HVAC系统的示例，并在FDS验证指南中进行了讨论。

如技术参考手册所述，**HVAC压力解决方案不直接耦合到FDS压力解决方案**。相反，在HVAC通风口的壁面边界条件下存在隐式耦合。有时这会导致稳定性问题。有两种方法可以尝试解决这个问题。

第一个方法是MISC行上的关键字**HVAC_PRES_RELAX，默认值为1.0**。在每个时间步骤中，FDS 都会评估 FDS 域与HVAC网络连接节点相邻的 FDS 气体单元中的平均压力，即 $P_{FDS}$。时间步$n+1$的压力$P^{n+1}_{FDS}$表示为：
$$
P_{node}^{n+1}=P_{node}^{n}\mathrm{(1-HVAC{\_}PRES{\_}RELAX)}+P_{FDS}^{n+1}\mathrm{HVAC{\_}PRES{\_}RELAX}
$$
将此参数设置得更接近于0，可以降低HVAC解决方案对FDS域中短暂、瞬态压力变化的灵敏度；然而，这样做也会导致HVAC解决方案延迟更长时间的压力变化。

第二种方法是在 MISC 行设置关键字 **HVAC_LOCAL_PRESSURE**。设置后，FDS 将使用通风口处的ZONE压力加上通风口法线流的滞止压力来确定连接到 FDS 域的节点的压力边界条件，而不是使用ZONE压力加上根据 H 的本地值得出的压力。

#### HVAC Duct Parameters

指定管道的典型输入行如下所示：

```fortran
&HVAC TYPE_ID='DUCT', ID='ductname', NODE_ID='node 1','node 2', AREA=3.14,
    LOSS=1.,1., LENGTH=2., ROUGHNESS=0.001, FAN_ID='fan 1', DEVC_ID='device 1' /
```

或者，如果您使用HVAC质量输运，如下所示：

```fortran
&HVAC TYPE_ID='DUCT', ID='ductname', NODE_ID='node 1','node 2', AREA=3.14,
    LOSS=1.,1., LENGTH=2., ROUGHNESS=0.001, FAN_ID='fan 1', DEVC_ID='device 1',
    N_CELLS=200 /
```

其中：

“AIRCOIL_ID”为风道内盘管的ID。盘管的运行可以通过装置或控制功能来控制。

AREA是管道的横截面积，单位为$m^2$.

DAMPER是指示风道中存在阻尼器的逻辑参数。阻尼器的状态由装置或控制功能控制(见第10.2.2节)。

DIAMETER为管道直径，单位为m。

“DEVC_ID”为风道内阻尼器、风机或风盘管所在DEVC的ID。另一个选项是CTRL_ID。

FAN_ID是管道中风机的ID。代替指定FAN_ID，您可以指定风管体积流率VOLUME_FLOW（$m^3/s$）。风机的运行可以通过装置或控制功能来控制。

LENGTH是管道的长度（m）。如果没有指定，它将自动计算为管道端点的XYZ之间的差，或者如果定义了WAYPOINTS，则作为端点之间沿路径的距离计算。

LOSS是一对实数，给出正向和反向无因次“小损失”损失系数($K_{minor}$)在管道中。较小的损失是通过三通、阀门和弯头等部件造成的压力损失。不过，您也可以使用 LOSS 表示墙壁摩擦损失，在这种情况下，请确保不设置 ROUGHNESS，这样HVAC求解器就不会计算摩擦系数。**正向**定义为从NODE_ID中列出的第一个节点到NODE_ID中列出的第二个节点的流。

MASS_FLOW是通过管道的固定质量流量(kg/s)。**不要为相同的管道同时指定MASS_FLOW和VOLUME_FLOW**。可以使用特征时间TAU_VF来定义tanh（TAU_VF>0）或$t^2$（TAU_VF<0）使流量随时间变化，或使用RAMP_ID指定随时间变化的流动。**只有当上游节点密度在求解过程中不会发生变化时，才应该指定MASS_FLOW**。

N_CELLS允许HVAC质量输运。它定义了离散管道中的单元数量。

NETWORK_ID用于烟雾视图可视化。在烟雾视图中，所有具有共同NETWORK_ID的管道和节点都可以作为一个组被选择或取消选择。如果没有给出值，则管道将被放置在未赋值的网络。

NODE_ID给出管道段两端节点的ID。管道中的正速度定义为从第一个节点流向第二个节点的流量。

PERIMETER与AREA一起用于指定**非圆形截面的管道**。

RAMP_LOSS如果指定了该RAMP，则该RAMP是LOSS的乘数。

REVERSE是一个逻辑参数，T表示指定的FAN_ID从第二个节点吹到第一个节点。REVERSE对VOLUME_FLOW或MASS_FLOW作为管道输入没有影响。如果风道指定了VOLUME_FLOW或MASS_FLOW，且需要逆流，则将输入的符号改为负。

ROUGHNESS是以m为单位的风管的绝对粗糙度，用于计算风管的摩擦系数。如果未设置ROUGHNESS，则HVAC求解器将不计算摩擦系数，并且壁面摩擦将为零-如果是这种情况，您可能希望在LOSS中考虑壁面摩擦损失。“完全光滑”的管道和圆管仍然有壁面损耗，**因此将粗糙度设置为零将告诉HVAC求解器计算最小摩擦系数(非零)-这与不设置粗糙度不同**。

ROUND表示圆形管道的标志。

SQUARE表示方形管道的标志。

VOLUME_FLOW是管道固定的流量（$m^3/s$）。只能指定MASS_FLOW或VOLUME_FLOW中的一个。可以使用特征时间TAU_VF来定义tanh（TAU_VF>0）或$t^2$（TAU_VF<0）使流量随时间变化，或使用RAMP_ID指定随时间变化的流动。VOLUME_FLOW不能被设备或控制功能控制。不过，这可以通过使用恒流量FAN来实现。

WAYPOINTS是单位为m的坐标数组，它定义了管道所经过的路径。目前这只用于HVAC网络的烟景可视化。最多可以定义30个WAYPOINTS。例如：WAYPOINTS(1,1:3)=1,1,1, WAYPOINTS(2,1:3)=2,2,2作为管道输入的一部分意味着管道从第一个节点开始，然后到达点(1,1,1)，然后到达点(2,2,2)，最后到达第二个节点。

注意:**风管只能输入AIRCOIL_ID、DAMPER或FAN_ID中的一个**。还请注意，如果指定了其中一个，但没有提供设备或控制功能，则将假设该项目处于on或open状态。

如果设置了ROUND或SQUARE，则只能设置AREA、DIAMETER或PERIMETER中的一个。否则需要三个中的两个。

为了减少HVAC求解器的计算成本，应将管道视为连接两个必须定义为节点的项目的任何长度的管道(即，连接到FDS域，过滤器或两个以上管道连接的位置)。也就是说，风管应该被认为是HVAC系统的任何部分，在给定的时间点，流动只能在一个方向上(流动可以随着时间的推移而逆转方向)。例如，图10.5的顶部显示了HVAC系统的一个部分，其中三通的流量经过一个膨胀接头、两个弯头、一个膨胀接头和一段直管，然后作为FDS域的连接终止。

![image-20240617151844874](..\FDS中钠燃烧模型添加.assets\image-20240617151844874.png)

这可以输入为每个单独的配件或管道及其相关的面积和损失，如图中间所示；然而，这将导致5个管道段(每个组件一个)与6个节点连接，产生11个参数(5个速度和6个压力)，必须求解。这是不需要的，因为无论流量是在管道的任何一部分，相同的流量存在于所有其他部分；因此，任何段的速度都可以通过面积比求出来，$v_1/v_2=A_2/A_1$。由于流动损失与速度的平方成正比，因此可以使用管道的总长度和有效面积(Aeff)或直径来构造等效的管道。通过将风管的所有拟合损失($K_{minor}$)相加，可将风管各节段的压力损失折算为单个有效损失(Keff)，如下所示:
$$
K_{\mathrm{eff}}=\sum_i(K_{\mathrm{minor}})_i\left(\frac{A_{\mathrm{eff}}}{A_i}\right)^2
$$
其中i是拟合，Ai是与拟合损失相关的面积。

#### HVAC Dampers

阻尼器可以用两种方式建模。

第一种方法是简单的二元(有流或无流)阻尼器。这可以通过添加关键字DAMPER以及CTRL_ID或DEVC_ID来放置在管道中。当控制或装置为T时，阻尼器将打开，当F时，阻尼器将关闭并阻塞100%的风道面积。下面的例子显示了一个带有阻尼器的管道，阻尼器与DEVC相连，DEVC在10秒关闭阻尼器。

```fortran
&HVAC TYPE_ID='DUCT',ID='EXHAUST 2',NODE_ID='TEE','EXHAUST 2',AREA=0.01,
    LENGTH=1.0,LOSS=0,0,DAMPER=T,DEVC_ID='TIMER'/
&DEVC QUANTITY='TIME',ID='TIMER',SETPOINT=10,INITIAL_STATE=T,XYZ=0,0,0/
```

为了使阻尼器处于关闭状态，然后在稍后的时间打开，DEVC的INITIAL_STATE不应设置为T。下面的例子显示了一个带有阻尼器的管道，它开始关闭，然后在10秒打开。

```fortran
&HVAC TYPE_ID='DUCT',ID='EXHAUST 2',NODE_ID='TEE','EXHAUST 2',AREA=0.01,
    LENGTH=1.0,LOSS=0,0,DAMPER=T,DEVC_ID='TIMER'/
&DEVC QUANTITY='TIME',ID='TIMER',SETPOINT=10,XYZ=0,0,0/
```

第二种方法是为管道指定RAMP_LOSS。这种方法将管道的LOSS数组乘以RAMP的输出。<font color=red>**这允许有泄漏的阻尼器和/或具有可变位置的阻尼器，而不是全开或全关。**</font>下面显示了一个例子，其中管道中的损耗在10秒时从1,1变化到11秒时的2000,2000。

```fortran
&HVAC TYPE_ID='DUCT',ID='EXHAUST 2',NODE_ID='TEE','EXHAUST 2',AREA=0.01,
    LENGTH=1.0,LOSS=1,1,RAMP_LOSS='LOSS RAMP'/
&RAMP ID='LOSS RAMP',T=10,F=1/
&RAMP ID='LOSS RAMP',T=11,F=2000/
```

#### HVAC Node Parameters

下面是三个示例管道节点输入，分别表示典型的T型连接(多个管道连接)、到FDS域的连接以及到FDS域外环境的连接。

```fortran
&HVAC TYPE_ID='NODE', ID='tee', DUCT_ID='duct 1','duct 2',..'duct n',
    LOSS=lossarray, XYZ=x,y,z /
&HVAC TYPE_ID='NODE', ID='FDS connection', DUCT_ID='duct 1', VENT_ID='vent',
    LOSS=enter,exit /
&HVAC TYPE_ID='NODE', ID='ambient', DUCT_ID='duct 1', LOSS=enter,exit,
    XYZ=x,y,z, AMBIENT=T /
```

其中：

AMBIENT是一个逻辑值。如果为T，则节点与环境相连(**即相当于SURF线上的OPEN边界条件**)。

DUCT_ID给出连接到节点的管道的ID。如果节点为AMBIENT或具有VENT_ID，则只允许一个管道。一个节点最多可连接10个管道。

FILTER_ID为ID提供了一个位于节点的过滤器。带有过滤器的节点必须有两个连接的管道。**这意味着过滤器不能位于环境节点、连接到VENT的节点或具有三个或更多管道的节点**。

LOSS是一个n × n的实数数组，表示节点的无因次损失系数。LOSS(I,J)为从风管I流向风管J的损失系数，以下游风管面积表示(参见10.2.1中关于如何调整面积变化的损失的讨论)。对于终端节点(例如，连接到环境或VENT的节点)，LOSS输入为一对数字，表示进入HVAC系统的流量和退出HVAC系统的流量的损耗系数。

NETWORK_ID用于烟雾视图可视化。在 Smokeview 中，可以将具有共同 NETWORK_ID 的所有管道和节点作为一个组来选择或取消选择。如果没有给定值，节点将被置于未指定网络中。

VENT_ID为节点连接到FDS计算域的VENT的名称。不应该具有两个相同VENT_ID的VENT。

XYZ是一个实数三元组，**表示节点的坐标**。**如果节点连接到FDS域，则不要指定XYZ**，因为FDS将把它作为VENT的质心计算。

**一个风管节点必须有两个或更多的风管连接到它**，或者它必须有AMBIENT=T或指定的VENT_ID。当将VENT定义为HVAC系统的组件时，必须将SURF_ID设置为' HVAC '，你必须设置VENT_ID。

允许HVAC系统的单个排气管道跨越多个网格；但是，整个排气口必须位于单一压力区内。

请注意，用于HVAC系统的VENT必须在整个模拟过程中存在。**VENT不应该有CTRL_ID或DEVC_ID**。

这也包括它所附着的固体表面；即，任何OBST所附的VENT也需要在整个模拟过程中存在。打开或关闭连接到HVAC系统的VENT，需要在连接到VENT的管道中安装一个阻尼器。

#### HVAC Fan Parameters

下面是FDS支持的三种风机的输入示例。

```fortran
&HVAC TYPE_ID='FAN', ID='constant volume', VOLUME_FLOW=1.0, LOSS=2./
&HVAC TYPE_ID='FAN', ID='quadratic', MAX_FLOW=1., MAX_PRESSURE=1000., LOSS=2. /
&HVAC TYPE_ID='FAN', ID='user fan curve', RAMP_ID='fan curve', LOSS=2. /
```

其中，

LOSS是风机不工作时流经风机的损失系数。FDS假定默认值为1。

MAX_FLOW为风机的最大体积流量，单位为$m^3/s$​。这个输入激活了一个二次风扇模型。取值必须大于0。

MAX_PRESSURE为风机失速压力，单位为Pa。这个输入激活了一个二次风扇模型。取值必须大于0。

RAMP_ID标识RAMP，该RAMP包含风机(Pa)与用户定义的风机曲线的体积流量($m^3/s$)的压降表。

TAU_FAN为风机定义tanh (TAU_FAN > 0)或$t^2$ ramp (TAU_FAN < 0)。这适用于由三种类型(恒定流量，二次型或用户定义的斜坡)的风机计算的流量。

VOLUME_FLOW为风机的固定体积流量，$m^3/s$。**如果您希望获得与时间相关的流量，请使用管道而非风机的 VOLUME_FLOW 输入**。

请注意，只能指定一组风扇模型输入（VOLUME_FLOW、RAMP_ID 或 MAX_FLOW + MAX_PRESSURE）。还要注意的是，FAN 定义的是一类风扇，而不是一个特定的风扇。因此，不止一个风道可以引用一个 FAN。

**Fan Curves**

在第 10.1 节中讨论了速度边界条件，其中风扇被简单地模拟为一个固体边界，**它可以吹出或吸入空气，与周围的压力场无关**。在暖通空调（HVAC）模型中，当使用 VOLUME_FLOW 指定风扇时，就会出现这种风扇建模方法。实际上，风机是根据安装在管道或歧管上的压降来运行的。一个非常简单的 "风机曲线 "如下所示：
$$
\dot{V}_{\mathrm{fan}}=\dot{V}_{\mathrm{max}}\mathrm{~sign}(\Delta p_{\mathrm{max}}-\Delta p)\sqrt{\frac{|\Delta p-\Delta p_{\mathrm{max}}|}{\Delta p_{\mathrm{max}}}}
$$
这个简单的“风扇曲线”是“二次”风扇模型，因为压力与体积流量的平方成正比。

无压差时的体积流量MAX_FLOW为$\dot{V}_{\mathrm{max}}$。压差$\Delta p=\Delta p_1-\Delta p_2$，表示下游室压差，或"zone”和上游。下标“1”表示下游，“2”表示上游。$\Delta p_{\mathrm{max}}$为风机可运行的最大压差，MAX_PRESSURE为正数。通过风扇的流量将从零压差时的$\dot{V}_{\mathrm{max}}$减小到$\Delta p_{\mathrm{max}}$时的$0 m^3/s$。如果压差超过这个值，空气将被迫向后通过风扇。如果下游压力变为负值，那么通过风机的体积流量就会增加超过MAX_FLOW。更复杂的风扇曲线可以通过定义RAMP来指定。在下面的示例输入中，每种类型指定一个风扇。VOLUME_FLOW为$10 m^3/s$的定容流量风机，MAX_FLUX=10,MAX_PRESSURE=500的二次型风机，以及RAMP设置增量为200pa的用户自定义风机二次型风机。

```fortran
&HVAC TYPE_ID='FAN', ID='constant volume', VOLUME_FLOW=10.0/
&HVAC TYPE_ID='FAN', ID='quadratic', MAX_FLOW=10., MAX_PRESSURE=500./
&HVAC TYPE_ID='FAN', ID='user fan curve', RAMP_ID='fan curve'/

&RAMP ID='fan curve',T=-10.00,F= 1000/
&RAMP ID='fan curve',T= -7.75,F= 800/
&RAMP ID='fan curve',T= -4.47,F= 600/
&RAMP ID='fan curve',T= 4.47,F= 400/
&RAMP ID='fan curve',T= 7.75,F= 200/
&RAMP ID='fan curve',T= 10.00,F= 0/
&RAMP ID='fan curve',T= 11.83,F= -200/
&RAMP ID='fan curve',T= 13.42,F= -400/
&RAMP ID='fan curve',T= 14.83,F= -600/
&RAMP ID='fan curve',T= 16.12,F= -800/
&RAMP ID='fan curve',T= 17.32,F=-1000/
```

图10.6显示了上述输入的风扇曲线。在验证指南中记录的`ashrae7`和`fan_test`示例案例中可以找到其他示例。

![image-20240617161701038](..\FDS中钠燃烧模型添加.assets\image-20240617161701038.png)

**Jet Fans**

风扇不必像电源或排气风扇那样安装在坚固的墙壁上。如果你只是想把气体吹向一个特定的方向，制造一个障碍物OBST，至少一个单元厚，并应用于一个简单的HVAC系统相关的VENT行上。这使得热的烟雾气体可以穿过障碍物，就像一个独立的风扇一样。参见示例案例`jet_fan.fds`。在火附近放置一个带百叶窗的风扇(对角线向下吹)的火焰(见图10.7)。

![image-20240617162031674](..\FDS中钠燃烧模型添加.assets\image-20240617162031674.png)

你也可以用四个平板在风扇周围做一个罩，形成一个短通道，把气体从一边吸进来，从另一边排出。代表风扇的障碍物可以放置在通道的中间(如果使用百叶窗风扇，则将风扇放置在通道的末端)。

**System Curves**

:question:HVAC系统可以用两条曲线来表征。一个，已经讨论过了，是风扇曲线，它描述了通过风扇的流量作为风扇上压头的函数。这是在最大压力下零流量和零压力下最大流量的曲线。第二个是系统曲线。这描述了HVAC系统中的流量如何随着风扇施加的压力的变化而变化。系统曲线说明了系统中的所有损失加上系统入口和出口的压力差。对于入口和出口压力相同的HVAC系统，系统曲线在零压力时流量为零，随着风扇压力的增加，流量也会增加。HVAC系统和风机的特定组合的工作点由这两条曲线的交点给出。

对于相对简单的HVAC网络，在任何给定的管道运行中只有一个风扇，并且网络进出口压力变化不大，FDS使用一种简单的方法来选择风扇压力，该方法基本上认为系统曲线与风扇曲线相反。对于更复杂的网络，FDS可以生成系统曲线。由于系统曲线取决于HVAC系统的具体配置(风扇和阻尼器的状态)以及系统入口和出口的压力，因此在每个时间步骤都要进行此操作。然后，通过找到该风扇曲线与该风扇系统曲线的交集来设置风扇的工作点(即，通过在风扇位置查找各种压力下HVAC系统中的流量建立的曲线)。这种方法显著地增加了HVAC求解器成本，因为它现在必须求解多个风机压力的系统曲线，确定工作点，然后执行用于壁面边界条件的HVAC解决方案。然而，由于HVAC求解器通常只占模拟总成本的很小一部分，因此增加的成本不应显著影响总体运行时间。

此方法通过在MISC行上设置HVAC_QFAN=T来打开。

#### HVAC Filter Parameters

**过滤器必须位于有两个连接管道的节点上**。过滤器不能位于环境节点、连接到排气口的节点或具有三个或更多管道的节点。过滤器的样例输入如下：

```fortran
&HVAC TYPE_ID='FILTER', ID='filter 1', LOADING=0., SPEC_ID='SOOT',
    EFFICIENCY=0.99, LOADING_MULTIPLIER=1, CLEAN_LOSS=2., LOSS=100./
```

其中，

AREA是与流量损失测量相关的面积，单位为$m^2$。通常这是过滤器的面积。如果没有提供，则使用两个附加风管面积的平均值。

CLEAN_LOSS是过滤器清洁(零负荷)时流过过滤器的无因次损失系数。

EFFICIENCY是从0到1的物种去除效率的数组，其中**0表示没有去除该物种，1表示完全过滤该物种**。使用SPEC_ID标识物种。

LOADING是一个数组，包含每个过滤物种的过滤器初始负载（千克）。

LOADING_MULTIPLIER 是一个物种乘数 Mi 的数组，用于在计算过滤器损耗系数时计算过滤器的总负载。

LOSS调用线性损耗系数模型，其中无量纲损耗系数 K 是总负载的线性函数，即$K_{\mathrm{FILTER}}=K_{\mathrm{CLEAN_LOSS}}+K_{\mathrm{LOSS}}\sum\left(L_{i}M_{i}\right)$，其中 Li 是物种负载，Mi 是乘数。只能指定 LOSS 或 RAMP_ID 中的一个。

RAMP_ID 用于标识包含过滤器压降表的 RAMP，压降表是总负载（上述 LOSS 定义中的求和项）的函数。只能指定 LOSS 或 RAMP_ID 中的一个。

SPEC_ID标识LOADING_MULTIPLIER和LOADING输入的跟踪物种。

过滤器输入示例如下。这些线条定义了一个过滤器，它能以 100% 的效率去除 PARTICULATE 物种。过滤器的初始损耗系数为 1，过滤器每捕获一千克 PARTICULATE，损耗系数就会增加 7332。更多详细信息，请参阅验证指南中的示例案例` HVAC_filter`。

```fortran
&SPEC ID='PARTICULATE',MW=28.,MASS_FRACTION_0=0.001,SPECIFIC_HEAT=1./
&HVAC TYPE_ID='NODE',ID='FILTER',DUCT_ID='DUCT1','DUCT2',XYZ(3)=0.55,
    FILTER_ID='FILTER'/
&HVAC TYPE_ID='FILTER',ID='FILTER',CLEAN_LOSS=1.,SPEC_ID='PARTICULATE',EFFICIENCY=1.,
    LOSS=7732.446,LOADING_MULTIPLIER=1./
```

注意，一个过滤器输入指的是一类过滤器，多个管道可以引用相同的过滤器定义。

#### HVAC Aircoil Parameters

空气盘管指的是一种从流经管道的空气中添加或去除热量的设备。在典型的HVAC系统中，这是通过将空气吹过装有工作流体（如冷冻水或制冷剂）的热交换器（因此称为空气盘管）来实现的。输入管路示例如下：

```fortran
&HVAC TYPE_ID='AIRCOIL', ID='aircoil 1', EFFICIENCY=0.5,
    COOLANT_SPECIFIC_HEAT=4.186, COOLANT_TEMPERATURE=10., COOLANT_MASS_FLOW=1./
```

其中，

COOLANT_MASS_FLOW为工作流体的流量(kg/s)。

COOLANT_SPECIFIC_HEAT是工作流体的比热(kJ/(kgK))。

COOLANT_TEMPERATURE是工作流体的入口温度(℃)。

EFFICIENCY为换热器效率，η，取值范围为0 ~ 1。**值为1表示换热器两侧出口温度相等**。

FIXED_Q为恒定热交换率。**负值表示热量从管道排出**。换热速率可由RAMP_ID或TAU_AC控制。

TAU_AC为空气线圈定义tanh (TAU_AC>0)或$t^2$坡道(TAU_AC<0)。这适用于空气线圈的FIXED_Q。或者，也可以指定RAMP_ID。

请注意，应指定 FIXED_Q 或 COOLANT_SPECIFIC_HEAT、COOLANT_MASS_FLOW、COOLANT_TEMPERATURE 和 EFFICIENCY 设置。在后一种情况下，热交换的计算分为两步。首先，确定出口温度，假设效率为100%(即两种流体在相同温度下出口)：
$$
T_{{\mathrm{fluid,out}}}=\frac{c_{p,\mathrm{gas}}u_{{\mathrm{duct}}}A_{{\mathrm{duct}}}\rho_{{\mathrm{duct}}}T_{{\mathrm{duct,in}}}+c_{{p,\mathrm{fluid}}}\dot{m}_{{\mathrm{fluid}}}T_{{\mathrm{fluid,in}}}}{c_{{p,\mathrm{gas}}}u_{{\mathrm{duct}}}A_{{\mathrm{duct}}}\rho_{{\mathrm{duct}}}+c_{{p,\mathrm{fluid}}}\dot{m}_{{\mathrm{fluid}}}}
$$
其次，利用EFFICIENCY计算实际换热量。
$$
\dot{q}_{\mathrm{coil}}=\eta c_{p,\mathrm{fluid}}\dot{m}_{\mathrm{fluid}}(T_{\mathrm{fluid,in}}-T_{\mathrm{fluid,out}})
$$
请注意，一个空气盘管输入指的是一类空气盘管，多个管道可以引用相同的空气盘管定义。

示例输入文件 `HVAC_aircoil.fds` 演示了如何使用空气盘管输入。恒定流量管道从地板抽走空气（定义为 28 g/mol，比热为 1 kJ/(kgK)），并以 1 立方米/秒的体积流量从天花板注入。工作流体的流速为 10 kg/s，温度为 100℃，比热为 4 kJ/(kgK)。空气盘管的效率为 50%。根据上述公式，空气盘管将为流经管道的气体增加 45.2 千瓦的热量，从而使管道出口温度达到 332 K。结果展示在图10.8。

![image-20240617165830742](..\FDS中钠燃烧模型添加.assets\image-20240617165830742.png)

#### Louvered HVAC Vents

所建模的HVAC系统可能会有百叶窗将离开通风口的气流重新定向，或者实际通风口的方向可能不在 FDS 的某个轴线上。要定义HVAC出口的流向，可以在通风口上使用关键字 UVW。UVW 是表示VENT流向的矢量。例如：

```fortran
&OBST XB=1.0,2.0,0.0,1.0,0.0,1.0 /
&VENT XB=1.0,1.0,0.0,1.0,0.0,1.0, SURF_ID='HVAC', ID='HVAC OUTLET', UVW=-1,0,1 /
```

上述输入定义了一个位于 y-z 平面、朝向 -x 方向的通风口。流量矢量显示，该通风口的流量方向为 -x，向上倾斜 45 度（x 和 z 分量大小相等）。FDS 将设置通风口的切向速度，以获得 UVW 所指示的指定方向。**只有在通气口向域输入气体时才会这样做**。请注意，UVW 的值已归一化为单位矢量。

#### HVAC Mass Transport

FDS 可以通过对单个HVAC管道进行离散化处理，来考虑HVAC网络中物种和焓传输的时间延迟。这可以通过HVAC管道输入的 N_CELLS 或设置 HVAC_MASS_TRANSPORT_CELL_L 来实现。输入 N_CELLS 将管道长度划分为 N_CELLS 均匀段。参数 HVAC_MASS_TRANSPORT_CELL_L 定义了单元长度，除非被 N_CELLS 改写，否则该长度将应用于输入文件中的所有管道。如果指定了单元长度，则管道的单元数取管道长度除以 HVAC_MASS_TRANSPORT_CELL_L 的整数。当前的暖通空调（HVAC）求解器不考虑暖通空调（HVAC）网络中的热损失。

如果一个风管被离散化，那么该风管中的所有其他风管也必须离散化。并不要求一个风管单元中的所有风管都使用相同的单元尺寸。风管单元是任何相互连接的HVAC组件的集合，其中两个组件之间存在通过穿越风管单元中的风管的路径。

如果您使用 DEVC 输出第 22.2.3 节所述的空间积分统计数据（如VOLUME MEAN、VOLUME INTEGRAL或MASS INTEGRAL），请注意，即使 XB 绑定的积分体积囊括了管道的空间位置，DEVC 也不会记录导管中的数量。例如，如果有 1 立方米的物种 1 在上游的 FDS 小室中初始化，并通过总体积大于 1 立方米的 HVAC 网络传输到下游的 FDS 小室，那么在其处于 HVAC 网络域期间，记录DENSITY的VOLUME INTEGRAL的 DEVC 输出的物种 1 的总质量值将减小为零。

默认情况下，**质量传输管道中的单元格初始化为环境值**。可以通过在 INIT 上指定 NODE_ID，再加上温度（TEMPERATURE）和/或 SPEC_ID，再加上体积（VOLUME_FRACTION）或质量（MASS_FRACTION），将管道初始化为其他值。然后，风道中的数值将通过对风道节点上的数值进行线性插值来设置。

#### Specified Flow vs. Unspecified Flow

在FDS中定义HVAC网络有两种基本方法。

在第一种方法中，我们可以指定足够多的 VOLUME_FLOW 和 MASS_FLOW 输入，这样网络中各处的所有流量都是已知的。例如，如果一个三通有三个管道，其中两个管道有指定流量，那么根据该节点的质量守恒，第三个管道的流量是已知的。如果HVAC网络中的所有地方都指定了流量，那么就不需要管道和节点的 LOSS 输入。不要过多指定流量。例如，如果一个节点有三个管道，则不要为其中两个以上的管道指定 VOLUME_FLOW 或 MASS_FLOW。这样可以确保任何数值舍入误差不会导致守恒误差。 

在第二种方法中，一个或多个管道的流量没有指定，在这种情况下，FDS 必须求解管道两端的压力，以确定通过管道的流量。举例来说，如果一个三通有三个管道，而只有一个管道有指定流量，那么 FDS 将使用其他两个管道的相对压降来确定流量。如果没有提供LOSS输入，则 FDS 可能无法正确求解流量。再比如，HVAC网络中的损耗会限制管道中流量随时间变化的速度。如果有一条管道连接两个房间，但没有给出 LOSS 输入，那么微小的压力变化就会导致管道速度的巨大变化，从而增加数值不稳定的风险。如果您指定了一个暖通空调（HVAC）网络，FDS 将对该网络中的流量进行求解，那么您必须为每个可能的流动路径提供 LOSS 输入。FDS 将在启动时执行检查，如果发现指定的损失不足，将返回错误信息；但是，这种检查可能无法发现所有情况。



### INIT(Initial Conditions)

| 可输入参数             | 类型            | 描述           | 单位     | 默认    |
| ---------------------- | --------------- | -------------- | -------- | ------- |
| BULK_DENSITY_FACTOR    | Real            | Section 17.2.2 |          | 1.      |
| BULK_DENSITY_FILE      | Character       | Section 17.2.2 |          |         |
| CELL_CENTERED          | Logical         | Section 15.5.3 |          | F       |
| CROWN_BASE_HEIGHT      | Real            | Section 17.2.1 | m        |         |
| CROWN_BASE_WIDTH       | Real            | Section 17.2.1 | m        |         |
| CTRL_ID                | Character       | Section 15.5.3 |          |         |
| DB                     | Character       | Section 20.1   |          |         |
| DENSITY                | Real            | Section 20.3   | $kg/m^3$ | Ambient |
| DEVC_ID                | Character       | Section 15.5.3 |          |         |
| DIAMETER               | Real            | Section 15.5.3 | μm       |         |
| DRY                    | Logical         | Section 17.2   |          | F       |
| DT_INSERT              | Real            | Section 15.5.3 | s        |         |
| DX                     | Real            | Section 15.5.3 | m        | 0.      |
| DY                     | Real            | Section 15.5.3 | m        | 0.      |
| DZ                     | Real            | Section 15.5.3 | m        | 0.      |
| HEIGHT                 | Real            | Section 15.5.3 | m        |         |
| HRRPUV                 | Real            | Section 20.4   | $kW/m^3$ |         |
| ID                     | Character       | Section 15.4   |          |         |
| INNER_RADIUS           | Real            | Section 15.5.3 | m        | 0.      |
| MASS_FRACTION(:)       | Real Array      | Section 20.1   | kg/kg    | Ambient |
| MASS_PER_TIME          | Real            | Section 15.5.3 | kg/s     |         |
| MASS_PER_VOLUME        | Real            | Section 15.5.3 | $kg/m^3$ | 1       |
| MULT_ID                | Character       | Section 7.6    |          |         |
| NODE_ID                | Character       | Section 10.2.8 |          |         |
| N_PARTICLES            | Integer         | Section 15.5.3 |          | 0       |
| N_PARTICLES_PER_CELL   | Integer         | Section 15.5.3 |          | 0       |
| ORIENTATION_RAMP(3)    | Character       | Section 15.5.4 |          |         |
| PART_ID                | Character       | Section 15.5.3 |          |         |
| PARTICLE_WEIGHT_FACTOR | Real            | Section 15.5.3 |          | 1.      |
| PATH_RAMP(3)           | Character       | Section 15.5.3 |          |         |
| RADIATIVE_FRACTION     | Real            | Section 20.4   |          | 0.      |
| RADIUS                 | Real            | Section 15.5.3 | m        |         |
| RAMP_PART              | Character       | Section 15.5.3 |          |         |
| RAMP_Q                 | Character       | Section 20.4   |          |         |
| SHAPE                  | Character       | Section 15.5.3 |          | ’BLOCK’ |
| SPEC_ID(N)             | Character Array | Section 20.1   |          |         |
| TEMPERATURE            | Real            | Section 20.2   | ℃        | TMPA    |
| TREE_HEIGHT            | Real            | Section 17.2.1 | m        |         |
| UNIFORM                | Logical         | Section 15.5.3 |          | F       |
| UVW(3)                 | Real Array      | Section 15.5.3 | m/s      | 0.      |
| VOLUME_FRACTION(:)     | Real Array      | Section 20.1   | mol/mol  | Ambient |
| XB(6)                  | Real Array      | Section 20.1   | m        |         |
| XYZ(3)                 | Real Array      | Section 15.5.3 | m        |         |

假设空气温度随高度不变，密度和压力随高度(z方向)而减小。

背景气体的初始浓度不能用这种方法来确定。

所有气体种类必须使用SPEC或REAC命名列表组指定。换句话说，列出的任何物种都必须单独跟踪，而不仅仅是一个集总物种的组成部分。

初始化某个区域的**温度和物质**：

```fortran
&INIT XB=0.0,0.1,0.0,0.025,0.0,0.1,
    MASS_FRACTION(1)=0.23, SPEC_ID(1)='OXYGEN',
    MASS_FRACTION(2)=0.06, SPEC_ID(2)='PROPANE',
    TEMPERATURE=60. /
```

:smile:如果同时初始化密度和温度，则FDS会用状态方程计算得到的温度覆盖指定的温度，因为温度是由状态方程计算得到的。

```fortran
&INIT XB=0.0,0.1,0.0,0.025,0.0,0.1,
    MASS_FRACTION(1)=0.23, SPEC_ID(1)='OXYGEN',
    MASS_FRACTION(2)=0.06, SPEC_ID(2)='PROPANE',
    TEMPERATURE=60., DENSITY=1.13 /
```

指定一个体积热源项：（表示以XB为界的区域产热为$1000kw /m^3$，其中25%来自辐射。）

```fortran
&INIT XB=0.0,0.1,0.0,0.025,0.0,0.1, HRRPUV=1000., RADIATIVE_FRACTION=0.25 /
```

:question:NOISE_VELOCITY噪声速度是什么意思？

对于某些类型的诊断测试，关闭速度场并练习模型的其他方面(如辐射或粒子输运)是有用的。为此，在MISC行设置FREEZE_VELOCITY=T。

### MATL(Material Properties)

| 可输入参数                     | 类型        | 描述          | 单位      | 默认   |
| ------------------------------ | ----------- | ------------- | --------- | ------ |
| A(:)                           | Real Array  | Section 9.2   | 1/s       |        |
| ABSORPTION_COEFFICIENT         | Real        | Section 8.3.2 | 1/m       | 50000. |
| ADJUST_H                       | Logical     | Section 9.4   |           | T      |
| ALLOW_SHRINKING                | Logical     | Section 9.2.3 |           | T      |
| ALLOW_SWELLING                 | Logical     | Section 9.2.3 |           | T      |
| BOILING_TEMPERATURE            | Real        | Section 9.2.6 | ℃         | 5000.  |
| CONDUCTIVITY                   | Real        | Section 8.3.2 | W/(mK)    | 0.     |
| CONDUCTIVITY_RAMP              | Character   | Section 8.3.2 |           |        |
| DENSITY                        | Real        | Section 8.3.2 | $kg/m^3$  | 0.     |
| E(:)                           | Real Array  | Section 9.2   | J/mol     |        |
| EMISSIVITY                     | Real        | Section 8.3.2 |           | 0.9    |
| GAS_DIFFUSION_DEPTH(:)         | Real Array  | Section 9.2   | m         | 0.001  |
| HEATING_RATE(:)                | Real Array  | Section 9.2   | ℃/min     | 5.     |
| HEAT_OF_COMBUSTION(:,:)        | Real Array  | Section 9.2   | kJ/kg     |        |
| HEAT_OF_REACTION(:)            | Real Array  | Section 9.2   | kJ/kg     | 0.     |
| ID                             | Character   | Section 8.1   |           |        |
| MATL_ID(:,:)                   | Character   | Section 9.2   |           |        |
| MAX_REACTION_RATE(:)           | Real Array  | Section 9.2.2 |           | ∞      |
| MW                             | Real        | Section 9.2.6 | **g/mol** |        |
| N_O2(:)                        | Real Array  | Section 9.2   |           | 0.     |
| N_REACTIONS                    | Integer     | Section 9.2   |           | 0.     |
| N_S(:)                         | Real Array  | Section 9.2   |           | 1.     |
| N_T(:)                         | Real Array  | Section 9.2   |           | 0.     |
| NU_MATL(:,:)                   | Real Array  | Section 9.2   | kg/kg     | 0.     |
| NU_PART(:,:)                   | Real Array  | Section 9.2   | kg/kg     | 0.     |
| NU_SPEC(:,:)                   | Real Array  | Section 9.2   | kg/kg     | 0.     |
| PART_ID(:,:)                   | Char. Array | Section 9.2   |           |        |
| PYROLYSIS_RANGE(:)             | Real Array  | Section 9.2.2 | ℃         | 80.    |
| REFERENCE_ENTHALPY             | Real        | Section 9.4   | kJ/kg     |        |
| REFERENCE_ENTHALPY_TEMPERATURE | Real        | Section 9.4   | K         |        |
| REFERENCE_RATE(:)              | Real Array  | Section 9.2   | 1/s       |        |
| REFERENCE_TEMPERATURE(:)       | Real Array  | Section 9.2   | ℃         |        |
| SPECIFIC_HEAT                  | Real        | Section 8.3.2 | kJ/(kgK)  | 0.     |
| SPECIFIC_HEAT_RAMP             | Character   | Section 8.3.2 |           |        |
| SPEC_ID(:,:)                   | Char. Array | Section 9.2   |           |        |
| SURFACE_OXIDATION_MODEL        | Logical     | Section 17.1  |           | F      |

在复杂热解模型中，动力学常数A（指前因子）和E（活化能）对于大多数材料来说是不可获取的，可以通过指定`REFERENCE_TEMPERATURE`来生成有效值。更确切地说，它只是在TGA或类似实验装置的背景下，**材料的质量分数以其最大速率下降的温度**。

![image-20240612095338472](..\FDS中钠燃烧模型添加.assets\image-20240612095338472.png)

液体蒸发（热解）模型中，`HEAT_OF_REACTION`表示汽化潜热。

### MESH

| 可输入参数           | 类型            | 描述          | 单位 | 默认        |
| -------------------- | --------------- | ------------- | ---- | ----------- |
| CHECK_MESH_ALIGNMENT | Logical         | Section 6.3.4 |      | F           |
| COLOR                | Character       | Section 6.3.3 |      | ’BLACK’     |
| CYLINDRICAL          | Logical         | Section 6.3.2 |      | F           |
| ID                   | Character       | Section 6.3.1 |      |             |
| IJK                  | Integer Triplet | Section 6.3.1 |      | 10,10,10    |
| MPI_PROCESS          | Integer         | Section 6.3.3 |      |             |
| MULT_ID              | Character       | Section 7.6   |      |             |
| RGB                  | Integer Triplet | Section 6.3.3 |      | 0,0,0       |
| TRNX_ID              | Character       | Section 6.3.5 |      |             |
| TRNY_ID              | Character       | Section 6.3.5 |      |             |
| TRNZ_ID              | Character       | Section 6.3.5 |      |             |
| XB(6)                | Real Sextuplet  | Section 6.3.1 | m    | 0,1,0,1,0,1 |



### MISC

| 可输入参数                   | 类型         | 描述             | 单位    | 默认        |
| ---------------------------- | ------------ | ---------------- | ------- | ----------- |
| AEROSOL_AL2O3                | Logical      | Section 14.3     |         | F           |
| AEROSOL_SCRUBBING            | Logical      | Section 13.6     |         | F           |
| AGGLOMERATION                | Logical      | Section 13.5     |         | T           |
| ALIGNMENT_TOLERANCE          | Real         | Section 6.3.4    |         | 0.001       |
| ALLOW_SURFACE_PARTICLES      | Logical      | Section 15.7.1   |         | T           |
| ALLOW_UNDERSIDE_PARTICLES    | Logical      | Section 15.7.1   |         | F           |
| BNDF_DEFAULT                 | Logical      | Section 22.5     |         | T           |
| C_DEARDORFF                  | Real         | Section 19.2     |         | 0.1         |
| CFL_MAX                      | Real         | Section 19.3.1   |         | 1.0         |
| CFL_MIN                      | Real         | Section 19.3.1   |         | 0.8         |
| CFL_VELOCITY_NORM            | Integer      | Section 19.3.1   |         |             |
| CHECK_HT                     | Logical      | Section 19.3.4   |         | F           |
| CHECK_VN                     | Logical      | Section 19.3.2   |         | T           |
| CNF_CUTOFF                   | Real         | Section 15.3.3   |         | 0.005       |
| CONSTANT_SPECIFIC_HEAT_RATIO | Logical      | Section 12.1.3   |         | F           |
| C_SMAGORINSKY                | Real         | Section 19.2     |         | 0.20        |
| C_VREMAN                     | Real         | Section 19.2     |         | 0.07        |
| C_WALE                       | Real         | Section 19.2     |         | 0.60        |
| DEPOSITION                   | Logical      | Section 13.4     |         | T           |
| EXTERNAL_FILENAME            | Character    | Section 18.8     |         |             |
| FIXED_LES_FILTER_WIDTH       | Real         | Section 19.2     | m       |             |
| FLUX_LIMITER                 | Integer      | Section 19.4     |         | 2           |
| FREEZE_VELOCITY              | Logical      | Section 20.5.2   |         | F           |
| GAMMA                        | Real         | Section 12.1.2   |         | 1.4         |
| GRAVITATIONAL_DEPOSITION     | Logical      | Section 13.4     |         | T           |
| GRAVITATIONAL_SETTLING       | Logical      | Section 13.4     |         | T           |
| GVEC(3)                      | Real Array   | Section 20.7     | $m/s^2$ | 0,0,-9.81   |
| H_F_REFERENCE_TEMPERATURE    | Real         | Section 22.10.25 | ℃       | 25.         |
| HUMIDITY                     | Real         | Section 12.1.1   | %       | 40.         |
| HVAC_LOCAL_PRESSURE          | Logical      | Section 10.2     |         | T           |
| HVAC_MASS_TRANSPORT_CELL_L   | Logical      | Section 10.2.8   |         | F           |
| HVAC_PRES_RELAX              | Real         | Section 10.2     |         | 1.0         |
| HVAC_QFAN                    | Logical      | Section 10.2.4   |         | F           |
| IBLANK_SMV                   | Logical      | Section 22.4     |         | T           |
| I_MAX_TEMP                   | Integer      | Section 19.5.1   | K       | 5000        |
| LES_FILTER_TYPE              | Character    | Section 19.2     |         | ’MEAN’      |
| LEVEL_SET_ELLIPSE            | Logical      | Section 17.5     |         | T           |
| LEVEL_SET_MODE               | Integer      | Section 17.5     |         | 0           |
| MAXIMUM_VISIBILITY           | Real         | Section 22.10.5  | m       | 30          |
| MAX_LEAK_PATHS               | Integer      | Section 10.3.2   |         | 200         |
| MAX_RAMPS                    | Integer      | Section 11       |         | 100         |
| MINIMUM_ZONE_VOLUME          | Real         | Section 10.3.4   | $m^3$   | 0           |
| MPI_TIMEOUT                  | Real         | Section 4.2      | s       | 600.        |
| NEIGHBOR_SEPARATION_DISTANCE | Real         | Section 8.4      | m       | 0.          |
| NOISE                        | Logical      | Section 20.5.1   |         | T           |
| NOISE_VELOCITY               | Real         | Section 20.5.1   | m/s     | 0.005       |
| NO_PRESSURE_ZONES            | Logical      | Section 10.3.1   |         | F           |
| NORTH_BEARING                | Real         | Section 17.5.4   | deg.    |             |
| NUCLEATION_SITES             | Real         | Section 13.7     | #$/m^3$ | $1×10^7$    |
| ORIGIN_LAT                   | Real         | Section 17.5.4   | deg.    |             |
| ORIGIN_LON                   | Real         | Section 17.5.4   | deg.    |             |
| OVERWRITE                    | Logical      | Section 5.5      |         | T           |
| PARTICLE_CFL                 | Logical      | Section 19.3.3   |         | F           |
| PARTICLE_CFL_MAX             | Real         | Section 19.3.3   |         | 1.0         |
| PARTICLE_CFL_MIN             | Real         | Section 19.3.3   |         | 0.8         |
| POROUS_FLOOR                 | Logical      | Section 15.6     |         | T           |
| PR                           | Real         | Section 19.2     |         | 0.5         |
| P_INF                        | Real         | Section 20.2     | Pa      | 101325      |
| RAMP_GX                      | Character    | Section 20.7     |         |             |
| RAMP_GY                      | Character    | Section 20.7     |         |             |
| RAMP_GZ                      | Character    | Section 20.7     |         |             |
| RESTART                      | Logical      | Section 5.6      |         | F           |
| RESTART_CHID                 | Character    | Section 5.6      |         | CHID        |
| RND_SEED                     | Integer      | Section 5.6      |         |             |
| SC                           | Real         | Section 20.5.1   |         | 0.5         |
| SHARED_FILE_SYSTEM           | Logical      | Section 6.3.3    |         | T           |
| SIMULATION_MODE              | Character    | Section 19.1     |         | ’VLES’      |
| SMOKE3D_16                   | Logical      | Section 22.8     |         | F           |
| SMOKE_ALBEDO                 | Real         | Reference [2]    |         | 0.3         |
| SOLID_PHASE_ONLY             | Logical      | Section 9.3      |         | F           |
| SOOT_DENSITY                 | Real         | Section 13.4     |         | 1800        |
| SOOT_OXIDATION               | Logical      | Section 13.4     |         | F           |
| TAU_DEFAULT                  | Real         | Section 11.1     | s       | 1.          |
| TERRAIN_IMAGE                | Character    | Section 22.10.20 |         |             |
| TEXTURE_ORIGIN(3)            | Real Triplet | Section 7.5.2    | m       | (0.,0.,0.)  |
| THERMOPHORETIC_DEPOSITION    | Logical      | Section 13.4     |         | T           |
| THERMOPHORETIC_SETTLING      | Logical      | Section 13.4     |         | T           |
| THICKEN_OBSTRUCTIONS         | Logical      | Section 7.2.1    |         | F           |
| TMPA                         | Real         | Section 20.2     | ℃       | 20.         |
| TURBULENCE_MODEL             | Character    | Section 19.2     |         | ’DEARDORFF’ |
| TURBULENT_DEPOSITION         | Logical      | Section 13.4     |         | T           |
| VERBOSE                      | Logical      | Section 6.3.3    |         |             |
| VISIBILITY_FACTOR            | Real         | Section 22.10.5  |         | 3           |
| VN_MAX                       | Real         | Section 19.3.2   |         | 1.0         |
| VN_MIN                       | Real         | Section 19.3.2   |         | 0.8         |
| Y_CO2_INFTY                  | Real         | Section 13.1.1   | kg/kg   |             |
| Y_O2_INFTY                   | Real         | Section 13.1.1   | kg/kg   |             |

`P_INF`和`TMPA`分别指定环境压力（101325Pa）和温度（默认20℃）/初始计算的温度。

`IBLANK_SMV`：默认情况下，**Smokeview 会对障碍物内的切片文件数据进行空白处理**。但是，对于大型案例，在 Smokeview 启动时加载这一功能的成本很高。如果希望 Smokeview 不存储此空白阵列，可在 MISC 上设置 IBLANK_SMV=F。另一种方法是从命令行运行 Smokeview，并添加 -noblank 作为选项。

`LEVEL_SET_MODE`：对于大面积野地火灾的模拟，由于网格划分不够精细，无法使用基于物理的模型预测火灾蔓延，FDS 中内置了一个基于水平集的经验模型[47]。该方法在欧拉框架内再现了基于拉格朗日的火灾前沿跟踪模型 FARSITE [48] 中使用的方法。这种方法利用了 Rothermel-Albini [49, 50] 地表火灾蔓延率公式，并假设在一定的风速、坡度和植被条件下，地表火灾从一点开始蔓延时，火锋呈椭圆形2 ，在给定的风速下，火锋的长宽比固定不变。**LEVEL_SET_MODE=1**：只执行水平集模拟。风不受地形影响，也没有火。**LEVEL_SET_MODE=2**：风场建立在地形之上，但当火点燃时，风场就“冻结”了。**LEVEL_SET_MODE=3**：风场随地形变化，但模拟中没有实际的火灾。它只是走在前面。**LEVEL_SET_MODE=4**：风和火是完全耦合的。当火锋到达一个给定的表面单元时，它燃烧的时间是有限的，单位面积的热量释放作为燃料模型的一部分。对于模态2到4，用于水平集方程的风速和风向取自地面以上的第一个网格单元。

### MULT(Multiplier Function Parameters)

| 可输入参数   | 类型       | 描述                                      | 单位 | 默认 |
| ------------ | ---------- | ----------------------------------------- | ---- | ---- |
| DX           | Real       | Spacing in the x direction                | m    | 0.   |
| DXB(6)       | Real Array | Spacing for all 6 coordinates             | m    | 0.   |
| DX0          | Real       | Translation in the x direction            | m    | 0.   |
| DY           | Real       | Spacing in the y direction                | m    | 0.   |
| DY0          | Real       | Translation in the y direction            | m    | 0.   |
| DZ           | Real       | Spacing in the z direction                | m    | 0.   |
| DZ0          | Real       | Translation in the z direction            | m    | 0.   |
| ID           | Character  | Identification tag                        |      |      |
| I_LOWER      | Integer    | Lower array bound, x direction            |      | 0    |
| I_LOWER_SKIP | Integer    | Lower array bound begin skip, x direction |      |      |
| I_UPPER      | Integer    | Upper array bound, x direction            |      | 0    |
| I_UPPER_SKIP | Integer    | Upper array bound end skip, x direction   |      |      |
| J_LOWER      | Integer    | Lower array bound, y direction            |      | 0    |
| J_LOWER_SKIP | Integer    | Lower array bound begin skip, y direction |      |      |
| J_UPPER      | Integer    | Upper array bound, y direction            |      | 0    |
| J_UPPER_SKIP | Integer    | Upper array bound end skip, y direction   |      |      |
| K_LOWER      | Integer    | Lower array bound, z direction            |      | 0    |
| K_LOWER_SKIP | Integer    | Lower array bound begin skip, z direction |      |      |
| K_UPPER      | Integer    | Upper array bound, z direction            |      | 0    |
| K_UPPER_SKIP | Integer    | Upper array bound end skip, z direction   |      |      |
| N_LOWER      | Integer    | Lower sequence bound                      |      | 0    |
| N_LOWER_SKIP | Integer    | Lower sequence bound begin skip           |      |      |
| N_UPPER      | Integer    | Upper sequence bound                      |      | 0    |
| N_UPPER_SKIP | Integer    | Upper sequence bound end skip             |      |      |

有时，障碍物、孔洞和通风口会在输入文件中重复出现。这样的创建过程可能很繁琐，也会使输入文件难以阅读。不过，如果一组特定的对象有规律地重复出现，您可以使用一种称为乘法器的工具。例如，如果要重复一个障碍物，可以在输入文件中创建如下一行：

```fortran
&MULT ID='m1', DX=1.2, DY=2.4, I_LOWER=-2, I_UPPER=3, J_LOWER=0, J_UPPER=5 /
&OBST XB=x1,x2,y1,y2,z1,z2, MULT_ID='m1' /
```

这就产生了按照下列公式排列障碍物的效果：

```fortran
x1’ = x1+DX0+iDX ; I_LOWER ≤ i ≤ I_UPPER
x2’ = x2+DX0+iDX ; I_LOWER ≤ i ≤ I_UPPER
y1’ = y1+DY0+ jDY ; J_LOWER ≤ j ≤ J_UPPER
y2’ = y2+DY0+ jDY ; J_LOWER ≤ j ≤ J_UPPER
z1’ = z1+DZ0+kDZ ; K_LOWER ≤ k ≤ K_UPPER
z2’ = z2+DZ0+kDZ ; K_LOWER ≤ k ≤ K_UPPER
```

如果需要在乘法运算之前移动障碍物的位置，则使用参数 DX0、DY0 和 DZ0。

这个想法的一个变体是用一个名为 DXB 的六元组代替参数 DX、DY 和 DZ。DXB 中的 DXB 中的六个条目分别递增 XB 所给出的障碍物坐标值。例如，X 坐标变换如下：

```fortran
x1’ = x1+DX0+nDXB(1) ; N_LOWER ≤ n ≤ N_UPPER
x2’ = x2+DX0+nDXB(2) ; N_LOWER ≤ n ≤ N_UPPER
```

N_LOWER 和 N_UPPER 用于表示 N 的范围。这种更灵活的输入方案允许您创建一个斜屋顶，例如，在该斜屋顶中，各个屋顶片段在上升到顶部时会缩短。下面的简短输入文件演示了这一功能。四个外围障碍物构成了金字塔底座的轮廓：

```fortran
&HEAD CHID='pyramid', TITLE='Simple demo of multiplier function' /
&MESH IJK=100,100,100, XB=0.0,1.0,0.0,1.0,0.0,1.0 /
&TIME T_END=0. /
&MULT ID='south', DXB=0.01,-.01,0.01,0.01,0.01,0.01, N_LOWER=0, N_UPPER=39 /
&MULT ID='north', DXB=0.01,-.01,-.01,-.01,0.01,0.01, N_LOWER=0, N_UPPER=39 /
&MULT ID='east', DXB=-.01,-.01,0.01,-.01,0.01,0.01, N_LOWER=0, N_UPPER=39 /
&MULT ID='west', DXB=0.01,0.01,0.01,-.01,0.01,0.01, N_LOWER=0, N_UPPER=39 /
&OBST XB=0.10,0.90,0.10,0.11,0.10,0.11, MULT_ID='south', COLOR='RED' /
&OBST XB=0.10,0.90,0.89,0.90,0.10,0.11, MULT_ID='north', COLOR='BLUE' /
&OBST XB=0.10,0.11,0.11,0.89,0.10,0.11, MULT_ID='west', COLOR='GREEN' /
&OBST XB=0.89,0.90,0.11,0.89,0.10,0.11, MULT_ID='east', COLOR='CYAN' /
&MULT ID='holes', DX=0.15, DZ=0.1, I_UPPER=1, K_UPPER=1 /
&HOLE XB=0.40,0.45,0.00,1.00,0.15,0.20, MULT_ID='holes' /
&TAIL /
```

该输入文件的最终结果是在每个面的底部以阶梯模式重复设置长方形障碍物，从而创建一个金字塔。注意本例中使用了 N_LOWER 和 N_UPPER，它们会自动使 FDS 按顺序而不是以数组的形式重复障碍物。

请注意，MULTiplication功能适用于 MESH、OBST、HOLE、VENT 和 INIT 行。**对于网格，它只适用于网格的边界 (XB)，而不适用于单元格数**。

还请注意，如果在包含 MULT_ID 的行中指定了颜色，该颜色将应用于对象的所有副本。不过，您也可以设置 COLOR='RAINBOW'，这将指示 FDS 为每个复制对象随机选择一种颜色。

#### Using MULT for Mesh Refinement

请注意，可以使用 I_LOWER_SKIP 和 I_UPPER_SKIP 等跳过 MULT 数组中的对象和网格。上式中的 i 会在此区间内跳过。下面以细化内部网格的多网格为例，说明这种方法的实用性。网格排列结果如图 7.13 所示。

```fortran
&MULT ID='interior fine mesh array',
    DX=1.0,I_LOWER=1,I_UPPER=2,
    DZ=1.0,K_LOWER=1,K_UPPER=2 /
&MULT ID='exterior coarse mesh array',
    DX=1.0,I_LOWER=0,I_LOWER_SKIP=1,I_UPPER_SKIP=2,I_UPPER=3,
    DZ=1.0,K_LOWER=0,K_LOWER_SKIP=1,K_UPPER_SKIP=2,K_UPPER=3 /
&MESH IJK=8,1,8, XB=0.0,1.0,-0.5,0.5,0.0,1.0, MULT_ID='interior fine mesh array' /
&MESH IJK=4,1,4, XB=0.0,1.0,-0.5,0.5,0.0,1.0, MULT_ID='exterior coarse mesh array' /
```

![image-20240618081807494](..\FDS中钠燃烧模型添加.assets\image-20240618081807494.png)

#### Using MULT to make shapes out of obstructions

使用 OBST 线制作的块状障碍物受限于 XB 所定义的方框内。不过，MULT 可用来创建障碍物阵列，每个障碍物阵列可以小到一个网格单元，并可将其调整为以下四种基本形状之一：**球形、圆柱形、圆锥形或方框形**。流动障碍物是通过使用 MULT_ID 创建的 OBST 数组与 OBST 行上定义的 SHAPE 的交叉点创建的。请注意，这种方法可能会占用大量内存，因为每个网格单元都可以是自己的 OBST，这与使用 BURN_AWAY 进行热解时分解 OBST 的方式类似。

雕刻形状的第一步是创建 MULT 行，定义 OBST 的复制。然后在 OBST 行上输入 SHAPE（形状），并输入所需的参数；参数列于表 7.2。

![image-20240618092114846](..\FDS中钠燃烧模型添加.assets\image-20240618092114846.png)

下面给出了一个球体的示例。**默认情况下，球心位于 (0,0,0)**，因此只需要 RADIUS。如果 RADIUS 大于 OBST 数组的半宽，问题不大，但最终结果不会是球体。如果 RADIUS 小于半宽，这也是允许的，但效率不高。

```FORTRAN
&MESH IJK=50,50,50, XB=-0.125,0.125,-0.125,0.125,-0.125,0.125/
&SURF ID='shape', COLOR='ORANGE'/
&MULT ID='cube array', DX=0.005,DY=0.005,DZ=0.005, I_UPPER=41,J_UPPER=41,K_UPPER=41/
&OBST XB=-0.105,-0.100,-0.105,-0.100,-0.105,-0.100
    MULT_ID='cube array'
    SURF_ID='shape'
    SHAPE='SPHERE'
    RADIUS=0.1/
```

![image-20240618092309202](..\FDS中钠燃烧模型添加.assets\image-20240618092309202.png)

要创建一个圆柱体，除了半径之外，我们还需要高度和方向。圆柱体底面中心 XYZ 的位置默认为 (0,0,0)。垂直方向（默认）圆柱体的示例如下图 7.15 所示。请注意，方向矢量的大小并不重要；该矢量仅用于指定方向。

![image-20240618093939352](..\FDS中钠燃烧模型添加.assets\image-20240618093939352.png)

关于精确区域调整的注意事项： **改变默认的方向（0,0,1）或使用带有多个网格的 SHAPE 会使面积调整算法失效**。因此，FDS 无法按照 SURF 线和 OBST 线 SHAPE 几何参数给出的精确面积，精确计算出表面的质量通量。FDS 产生的质量通量将由 SURF 线和 OBST 所对应的网格单元的大小决定。如果需要调整方向或进行多网格计算，请首先运行一个示例案例，查看表面实现的总流速（通常可在 CHID_hrr.csv 文件中找到）。然后在相应的 SURF 行上手动调整质量通量（或 HRRPUA）。:question:<font color=red>**在这里改变HEIGHT，为什么smokeview中的高度不变？**</font>

```fortran
&SURF ID='shape', COLOR='DARK GRAY'/
&MULT ID='cube array', DX=0.005,DY=0.005,DZ=0.005, I_UPPER=41,J_UPPER=41,K_UPPER=41/
&OBST XB=-0.105,-0.100,-0.105,-0.100,-0.105,-0.100
    MULT_ID='cube array'
    SURF_ID='shape'
    SHAPE='CYLINDER'
    RADIUS=0.05
    HEIGHT=0.2
    XYZ=0,0,-0.1
    ORIENTATION=0,0,1/
```

锥体所需的输入参数与圆柱体基本相同。底面中心的位置 使用 XYZ 指定底面中心的位置，同时必须指定底面的半径、高度和方位。下图 7.16 是一个示例。

```fortran
&SURF ID='shape', COLOR='FOREST GREEN'/
&MULT ID='cube array', DX=0.005,DY=0.005,DZ=0.005, I_UPPER=41,J_UPPER=41,K_UPPER=41/
&OBST XB=-0.105,-0.100,-0.105,-0.100,-0.105,-0.100
    MULT_ID='cube array'
    SURF_ID='shape'
    SHAPE='CONE'
    RADIUS=0.05
    HEIGHT=0.2
    XYZ=0,0,-0.1
    ORIENTATION=0,0,1/
```

![image-20240618100747599](..\FDS中钠燃烧模型添加.assets\image-20240618100747599.png)

最后，方框形状可以定义旋转立方体。方框形状由其高度（HEIGHT）、宽度（WIDTH）和长度（LENGTH）局部定义。方块中心的位置以 XYZ 为单位。**角度 THETA 的单位是度，它指定了方框相对于全局 Z 轴的旋转，遵循右手定则**。随后，方向矢量可以改变相对于 THETA 旋转参考帧的方向。这个方向向量可以改变方框的方向，使局部高度方向与之相匹配。图 7.17 是一个简单的示例。

```fortran
&SURF ID='shape', COLOR='GRAY'/
&MULT ID='cube array', DX=0.005,DY=0.005,DZ=0.005, I_UPPER=41,J_UPPER=41,K_UPPER=41/
&OBST XB=-0.105,-0.100,-0.105,-0.100,-0.105,-0.100
    MULT_ID='cube array'
    SURF_ID='shape'
    SHAPE='BOX'
    LENGTH=0.075
    WIDTH=0.025
    HEIGHT=0.05
    XYZ=0,0,0.01
    ORIENTATION=0.5,0,1
    THETA = 45. /
```

![image-20240618101333092](..\FDS中钠燃烧模型添加.assets\image-20240618101333092.png)



### RAMP(Ramp Function Parameters)

![image-20240530102225687](..\FDS中钠燃烧模型添加.assets\image-20240530102225687.png)

#### 与时间有关的函数设置

可以通过使用预定义函数或用户定义的函数指定时间历史来控制事物打开或关闭的速率。参数TAU_Q、TAU_T和TAU_V表示放热速率(HRRPUA)；表面温度(TMP_FRONT)；和/或法向速度(VEL, VOLUME_FLOW)或MASS_FLUX_TOTAL将增加到它们的规定值，如下所示，以热释放率$\dot{Q}\left( t \right)$为例：
$$
\dot{Q}\left( t \right)=\left\{ \begin{align}
  & {{{\dot{Q}}}_{0}}{{\left( t/\tau  \right)}^{2}}\text{if TAU }\!\!\_\!\!\text{ Q is negative} \\ 
 & {{{\dot{Q}}}_{0}}\tanh \left( t/\tau  \right)\text{  if TAU }\!\!\_\!\!\text{ Q is positive} \\ 
\end{align} \right.
$$
${{\dot{Q}}_{0}}$是用户指定的热释放率。如果火焰沿着t平方曲线上升，那么在TAU_Q秒后它保持不变。这些规则也适用于TAU_T和TAU_V。所有TAU的默认值为1秒（可以通过在MISC行设置**TAU_DEFAULT来更改默认的加速时间**）。如果需要tanh或t平方以外的增量，则可以输入用户定义的函数。为此，将RAMP_Q、RAMP_T或RAMP_V设置为一个字符串，该字符串指定用于特定表面类型的ramp 函数，然后在输入文件的某个地方生成表单的行：

```fortran
&RAMP ID='rampname1', T= 0.0, F=0.0 /
&RAMP ID='rampname1', T= 5.0, F=0.5 /
&RAMP ID='rampname1', T=10.0, F=0.7 /
```

其中，T为时间，F为放热速率、壁面温度、速度、质量分数等的比值。<font color=red>**线性插值**</font>[^f3]（**对应源码中的EVALUATE_RAMP**）用于填充中间时间点。每个RAMP行必须具有唯一的ID，并且行必须以单调递增的T列出。还要注意，TAU和RAMP是相互排斥的。对于给定的表面量，两者都不能规定。例如，可以通过管路控制一个简单的吹气孔。

------

[^f3]:默认情况下，FDS使用线性插值函数来查找用户指定点之间与时间或温度相关的值。默认的插值点数是5000，对于大多数应用来说已经足够了。但是，可以通过在任何RAMP线上指定NUMBER_INTERPOLATION_POINTS来更改此值

```fortran
&SURF ID='BLOWER', VEL=-1.2, TMP_FRONT=50., RAMP_V='BLOWER RAMP', RAMP_T='HEATER RAMP' /
&RAMP ID='BLOWER RAMP', T= 0.0, F=0.0 /
&RAMP ID='BLOWER RAMP', T=10.0, F=1.0 /
&RAMP ID='BLOWER RAMP', T=80.0, F=1.0 /
&RAMP ID='BLOWER RAMP', T=90.0, F=0.0 /
&RAMP ID='HEATER RAMP', T= 0.0, F=0.0 /
&RAMP ID='HEATER RAMP', T=20.0, F=1.0 /
&RAMP ID='HEATER RAMP', T=30.0, F=1.0 /
&RAMP ID='HEATER RAMP', T=40.0, F=0.0 /
```

使用TAU_T或RAMP_T来控制表面温度的上升。t时刻的表面温度 Tw (t)为：
$$
T_w\left(t\right)=T_0+f\left(t\right)\left(TMP{\_}FRONT-T_0\right)
$$
其中f (t)为时刻t时的 RAMP_T计算结果，T0为环境温度，TMP_FRONT 与RAMP_T在同一SURF线上指定。

#### 与温度有关的函数设置

<font color=red>**热物性**</font>，如热导率和比热会随着温度的变化而显著变化。在这种情况下，像这样使用RAMP函数：

```fortran
&MATL ID = 'STEEL'
FYI = 'A242 Steel'
SPECIFIC_HEAT_RAMP = 'c_steel'
CONDUCTIVITY_RAMP = 'k_steel'
DENSITY = 7850. /
&RAMP ID='c_steel', T= 20., F=0.45 /
&RAMP ID='c_steel', T=377., F=0.60 /
&RAMP ID='c_steel', T=677., F=0.85 /
&RAMP ID='k_steel', T= 20., F=48. /
&RAMP ID='k_steel', T=677., F=30. /
```

<font color=blue>*注意，对于temperature ramps，与time ramps相反，参数F是实际的物理量，而不是其他量的某一部分。*</font>因此，如果使用了CONDUCTIVITY_RAMP，则不应该给出电导率的值。还请注意，对于温度T，低于或高于给定范围的值，FDS 将假定等于指定的第一个或最后一个F的恒定值。还要注意，<font color=blue>*材料的密度不能用RAMP函数来控制。*</font>

:smile:如果网格中的温度高于或低于RAMP的端点，则将使用端点值。FDS将不会推断出RAMP的末端。

#### 空间依赖的速度剖面

与在SURF上使用PROFILE= ' ATMOSPHERIC '类似，可以指定PROFILE= ' RAMP '来生成表面上速度法向分量的1D或2D剖面。下面的代码在' XMIN '边界上生成一个 u(z)配置文件：

```fortran
&SURF ID='inlet', VEL=-7.72, PROFILE='RAMP', RAMP_V_Z='u_prof' /
&VENT MB='XMIN', SURF_ID='inlet'/
&RAMP ID='u_prof', T=0., F=0. /
&RAMP ID='u_prof', T=0.0098, F=0. /
&RAMP ID='u_prof', T=0.01005, F=0.2474 /
&RAMP ID='u_prof', T=0.01029, F=0.4521 /
&RAMP ID='u_prof', T=0.01077, F=0.6256 /
&RAMP ID='u_prof', T=0.01174, F=0.7267 /
&RAMP ID='u_prof', T=0.01368, F=0.8238 /
&RAMP ID='u_prof', T=0.01562, F=0.8795 /
&RAMP ID='u_prof', T=0.01756, F=0.9378 /
&RAMP ID='u_prof', T=0.0195, F=0.9663 /
&RAMP ID='u_prof', T=0.02144, F=0.9922 /
&RAMP ID='u_prof', T=0.02338, F=0.9987 /
&RAMP ID='u_prof', T=0.02532, F=1 /
&RAMP ID='u_prof', T=0.0588, F=1 /
```

注意，V表示垂直于表面的速度分量。此外，还可以指定RAMP_V_X 和RAMP_V_Y，并将它们添加到SURF中。注意，只有平面方向上的轮廓会影响给定的表面。也就是说，如果曲面面向y - z平面，则只有RAMP_V_Y和RAMP_V_Z适用。<font color=blue>*在 RAMP定义中，T是自变量，F是因变量。*</font>在本例中，T是z 坐标(以米为单位)，F是与SURF线上VEL相乘的因子。两个ramp可以应用于表面。==（不太理解）==

T不需要与FDS网格直接相关。速度点将通过ramp函数线性插值。实际上，该功能便于将实验数据直接作为FDS的边界条件。基本上只需要从数据中列出T和F(如果需要，可以设置VEL=-1 )。这种特殊情况的结果包含在FDS验证指南[^f4]的“Backward Facing Step”标题下。在此问题中，台阶高度为h = 0:0098 m， 入口型线的规格对于正确匹配台阶下游的再附着点至关重要。

-----------

[^f4]:K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 3: Validation. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 3, 40, 144

### REAC(Reaction Parameters)

| 可输入参数                    | 类型        | 描述           | 单位    | 默认   |
| ----------------------------- | ----------- | -------------- | ------- | ------ |
| A                             | Real        | Section 13.3   |         |        |
| AIT_EXCLUSION_ZONE(6,:)       | Real Array  | Section 13.1.7 | m       |        |
| AIT_EXCLUSION_ZONE_CTRL_ID(:) | Char. Array | Section 13.1.7 |         | ’null’ |
| AIT_EXCLUSION_ZONE_DEVC_ID(:) | Char. Array | Section 13.1.7 |         | ’null’ |
| AUTO_IGNITION_TEMPERATURE     | Real        | Section 13.1.7 | ℃       | -273   |
| CHECK_ATOM_BALANCE            | Logical     | Section 13.2   |         | T      |
| CO_YIELD                      | Real        | Section 13.1.1 | kg/kg   | 0      |
| CRITICAL_FLAME_TEMPERATURE    | Real        | Section 13.1.6 | ℃       | 1427   |
| E                             | Real        | Section 13.3   | J/mol   |        |
| EPUMO2                        | Real        | Section 13.1.2 | kJ/kg   | 13100  |
| EQUATION                      | Character   | Section 13.2.5 |         |        |
| FUEL                          | Character   | Section 13.1.1 |         |        |
| FUEL_C_TO_CO_FRACTION         | Real        | Section 13.1.3 |         | 2/3    |
| FUEL_H_TO_H2_FRACTION         | Real        | Section 13.1.3 |         | 0      |
| FUEL_N_TO_HCN_FRACTION        | Real        | Section 13.1.3 |         | 1/5    |
| FUEL_RADCAL_ID                | Character   | Section 13.1.1 |         |        |
| HCN_YIELD                     | Real        | Section 13.1.1 | kg/kg   | 0      |
| HEAT_OF_COMBUSTION            | Real        | Section 13.1.2 | kJ/kg   |        |
| HOC_COMPLETE                  | Real        | Section 13.1.4 | kJ/kg   |        |
| ID                            | Character   | Section 13.1.1 |         |        |
| IDEAL                         | Logical     | Section 13.1.1 |         | F      |
| LOWER_OXYGEN_LIMIT            | Real        | Section 13.1.6 | mol/mol |        |
| N_S(:)                        | Real Array  | Section 13.3   |         |        |
| N_SIMPLE_CHEMISTRY_REACTIONS  | Integer     | Section 13.1.3 |         | 1      |
| N_T                           | Real        | Section 13.3   |         |        |
| NU(:)                         | Real Array  | Section 13.3   |         |        |
| PRIORITY                      | Integer     | Section 13.2.3 |         | 1      |
| RADIATIVE_FRACTION            | Real        | Section 14.1   |         |        |
| RAMP_CHI_R                    | Character   | Section 14.1   |         |        |
| REAC_ATOM_ERROR               | Real        | Section 13.2   | atoms   | 1.E-5  |
| REAC_MASS_ERROR               | Real        | Section 13.2   | kg/kg   | 1.E-4  |
| REVERSE                       | Logical     | Section 13.3.2 |         | F      |
| SOOT_YIELD                    | Real        | Section 13.1.1 | kg/kg   | 0.0    |
| SPEC_ID_N_S(:)                | Char. Array | Section 13.3   |         |        |
| SPEC_ID_NU(:)                 | Char. Array | Section 13.3   |         |        |
| THIRD_BODY                    | Logical     | Section 13.3   |         | F      |
| THIRD_EFF(:)                  | Real Array  | Section 13.3.3 |         |        |
| THIRD_EFF_ID(:)               | Char. Array | Section 13.3.3 |         |        |

对于单步反映：丙烷完全燃烧
$$
C_3H_8+5O_2\to3CO_2+4H_2O
$$
丙烷的速率表达式为：$\frac{\mathrm{d}C_{{\mathrm{C_{3}H_{8}}}}}{\mathrm{d}t}=-k\prod{C_{\alpha}}^{{N_{S,\alpha}}}$。其中，$C_{\alpha}$为组分$\alpha$的浓度，单位为$mol/cm^3$，反应率常数定义为$k=AT^{N_T}\mathrm{e}^{-E_a/RT}$。

$A$为指前因子（$((\mathrm{mol/cm}^3)^{1-n})/\mathrm{s}$），$n=\sum N_{S,\alpha}$为反应级数。

$E_a$为活化能（$J/mol$）

$N_{S,\alpha}$为包含浓度指数的数组，默认值为化学计量系数。

$N_T$为温度指数，默认值为0，表示没有温度相关性。

$R$为通用气体常数，$8.314J/(mol\cdot K)$。

单步丙烷反应速率表达式为：
$$
\frac{\mathrm{d}C_{\mathrm{C}_3\mathrm{H}_8}}{\mathrm{d}t}=-8.6\times10^{11}T^0\mathrm{~e}^{-125520/RT}C_{\mathrm{C}_3\mathrm{H}_8}^{0.1}C_{\mathrm{O}_2}^{1.65}
$$
`REAC`的输入参数如下：

```fortran
&REAC ID = 'R1'
        FUEL = 'PROPANE'
        A = 8.6e11
        E = 125520
        SPEC_ID_NU = 'PROPANE','OXYGEN','CARBON DIOXIDE','WATER VAPOR'
        NU = -1,-5,3,4
        SPEC_ID_N_S = 'PROPANE','OXYGEN'
        N_S = 0.1,1.65 /
```

`SPEC_ID_NU`包含化学反应中**被追踪的组分**，若原始组分设置了`LUMPED_COMPONENT_ONLY=T`则不会被追踪。

`SPEC_ID_N_S`包含有指数`N_S`的组分，代表上述的$N_{S,\alpha}$，且只能包含原始组分。化学计量系数`NU`直接通过化学反映得到。

`AUTO_IGNITION_TEMPERATURE`自动点燃温度（℃），低于此温度时不会发生燃烧。当网格尺寸大于10厘米时，AIT值可能需要降低。AIT的目的只是为了防止燃料和氧气自燃，这是FDS的默认行为。

`AIT_EXCLUSION_ZONE`指定一个体积，即使在其他地方强制执行AIT，也会自动着火。参数分别为xyz的下限和上限。

如果一个复杂化学反应（非C、H、O）被指定了，FUEL输入可以不要求，FDS会假定SPEC_ID_NU中的第一个物质为燃料（NU为负）。



### SLCF (Slice File Parameters)

| 可输入参数    | 类型       | 描述                       | 单位 | 默认 |
| ------------- | ---------- | -------------------------- | ---- | ---- |
| AGL_SLICE     | Real       | Section 22.10.20           | m    |      |
| CELL_CENTERED | Logical    | Section 22.4               |      | F    |
| DB            | Character  | Section 22.4               |      |      |
| ID            | Character  | Section 22.4               |      |      |
| MAXIMUM_VALUE | Real       | Reference [^17]            |      |      |
| MESH_NUMBER   | Integer    | Section 22.4               |      |      |
| MINIMUM_VALUE | Real       | Reference [^17]            |      |      |
| PART_ID       | Character  | Section 22.12              |      |      |
| PBX, PBY, PBZ | Real       | Section 22.4               | m    |      |
| PROP_ID       | Character  | Section 22.10.18           |      |      |
| QUANTITY      | Character  | Section 22.12              |      |      |
| QUANTITY2     | Character  | Section 22.12              |      |      |
| REAC_ID       | Character  | See QUANTITY=‘HRRPUV REAC‘ |      |      |
| SPEC_ID       | Character  | Section 22.12              |      |      |
| VECTOR        | Logical    | Section 22.4               |      | F    |
| VELO_INDEX    | Integer    | Section 22.10.24           |      | 0    |
| XB(6)         | Real Array | Section 22.4               | m    |      |

通过 SLCF（"切片文件"）名表组参数（表 23.29）可以记录多个点的各种气相量。切片 "是指整个域的一个子集。它可以是一条线、一个平面或一个体积，具体取决于 XB 的值。六元组 XB 表示 "切片 "平面的边界。**XB 的规定与 OBST 或 VENT 组相同，6 个值中可以有 0、2 或 4 个相同，分别表示体积、平面或直线**。举例来说，如果希望保存整个平面 y = 5.3 的域切面，可以指定 PBY=5.3 而不是 XB。PBX 和 PBZ 分别控制垂直于 x 轴和 z 轴的平面。另一种指定域中间切平面的方法是使用 DB，其值为 "XMID"、"YMID "或 "ZMID"。**:exclamation:对于3D切片，在Smokeview中打开该切片后，键盘上执行“w“切换3D范围**。

默认情况下，每次模拟都会保存 1-D 和 2-D 切片文件 NFRAMES 次。您可以使用 DUMP 行中的 DT_SLCF 控制输出频率。如果 "切片 "是三维体，则其输出频率由参数 DT_SL3D 控制。您可以在 DUMP 上指定 DT_SL3D 的值，也可以提供一系列离散时间。请注意，如果 DT_SL3D 较小，3-D 切片文件可能会变得非常大。

如果给定的 SLCF 线条具有 VECTOR=T 属性，则可在 Smokeview 中创建动画矢量。如果两个 SLCF 条目在同一平面内，则只需其中一条线具有 VECTOR=T 属性，否则将创建一组多余的速度分量切片。

**通常情况下，FDS 在单元角处平均切片文件数据**。例如，**气体温度是在单元中心计算的，但它们被线性插值到单元角**，并输出到 Smokeview 读取的文件中。<font color=red>为避免这种情况发生，可设置 CELL_CENTERED=T 这样 FDS 就会强制输出以单元格为中心的实际数据，而不进行平均</font>。请注意，此功能主要用于诊断，因为它可以让您直观地看到 FDS 实际计算的值。如果 CELL_CENTERED=T 与 VECTOR=T 结合使用，则将显示交错的速度分量。例如

```fortran
&SLCF PBY=0, QUANTITY='VELOCITY', VECTOR=T, CELL_CENTERED=T /
```

将在 Smokeview 中以单元面法向量的形式显示交错的速度分量。

切片文件信息记录在标有 CHID_n.sf 的文件中（见第 27.9 节），其中 n 是切片文件的索引。一个简短的 Fortran 程序 fds2ascii.f90 可以从一行、一个平面或一卷数据中生成一个文本文件。详见第 22.11 节。

默认情况下，Smokeview 会对障碍物内的切片文件数据进行空白处理。但是，对于大型案例，在 Smokeview 启动时加载这一功能的成本很高。如果希望 Smokeview 不存储此空白阵列，可在 MISC 上设置 IBLANK_SMV=F。另一种方法是从命令行运行 Smokeview，并添加 -noblank 作为选项。

您可以通过 SLCF 上的 ID 添加名称，作为发送到 Smokeview 的标识符。这只是可选项。



### SPEC(Species Parameters)

| 可输入参数                  | 类型        | 描述             | 单位     | 默认  |
| --------------------------- | ----------- | ---------------- | -------- | ----- |
| AEROSOL                     | Logical     | Section 13.4     |          | F     |
| **BACKGROUND**              | Logical     | Section 12       |          | F     |
| BETA_LIQUID                 | Real        | Section 15.3.1   | 1/K      |       |
| C                           | Real        | Section 12.1.2   |          |       |
| CONDUCTIVITY                | Real        | Section 12.1.2   | W/(mK)   |       |
| CONDUCTIVITY_LIQUID         | Real        | Section 15.3.1   | W/(mK)   |       |
| CONDUCTIVITY_SOLID          | Real        | Section 13.4     | W/(mK)   | 0.26  |
| COPY_LUMPED                 | Logical     | Section 12.2     |          | F     |
| DENSITY_LIQUID              | Real        | Section 15.3.1   | $kg/m^3$ |       |
| DENSITY_SOLID               | Real        | Section 13.4     | $kg/m^3$ | 1800. |
| DIFFUSIVITY                 | Real        | Section 12.1.3   | $m^2/s$  |       |
| ENTHALPY_OF_FORMATION       | Real        | Section 15.3.1   | kJ/mol   |       |
| EPSILONKLJ                  | Real        | Section 12.1.2   |          | 0.    |
| FIC_CONCENTRATION           | Real        | Section 22.10.18 | ppm      | 0.    |
| FLD_LETHAL_DOSE             | Real        | Section 22.10.18 | ppm×min  | 0.    |
| FORMULA                     | Character   | Section 12.1.2   |          |       |
| H                           | Real        | Section 12.1.2   |          |       |
| HEAT_OF_VAPORIZATION        | Real        | Section 15.3.1   | kJ/kg    |       |
| H_V_REFERENCE_TEMPERATURE   | Real        | Section 15.3.1   | ℃        |       |
| ID                          | Character   | Section 12.1.1   |          |       |
| LUMPED_COMPONENT_ONLY       | Logical     | Section 12.2     |          | F     |
| MASS_EXTINCTION_COEFFICIENT | Real        | Section 18.3.5   |          | 0     |
| MASS_FRACTION(:)            | Real Array  | Section 12.2     |          | 0     |
| MASS_FRACTION_0             | Real        | Section 12.1.1   |          | 0     |
| MASS_FRACTION_COND_0        | Real        | Section 13.7     |          | 0     |
| MAX_DIAMETER                | Real        | Section 13.5     | m        |       |
| MEAN_DIAMETER               | Real        | Section 13.4     | m        |       |
| MELTING_TEMPERATURE         | Real        | Section 15.3.1   | ℃        |       |
| MIN_DIAMETER                | Real        | Section 13.5     | m        |       |
| MW                          | Real        | Section 12.1.2   | g/mol    | 29.   |
| N                           | Real        | Section 12.1.2   |          |       |
| N_BINS                      | Integer     | Section 13.5     |          |       |
| O                           | Real        | Section 12.1.2   |          |       |
| PR_GAS                      | Real        | Section 12.1.2   |          | PR    |
| PRIMITIVE                   | Logical     | Section 12.1.2   |          |       |
| RADCAL_ID                   | Character   | Section 12.1.5   |          |       |
| RAMP_CP                     | Character   | Section 12.1.2   |          |       |
| RAMP_CP_L                   | Character   | Section 15.3.1   |          |       |
| RAMP_D                      | Character   | Section 12.1.2   |          |       |
| RAMP_G_F                    | Character   | Section 12.1.2   |          |       |
| RAMP_K                      | Character   | Section 12.1.2   |          |       |
| RAMP_MU                     | Character   | Section 12.1.2   |          |       |
| REFERENCE_ENTHALPY          | Real        | Section 12.1.2   |          |       |
| REFERENCE_TEMPERATURE       | Real        | Section 12.1.2   | kJ/kg    | 25.   |
| SIGMALJ                     | Real        | Section 12.1.2   | ℃        | 0     |
| SPEC_ID(:)                  | Char. Array | Section 12.2     |          |       |
| SPECIFIC_HEAT               | Real        | Section 12.1.2   | kJ/(kgK) |       |
| SPECIFIC_HEAT_LIQUID        | Real        | Section 15.3.1   | kJ/(kgK) |       |
| THERMOPHORETIC_DIAMETER     | Real        | Section 13.4     | m        |       |
| TURBULENT_SCHMIDT_NUMBER    | Real        | Section 12.1.2   |          | 0.5   |
| VAPORIZATION_TEMPERATURE    | Real        | Section 15.3.1   | ℃        |       |
| VISCOSITY                   | Real        | Section 12.1.2   | kg/(ms)  |       |
| VISCOSITY_LIQUID            | Real        | Section 15.3.1   | kg/(ms)  |       |
| VOLUME_FRACTION(:)          | Real Array  | Section 12.2     |          |       |

如果要使用一个物种作为背景物种，则应该在SPEC行设置参数`background =T`。**默认的背景物种是AIR**，它被定义为由N2、O2、CO2和H2O组成的集总物种。

如果在输入文件中没有定义背景物种，那么FDS将通过在内部创建如下所示的输入行来创建AIR的背景物种。

```fortran
&SPEC ID='NITROGEN', LUMPED_COMPONENT_ONLY=T /
&SPEC ID='OXYGEN', LUMPED_COMPONENT_ONLY=T /
&SPEC ID='WATER VAPOR', LUMPED_COMPONENT_ONLY=T /
&SPEC ID='CARBON DIOXIDE', LUMPED_COMPONENT_ONLY=T /
&SPEC ID='AIR', BACKGROUND=T,
        SPEC_ID(1)='NITROGEN', MASS_FRACTION(1)=0.76274,
        SPEC_ID(2)='OXYGEN', MASS_FRACTION(2)=0.23054,
        SPEC_ID(3)='WATER VAPOR', MASS_FRACTION(3)=0.00626,
        SPEC_ID(4)='CARBON DIOXIDE', MASS_FRACTION(4)=0.00046 /
```

假设扩散系数是**给定物种和背景物种之间的二元扩散系数**。

`EPSILONKLJ`和`SIGMALJ`是Lennard-Jones中的势参数，可以用来计算导热系数和扩散系数。

当定义集总种类时，必须使用MASS_FRACTION或VOLUME_FRACTION来定义物质组分。

:smile:**如果不是一个简单的化学问题，则应该指定PVC的生成焓或反应的燃烧热**。



### SURF(Surface Properties)

与对流传热系数一样（Section 8.2.2），有一个选项可以指定一个固定的`MASS_TRANSFER_COEFFICIENT`(m/s)在描述液池的SURF线上。

| 可输入参数                          | 类型           | 描述           | 单位         | 默认        |
| ----------------------------------- | -------------- | -------------- | ------------ | ----------- |
| ADIABATIC                           | Real           | Section 8.2.3  |              | F           |
| AREA_MULTIPLIER                     | Real           | Section 9.1.2  |              | 1.0         |
| BACKING                             | Character      | Section 8.3.3  |              | ’EXPOSED’   |
| BLOWING                             | Logical        | Section 8.2.2  |              |             |
| BURN_AWAY                           | Logical        | Section 9.2.8  |              | F           |
| BURN_DURATION                       | Real           | Section 9.2.7  | s            | 1000000     |
| CELL_SIZE(:)                        | Real Array     | Section 8.3.8  | m            |             |
| CELL_SIZE_FACTOR(:)                 | Real Array     | Section 8.3.8  |              | 1.0         |
| COLOR                               | Character      | Section 7.5    |              |             |
| CONVECTION_LENGTH_SCALE             | Real           | Section 8.2.2  | m            | 1.          |
| CONVECTIVE_HEAT_FLUX                | Real           | Section 8.2.2  | $kW/m^2$     |             |
| CONVERT_VOLUME_TO_MASS              | Logical        | Section 10.1.6 |              | F           |
| DEFAULT                             | Logical        | Section 7.1    |              | F           |
| DELTA_TMP_MAX                       | Real           | Section 8.3.8  | ℃            | 10          |
| DRAG_COEFFICIENT                    | Real           | Section 17.3   |              | 2.8         |
| DT_INSERT                           | Real           | Section 15.5.1 | s            | 0.01        |
| E_COEFFICIENT                       | Real           | Section 15.7   | $m^2/(kgs)$  |             |
| EMBER_GENERATION_HEIGHT(2)          | Real           | Section 17.5.2 | m            |             |
| EMBER_IGNITION_POWER_MEAN           | Real           | Section 17.5.3 | kW           |             |
| EMBER_IGNITION_POWER_SIGMA          | Real           | Section 17.5.3 | kW           | 0.001       |
| EMBER_TRACKING_RATIO                | Real           | Section 17.5.2 |              | 100         |
| EMBER_YIELD                         | Real           | Section 17.5.2 | kg/kg        |             |
| EMISSIVITY                          | Real           | Section 8.2.2  |              | 0.9         |
| EMISSIVITY_BACK                     | Real           | Section 8.3.3  |              |             |
| EXTERNAL_FLUX                       | Real           | Section 9.3    | $kW/m^2$     |             |
| EXTINCTION_TEMPERATURE              | Real           | Section 9.1.3  | ℃            | -273.       |
| FREE_SLIP                           | Logical        | Section 10.1.7 |              | F           |
| GEOMETRY                            | Character      | Section 8.3.7  |              | ’CARTESIAN’ |
| HEAT_OF_VAPORIZATION                | Real           | Section 9.1.3  | kJ/kg        |             |
| HEAT_TRANSFER_COEFFICIENT           | Real           | Section 8.2.2  | $W/(m^2K)$   |             |
| HEAT_TRANSFER_COEFFICIENT_BACK      | Real           | Section 8.2.2  | $W/(m^2K)$   |             |
| HEAT_TRANSFER_MODEL                 | Character      | Section 8.2.2  |              |             |
| HORIZONTAL                          | Logical        | Section 8.3.7  |              | F           |
| HRRPUA                              | Real           | Section 9.1    | $kW/m^2$     |             |
| HT3D                                | Logical        | Section 8.4    |              | F           |
| ID                                  | Character      | Section 7.1    |              |             |
| IGNITION_TEMPERATURE                | Real           | Section 9.1.3  | ℃            | 5000.       |
| INERT_Q_REF                         | Logical        | Section 9.1.4  |              | F           |
| INIT_IDS                            | Char. Array    | Section 17.2.1 |              |             |
| INIT_PER_AREA                       | Real           | Section 17.2.1 | $m^{−2}$     |             |
| INNER_RADIUS                        | Real           | Section 15.4.1 | m            |             |
| INTERNAL_HEAT_SOURCE                | Real Array     | Section 8.3.6  | $kW/m^3$     |             |
| LAYER_DIVIDE                        | Real           | Section 8.3.5  |              | N_LAYERS/2  |
| LEAK_PATH                           | Int. Pair      | Section 10.3.2 |              |             |
| LEAK_PATH_ID                        | Character Pair | Section 10.3.2 |              |             |
| LENGTH                              | Real           | Section 15.4.1 | m            |             |
| MASS_FLUX(:)                        | Real Array     | Section 10.1.6 | $kg/(m^2 s)$ |             |
| MASS_FLUX_TOTAL                     | Real           | Section 10.1.2 | $kg/(m^2 s)$ |             |
| MASS_FLUX_VAR                       | Real           | Section 10.1.9 |              |             |
| MASS_FRACTION(:)                    | Real Array     | Section 10.1.6 |              |             |
| MASS_PER_VOLUME(:)                  | Real Array     | Section 17.2   | $kg/m^3$     |             |
| MASS_TRANSFER_COEFFICIENT           | Real           | Section 9.2.6  | m/s          |             |
| MATL_ID(:,:)                        | Char. Array    | Section 9.2    |              |             |
| MATL_MASS_FRACTION(:,:)             | Real Array     | Section 9.2    |              |             |
| MAXIMUM_SCALING_HEAT_FLUX           | Real           | Section 9.1.4  | $kW/m^2$     |             |
| MINIMUM_BURNOUT_TIME                | Real           | Section 17.3.1 | s            | 1000000     |
| MINIMUM_LAYER_THICKNESS             | Real           | Section 8.3.8  | m            | 1.E-4       |
| MINIMUM_SCALING_HEAT_FLUX           | Real           | Section 9.1.4  | $kW/m^2$     | 0           |
| MLRPUA                              | Real           | Section 9.1    | $kg/(m^2 s)$ |             |
| MOISTURE_FRACTION(:)                | Real Array     | Section 17.2   |              | 0.          |
| N_LAYER_CELLS_MAX(:)                | Integer Array  | Section 8.3.8  |              | 1000        |
| NEAR_WALL_EDDY_VISCOSITY            | Real           | Section 19.2   | $m^2/s$      |             |
| NEAR_WALL_TURBULENCE_MODEL          | Character      | Section 19.2   |              |             |
| NET_HEAT_FLUX                       | Real           | Section 8.2.2  | $kW/m^2$     |             |
| NO_SLIP                             | Logical        | Section 10.1.7 |              | F           |
| NPPC                                | Integer        | Section 15.5.1 |              | 1           |
| NUSSELT_C0                          | Real           | Section 8.2.2  |              |             |
| NUSSELT_C1                          | Real           | Section 8.2.2  |              |             |
| NUSSELT_C2                          | Real           | Section 8.2.2  |              |             |
| NUSSELT_M                           | Real           | Section 8.2.2  |              |             |
| PARTICLE_EXTRACTION_VELOCITY        | Real           | Section 15.6   | m/s          |             |
| PARTICLE_MASS_FLUX                  | Real           | Section 15.5.1 | $kg/(m^2 s)$ |             |
| PARTICLE_SURFACE_DENSITY            | Real           | Section 15.5.1 | $kg/m^2$     |             |
| PART_ID                             | Character      | Section 15.5.1 |              |             |
| PLE                                 | Real           | Section 16.5   |              | 0.3         |
| PROFILE                             | Character      | Section 10.5   |              |             |
| RADIUS                              | Real           | Section 15.4.1 | m            |             |
| RAMP_EF                             | Character      | Section 11.1   |              |             |
| RAMP_HEAT_TRANSFER_COEFFICIENT      | Real           | Section 8.2.2  |              |             |
| RAMP_HEAT_TRANSFER_COEFFICIENT_BACK | Real           | Section 8.2.2  |              |             |
| RAMP_MF(:)                          | Character      | Section 11.1   |              |             |
| RAMP_PART                           | Character      | Section 11.1   |              |             |
| RAMP_Q                              | Character      | Section 11.1   |              |             |
| RAMP_T                              | Character      | Section 11.1   |              |             |
| RAMP_T_I                            | Character      | Section 8.3.4  |              |             |
| RAMP_TMP_BACK                       | Character      | Section 8.3.9  |              |             |
| RAMP_TMP_GAS_BACK                   | Character      | Section 8.3.3  |              |             |
| RAMP_TMP_GAS_FRONT                  | Character      | Section 8.3.3  |              |             |
| RAMP_V                              | Character      | Section 11.1   |              |             |
| RAMP_V_X                            | Character      | Section 11.3   |              |             |
| RAMP_V_Y                            | Character      | Section 11.3   |              |             |
| RAMP_V_Z                            | Character      | Section 11.3   |              |             |
| REFERENCE_HEAT_FLUX                 | Real Array     | Section 9.1.4  | $kW/m^2$     |             |
| REFERENCE_HEAT_FLUX_TIME_INTERVAL   | Real           | Section 9.1.4  | s            | 1.0         |
| REFERENCE_THICKNESS                 | Real Array     | Section 9.1.4  | m            |             |
| RENODE_DELTA_T                      | Real           | Section 8.3.8  | K            | 2           |
| RGB(3)                              | Integer Array  | Section 7.5    |              | 255,204,102 |
| ROUGHNESS                           | Real           | Section 10.1.7 | m            | 0.          |
| SHAPE_FACTOR                        | Real           | Section 17.3   |              | 0.25        |
| SPEC_ID                             | Character      | Section 10.1.6 |              |             |
| SPREAD_RATE                         | Real           | Section 9.1.1  | m/s          |             |
| STRETCH_FACTOR(:)                   | Real Array     | Section 8.3.8  |              | 2.          |
| SURFACE_VOLUME_RATIO(:)             | Real           | Section 17.2   | 1/m          |             |
| TAU_EF                              | Real           | Section 11.1   | s            | 1.          |
| TAU_MF(:)                           | Real Array     | Section 11.1   | s            | 1.          |
| TAU_PART                            | Real           | Section 11.1   | s            | 1.          |
| TAU_Q                               | Real           | Section 11.1   | s            | 1.          |
| TAU_T                               | Real           | Section 11.1   | s            | 1.          |
| TAU_V                               | Real           | Section 11.1   | s            | 1.          |
| TEXTURE_HEIGHT                      | Real           | Section 7.5.2  | m            | 1.          |
| TEXTURE_MAP                         | Character      | Section 7.5.2  |              |             |
| TEXTURE_WIDTH                       | Real           | Section 7.5.2  | m            | 1.          |
| TGA_ANALYSIS                        | Logical        | Section 9.3.2  |              | F           |
| TGA_FINAL_TEMPERATURE               | Real           | Section 9.3.2  | ℃            | 800.        |
| TGA_HEATING_RATE                    | Real           | Section 9.3.2  | ℃/min        | 5.          |
| THICKNESS(:)                        | Real Array     | Section 8.1    | m            |             |
| TIME_STEP_FACTOR                    | Real           | Section 8.3.8  |              | 10.         |
| TMP_BACK                            | Real           | Section 8.3.9  | ℃            |             |
| TMP_FRONT                           | Real           | Section 8.2.1  | ℃            | 20.         |
| TMP_FRONT_INITIAL                   | Real           | Section 8.2.3  | ℃            |             |
| TMP_GAS_FRONT                       | Real           | Section 8.3.3  | ℃            |             |
| TMP_GAS_BACK                        | Real           | Section 8.3.3  | ℃            |             |
| TMP_INNER                           | Real           | Section 8.3.4  | ℃            | 20.         |
| TRANSPARENCY                        | Real           | Section 7.5    |              | 1.          |
| VARIABLE_THICKNESS                  | Logical        | Section 8.4.5  |              | F           |
| VEG_LSET_BETA                       | Real           | Section 17.5   |              | 0.          |
| VEG_LSET_CHAR_FRACTION              | Real           | Section 17.5   |              | 0.2         |
| VEG_LSET_FIREBASE_TIME              | Real           | Section 17.5   | s            |             |
| VEG_LSET_FUEL_INDEX                 | Integer        | Section 17.5   |              |             |
| VEG_LSET_HT                         | Real           | Section 17.5   |              | 0.          |
| VEG_LSET_IGNITE_TIME                | Real           | Section 17.5   | s            |             |
| VEG_LSET_M1                         | Real           | Section 17.5   |              | 0.03        |
| VEG_LSET_M10                        | Real           | Section 17.5   |              | 0.04        |
| VEG_LSET_M100                       | Real           | Section 17.5   |              | 0.05        |
| VEG_LSET_MLW                        | Real           | Section 17.5   |              | 0.70        |
| VEG_LSET_MLH                        | Real           | Section 17.5   |              | 0.70        |
| VEG_LSET_QCON                       | Real           | Section 17.5   | $kW/m^2$     | 0.          |
| VEG_LSET_ROS_00                     | Real           | Section 17.5   | m/s          | 0.          |
| VEG_LSET_ROS_BACK                   | Real           | Section 17.5   | m/s          | 0.          |
| VEG_LSET_ROS_FLANK                  | Real           | Section 17.5   | m/s          | 0.          |
| VEG_LSET_ROS_HEAD                   | Real           | Section 17.5   | m/s          | 0.          |
| VEG_LSET_SIGMA                      | Real           | Section 17.5   | 1/m          | 0.          |
| VEG_LSET_SURF_LOAD                  | Real           | Section 17.5   | $kg/m^2$     | 0.3         |
| VEG_LSET_TAN2                       | Real           | Section 17.5   |              |             |
| VEG_LSET_WIND_EXP                   | Real           | Section 17.5   |              | 1.          |
| VEL                                 | Real           | Section 10.1   | m/s          |             |
| VEL_BULK                            | Real           | Section 10.5   | m/s          |             |
| VEL_GRAD                            | Real           | Section 10.1.5 | 1/s          |             |
| VEL_PART                            | Real           | Section 15.5.1 | m/s          |             |
| VEL_T(2)                            | Real Array     | Section 10.1.4 | m/s          |             |
| VOLUME_FLOW                         | Real           | Section 10.1   | $m^3/s$      |             |
| WIDTH                               | Real           | Section 15.4.1 | m            |             |
| XYZ(3)                              | Real Array     | Section 9.1.1  | m            |             |
| Z0                                  | Real           | Section 16.5   | m            | 10.         |
| Z_0                                 | Real           | Section 16.2.2 | m            | 0.          |



`TMP_INNER`如果表面不是绝热的，它有材料属性，使用TMP_INNER来设置表面和内部温度。



### TIME (Time Parameters)

| 可输入参数         | 类型    | 描述          | 单位 | 默认          |
| ------------------ | ------- | ------------- | ---- | ------------- |
| DT                 | Real    | Section 6.2.2 | s    |               |
| DT_END_FILL        | Real    | Section 6.2.2 | s    | $1.0×10^{−6}$ |
| DT_END_MINIMUM     | Real    | Section 6.2.2 | s    | 2.*EPSILON    |
| DT_EXTERNAL        | Real    | Section 18.8  | s    | 0             |
| LIMITING_DT_RATIO  | Real    | Section 4.2   |      | 0.0001        |
| LOCK_TIME_STEP     | Logical | Section 6.2.2 |      | F             |
| RESTRICT_TIME_STEP | Logical | Section 6.2.2 |      | T             |
| T_BEGIN            | Real    | Section 6.2.1 | s    | 0.            |
| T_END              | Real    | Section 6.2.1 | s    | 1.            |
| TIME_SHRINK_FACTOR | Real    | Section 6.2.3 |      | 1.            |
| WALL_INCREMENT     | Integer | Section 8.3.8 |      | 2             |

TIME 是一组参数的名称，用于定义模拟的持续时间和用于推进离散方程求解的初始时间步长。

#### Basics

通常情况下，只需通过参数 T_END 在这一行输入模拟的持续时间。默认值为 1 秒。 例如，下一行将指示 FDS 运行模拟 5400 秒。

```fortran
&TIME T_END=5400. /
```

如果将 T_END 设为零，则只执行设置工作，以便在 Smokeview 中快速检查几何体。

要以零以外的数字开始时间线，可使用参数 T_BEGIN 指定写入文件的第一个时间步的时间。这对于匹配实验数据或视频记录的时间线非常有用。

#### Controlling the Time Step

**可以用 DT 指定初始时间步长**。该参数通常是通过网格单元的大小除以流动的特征速度自动设置的。在计算过程中，会对时间步长进行调整，以满足 CFL（Courant、Friedrichs、Lewy）条件。DT的默认值为$(\delta x\delta y\delta z)^{\frac13}/V_{\mathrm{char}}$ s。特征速度尺度估计为$V_{char}=0.2\sqrt{gH}\mathrm{~ m/s}$，$\delta x$、$\delta y$、$\delta z$是最小网格单元的尺寸，$H$是计算域的高度，$g$是重力加速度。从物理上讲，特征速度是浮力烟羽在计算域高度上的平均速度估计值，它为典型火灾模拟中的时间步长提供了合理的初始值。默认情况下，时间步长不允许超过其初始值。要允许这种情况发生，请设置 RESTRICT_TIME_STEP=F。

如果在模拟开始时会有突发事件发生，如喷水灭火器启动，那么设置初始时间步长以避免因时间步长过大而导致数值不稳定是有好处的。通过监控输出文件 job_name.out 中记录的初始时间步长，尝试使用不同的 DT 值。

**在显式预测-校正时间更新的第一部分结束时，将对时间步长进行检查，以确保其在适当的稳定范围内**。如果不在范围内，则将时间步长向上或向下调整 10%（或直到在范围内），并重新运行时间步长的预测部分。如果要防止 FDS 自动改变时间步长，**可在 TIME 行设置 LOCK_TIME_STEP 等于 T**，这样就不会调整指定的时间步长 DT。该参数仅用于诊断目的，例如为程序执行计时。如果初始时间步长设置过高，可能会导致数值不稳定。

名为 CHID.out 的诊断输出文件包含每个网格的时间步长和 CFL 编号信息。但是，对于涉及数十或数百个网格的仿真，评估全局时间步长信息可能比较困难。**对于时间步长的详细信息，有一个名为 CHID_cfl.csv 的可选输出文件**，其中包含每个时间步长的时间（秒）、时间步长大小（秒）、最大 CFL 数、出现最大 CFL 值的网格和网格索引、出现最大 CFL 数的网格单元六个面上的六个速度分量，以及出现最大 CFL 的发散（1/s）、粘度（kg/m/s）、HRRPUV（kW/m3）和燃烧混合时间（秒）。此外，还列出了最大 VN（冯-诺依曼）数以及出现该值的网格和单元指数。<font color=red>**要输出此文件，请在 DUMP 行将 CFL_FILE 设置为 T。通常设置为 F**</font>。

**The Final Time Step**

**在某些特殊情况下，可能需要控制计算的最后时间步长**。默认情况下，**FDS 将最后一个时间步长设置为 T_END - T**，其中 T 为当前时间。由于采用浮点运算，最后时间步长可能会非常小，从而导致意想不到的后果。您可以使用参数 DT_END_MINIMUM 或 DT_END_FILL（不必同时使用这两个参数）来控制最后的时间步长。使用 DT_END_MINIMUM 的效果是为最终时间步长设置一个最小值，因此 T_END 不会被严格遵守（因此我们默认的 DT_END_MINIMUM 值大致为机器ε）。最终的模拟时间将是 T + DT_END_MINIMUM。或者，也可以将 DT_END_FILL 设置为某个值（应小于最后一个时间步长）。如果 T+DT+DT_END_FILL > T_END，其中 DT 是计算出的稳定时间步长（或指定的时间步长），FDS 将重新计算时间步长为 DT = T_END - T。

#### Steady-State Applications

在某些应用中，有时只需要稳态解（时间平均意义上的）。在 FDS 等随时间变化的代码中，达到稳态要求模拟运行足够长的时间，以形成稳态流场和气体温度场，并在固体表面形成稳态温度曲线。**由于必须对表面进行深度加热，因此形成稳态温度曲线可能需要很长时间**。这可能导致计算成本过高。**在稳态边界条件下，表面升温所需的时间与其比热成正比**。因此，在稳定条件下，可以通过降低比热来加快加热时间。因此保持架 MATL 中的 SPECIFIC_HEAT 不变，但仍能提供缩短表面加热时间的方法，**可以使用 TIME_SHRINK_FACTOR 的 MISC 输入**。<font color=red>MATL 上的 SPECIFIC_HEAT 输入值将根据该系数进行缩减</font>。当 TIME_SHRINK_FACTOR 为 10 时，各种材料的比热会降低 10 倍。这可将固体材料的加热速度大致提高 10 倍。在验证实验中，一个稳定的热源会将一个隔间加热到接近平衡状态，此时测量的是时间平均流量。

TIME_SHRINK_FACTOR 不会缩短流量和气体温度场的形成时间，但其形成速度往往比壁温曲线快得多。

请注意，当使用 TIME_SHRINK_FACTOR 时，QUANTITY='TIME'的设备或带有 DELAY 的设备或控制功能的值将根据 TIME_SHRINK_FACTOR 的值进行调整。例如，如果为 TIME_SHRINK_FACTOR 为 10 的 CTRL 输入指定了 10 秒的 DELAY，那么 FDS 将把 DELAY 调整为 1 秒。然而，使用基于时间的设备或控制功能会改变模拟结果，这意味着**非稳定的情况下可能不再适合使用 TIME_SHRINK_FACTOR**。

`WALL_INCREMENT`：改进时间解析度。将其设置为1，会迫使固相求解在每个时间步更新而不是每两个时间步。

### VENT(Vent Parameters)

| 可输入参数           | 类型          | 描述           | 单位      | 默认       |
| -------------------- | ------------- | -------------- | --------- | ---------- |
| COLOR                | 字符型        | Section 7.5    |           |            |
| CTRL_ID              | 字符型        | Section 18.4.2 |           |            |
| DB                   | 字符型        | Section 7.4.1  |           |            |
| DEVC_ID              | 字符型        | Section 18.4.2 |           |            |
| DYNAMIC_PRESSURE     | Real          | Section 10.4   | Pa        | 0.         |
| GEOM                 | Logical       | Section 17.5   |           | F          |
| ID                   | 字符型        | Section 7.4.1  |           |            |
| IOR                  | Integer       | Section 7.4.4  |           |            |
| L_EDDY               | Real          | Section 10.1.8 | m         | 0.         |
| L_EDDY_IJ(3,3)       | Real Array    | Section 10.1.8 | m         | 0.         |
| MB                   | 字符型        | Section 7.4.1  |           |            |
| MULT_ID              | 字符型        | Section 7.6    |           |            |
| N_EDDY               | Integer       | Section 10.1.8 |           | 0          |
| OBST_ID              | 字符型        | Section 18.4.2 |           |            |
| OUTLINE              | Logical       | Section 7.4.1  |           | F          |
| PBX, PBY, PBZ        | Real          | Section 7.4.1  |           |            |
| PRESSURE_RAMP        | 字符型        | Section 10.4   |           |            |
| RADIUS               | Real          | Section 7.4.2  | m         |            |
| REYNOLDS_STRESS(3,3) | Real Array    | Section 10.1.8 | $m^2/s^2$ | 0.         |
| RGB(3)               | Integer Array | Section 7.5    |           |            |
| SPREAD_RATE          | Real          | Section 9.1.1  | m/s       | 0.05       |
| SURF_ID              | 字符型        | Section 7.4.1  |           | ’INERT’    |
| TEXTURE_ORIGIN(3)    | Real Array    | Section 7.5.2  | m         | (0.,0.,0.) |
| TMP_EXTERIOR         | Real          | Section 7.4.2  | ℃         |            |
| TMP_EXTERIOR_RAMP    | 字符型        | Section 7.4.2  |           |            |
| TRANSPARENCY         | Real          | Section 7.5    |           | 1.0        |
| UVW(3)               | Real Array    | Section 10.2.7 |           |            |
| VEL_RMS              | Real          | Section 10.1.8 | m/s       | 0.         |
| XB(6)                | Real Array    | Section 7.4.1  | m         |            |
| XYZ(3)               | Real Array    | Section 9.1.1  | m         |            |

> VENT可以用来对建筑的通风系统的组成部分进行建模，如扩散器或回流。可以通过SURF_ID在其上指定火焰燃烧范围。

从字面上看，VENT只是作为一种将特定边界条件应用于固体表面上的矩形斑块的手段。例如，**火灾通常是通过OBST线首先产生固体障碍物，然后在固体的一个表面上指定一个VENT，使用带有燃料的热和燃烧特性的SURF_ID**。

```fortran
&OBST XB=0.0,5.0,2.0,3.0,0.0,4.0, SURF_ID='big block' /
&VENT XB=1.0,2.0,2.0,2.0,1.0,3.0, SURF_ID='hot patch' /
```

指定一个大型障碍物(具有文件中其他地方的属性，名称为“big block”)，并将“patch”应用于其中一个面，其可选属性名称为“hot patch”。需要注意的是，VENT的表面属性会覆盖其下的物体属性。

**VENT必须始终连接在固体障碍物上**。有时，VENT的一部分可能超出实体，在这种情况下，它要么被忽略，要么触发错误消息。只有一部分靠近固体表面的VENT会被考虑。因此，如果给VENT一个SURF_ID，指定HRRPUA(单位面积热量释放率)的值，这个速率将只应用于VENT下面有固体的部分。对于给定的固体表面，只能设置一个`VENT`，且必须附着在固体物件上。若一个OBST的表面和VENT重合，则VENT的性质会覆盖OBST面的性质。**若VENT的大小超出了OBST表面大小，则只有与OBST表面相重合的部分会被纳入计算**。

:question:此外，VENT通过在一侧有一个固体单元和在另一侧有一个气体单元来确定其方向。**不要将VENT扩展为具有多个方向**。

`XB=x1,x2,y1,y2,z1,z2`表示某个与固体表面相邻的平面。可以通过`MB`（Mesh Boundary）参数指定一整个面，其参数包括`XMAX, XMIN, YMAX, YMIN, ZMAX or ZMIN`。

> 在进行多网格模拟时，要小心使用MB快捷方式；也就是说，在使用多个矩形网格时。由字符串MB指定的平面可能会错误地应用于多个网格，可能会导致平面是实体墙还是开放边界的混淆。**但是可以用DB参数替换MB，通过对不同域的边界指定SURF_ID来区分**。在Smokeview中检查几何形状，确保通风口被正确指定。

**在`VENT`行上的参数`OUTLINE=T`会使`VENT`在Smokeview视图中被绘制为轮廓**。

**********

1. `SURF_ID`可以指定的参数：

   1. `OPEN`、`MIRROR`等参数，均表示沿着整个计算域的边界。`OPEN`边界禁用压力`ZONES`，这可能会改变问题的求解。

   2. `PERIODIC`与域的另一侧的另一个周期性VENT结合使用。

      1. 对于单个网格而言：

      2. ```fortran 
         &VENT MB='XMIN', SURF_ID='PERIODIC' /
         &VENT MB='XMAX', SURF_ID='PERIODIC' /
         ```

      3. 对于多个网格而言：整个域必须是单个大块，并且必须使用PBX, PBY或PBZ指定VENT平面。

      4. ```fortran
         &VENT PBX=0, SURF_ID='PERIODIC' /
         &VENT PBX=1, SURF_ID='PERIODIC' /
         ```

   3. `HVAC`表示VENT连接在一个HVAC系统中。

2. `PBX、PBY、PBZ`分别表示垂直于xyz轴的整个平面。

*************

#### Special Vents

有四个保留的SURF_ID可以应用于VENT - ' OPEN '， ' MIRROR '， ' PERIODIC '和HVAC。术语保留意味着这些surf_id不应该由您显式定义。**它们的属性是预定义的**。

**Open Vents**

第一个特殊的VENT由参数SURF_ID= ' OPEN '调用。**这仅在VENT应用于计算域的外部边界时使用，其中它表示对外部的被动开放**。默认情况下，FDS假定计算域的外部边界(MESH行上的XBs)是一个固体壁面。**要创建完全或部分开放的域，请在外部网格边界上使用open通风口**。通过简单地将其指定为OPEN，有时可以方便地指定向计算域外部打开的门或窗。但是，请记住，**这种开口上的压力边界条件是不完善的，建议如果通过门或窗户的流量很重要，您应该将域扩展几米，而不是使用OPEN边界**<font color=red>(在输入卡中如何设置？)</font>。您仍然需要使用OPEN边界来打开计算域的一个或多个侧面，但是这些开口将离建模的门或窗足够远，从而不会影响流型。

默认情况下，假定在' OPEN '出口之外存在环境条件。然而，在某些情况下，您可能想要改变这个假设，例如，温度。**如果您假设的温度不是环境温度**，则指定TMP_EXTERIOR和SURF_ID= ' OPEN '。您可以使用渐变函数TMP_EXTERIOR_RAMP修改该参数的时间历史。谨慎地使用这个选项——在很多情况下，如果你想描述建筑物的外部，最好在计算中明确地包括外部，因为进出门窗的流动将更自然地被捕捉到。有关更多细节，请参见第16.5.1节。如果要指定OPEN边界处的非环境压力，请参见第10.4节。

<font color=red>**OPEN 压力边界条件在气流主要为法向气流时最为稳定**</font>。即，大部分流入或大部分流出。这是因为，如果气流与通气孔平行，则开放边界处的规定压力条件不佳（输入的微小扰动可能导致输出的巨大变化）。例如，假设室外流在x方向上为10m /s，在z方向上为±0.001 m/s，顶部边界为OPEN。这个流动的动能大约是$k=50m^2/s^2$。当垂直速度为正时(+0.001 m/s)，则规定的滞止压力边界条件设为$H=k=50m^2/s^2$。但当垂直速度为负(-0.001 m/s)时，$H = 0$(见[1])。由于这个原因，**在室外应用中应该小心使用OPEN通风口**。参见第16.2节了解另一种方法。

**在模拟过程中，可以打开或关闭通往计算域外部的通风口**(OPEN通风口)。最好是通过制造或移除覆盖在OPEN通风口上的薄障碍物来完成。有关详细信息，请参见第18.4.2节。

**Mirror Vents**

一个带有SURF_ID= ' MIRROR '的VENT表示一个对称平面。通常，MIRROR跨越计算域的整个面，实质上是将域的大小加倍，MIRROR充当对称平面。MIRROR另一侧的流动正好相反。从数值角度来看，MIRROR是一个无通量、自由滑移边界。**与OPEN一样，MIRROR只能在计算域的外部边界指定**。通常，OPEN或MIRROR通风口是沿着计算域的整个一侧指定的，在这种情况下，“MB”表示法很方便。

在传统的RANS (Reynolds - Average Navier-Stokes)模型中，对称边界通常被用作节省计算时间的一种方法。然而，由于FDS是一个LES(大涡模拟)模型，对称边界的使用应该仔细考虑。原因是LES模型不计算N-S方程的时间平均解。换句话说，对于RANS模型，火羽被表示为轴对称流场，因为如果你在足够长的时间内对实际流场进行时间平均，那就是你所期望的。因此，对于RANS模型，沿羽流中心线的对称边界是合适的。然而，在LES模型中，方程中没有时间平均，也没有时间平均的对称解。沿着火羽的中心线放置MIRROR边界将完全改变其动力学。它会产生一种非常类似于垂直墙壁附近的火灾流场的东西。因此，不建议在紊流火羽的中心线处采用镜像边界条件。:question:**如果火焰或燃烧器很小，并且流动是层流的，那么MIRROR边界条件是有意义的**。实际上，在二维计算中，MIRROR边界条件是在第三个坐标方向上使用的(这是自动完成的，不需要显式指定)。

**Periodic Vents**

带有SURF_ID= ' PERIODIC '的VENT可以与域的另一侧的另一个周期性VENT结合使用。如果域仅由单个网格组成，则可表示为：

```fortran
&VENT MB='XMIN', SURF_ID='PERIODIC' /
&VENT MB='XMAX', SURF_ID='PERIODIC' /
```

指定仿真在x方向上是周期性的。对于应用PERIODIC边界条件的**多网格域**，整个域必须是单个大块，并且必须使用PBX, PBY或PBZ指定VENT平面。例如，如果$x_{min}=0,x_{max}=1$，则可使用：

```fortran
&VENT PBX=0, SURF_ID='PERIODIC' /
&VENT PBX=1, SURF_ID='PERIODIC' /
```

默认情况下，为了处理具有多个网格的周期域的最一般情况(想象一个周期通道被分成几个网格)，FDS将压力边界条件视为我们所说的“插值边界”。这意味着压力泊松方程的矩阵是排列好的狄利克雷边界条件(解的值在边界处指定)。这可能导致解中的小误差，有时需要使用泊松方程的真周期矩阵。但是使用当前的求解器(Fishpak)，这只能用于单个网格。如果你想为单个网格情况实现真正的周期边界，在PRES线上设置适当的FISHPAK_BC值为零。例如，

```fortran
&PRES FISHPAK_BC(1:3)=0,0,0 /
```

周期性通风口不能用于连接偏移通风口或不同坐标方向的通风口。对于此类情况，您必须使用HVAC功能(见第10.2节)。

**HVAC Vents**

带有SURF_ID= ' HVAC '的通风口表示该通风口连接到HVAC系统。HVAC系统输入的描述见第10.2节。



**Circular Vents**

圆形或半圆形通风口可以指定为坐标为XB的矩形与圆心为XYZ、半径为RADIUS的圆的交点。被分配到相应 SURF_ID 的矩形表面单元将是那些中心点位于交叉点内的单元。在Fire/circular_burner.fds算例中，以下两行创建了一个直径为1m的圆形通风口，以$0.02 kg/m^2/s$的速度流动丙烷气体：

```fortran
&SURF ID='BURNER', MASS_FLUX(1)=0.02, SPEC_ID(1)='PROPANE', TAU_MF(1)=0.01 /
&VENT XB=-0.6,0.6,-0.6,0.6,0,0, XYZ=0,0,0, RADIUS=0.5, SURF_ID='BURNER',
    SPREAD_RATE=0.05 /
```

XB坐标指定了通风口的方向。在这种情况下，指定的区域的范围XB足够大，可以容纳整个圆。还请注意，在本例中，参数SPREAD_RATE使火焰以0.05 m/s的速率向外蔓延。通过排气口的丙烷的质量通量如图7.10所示。注意，质量通量随着“t平方”曲线而增加。这是一场以线性速度径向蔓延的火灾的预期结果。在这种情况下，火在10s达到圆的半径，和预期的一样。还要注意，参数TAU_MF表明，一旦火焰前缘到达给定的网格单元，燃料应该迅速上升。换句话说，TAU_MF 控制燃料的局部上升；SPREAD_RATE 控制全局上升。升压后，燃料的流速等于 乘以单位面积的燃料质量流量。即使在粗网格上粗略地分解了圆，也会调整燃料流量以产生由圆形通风口控制的所需值。

![image-20240617101428989](..\FDS中钠燃烧模型添加.assets\image-20240617101428989.png)

#### Controlling Vents

在某些情况下，可以使用“设备”和“控件”来控制VENT功能，通过DEVC_ID或CTRL_ID指定。有关详细信息，请参见第18.4.2节。

**Activating and Deactivating Vents**

当设备或控制功能应用于VENT时，目的是通过其DEVC_ID激活或停用与VENT相关的任何时间斜坡。例如，要控制风扇，请执行以下操作：

```fortran
&SURF ID='FAN', VOLUME_FLOW=5. /
&VENT XB=..., SURF_ID='FAN', DEVC_ID='det2' /
&DEVC ID='det2', XYZ=..., QUANTITY='TIME', SETPOINT=30., INITIAL_STATE=F /
```

请注意，**在30秒时，“FAN”的“状态”从F变为T，或者更简单地说，“FAN”打开**。由于没有与' FAN '关联的显式时间函数，因此默认的1秒加速将从30秒开始，而不是0秒。如果INITIAL_STATE=T，那么风扇应该在30秒关闭。本质上，VENT的“激活”导致所有相关的时间函数延迟，直到达到设备SETPOINT。VENT的“停用”将关闭所有时间功能。通常，这意味着SURF行的参数全部无效，因此用一个简单的示例检查功能是一个好主意。“MIRROR”或“OPEN”排气口不应被激活或关闭。<font color=red>**然而，你可以在’OPEN’ VENT前放置一个障碍物，然后创建或移除它来模拟门或窗的关闭或打开**</font>。

在某些情况下，您可能需要创建或移除具有VENT的障碍物。如果障碍物重叠，可能会混淆哪个VENT与哪个OBST有关。如果遇到这样的情况，给OBST一个ID，并在VENT行上分配这个OBST_ID。

#### Trouble-Shooting Vents

与输入文件中的大多数条目不同，指定VENTs的顺序可能很重要。可能在某些情况下，将一个通风口置于另一个通风口之上是很方便的。如前所述，这是因为VENT的属性是从几何体上覆盖几何体下的面。例如，假设您想要指定一个隔间的天花板具有一组特定的表面属性，并且您指定整个天花板具有适当的SURF_ID。然后，您希望在天花板上指定一个较小的块，以具有另一组表面属性，例如空气供应。在这种情况下，您必须先指定供应通风口，因为对于天花板的该区域，FDS 将忽略天花板属性并应用供应属性。现在，通风孔的规则是 "先到先得"。但是请记住，第二个VENT并没有被完全拒绝——只在重叠的地方。FDS还将向屏幕(或标准错误)打印一个警告，说明哪个VENT具有优先级。**此外，如果任何VENTs都应用OPEN边界条件，请小心OPEN边界禁用压力ZONEs**，这将改变问题的解决方案。

Smokeview 可以帮助识别两个VENT重叠的位置，假定每个通风口都有独特的 COLOR。由于 Smokeview 绘制的VENT是相互重叠的，因此重叠的区域会有颗粒感，看起来很别扭，而且会随着场景的移动而改变图案。

如果出现错误消息，要求指定通风口的方向，请首先检查以**确保通风口是平面**。如果排气口是一个平面，那么可以通过指定`IOR`参数强制其方向。如果VENT的法线方向在x正方向，则设置`IOR=1`。如果**法线**方向在负x方向，则设置`IOR=-1`。**对于y和z方向，分别使用数字2和3**。`IOR`只能在某些情况解决这个问题。

### Coloring Obstructions, Geometry, Vents, Surfaces, and Meshes

在可视化模拟结果时，为对象分配有意义的颜色或图案非常有用。在FDS中有两种方法可以做到这一点。要么指定一个单一的颜色，要么指定一个纹理贴图，这本质上是你选择的图像。

#### Colors

FDS中许多项目的颜色可以通过两种方式规定：整数颜色值(RGB)的三元组或字符串(COLOR)。三个RGB整数的范围是0到255，表示红色，绿色和蓝色的数量组成了这个颜色。如果按名称定义COLOR，那么键入的名称必须与颜色表中列出的名称完全一致，这一点很重要。可以在SURF线上指定颜色参数，在这种情况下，该类型的所有表面都将具有该颜色，或者可以将颜色参数直接应用于浸入几何形状的障碍物或通风口。例如：

```fortran
&SURF ID='UPHOLSTERY', ..., RGB=0,255,0 /
&OBST XB=..., COLOR='BLUE' /
&GEOM GEOM_ID=..., COLOR='BLUE' /
```

将所有UPHOLSTERY上色为绿色和这个特殊的障碍或几何形状上色为蓝色。

障碍物，几何形状和通风口可以单独着色，覆盖SURF线指定的颜色。**特殊情况COLOR= ' INVISIBLE '导致通风口、几何形状或障碍物不被烟雾视图绘制**。另一种特殊情况**COLOR= ' RAINBOW '**导致通风口，障碍物或网格的颜色从RGB值的整个范围中随机选择，当使用MULT命名列表组并希望区分多重阻塞、通气或网格时，这可能很有用。

#### Texture Maps

在计算域内，有多种方法规定各种物体的颜色，但也有一种方法将**图像粘贴到障碍物上**，以使烟雾视图图像更加逼真。这种技术被称为“纹理映射”。例如，要将木镶板图像应用于墙壁，请向SURF线添加定义镶板的物理属性的行：

```fortran
&SURF ID='wood paneling',..., TEXTURE_MAP='paneling.jpg', TEXTURE_WIDTH=1.,
    TEXTURE_HEIGHT=2. /
```

假设在工作目录中存在一个名为paneling.jpg的JPEG文件，那么在使用paneling的任何地方，Smokeview都会加载并显示该图像。注意，当第一次调用烟雾视图时，图像不会出现。**这是一个由显示/隐藏菜单控制的选项**。参数TEXTURE_WIDTH和TEXTURE_HEIGHT是图像的物理尺寸。在上述案例下，JPEG图像是1米宽2米高的镶板。烟雾视图尽可能频繁地复制图像，使其看起来在需要的地方应用了面板。仔细考虑图像在场景中是如何重复的。如果图像有明显的方向，则应该将真正的三重体TEXTURE_ORIGIN添加到应该应用纹理映射的VENT或OBST线上。例如，

```fortran
&OBST XB=1.,2.,3.,4.,5.,7., SURF_ID='wood paneling', TEXTURE_ORIGIN=1.,3.,5. /
```

对尺寸为1米× 1米× 2米的障碍物应用镶板，使镶板的图像位于点(1,3,5)。TEXTURE_ORIGIN的默认值是(0,0,0)，全局默认值可以通过在MISC行中添加TEXTURE_ORIGIN语句来更改。

**对于球体的几何形状**，GEOM线上的参数TEXTURE_MAPPING= ' SPHERICAL '让烟雾视图知道将纹理包裹在球体周围，而不是从上方将其平放。以下来自测试用例geom_texture3a.fds的FDS输入行。FDS使用图像sphere_cover_03.png定义一个球体作为纹理贴图(该图像在烟雾视图安装目录中找到)。图7.11显示了使用这些输入线以及应用的矩形纹理映射的纹理映射球体。

```fortran
&SURF ID='surf1'
    TEXTURE_MAP='sphere_cover_03.png',COLOR='BLUE',
    TEXTURE_WIDTH=1.0,TEXTURE_HEIGHT=1.0,TEXTURE_ORIGIN=0.0,0.0,0.0,
    TEXTURE_MAPPING='SPHERICAL'/
&MOVE ID='SPHERE_ROT', AXIS=0.,0.,1., ROTATION_ANGLE=270. /
&GEOM ID='sphere1',SURF_ID='surf1',SPHERE_RADIUS=0.5,
    N_LAT=25,N_LONG=50,SPHERE_ORIGIN=0.0,0.0,0.0,MOVE_ID='SPHERE_ROT'
```

![image-20240617104746731](..\FDS中钠燃烧模型添加.assets\image-20240617104746731.png)

## 注意事项

在FDS中任何计算开始之前，温度均为环境温度。流动速度为0，所有物质的质量份额都是均匀的。FUG P.240

![image-20240530103755731](..\FDS中钠燃烧模型添加.assets\image-20240530103755731.png)

## 时间步长

FDS中的时间步长表示为：
$$
0.8\leq CFL=\Delta t\left(\frac{\left\|\vec{\nu}\right\|}{\triangle x}+\left|\nabla\cdot\vec{\nu}\right|\right)\leq1.0
$$
如果CFL数增长超过上限，则将时间步长设置为允许的90%，如果低于下限，则增加10%；通常，当网格间距减少1/2时，时间步长减少1/2，即总计算量增加16倍。

## 湍流

### 湍流尺度

湍流主要是由大尺度和小尺度的相互作用决定的，两者之间存在较大区别，例如：动能生成尺度；动能耗散，生成热的尺度。

![image-20240530103916421](..\FDS中钠燃烧模型添加.assets\image-20240530103916421.png)

<center>湍流中的尺度</center>

在积分尺度上，流动结构分解成更小的结构，连接了以上两个尺度。在湍流文献中，这个结构通常用波数表示：k=\frac{2\pi}L
$$
k=\frac{2\pi}L
$$
因此，最小的可解析涡流$L=2\vartriangle x$具有的波数为${{k}_{0}}=\frac{\pi }{\vartriangle x}$。

![image-20240530104026019](..\FDS中钠燃烧模型添加.assets\image-20240530104026019.png)

<center>一个数值网格的尺度和解析度</center>

在网格分辨率有限的情况下，也就是最小波数有限的情况下，能量谱不能完全解析，不能解析的部分必须用亚网格尺度(SGS)模型进行建模。

为了模拟湍流，必须近似小尺度对大尺度的影响。主要的两种方法是基于空间或时间的手段。

#### 火灾中的湍流建模

在火灾模拟中，两类湍流模型是常见的：直接数值模拟(DNS)和大涡模拟(LES)。尽管对于实际应用来说，只有LES是合适的。

![image-20240530104329456](..\FDS中钠燃烧模型添加.assets\image-20240530104329456.png)

<center>DNS和LES模拟中尺度的解析和模拟概述</center>

![image-20240530104353847](..\FDS中钠燃烧模型添加.assets\image-20240530104353847.png)

<center>不同建模方法的解析尺度</center>

LES的一般思想是为空间过滤量制定方程。在LES的情况下，对于任何场量$\phi =\phi \left( x,y,z,t \right)$，这个滤波器为：
$$
\left\langle\phi\right\rangle=\overline{\phi}=\frac1V\underset{V}{\operatorname*{\int}}\phi dV
$$
为简单起见，使用空间滤波速度$\left\langle {\vec{v}} \right\rangle $的不可压缩等温流的LES方程为：
$$
\partial_t\left(\rho\left\langle\vec{\nu}\right\rangle\right)+\nabla\cdot\left(\rho\left\langle\vec{\nu}\right\rangle\left\langle\vec{\nu}\right\rangle\right)=-\nabla\left\langle p\right\rangle+\mu\nabla^2\left\langle\vec{\nu}\right\rangle-\nabla\cdot\underbrace{\left(\left\langle\rho\vec{\nu}\vec{\nu}\right\rangle-\rho\left\langle\vec{\nu}\right\rangle\left\langle\vec{\nu}\right\rangle\right)}_{\tau_{\mathrm{sgr}}}\tag{运动方程}\label{滤波后的运动方程}
$$
残余应力张量${{\tau }_{sgs}}$必须表征尺度相互作用，这里采用Boussinesq假设：
$$
\tau_{sgs}-\frac13tr\left(\tau_{sgs}\right)I=-2\mu_t\left\langle S\right\rangle
$$
$\left\langle S \right\rangle $为滤波张量，${{\mu }_{t}}$为湍流黏度，需要指定。

因此，LES方程中的$\left\langle {\vec{v}} \right\rangle $和N-S方程中的$\vec{v}$一样，但其有效黏度为：
$$
\mu_{eff}=\mu_{mol}+\mu_t
$$
由于滤波后的$\eqref{滤波后的运动方程}$几乎等于未滤波后的运动方程，所以在下面省略了滤波括号。

#### Deardorff模型

另一种方法是由Deardorff给出的，这是<font color=red>**当前FDS的默认模型**</font>。它使用速度的平均网格值($\bar{v}$)及加权平均数($\hat{v}$)，得出湍流粘度：
$$
\mu_t=\rho C_V\triangle\sqrt{k_{sgs}}
$$
其中，${{k}_{sgs}}=\frac{1}{2}{{\left( \bar{v}-\hat{v} \right)}^{2}}$，文献中常量${{C}_{V}}=0.1$。

#### 在FDS中的实现

FDS提供了不同的模拟模式，参见FDS理论手册中的7.2节：DNS(直接数值模拟)、LES(大涡模拟)、VLES(超大涡模拟)和SVLES(简单超大涡模拟-简化物理的VLES)。**默认模式为VLES**。

以下是目前可用的湍流粘度模型：

a)     常系数Smagorinsky

b)    动态Smagorinsky

c)     Deardorff

d)    Vreman涡流粘度

e)     重整化群涡动粘度

f)     适应壁面的局部涡流粘度

## 热解模型[^f5]（FVG）

固体表面可以由多层组成，每层可以由多种材料组成。每种物质成分可能经历几个相互竞争的反应，而这些反应中的每一个都可能产生其他一些固体成分(残留物)、气体燃料和/或水蒸气。

### 热解质量守恒

对应FDS参数（surf_mass_conservation）

四种独立的建模选项：

1. SURF线既可以与VENT线指定的固体表面相关联，也可以与PART线所描述的固体颗粒相关联；
2. SURF几何可以是CARTESIAN，CYLINDRICAL，或SPHERICAL；
3. 材料MATL可以是碳化(非零NU_RESIDUE)或非碳化；
4. 热解产物可以是由混合组分模型定义的燃料气体，也可以是由SPEC线定义的附加气体。

对于大多数算例，壁面厚度（或圆柱体、球体的半径）为0.01m，材料密度为$360kg/{{m}^{3}}$，在碳化情况下，气体产物的产率为0.5，即原始质量的一半。**对于笛卡尔表面**，碳化情况下每单位表面积的质量损失率为$1.8kg/{{m}^{2}}$，非碳化的为$3.6kg/{{m}^{2}}$；**对于圆柱表面**[^f6]，单位表面积的体积为$r/2$，因此碳化的质量损失率为$360\left( 1-0.5 \right)\times r/2=0.9kg/{{m}^{2}}$，非碳化为$1.8kg/{{m}^{2}}$；**对于球形表面**，单位表面积的体积为$r/3$，因此碳化的质量损失率为$360\left( 1-0.5 \right)\times r/3=0.6kg/{{m}^{2}}$，非碳化为$1.2kg/{{m}^{2}}$。

------

[^f5]: 对应6.8.0 FVG chapter 12 & FUG chapter 9
[^f6]: 圆柱单位表面积的体积的解释：[Theory for pyrolysis in FDS Verification Guide · firemodels/fds · Discussion #12604 (github.com)](https://github.com/firemodels/fds/discussions/12604)

### 固体表面热解

通过将单位面积的质量乘以VENT的面积来计算分析质量损失，在所有情况下都是$1m^2$。炭化材料的期望结果与计算结果如图a所示。非炭化材料的预期结果与计算结果如图b所示。

![image-20240530110010665](..\FDS中钠燃烧模型添加.assets\image-20240530110010665.png)

<center>a.作为VENTs引入的炭化表面的分析与预测质量变化的比较</center>

![image-20240530110036075](..\FDS中钠燃烧模型添加.assets\image-20240530110036075.png)

<center>b.作为VENTs引入的非炭化表面的分析与预测质量变化的比较</center>

### 离散颗粒的热解

对于拉格朗日粒子，质量的期望值由物质密度乘以粒子体积乘以残留分数得到。**对于笛卡尔曲面(板)**，颗粒面积为SURF线上参数LENGTH和WIDTH的乘积的两倍，两者均取0.05m。因此，对于碳化，平板颗粒的期望质量为$360\left( 1-0.5 \right)\times 2\delta LW=0.009kg$，对于非碳化则为$0.018kg$。值得注意的是，对于一半厚度$\delta =0.01m$，在SURF中也被指定为THICKNESS。**对于圆柱形颗粒**，LENGTH为0.1m，半径r（通过THICKNESS指定）为0.01m。对于碳化，颗粒的期望质量为$360\left( 1-0.5 \right)\times \pi {{r}^{2}}L=0.00565kg$，对于非碳化则为$0.0113kg$。**对于球形颗粒**，碳化情况下的颗粒的期望质量为$360\left( 1-0.5 \right)\times 4\pi {{r}^{3}}/3=7.54\times {{10}^{-4}}kg$，对于非碳化则为$1.51\times {{10}^{-3}}kg$。

#### 碳化颗粒

炭化材料的分析结果与计算结果如图 a所示。图 b比较了非炭化材料的解析结果和计算结果。

![image-20240530110318241](..\FDS中钠燃烧模型添加.assets\image-20240530110318241.png)

<center>a.炭化颗粒表面质量变化的分析与预测比较</center>

![image-20240530110339810](..\FDS中钠燃烧模型添加.assets\image-20240530110339810.png)

<center>b.非炭化颗粒表面质量变化的分析与预测比较</center>

#### 产生多种气体的粒子

下图显示了三个测试案例的结果，涉及0.1 kg的扁平、圆柱形或球形颗粒在一个单位立方体中同时产生燃料气体和水蒸气，例如木材或植被。

![image-20240530110424761](..\FDS中钠燃烧模型添加.assets\image-20240530110424761.png)

<center>产生水和燃气的粒子的分析和预测质量变化的比较</center>

### 固体颗粒分解速率

对应FDS参数（part_baking_soda）

在这种情况下，我们提出了一个简单的解析解，在等温条件下具有恒定反应速率的**球形颗粒的固相分解**。设m(t)为半径为r(t)的球形粒子的质量，随时间变化，初始质量为m0 = m(t =0)，反应程度定义为，
$$
\alpha\equiv\frac{m_0-m}{m_0}
$$

#### 一阶反应模型

材料的密度$\rho $为常数，体积表示为$V\left( t \right)$。对于一阶反应，$\alpha $的变化率表示为[^12]，
$$
\frac{d\alpha}{dt}=k\left(1-\alpha\right)
$$
其中，反应的速率常数为$k=A{{e}^{-{{E}_{a}}/\left( RT \right)}}$。A为Arrhenius参数（1/s），Ea为活化能（J/mol），R为通用气体常数（8.3145J/mol/K），T为温度（K）。

定密度积分可得：
$$
\int\frac{d\alpha}{1-\alpha}=k\int dt\Rightarrow\left[\ln\left(1-\alpha\right)\right]_{\alpha_0}^\alpha=-kt
$$

$$
\frac{1-\alpha}{1-\alpha_0}=e^{-kt};\quad\alpha_0=0;\quad\alpha=1-\frac m{m_0}
$$

$$
\frac m{m_0}=e^{-kt}\Rightarrow\frac{\rho V}{\rho_0V_0}=e^{-kt}\Rightarrow r^3=r_0^3e^{-kt}
$$

<font color=red>**举例**</font>

取$A=3.4e11\text{ 1/s, }{{E}_{a}}=103000\text{ J/mol, }{{\text{r}}_{0}}=2.5\mu m$，并将FDS与$T=\left[ 420,450,500 \right]K$的解析解进行比较，结果如下图所示。

![image-20240530110839038](..\FDS中钠燃烧模型添加.assets\image-20240530110839038.png)

<center>等温条件下一阶和收缩体积固体相反应的粒径分析与预测比较</center>

#### 收缩体积反应模型

体积收缩时$\alpha $的变化率由下式定义[^12]，
$$
\frac{d\alpha}{dt}=k3\left(1-\alpha\right)^{2/3}
$$
对于该模型，首先将反应程度$\alpha $转换回粒子质量是有帮助的，
$$
\frac{dm}{dt}=-k3m_0^{1/3}m^{2/3}\tag{粒子质量}\label{粒子质量}
$$
积分后可得，
$$
\int m^{-2/3}dm=-k3m_0^{1/3}\int dt
$$

$$
m^{1/3}=m_0^{1/3}\left(1-kt\right)
$$

$$
\left(\rho V\right)^{1/3}=\left(\rho_0V_0\right)^{1/3}\left(1-kt\right)
$$

在物理上，密度将保持不变，而体积将收缩，导致粒子半径线性减小，
$$
r=r_0\left(1-kt\right)
$$
然而，没有建立FDS反应方程来模拟收缩体积模型。相反，对于相同的动力学参数，我们可以通过保持体积恒定(ALLOW_SHRINKING=F)并调整指数前因子来考虑初始质量来实现粒子的正确质量衰减。通过保持体积恒定，式$\eqref{粒子质量}$可以用材料$\alpha $的固体密度表示如下:
$$
\frac{d\rho_{s,\alpha}}{dt}=-k3\underbrace{\rho_{s,\alpha}\left(0\right)^{1/3}}_{\text{adjustment factor}}\rho_{s,\alpha}^{2/3}
$$
因此，为了匹配收缩体积模型的初始衰减，必须将A乘以因子${{\rho }_{s,\alpha }}{{\left( 0 \right)}^{1/3}}$，并将反应的阶数改为$\rho _{s,\alpha }^{2/3}$。

<font color=red>**举例**</font>

考虑适用于球形小苏打(NaHCO3)颗粒的收缩体积模型，取$A=3.4e11\times 3{{\left( 2200 \right)}^{1/3}}\text{=133e11 1/s, }{{E}_{a}}=103000\text{ J/mol, }{{\text{r}}_{0}}=2.5\mu m$（注意，粒子的初始密度为$2200kg/{{m}^{3}}$），将FDS与T = [420;450;500] K时速率常数的粒径解析解进行比较。设置ALLOW_SHRINKING=F，并报告粒子直径为$d\left( t \right)={{d}_{0}}{{\left( {{\rho }_{s}}\left[ t \right]/{{\rho }_{s}}\left[ 0 \right] \right)}^{1/3}}$。结果如[一阶反应模型](#一阶反应模型)图例所示，并与具有相同Arrhenius 参数的一阶模型的速率进行了比较。值得注意的是，对于相同的参数集，收缩体积模型导致的衰减率明显高于一阶反应。

### 热解能量守恒

对应FDS参数matl_e_cons

创建了9个简单的测试用例来验证确保MATL反应能量守恒的过程。每种情况都是一个边长为1米的立方体，每个维度上有4个网格单元。定义了一种或多种材料和气体。所有材料的密度定义为$1kg/{{m}^{3}}$。所有的物种都以分子量为1000g /mol来定义。这样做是为了方便，因为这意味着以kJ/mol为单位的生成热与以kJ/kg为单位的焓值相同。对于所定义的每种材料，单个壁面网格VENT是用SURF定义的，这样网格单元包含1kg材料。WALL ENTHALPY是每个壁面单元的输出。下面用图 a和图b所示的结果解释了这些情况。

![image-20240530111527941](..\FDS中钠燃烧模型添加.assets\image-20240530111527941.png)

<center>a.matl_e_cons测试用例1-6的解析解与预测壁焓比较</center>

在Case 1中，给定一种物质的生成热为0 kJ/mol。定义单一材料比热为0.5 kJ/kg/K，在参考温度为300℃，热解范围为40 K的条件下，反应产生的气体物质的反应热为 1000 kJ/kg。如下所示，
$$
\begin{aligned}&H_{MATL1}\left(300°\mathbb{C}\right)+H_{MATL1,adj}+1000kJ/kg=H_{SPEC1}\left(300°\mathbb{C}\right)\\&286.575kJ/kg+H_{MATL1,adj}+1000kJ/kg=275kJ/kg\\&H_{MATL1,adj}=-1011.575kJ/kg\end{aligned}
$$
在环境温度下，使得壁面单元的焓值为$298.15K\times 0.5kJ/kg/K-1011.575kJ/kg=-865kJ/kg$

Case 2重复Case 1，物质生成热为1000 kJ/mol。这使得预期的环境焓 -1865 kJ/kg。

Case 3将Case 1和Case 2合并为单个输入。Case 1材料从使用参考温度和热解范围改为使用从Case 1输出文件中获取的结果$A\left( 7.68\times {{10}^{31}}\text{ 1/s} \right)$和$E\left( 371000\text{ J/mol} \right)$。这种情况下测试虚拟TGA(Case 1材料将只有有相同的调整，如果有相同的参考温度)，且多组反应被正确处理。

Case 4采用Case 1，改变反应，产生等量的气体和第二种物质。第二种材料的比热为1.5 kJ/kg/K，在400℃的参考温度下，反应产生的气体物质的反应热为500 kJ/kg。这种情况下有两个总反应包含两种总物质。解决方案可以手工找到，首先找到第二个材料的调整值(按照Case 1的示例)，然后使用该调整值找到第一个材料的值。

Case 5采用Case 4，并对第一种物质添加第二反应。该反应创建了第一种材料的第二个副本，在280℃的参考温度下，反应热为500 kJ/kg。这可以看作是一个相变。第二次复制也产生等量的气体和其他物质，期望反应热为500 kJ/kg。现在这是一个超定系统，因为有三种材料和四种反应；然而，请注意，产生气体的平行路径具有相同的总焓变。直接热解的第一个物质的反应热为1000 kJ/kg，相变路径在相变和热解之间也有1000 kJ/kg的总焓变。因此，即使系统是超定的，也期望得到一个精确的解。这在结果中可以看到，Case 5中的第一和第二物质焓与Case 4的焓相匹配。

Case 6采用Case 5，将相变后的反应热增加到1000kJ /kg。现在，一个精确解不再被期待。可以看出，第二种材料具有相同的焓，而第一种材料及其相变具有不同的环境焓。相变后的物质焓改变了333 kJ/kg，但反应焓改变了500 kJ/kg，所以能量没有完全守恒。作为最小二乘解，它是尽可能守恒的。

Case 7采用Case 4并从第二种材料中除去反应。这是一个待定的系统，有两种物质和一个反应。按照Case 1的过程，可以得到，
$$
H_{MATL1,adj}-0.5H_{MATL2,adj}=-719.2125kJ/kg
$$
最小矩阵解为${{H}_{MATL1,adj}}=-575.37kJ/kg$，${{H}_{MATL2,adj}}=287.68kJ/kg$。它可以通过取解向量的范数来证明这是一个最小解。这可以用${{H}_{MATL1,adj}}$表示
$$
H_{MATL1,adj}^2+\left(2\left(H_{MATL1,adj}+791.2125kJ/kg\right)\right)^2
$$
最小值是导数为0时的解或者如下，
$$
10H_{MATL1,adj}+8\times791.2125kJ/kg=-575.37kJ/kg
$$
Case 8采用Case 1并删除产气量。在这种情况下，FDS将假设虚拟材料与原始材料具有相同的比热。这导致最小二乘解，其中反应焓在原始材料和原始材料上分裂，使壁面单元的预期环境温度焓为$298.15K\times 0.5kJ/kg/K-500kJ/kg=-353.425kJ/kg$。

Case 9采用Case 1，并产生与第一材料具有相同比热的第二材料的粒子。这和Case 8是一样的，且环境焓是一样的。

![image-20240530112140640](..\FDS中钠燃烧模型添加.assets\image-20240530112140640.png)

<center>b.matl_e_cons测试用例7-9解析解与预测壁焓的比较</center>

### 小物体的燃烧速率

对应FDS参数cell_burn_away

在FDS中，假设固体内部的热传导和热解仅是深度的函数。在整个固体障碍物燃烧殆尽的情况下，可能会出现问题。例如，一个单一的网格单元，每边4cm，由密度为${{\rho }_{s}}=50kg/{{m}^{3}}$，反应速率为${{r}_{s}}=0.05{{s}^{-1}}$的材料组成。这个单一网格单元的燃烧速率$\dot{m}$可表示为，
$$
\dot{m}=\delta\rho_sr_sA\tag{燃烧速率}\label{燃烧速率}
$$
其中$\delta $是表层的厚度，A是单个网格单元的六个面的面积。假如设置了层厚度，则有$\delta A=V$，$V$是网格的体积，并且该网格的质量表示为$m=\delta A{{\rho }_{s}}$，式$\eqref{燃烧速率}$即变为
$$
\dot{m}=mr_s=m_0r_se^{-r_st}
$$
下图展示了燃烧速率的计算值和解析值。注意，燃烧速率与质量成正比，在这种情况下，质量呈指数衰减为零，因为我们指定了THICKNESS为$V/A$，并在定义单个固体网格单元的OBST线上设置BULK_DENSITY为$50 kg/m ^3$。

![image-20240530142040829](..\FDS中钠燃烧模型添加.assets\image-20240530142040829.png)

<center>固定反应速率下单个网格单元的燃烧速率</center>

### 液体表面的蒸发

#### 质量守恒

对应FDS参数surf_mass_vent_liquid

为了验证液体燃料蒸发模型，将1 cm深的庚烷池暴露在$50 kW/m^2$热流下，跟踪燃料蒸气和表面密度的演变。结果如下图所示。请注意，在“非共形（nonconforming）”的情况下，指定的池尺寸与指定的网格不一致，但预计生成相同的燃料蒸气量。

![image-20240530142148765](..\FDS中钠燃烧模型添加.assets\image-20240530142148765.png)

<center>液体表面质量变化的解析值与预测值比较</center>

#### 蒸发速率

对应FDS参数water_pool

在这个例子下，相对湿度为$RH=25%$，温度${{T}_{a}}=305\text{K}$的空气以$U=0.15m/s$的速度吹过长$L=1.2m$，宽$W=1m$，表面温度为${{T}_{s}}=293\text{K}$的水池。水的蒸发速率可用如下表示：
$$
\dot{m}=LWh_m\rho_{film}\ln\left(1+B\right)\approx1.42\times10^{-5}kg/s;B=\frac{Y_{s\nu}-Y_g}{1-Y_{s\nu}}\approx0.00925
$$
${{h}_{m}}$为传质系数，${{\rho }_{film}}$是表面薄层内的密度，$B$是Spalding传质数，${{Y}_{sv}}$为液体表面水蒸气的“表面蒸汽”质量分数，${{Y}_{g}}$为环境气体中水蒸气的质量分数。表层的组成由Clausius-Clapeyron平衡蒸汽压方程得到。表面水蒸气的体积和质量分数为：
$$
X_{s\nu}=\exp\biggl[-\frac{h_{\nu}W_{H_{2}O}}{R}\biggl(\frac{1}{T_{s}}-\frac{1}{T_{b}}\biggr)\biggr]\approx0.0278;Y_{s\nu}=\frac{X_{s\nu}W_{H_{2}O}}{X_{s\nu}W_{H_{2}O}+\begin{pmatrix}1-X_{s\nu}\end{pmatrix}W_{air}}\approx0.0175
$$
环境气体中水蒸气的体积和质量分数为：
$$
X_{{_{\mathrm{g}}}}=\frac{RH}{100}\exp\left[-\frac{h_{{_{\nu}}}W_{{_{H_{2}O}}}}{R}{\left(\frac{1}{T_{{_{a}}}}-\frac{1}{T_{{_{b}}}}\right)}\right]\approx0.0134\mathrm{~;~}Y_{{_{\mathrm{g}}}}=\frac{X_{{_{\mathrm{g}}}}W_{{_{H_{2}O}}}}{X_{{_{\mathrm{g}}}}W_{{_{H_{2}O}}}+\left(1-X_{{_{\mathrm{g}}}}\right)W_{{_{air}}}}\approx0.0084
$$
其中，${{h}_{v}}=2260kJ/kg$为水的蒸发热，${{W}_{{{H}_{2}}O}}=18kg/kmol$为水的摩尔质量，${{T}_{b}}=373K$为水的沸点，$R=8.3145kJ/kmol/K$为通用气体常数，${{W}_{air}}=29kg/kmol$为空气的摩尔质量。传质系数表示为，
$$
h_m=\frac{ShD}L\approx1.06\times10^{-3}m/s
$$
Sh为Sherwood数，$D=2.10\times {{10}^{-5}}{{m}^{2}}/s$是在$T=293K$下，水蒸气进入空气的扩散系数。Sh数的经验关系式为，
$$
Sh=0.037Sc^{1/3}\mathrm{~Re~}^{4/5}\approx60.8\text{ ; S}c=0.71\text{ ; Re}=\frac{\rho_aUL}\mu\approx12062
$$
在$T=293K$时，空气的动力粘度为$\mu =1.8\times {{10}^{-5}}kg/m/s$，液体表面的气体密度为，
$$
\rho_{film}=\frac{p_0W_{air}}{1000RT_s}\approx1.21kg/m^3
$$
其中${{p}_{0}}=101325Pa$。

注意，在输入文件中设置了ADJUST_H=F，以使分析结果的计算更容易。

下图比较了FDS的预测值和理论的蒸发速率。预测值和理论值并不完全相同，因为上面使用的标称参数没有考虑到池上表面温度和水蒸气浓度的微小变化。尽管如此，两者应该相对接近。

![image-20240530142520680](..\FDS中钠燃烧模型添加.assets\image-20240530142520680.png)

<center>水池的蒸发速率</center>

### 表面发射率的变化

对应FDS的参数emissivity

对于热厚材料，表面发射率计算为第一凝聚相网格单元中各个发射率值的质量加权和。在此验证测试中，初始材料的发射率为1.0，以恒定速率$0.1s^{-1}$转换为另一种材料，发射率为0.0。因此，表面发射率应在10秒内从1.0线性变化到0.0。

![image-20240530142618338](..\FDS中钠燃烧模型添加.assets\image-20240530142618338.png)

<center>固体材料发射率的测试</center>

### 收缩和膨胀材料

对应FDS参数为shrink_swell

多组分材料的单层包含反应物质(1)和惰性基质(2)。如果反应的生成物(3)的密度高于反应物(${{\rho }_{3}}>{{\rho }_{1}}$)，则层厚$\Delta $应收缩，反之膨胀（厚度增加）。如果惰性材料具有静态基质结构(ALLOW_SHRINKING=.FALSE. or ALLOW_SWELLING=.FALSE.)则层的厚度不应该改变。六个测试用例的参数如下表所示。下图显示了表面密度(显然不应该改变)和表面厚度随模拟时间的变化。

![image-20240530142707496](..\FDS中钠燃烧模型添加.assets\image-20240530142707496.png)

![image-20240530142712100](..\FDS中钠燃烧模型添加.assets\image-20240530142712100.png)

<center>收缩和膨胀表面的测试</center>

### 固体物质的焓

对应FDS参数为enthalpy

考虑一块导热材料的薄板，其一侧暴露在高温热源，另一侧暴露在环境温度空隙中。在热薄极限下，板坯的温度由下式控制
$$
\frac{dT_s}{dt}=\frac{\dot{q}_{front}^{^{\prime\prime}}+\dot{q}_{back}^{^{\prime\prime}}}{c_s\rho_s\delta}
$$
在本例中，楼板正面的初始暴露功率为3kw /m2。原始材料A发生反应生成材料B。反应速率恒定，为6 kg/(m3·s)，在这种情况下，这意味着初始密度为30 kg/m3的材料A在5 s内消失。这可以通过在反应速率项中设置ns 和E为0，A为6 kg/(m3·s)来实现：
$$
r=\rho_{s,A}^{n_s}A\exp\biggl(-\frac E{RT_s}\biggr)
$$
两种材料的密度和热导率分别为30 kg/m3和10 W/(m·K)。前后的发射率为1。材料A的比热在80℃以上从1.0 kJ/(kg·K)变化到0.1 kJ/(kg·K) ，而材料B的比热恒定在1.0 kJ/(kg·K)。板厚1毫米。值得注意的是，“解析”解实际上是上述方程为了确保计算精度而在较小时间步下的简单数值积分。本例(下图)测试了许多特征，包括反应速率、质量加权比热和辐射边界条件。注意，对流换热已关闭，正确的稳态温度由FDS计算。

![image-20240530142959316](..\FDS中钠燃烧模型添加.assets\image-20240530142959316.png)

<center>固体材料焓的测试</center>

### 一个简单的两步热解示例

对应FDS的参数为two_step_solid_reaction

在考虑实际的实验测量之前，有必要检查FDS内常微分方程解算器的准确性。考虑一组简化的常微分方程，描述固体材料在热降解过程中三种组分的质量分数：
$$
\begin{aligned}
&\frac{dY_a}{dt} =-K_{ab}Y_{a}  \\
&\frac{dY_b}{dt} =K_{ab}Y_a-K_{bc}Y_b  \\
&\frac{dY_c}{dt} =K_{bc}Y_a 
\end{aligned}
$$
其中，组分a的质量分数初始为1，解析解为，
$$
\begin{aligned}
&Y_{a}(t) =\exp\left(-K_{ab}t\right)  \\
&Y_{b}(t) =\frac{K_{ab}}{K_{bc}-K_{ab}}\exp\left(-K_{ab}t\right)-\exp\left(-K_{bc}t\right)  \\
&Y_{c}(t) =\begin{bmatrix}K_{ab}\left(1-\exp\left(-K_{bc}t\right)\right)+K_{bc}\left(\exp\left(-K_{ab}t\right)-1\right)\end{bmatrix}/\left(K_{ab}-K_{bc}\right) 
\end{aligned}
$$
参数为${{K}_{ab}}=0.389,{{K}_{bc}}=0.262$对应的解析解和数值解在下图表示。

![image-20240530143141222](..\FDS中钠燃烧模型添加.assets\image-20240530143141222.png)

<center>两步固体热解计算值解析解的比较</center>

### Interpreting Bench-Scale Measurements

本节描述了一种推导和应用**固体热分解动力学**参数值的方法，该方法遵循Lyon[^13]所描述的方法。这是热重分析(Thermo-Gravimetric Analysis-TGA)和微燃烧量热法(Micro-Combustion Calorimetry-MCC)等测量方法的基础理论。

#### 通用理论

考虑一个小的固体材料样品，它以相对缓慢的恒定速率加热。设固体由N个材料组分组成，各组分质量分数记为${{Y}_{\alpha }}\left( t \right)$。当固体被加热时，各组分发生反应，生成待定气体或单个固体残渣，其质量分数记为${{Y}_{r}}\left( t \right)$，产率记为${{v}_{r}}$。各组分质量分数的控制方程为：
$$
\frac{dY_\alpha}{dt}=-A_\alpha Y_\alpha\exp\biggl(-\frac{E_\alpha}{RT}\biggr);Y_\alpha\begin{pmatrix}0\end{pmatrix}=Y_{\alpha,0};\alpha{=}1,\mathrm{N}\tag{质量分数1}\label{质量分数1}
$$

$$
\frac{dY_r}{dt}=-\nu_r\sum_\alpha\frac{dY_\alpha}{dt};Y_r\begin{pmatrix}0\end{pmatrix}=0\tag{质量分数2}\label{质量分数2}
$$

在标准试验装置中，样品的温度随时间线性增加，$dT/dt=\beta $。由于试验结果通常以温度的函数而不是时间的函数表示，$\eqref{质量分数1}$重写为，
$$
\frac{dY_\alpha}{dT}=-\frac{A_\alpha}\beta Y_\alpha\exp\left(-\frac{E_\alpha}{RT}\right);Y\left(T=T_0\right)=Y_{\alpha,0}\tag{重写方程}\label{重写方程}
$$
各物质组分的分解速率$-d{{Y}_{\alpha }}/dt$在温度为${{T}_{\alpha ,p}}$时达到峰值${{r}_{\alpha ,p}}$。在这个温度下，${{Y}_{\alpha }}$的二阶导为0，
$$
\begin{aligned}
\frac{d^2Y_\alpha}{dT^2}& =-\frac{A_\alpha}\beta\frac{dY_\alpha}{dT}\exp\biggl(-\frac{E_\alpha}{RT_{\alpha,p}}\biggr)-\frac{A_\alpha}\beta Y_\alpha\exp\biggl(-\frac{E_\alpha}{RT_{\alpha,p}}\biggr)\frac{E_\alpha}{RT_{\alpha,p}}\biggr)  \\
&=-\frac{dY_\alpha}{dT}\Bigg[\frac{A_\alpha}\beta\exp\Bigg(-\frac{E_\alpha}{RT_{\alpha,p}}\Bigg)-\frac{E_\alpha}{RT_{\alpha,p}^2}\Bigg]=0
\end{aligned}\tag{二阶导}\label{二阶导}
$$
式$\eqref{重写方程}$可以从${{Y}_{\alpha ,0}}$到${{Y}_{\alpha ,p}}$，${{T}_{0}}$到${{T}_{\alpha ,p}}$积分得到下式，
$$
\int_{Y_{\alpha,0}}^{Y_{\alpha,p}}\left(\frac{dY_\alpha^{'}}{Y_\alpha^{'}}\right)=-\frac{A_\alpha}\beta\int_{T_0}^{T_{\alpha,p}}\exp\left(-\frac{E_\alpha}{RT^{'}}\right)dT^{'}\approx-\frac{A_\alpha RT_{\alpha,p}^2}{\beta\left(E_\alpha+2RT_{\alpha,p}\right)}\exp\left(\frac{-E_\alpha}{RT_{\alpha,p}}\right)
$$
利用式$\eqref{二阶导}$消去${{A}_{\alpha }}$得
$$
\ln\left(\frac{Y_{\alpha,p}}{Y_{\alpha,0}}\right)=-\frac{E_\alpha}{E_\alpha+2RT_{\alpha,p}}=-1\quad\left(E_\alpha\gg2RT_{\alpha,p}\right)
$$
或者更简单的，${{Y}_{\alpha ,p}}\approx {{Y}_{\alpha ,0}}/e$。活化能可通过式$\eqref{质量分数1}$和式$\eqref{二阶导}$计算得到，
$$
E_\alpha=RT_{\alpha,p}^2\frac{A_\alpha}\beta\exp\biggl(-\frac{E_\alpha}{RT_{\alpha,p}}\biggr)=\frac{RT_{\alpha,p}^2}\beta\frac{r_{\alpha,p}}{Y_{\alpha,p}}\approx\frac{RT_{\alpha,p}^2}\beta\frac{er_{\alpha,p}}{Y_{\alpha,0}}\tag{活化能}\label{活化能}
$$
然后可以直接根据式$\eqref{质量分数}$计算得到${{A}_{\alpha }}$，
$$
A_\alpha=\frac{r_{\alpha,p}}{Y_{\alpha,p}}\exp\left(\frac{E_\alpha}{RT_{\alpha,p}}\right)\approx\frac{er_{\alpha,p}}{Y_{\alpha,0}}\exp\left(\frac{E_\alpha}{RT_{\alpha,p}}\right)\tag{Aa}\label{Aa}
$$
注意，${{A}_{\alpha }}$和${{E}_{\alpha }}$的公式可以用通过检查质量损失率随温度变化的曲线直接得到的参数来计算。对于每一个峰，${{T}_{\alpha ,p}}$的值很容易通过检查得到。初始质量分数${{Y}_{\alpha ,0}}$可以根据每个峰下的相对面积来估计。${{Y}_{\alpha ,0}}$之和应为1。

反应速率${{r}_{\alpha ,p}}$需要稍微解释一下。通常，TGA之类的测试生成归一化样本质量($m/{{m}_{0}}$)及其随时间的一阶导数($-d\left( m/{{m}_{0}} \right)/dt$)的图。而上述分析中的反应速率可以解释为组分质量分数随时间的变化：
$$
r_\alpha=-\frac{dY_\alpha}{dt}
$$
两种速率的关系为，
$$
\sum_\alpha\frac{dY_\alpha}{dt}=\frac1{1-\nu_r}\frac{d(m/m_0)}{dt}
$$
因此，方程$\eqref{活化能}$和$\eqref{Aa}$需要的反应速率${{r}_{\alpha ,p}}$与归一化质量损失率曲线的关系如下，
$$
r_{\alpha,p}=-\frac1{1-\nu_r}\frac{d\left(m/m_0\right)}{dt}\Big|_{T=T_{\alpha,p}}\tag{反应速率}\label{反应速率}
$$
下一节中的示例描述了如何解释bench-scale材料测试的输出。

#### Interpreting TGA Data

对应的FDS的参数为tga_sample

下图左侧图的实心曲线显示了在TGA装置中以5℃/min的速率加热的小固体样品的测量归一化质量。右侧图的实线是质量损失率，或者减去左边图的一阶导数。本例的目的是从方程$\eqref{活化能}$和$\eqref{Aa}$来数值求解ODE方程$\eqref{质量分数1}$和$\eqref{质量分数2}$，得到动力学参数${{A}_{\alpha }}$和${{E}_{\alpha }}$。通常，这相当于质量损失率曲线中峰值的数量，但对于实际情况，需要进行一些判断。在这个例子中，假设有两个材料组分，每个组分都在特定的温度附近发生一次反应。经检查，${{T}_{1,p}}=300,{{T}_{2,p}}=500$。测量的下一个信息是剩余分数，它从左侧的图中获得，${{v}_{r}}=0.53$。由式$\eqref{反应速率}$，反应速率由右图的峰值质量损失率换算得到${{r}_{1,p}}=0.00045/0.47{{s}^{-1}}\text{ ; }{{r}_{2,p}}=0.0001/0.47{{s}^{-1}}$。最后，从右侧图中峰下的相对面积估计两组分的初始质量分数。在此例中，${{Y}_{1,0}}=0.6\text{ , }{{Y}_{2,0}}=0.4$。

![image-20240530144924744](..\FDS中钠燃烧模型添加.assets\image-20240530144924744.png)

<center>TGA分析结果。左：归一化的样品质量为温度的函数；右：相应的质量损失率</center>

在FDS的输入文件`tga_sample.fds`中，这些信息被转化为以下表达，

```fortran
&SURF ID = 'SAMPLE'
...
MATL_ID(1,1:2) = 'component 1','component 2'
MATL_MASS_FRACTION(1,1:2) = 0.6,0.4 /
&MATL ID = 'component 1'
...
N_REACTIONS = 1
REFERENCE_TEMPERATURE = 300.
REFERENCE_RATE = 0.0016
HEATING_RATE = 5.
NU_SPEC = 0.47
SPEC_ID = 'OFF-GAS'
NU_MATL = 0.53
MATL_ID = 'residue' /
&MATL ID = 'component 2'
...
N_REACTIONS = 1
REFERENCE_TEMPERATURE = 500.
REFERENCE_RATE = 0.0005
HEATING_RATE = 5.
NU_SPEC = 0.47
SPEC_ID = 'OFF-GAS'
MATL_ID = 'residue' /
```

注意，FDS输入参数REFERENCE_RATE表示${{r}_{\alpha ,p}}/{{Y}_{\alpha ,0}}$的量。还请注意每种材料成分具有相同的残留物产率，NU_MATL。仅从TGA数据来看，几乎不太可能确定存在多少特殊的材料组分或反应序列。这个练习的要点仅仅是让FDS模拟总质量损失率曲线。

#### TGA热速率的影响

对应FDS的参数为birch_tga

这是一个比较候选固相模型与TGA数据的例子，显示了样品加热速率的影响。样品案例birch_tga_1step_2和birch_tga_1step_20 模拟了两个标准的TGA实验，其中小样本桦木分别以2℃/min和20℃/min的恒定速率缓慢加热。木材模型只包括一个反应，将原始木材转化为炭和燃料气体。在模拟中也有一个反应，除了蒸发木材中的少量水分之外什么都不做。这种蒸发在下图中，温度在100℃附近是显著的。

![image-20240530145954371](..\FDS中钠燃烧模型添加.assets\image-20240530145954371.png)

<center>桦木固相模型与TGA数据的比较</center>

#### 碳化样品的TGA

对应FDS的参数为Needle_TGA

在本节中，根据一组TGA测量结果推导出长叶松针的动力学参数[^f7]。表中列出的Case A和B用于推导所有8个案例的动力学参数。所有8种情况的质量和质量损失率曲线如图b至图e所示。

假定松针由水分和三种固相组分组成，分别占总干质量的0.25、0.50和0.25，在250℃、350℃和425℃时达到峰值分解率。这些估计是通过检查图a所示的实验数据得到的。进一步假设干质量的0.25转化为焦炭，并根据Case B估计氧化反应的动力学。

<center>表 松针TGA实验参数。注意，加热速率是指样品在大约100℃下干燥后温度的线性上升</center>

![image-20240530150356542](..\FDS中钠燃烧模型添加.assets\image-20240530150356542.png)

![image-20240530150402457](..\FDS中钠燃烧模型添加.assets\image-20240530150402457.png)

<center>a. Case A(左)和B(右)的质量损失率。这些Case是用来为所有8种Case A-H确定动力学</center>

![image-20240530150434671](..\FDS中钠燃烧模型添加.assets\image-20240530150434671.png)

<center>b. 松针TGA校准结果，Case A(左)和B(右)。(上)样品温度随时间的变化。(中)样品质量分数随时间的变化。(下)样品质量损失率随时间的变化。</center>

![image-20240530150451074](..\FDS中钠燃烧模型添加.assets\image-20240530150451074.png)

<center>c. 松针的TGA校准结果，Case C(左)和D(右)。(上)样品温度随时间的变化。(中)样品质量分数随时间的变化。(下)样品质量损失率随时间的变化。</center>

![image-20240530150508949](..\FDS中钠燃烧模型添加.assets\image-20240530150508949.png)

<center>d. 松针的TGA校准结果，Case E(左)和F(右)。(上)样品温度随时间的变化。(中)样品质量分数随时间的变化。(下)样品质量损失率随时间的变化</center>

![image-20240530150524725](..\FDS中钠燃烧模型添加.assets\image-20240530150524725.png)

<center>e. 松针TGA校准结果，Case G(左)和H(右)。(上)样品温度随时间的变化。(中)样品质量分数随时间的变化。(下)样品质量损失率随时间的变化。</center>

------

[^f7]: TGA data provided by the Forest Products Laboratory of the U.S. Forest Service

#### Interpreting MCC Data

对应FDS的参数为cable_XX_mcc

本节介绍一种解释微燃烧量热计(MCC)测量结果的方法。热解燃烧流量量热计(PCFC)是由美国联邦航空管理局(FAA)的Lyon和Walters[^14]研制的，是一种用耗氧量热法测量微小的(4 mg ~ 6 mg)材料样品燃烧产生热量的装置。样品在厌氧气氛(通常是N2)中以规定的加热速率热解，所得气体与多余的氧气混合，并在单独的室中燃烧。试样的放热率是通过测量从燃烧室流出的氧气浓度随时间的变化得到的。该方法论是ASTM D 7309标准测试的基础[^15]。

几种电缆的护套和绝缘材料的PCFC测量结果如下图a所示。这些样品在PCFC中以1℃/s的速率在100℃至600℃的氮气气氛中热解，排出物在由20% O2和80% N2组成的混合物中在900°C下燃烧。所得到的曲线显示了样品在加热时的放热率，用原始样品的质量归一化。曲线上通常有一个、两个或三个明显的峰值，对应于发生重大分解反应的温度。每个峰可以用单位质量放热速率的最大值${{\dot{q}}_{\alpha ,p}}$、温度${{T}_{\alpha ,p}}$和发生该特定反应的原始样品质量的相对分数${{Y}_{\alpha ,0}}$来表征。曲线下的面积为样品加热速率$\beta $乘以原始样品每单位质量能量释放量$\Delta {{h}^{'}}$。
$$
\int_0^\infty\dot{q}(T)dT=\beta\Delta h^{^{\prime}}
$$
![image-20240530150904022](..\FDS中钠燃烧模型添加.assets\image-20240530150904022.png)

<center>a. 电缆绝缘(左)和护套材料(右)的微量热分析结果</center>

后一个量通过关系式与更常规[^f8]的燃烧热有关，
$$
\Delta h=\frac{\Delta h^{^{\prime}}}{1-\nu_r}
$$
其中，${{v}_{r}}$是原始质量的残留分数，有时这被称为“炭产率”。注意，假设对所有的反应都是一样的。

MCC测量与TGA类似，可以从放热速率曲线中推导出各种反应的动力学参数${{A}_{\alpha }}$和${{E}_{\alpha }}$。作为如何处理MCC数据的示例，请参考图a所示的两个图。图中的实线曲线显示了多芯控制电缆绝缘和护套材料的微量热测量结果(这些数字除了与所研究的其他电缆区分外，没有特别的含义)。

以电缆11为例，绝缘材料呈现两个相当明确的峰值，而护套材料呈现三个峰值。因此，使用两种固体成分来模拟绝缘材料，每一种都经历一次单步反应，产生燃料气体和固体残留物。护套材料使用三个实体组件建模。所述绝缘材料的残留物产率为6%；对于夹套为49%，只需在测量前后称重即可获得。目前还不知道哪一个反应会产生多少残留物。相反，假设每个反应产生相同相对量的残留物。图a中的虚线是MCC测量的FDS模拟结果。为了模拟样品加热，以实验规定的速率(1℃/s或60℃/min，FDS所需的单位)加热由固体组分混合物和绝缘衬底组成的非常薄的薄片。每个反应的动力学参数由式$\eqref{活化能}$和$\eqref{Aa}$计算。${{T}_{\alpha ,p}}$的值直接从图中获得，反应$\alpha $的峰值反应率${{r}_{\alpha ,p}}$从下式获得，
$$
r_{\alpha,p}=\frac{\dot{q}_{\alpha,p}}{\Delta h^{\prime}},\Delta h^{\prime}=\frac1\beta\int_0^\infty\dot{q}(T)dT
$$
其中，${{\dot{q}}_{\alpha ,p}}$是反应$\alpha $的峰值热释放率，${{Y}_{\alpha ,0}}$的值可以从曲线下方的相对面积估算得到，他们的和应该为1。检查所有这些量的单位是很重要的，因为这些实验的结果往往以不同的方式呈现，这取决于特定的应用。单位的错误可能导致${{A}_{\alpha }}$和/或${{E}_{\alpha }}$的值不可避免地出现虚假结果。因此，**通过输入反应参数来避免直接计算动力学参数**。

图a中的虚线是对各材料成分在FDS内的式进行数值积分的结果。描述发生**单一反应的单一材料组分**的FDS的典型输入行是，

```fortran
&MATL ID = 'Cable 11 Jacket Component A'
...
N_REACTIONS = 1
REFERENCE_TEMPERATURE = 300.
REFERENCE_RATE = 0.0064
HEATING_RATE = 60.
NU_MATL = 0.49
MATL_ID = 'char'
NU_SPEC = 0.51 /
```

只显示相关参数。其他参数与本练习无关。请注意，REFERENCE_TEMPERATURE是以℃为单位的${{T}_{\alpha ,p}}$。REFERENCE_RATE实际上是${{r}_{\alpha ,p}}/{{Y}_{\alpha ,0}}$，单位为s−1。HEATING_RATE是$\beta $，单位为℃/min。NU_MATL为${{v}_{r}}$，NU_SPEC为$1-{{v}_{r}}$。表a列出了电缆绝缘和护套材料的所有动力学参数。峰值温度很容易估计，${{r}_{p,i}}/{{Y}_{0,i}}$可以微调到与数据非常匹配。请注意，可以计算${{A}_{i}}$和${{E}_{i}}$的值并将其直接输入到FDS中，而不是输入表中列出的值。但是，${{A}_{i}}$和${{E}_{i}}$的值是相当大的数字，它们本身没有什么意义。

<center>a. 用于导出电缆11材料的动力学常数的参数。两者的加热速率均为60℃/min</center>

![image-20240530152011715](..\FDS中钠燃烧模型添加.assets\image-20240530152011715.png)

------

[^f8]: In fire protection engineering, it is typically assumed that the heat of combustion is the energy released per unit mass of vaporized fuel.

### 锥数据外推模型

对应FDS的参数为cone_demo_2

本节测试一个模型，用于将锥形量热计的热释放率数据外推到热通量，而不是锥形试验期间使用的模型。在这种情况下，通过为表面分配HRRPUA和RAMP_Q，进行$50 kW/m^2$的锥形测试。表面是给定的IGNITION_TEMPERATURE，温度为0℃，所以它立即点燃。表面暴露在锯齿形的EXTERNAL_FLUX中，其变化范围在$10 kW/m^2$和$ 110 kW/m^2$之间。结果如下图所示。

![image-20240530152233798](..\FDS中钠燃烧模型添加.assets\image-20240530152233798.png)

<center>锥数据外推模型</center>

### Melting Ice Cube

对应FDS的参数为ice_cube

本节测试MATL反应产生颗粒的能力。一个10厘米立方体(1公斤)的冰块定义为10 kW/m2的EXTERNAL_FLUX。产生的水滴的质量被跟踪。结果如下图所示。

![image-20240530152316062](..\FDS中钠燃烧模型添加.assets\image-20240530152316062.png)

<center>根据表面反应特征检查颗粒产量</center>

## 拉格朗日粒子

## 反应时间尺度模型

在本节中，我们提供了一个基于流场局部状态的混合时间表达式。我们在这里提出的模型背后的基本思想是考虑扩散、亚网格尺度(SGS)平流和浮力加速这三个物理过程，并将这些过程中(局部)最快的过程作为控制流动时间尺度。

当LES过滤器宽度(单元大小)变化时，考虑SGS模型的行为是很重要的。扩散、SGS平流和浮力加速度的混合时间随过滤器宽度的不同而不同，如果我们观察过滤器尺度的极限，就会出现一幅有趣的画面。参考图a，让我们沿着代表假设流动条件的时间尺度模型的粗黑线沿水平轴从左向右移动。

![image-20240530152408500](..\FDS中钠燃烧模型添加.assets\image-20240530152408500.png)

<center>a. 反应时间尺度模型</center>

首先，注意反应时间范围必须大于或等于化学的时间尺度，${{\tau }_{chem}}$，其是火焰厚度遍历时间的顺序，${{\tau }_{chem}}\sim\delta /{{s}_{L}}$，$\delta ={{D}_{F}}/{{s}_{L}}$，DF是燃料的扩散系数，sL是火焰速度。在稍微大一点的尺度上，我们期望混合时间随过滤器宽度的平方而变化，因为混合是由分子扩散控制的。在这个体系中，表示为${{\tau }_{\text{d}}}$，数值解是一个DNS。当$\Delta $小于 Kolmogorov标度$\eta $ (最小湍流漩涡的长度标度)时，该标度定律有效(在本讨论中，我们假设 Schmidt数(Sc)为阶单位)。对于足够高的雷诺数流动(例如存在一个惯性的子范围)，当过滤器宽度增加到超过柯Kolmogorov尺度时，我们会遇到一个标记为${{\tau }_{\text{u}}}$的区域，在那里湍流平流控制混合速率。在这里，混合时间随滤波器宽度的三分之二次方而变化[^16]。这是大多数LES子模型有效的机制( 理解这一点很重要)

现在，让我们想象一下，当滤波器宽度超过惯性子范围增加到比火焰本身的高度更大的长度尺度时，混合时间会发生什么变化(实际上野火建模中是可能的)。我们不会期望惯性范围尺度通过所谓的“含能”湍流长度尺度范围继续向上。相反，对于火灾，我们期望浮力加速度在这些相对粗糙的尺度上控制混合。基于恒定加速度的时间尺度为滤波器宽度的平方根，如图中标记为${{\tau }_{\text{g}}}$的区域所示。考虑到图的对数-对数性质，这种缩放的变化可能看起来很小，但是对于大的单元格大小来说，基于加速的时间尺度的影响确实很显著。最后，请注意火焰高度对反应时间尺度有限制，这里表示为${{\tau }_{\text{flame}}}$，因为所有的燃料都必须在一个网格内消耗。

当然，物理过程的相对重要性将取决于流量。例如，如果重力较弱，${{\tau }_{\text{g}}}$线向上移动，在火焰时间尺度达到之前可能不会影响反应时间。如果流动是高度湍流的，惯性范围尺度可能更占优势，这将通过${{\tau }_{\text{u}}}$线的降低表示。或者，对于高湍流射流火焰，火焰可能在加速度时间尺度产生任何影响之前达到。也许对于低应变火灾来说，更典型的情况是，如果惯性子范围不存在(如果雷诺数相对于弗劳德数过低)，那么图a中的${{\tau }_{\text{u}}}$线就会向上移动，我们只剩下扩散和浮力来控制混合。

图a中粗体实线在数学上表示为：
$$
\tau_{\mathrm{mix}}=\max\left(\tau_{chem},\min\left(\tau_{\mathrm{d}},\tau_{\mathrm{u}},\tau_{\mathrm{g}},\tau_{\mathrm{flame}}\right)\right)
$$
子模型的数学细节如下：
$$
\begin{aligned}
&\tau_{\mathrm{d}} =\frac{\Delta^2}{D_F}  \\
&\tau_{\mathbf{u}} =\frac{C_u\Delta}{\sqrt{(2/3)k_{sgs}}}  \\
&\tau_{\mathrm{g}} =\sqrt{2\Delta/g} 
\end{aligned}
$$
式中DF为燃料种类的扩散系数。注意，ksgs是单位质量的未闭合亚格子动能，默认情况下取自湍流粘度模型。校准平流时间尺度常数以匹配Heskestad火焰高度关联式，设为 Cu = 0.4。加速度时间尺度${{\tau }_{\text{g}}}$是在恒定加速度$g = 9.81 m/s^2$下，从静止开始移动距离$\Delta $所需的时间。

## Specify Lumped Species

see 6.8.0 FUG 12.2

## 程序求解流程

求解程序使用二阶显式预估-校正格式。流程如下：

![image-20240530153201184](..\FDS中钠燃烧模型添加.assets\image-20240530153201184.png)

![image-20240530153204990](..\FDS中钠燃烧模型添加.assets\image-20240530153204990.png)

<center>FDS求解流程</center>

## FDS中的输出文件格式

代码输出包括文件 CHID.out，以及下文所述的各种数据文件。**这些输出文件大多由 dump.f90 中的子程序写出，很容易修改以适应各种绘图软件包**。

### Diagnostic Output (.out)





## File Extension Glossary

| File extension | Short Description                          | Reference                |
| -------------- | ------------------------------------------ | ------------------------ |
| .be            | Data values for .gcf,.gsf,.iso files       | Section 27.17            |
| .bf            | Boundary files                             | Section 27.11            |
| .bingeom       | Binary geometry files                      | Section 27.19            |
| .bnd           | Min/Max Bound files                        | Smokeview User’s Guide   |
| .fds           | FDS input files                            | FDS User’s Guide Part II |
| .gbf           | Geometry boundary files                    | **To be deprecated**     |
| .gcf           | CFACE geometry files                       | Section 27.16            |
| .ge            | Geometry vertices and faces                | Section 27.20            |
| .ge2           | Geometry face properties                   | Section 27.20            |
| .gsf           | Unstructured slice files                   | Section 27.16            |
| .ini           | Smokeview configuration files              | Smokeview User’s Guide   |
| .iso           | Isosurface files                           | Section 27.15            |
| .out           | FDS output log files                       | Section 27.1             |
| .prt5.gbnd     | Global bounds of all particle files        |                          |
| .prt5          | Particle files                             | Section 27.12            |
| .q             | Plot3D files                               | Section 27.10            |
| .restart       | FDS restart files                          | Section 5.6              |
| .s3d           | 3D smoke files                             | Section 27.14            |
| .sf            | Slice files                                | Section 27.9             |
| .sinfo         | Slice parameter files                      | Smokeview User’s Guide   |
| .smv           | Smokeview files                            | Smokeview User’s Guide   |
| .ssf           | Smokeview script files                     | Smokeview User’s Guide   |
| .stop          | If present, stops a simulation gracefully  | Section 5.6              |
| .sz            | Size files for Smokeview memory allocation |                          |
| .ter           | Terrain data files                         | Section 27.18            |
| .xyz           | Plot3D mesh files                          | Section 27.10            |
| _devc.csv      | Device files                               | Section 27.3             |
| _git.txt       | Git revision                               |                          |
| _hrr.csv       | Heat Release Rate files                    | Section 27.2             |



## Smokeview使用技巧

1. 通过在Smokeview中切换**“q”**键，您可以通过显示您指定的VENT来消除颗粒状颜色重叠，而不是FDS重新定位它的位置。这个技巧也适用于两个障碍物的面重叠的地方。
2. ![image-20240605101028607](..\FDS中钠燃烧模型添加.assets\image-20240605101028607.png)![image-20240605101039686](..\FDS中钠燃烧模型添加.assets\image-20240605101039686.png)
3. 



# 火灾动力学

生成热：化学反应中由稳定的单质反应生成某化合物时的反应热，即为该化合物的生成热。

反应热：是指当生成物的温度和反应物的温度相同，且反应过程中只做体积功时，反应过程所吸收或放出的能量。

燃烧热：反应物与生成物之间的化学能之差（焓差）。燃烧热是燃料和氧化剂在标准条件下发生反应并形成产物时的反应焓。Heat of combustion, enthalpy of combustion, calorific value, and heating value are synonyms, the latter two being used more commonly in the heating industry.

生成焓？

# 案例

## 池火

池火对于研究火灾的发展是很有趣的，因为它们相对容易处理。人们需要一个防火的平底锅，比如用钢板做的，然后倒入可燃液体。点火后不久，由于液体的蒸发，它达到准稳态。池火的缺点之一是燃料供应有限。这也是在火灾实验中经常使用燃气燃烧器的原因之一。这一点，与燃气燃烧器作为点火源有关的良好再现性。同样，在FDS中，大多数池火模拟被建模为燃气燃烧器（**见FDS 6.8.0用户手册11.4 Simple Pyrolysis Models**）。

这个例子演示了一个极简FDS仿真的设置和分析。从一个简单的固定放热速率的池火开始，用不同的参数对模型进行扩展。通过与简单分析方法的比较，验证了所得结果。

### 案例设置

池表面积为1m2，位于z=0m处。火的放热速率为10MW，对模拟域的横向边界和顶部边界进行密封，并对计算域进行扩展->$\left[ -2.5m,2.5m \right]\times \left[ -2.5m,2.5m \right]\times \left[ 0m,10m \right]$，网格分辨率为0.2m。

```fortran
10.	"--------------------------------------------------------------------------------------------"
11.	"Output files will be tagged with 'pool_fire', 'TITLE' is just an description"
12.	"--------------------------------------------------------------------------------------------"
13.	&HEAD CHID = 'pool_fire', TITLE = 'Example of a pool fire'  /
14.	
15.	"--------------------------------------------------------------------------------------------"
16.	"Mesh with 25/25/50 cells in X/Y/Z axes that extends from X/Y/Z = -2.5/-2.5/0 to 2.5/2.5/10 m"
17.	"--------------------------------------------------------------------------------------------"
18.	&MESH IJK = 25,25,50, XB = -2.5,2.5, -2.5,2.5, 0.0,10 /
19.	
20.	"--------------------------------------------------------------------------------------------"
21.	"End of simulation time is 30 s"
22.	"--------------------------------------------------------------------------------------------"
23.	&TIME T_END = 30.0 / End of simulation time is 30 s
24.	
25.	"--------------------------------------------------------------------------------------------"
26.	"Specifying FDS default fuel 'METHANE' for the reaction"
27.	"--------------------------------------------------------------------------------------------"
28.	&REAC FUEL = 'METHANE' /
29.	
30.	"--------------------------------------------------------------------------------------------"
31.	"Surface 'BURNER' with a heat release rate of 1000 kW/m^2"
32.	"--------------------------------------------------------------------------------------------"
33.	&SURF ID = 'BURNER', HRRPUA = 1000., COLOR = 'RASPBERRY' / Surface with ID /
34.	
35.	"--------------------------------------------------------------------------------------------"
36.	"Vent in the X-Y plane at Z = 0 that extends from X/Y = -0.5/-0.5 to 0.5/0.5"
37.	"Surface 'BURNER' is assigned to the vent"
38.	"--------------------------------------------------------------------------------------------"
39.	&VENT XB = -0.5,0.5, -0.5,0.5, 0.0,0.0, SURF_ID='BURNER'/
40.	
41.	"--------------------------------------------------------------------------------------------"
42.	"Slice file in the Y-Z plane at X = 0 with quantity 'temperature'"
43.	"CELL_CENTERED prevents FDS from interpolating the results to the cell corners"
44.	"--------------------------------------------------------------------------------------------"
45.	&SLCF PBX = 0, QUANTITY = 'TEMPERATURE', CELL_CENTERED = .TRUE. /
46.	
47.	"--------------------------------------------------------------------------------------------"
48.	"FDS does not look after this line"
49.	"--------------------------------------------------------------------------------------------"
50.	&TAIL /
```

![image-20240531091344751](..\FDS中钠燃烧模型添加.assets\image-20240531091344751.png)![image-20240531091350887](..\FDS中钠燃烧模型添加.assets\image-20240531091350887.png)![image-20240531091408231](..\FDS中钠燃烧模型添加.assets\image-20240531091408231.png)

用`fdsreader`对温度的处理结果为：

```python
import os
import fdsreader
from matplotlib import cm, pyplot as plt
	
data_dir='./'
sim = fdsreader.Simulation(data_dir)
slice_temp = sim.slices[0]
time = 20
time_index = slice_temp.get_nearest_timestep(time)
	
plt.figure(figsize=(4,6))
plt.imshow(slice_temp[0].data[time_index].T, origin='lower', 
           extent=slice_temp[0].extent.as_list(), cmap='jet',
	           vmin=20, vmax=1200)
plt.xlabel("X / m")
plt.ylabel("Z / m")
plt.colorbar(label="Temperature / $\sf ^\circ C$")
plt.savefig('pool_fire_1mw_temperatures_slice.png', bbox_inches='tight')
plt.close()
```

![image-20240531091619400](..\FDS中钠燃烧模型添加.assets\image-20240531091619400.png)

<center>t=20s时x-z切面（y=0）温度云图</center>

## 图片转视频

```diff
ffmpeg -framerate 10 -i img%03d.jpg -c:v libx264 -r 30 -pix_fmt yuv420p output.mp4
```

>  在这个命令中，`-framerate`指定了图片的帧率，即每秒显示的图片数量。`-i img%03d.jpg`指定了输入图片的文件名模式，其中`%03d`表示一个三位数的数字序列。你需要根据你的图片文件名进行相应的调整。`-c:v libx264`指定了视频编码为H.264，`-r 30`指定了输出视频的帧率为30fps，`-pix_fmt yuv420p`指定了像素格式为YUV420P，这是一种常见的兼容性较好的像素格式。`output.mp4`是输出视频的文件名，你可以根据需要修改。

# FDS中的注意事项

指定HEAT_OF_COMBUSTION将导致FDS根据SPEC输入重新计算任何燃料种类的**生成焓**。若未指定，程序中如何计算？

MASS_FRACTION：怎么计算的？

VOLUME_FRACTION

FIXED_MIX_TIME：湍流预混合时间

如果要指定反应顺序发生，请使用参数PRIORITY（P179），注意，在这个反应方案中，消防模型应用于第一个反应，而不是第二个和第三个反应，因为默认的消光模型只应用于多个快速反应中的第一个反应。

BACKGROUND=T？

&DUMP DT_HRR=10

&COMB FIXED_MIX_TIME

默认情况下，FDS使用混合控制燃烧模型，这意味着反应速率是无限的，仅受物种浓度的限制。然而，FDS也可以使用阿伦尼乌斯模型使用**有限速率反应**(需要非常细的网格分辨率，对于大规模火灾模拟不适用，建议在DNS模式下调用有限速率反应)

求解器指定：通过在COME行中设置ODE_SOLVER

液滴燃烧：P204

通过CHID.out文件查看更多信息，如何调整湍流普朗特数和湍流施密特数，各自的定义是什么？

环境温度TMPA默认为20℃，可以在源程序中改，或在MISC中定义。

Enthalpy of Formation：$H_F$——>heat of formation

:interrobang:以下两个表达式的计算方式不同（read.f90）：

![image-20240528085524513](..\FDS中钠燃烧模型添加.assets\image-20240528085524513.png)

![image-20240528085538756](..\FDS中钠燃烧模型添加.assets\image-20240528085538756.png)

Fuel FORMULA for SIMPLE_CHEMISTRY can only contain C,H,O, and N. 

设置点燃温度？

FDS如何激活热解模型的？需要设置哪些参数？

可参考：circular_burner.fds、specified_hrr.fds



# 参考文献

文献[^3]对湍流燃烧进行了较为详细的描述。

[^1]:钠冷快堆柱状流钠火仿真研究_汤烨鑫
[^2]:钠冷快增殖堆池式钠火事故分析计算_王学容
[^3]:钠火事故钠滴燃烧仿真研究_唐绪聪
[^4]:【钠物性】Thermodynamic and transport properties of sodium liquid and vapor
[^5]:【钠表面张力】Experimental investigation of the  surface tension of liquid sodium
[^6]:Klause J, Kurge D. Solar thermal plant power and process heat[J]. Deutsches zentrum  fur luft und raumfahrt. 2003.7: 181-216.
[^7]:Luster V.P and Freudenstein K.F. Feedback from practical experience with large sodium  fire accident[C]. IWGFR/92, O-arai, Japan, 1996. 
[^8]:Mikami H, Shono A. Sodium leak at monju(I)-Cause and Consequence[J]. IWGFR/92,  O-arai, Japan, Nov.1996. 
[^9]:Funada T and Yamagishi Y. Sodium Leak at Monju(II)-Sodium leak, burning and  aerosol behavior[J]. IWGFR/92, O-arai, Japan, Nov.1996.
[^10]:Malet J C. Generation IV roadmap descripion of candidate Liquid-Mental- Cooled  reactor systems report[J]. Nuclear energy research advisory committee and the  generation IV international forum, 2002(3): 96-168.
[^11]:【物性】Numerical modeling of sodium fire—Part I Spray combustion
[^12]:A. Khawam and D. R. Flanagan. Solid-State Kinetic Models: Basics and Mathematical Fundamentals. J. Phys. Chem. B, 110:17315–17328, 2006. 177
[^13]:R.E. Lyon. Heat Release Kinetics. Fire and Materials, 24:179–186, 2000. 189
[^14]:R.E. Lyon and R.N. Walters. Pyrolysis Combustion Flow Calorimetry. Journal of Analytical and Applied Pyrolysis, 71(1):27–46, March 2004. 199
[^15]:American Society for Testing and Materials, West Conshohocken, Pennsylvania. ASTM D 7309-11, Standard Test Method for Determining Flammability Characteristics of Plastics and Other Solid Materials Using Microscale Combustion Calorimetry, 2011. 199
[^16]:Stephen B. Pope. Turbulent Flows. Cambridge University Press, 2000. 10, 25, 27, 28, 29, 43, 52, 105, 171, 172, 181
[^17]:G.P. Forney. Smokeview, A Tool for Visualizing Fire Dynamics Simulation Data, Volume I: User’s Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, sixth edition,May 2013. v, 3, 7, 300, 407, 416, 426, 467
[^18]:B. Ralph and R. Carvel. Coupled hybrid modelling in fire safety engineering; a literature review. Fire Safety Journal, 100:157 – 170, 2018. 126
[^19]:N. Jarrin. Synthetic Inflow Boundary Conditions for the Numerical Simulation of Turbulence. PhD thesis, The University of Manchester, Manchester M60 1QD, United Kingdom, 2008. 123, 124
[^20]:T.L. Bergman, A.S. Lavine, F.P. Incropera, and D.P. DeWitt. Fundamentals of Heat and Mass Transfer.John Wiley and Sons, New York, 7th edition, 2011. 74, 75, 478, 479
[^21]:H.S. Mickely, R.C. Ross, and A.L. Squyers. Heat, Mass, and Momentum Transfer for Flow Over a Flat Plate with Blowing or Suction. Technical Note 3208, National Advisory Committee for Aeronautics,Washington, DC, July 1954. 77
[^22]:B. Ralph and R. Carvel. Coupled hybrid modelling in fire safety engineering; a literature review. Fire Safety Journal, 100:157 – 170, 2018. 126
[^23]:K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 3: Validation. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 3, 43, 152

[^24]:K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. Vol. 1: Mathematical Model; Vol. 2: Verification Guide; Vol. 3: Validation Guide; Vol. 4: Software Quality Assurance. v, 60, 76, 104, 157, 173, 313
[^25]:F. Bisetti, G. Blanquart, and H. Pitsch. Direct numerical simulation of soot formation in turbulent non-premixed flames. Technical report, Stanford Center for Turbulence Research, 2008. 158
[^26]:Sebastian Ferreyro Fernandez. ADVANCED SOOT AND RADIATION MODELS FOR LAMINAR AND TURBULENT FLAMES. PhD thesis, The Pennsylvania State University, 2018. 158
[^27]:W. Grosshandler. RadCal: A Narrow Band Model for Radiation Calculations in a Combustion Environment. NIST Technical Note 1402, National Institute of Standards and Technology, Gaithersburg, Maryland, 1993. 4, 159
[^28]:D. Purser and J. Purser. HCN Yields and Fate of Fuel Nitrogen for Materials under Different Combustion Conditions in the ISO 19700 Tube Furnace and Large-scale Fires. In Fire Safety Science –Proceedings of the Ninth International Symposium, pages 1117–1128. International Association of Fire Safety Science, 2008. 169
[^29]:K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 1: Mathematical Model. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 3, 75, 80, 123, 125, 171, 187, 188, 196, 202, 211, 281, 310, 312, 315, 324, 373, 384, 395, 398, 435
[^30]:C. Beyler. SFPE Handbook of Fire Protection Engineering, chapter Flammability Limits of Premixed and Diffusion Flames. Springer, New York, 5th edition, 2016. 172, 173, 174
[^31]:C.K. Westbrook and F.L. Dryer. Simplified Reaction Mechanisms for the Oxidation of Hydrocarbon Fuels in Flames. Combustion Science and Technology, 27:31–43, 1981. 184, 185
[^32]:J. Andersen, C.L. Rasmussen, T. Giselsson, and P. Glarborg. Global Combustion Mechanisms for Use in CFD Modeling Under Oxy-Fuel Conditions. Energy & Fuels, 23(3):1379–1389, 2009. 185
[^33]:W. P. Jones and R. P. Lindstedt. Global reaction schemes for hydrocarbon combustion. Combustion and Flame, 73:233–249, 1988. 186
[^34]:M.M. Khan, A. Tewarson, and M. Chaos. SFPE Handbook of Fire Protection Engineering, chapter Combustion Characteristics of Materials and Generation of Fire Products. Springer, New York, 5th edition, 2016. 177, 178, 180, 188, 193, 194
[^35]:J.R. Hartman, A.P. Beyler, S. Riahi, and C.L.Belyer. Smoke oxidation kinetics for application to prediction of clean burn patterns. Fire and Materials, 36:177–184, 2012. 189



[^p3]:

