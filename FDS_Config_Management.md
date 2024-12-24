# Overview of FDS and Smokeview

本文件介绍了火灾动力学模拟器 (FDS) 及其配套程序 Smokeview 的开发和部署过程。本软件质量保证 (SQA) 计划旨在指导对模型进行修改的规划，对模型的软件和相关文档进行必要的审查，确定在发布更新模型之前要进行的测试，描述问题报告和解决程序，并确保所有记录、源代码和发布的软件在代码的生命周期内可用。虽然本报告和我们的许多做法都遵循 ASTM 国际标准 1355-05 “确定性火灾模型预测能力评估标准指南”[^2]，该标准被广泛用于指导模型的文档编制、验证和确认，但我们也遵循了其他标准。最值得注意的是，电气和电子工程师学会 (IEEE) 标准 IEEE 730-2002 [^4] 和 828 [^1]，它们定义了软件质量保证重要领域的最佳实践，并为本计划的结构和内容提供了指导。

构成 FDS 文件的各卷部分基于 ASTM E 1355《确定性火灾模型预测能力评估标准指南》[^2]。ASTM E 1355 概述了评估火灾模型准确性的过程。第 1 卷至第 3 卷就是这一评估过程的结果。本卷的主要目的是描述模型软件的开发和维护过程。像 FDS 这样的模型不可能一成不变。随着火灾科学的不断进步，模型需要不断更新和改进，但仍要能够可靠地预测最初设计时所针对的各种现象。

本文件中概述的 SQA 流程和要求专门适用于 FDS 和 Smokeview，并侧重于确保模型数值预测的质量。任何可能用于为模型开发输入文件的用户界面都不包括在此流程中。用户必须确保为模拟开发的输入文件准确反映所需的模型输入，无论是使用第三方界面开发还是使用电子表格或文本编辑程序手动输入。这些输入文件将作为下文概述的模型文件的一部分。

本章简要介绍火灾动态模拟器 (FDS) 和 Smokeview，包括其历史、开发人员、功能和应用。

## Model Type

FDS 是火灾驱动流体流动的计算流体动力学 (CFD) 模型。该模型对纳维-斯托克斯方程的一种形式进行数值求解，该方程适用于低速热驱动流动，重点关注火灾产生的烟雾和热量传输。质量、动量和能量守恒方程中的偏导数采用有限差分近似计算，解法在三维直线网格上及时更新。热辐射采用有限体积技术在与流动求解器相同的网格上进行计算。拉格朗日粒子用于模拟喷洒水滴、燃料喷射和无法解决的子网格物体。

Smokeview 是 FDS 的配套程序，可生成结果的图像和动画。近年来，其开发者格伦-福尼（Glenn Forney）在 Smokeview 中增加了以相当逼真的方式将火和烟可视化的功能。从某种意义上说，Smokeview 现在通过其三维渲染成为物理模型不可分割的一部分，因为它可以让人们以普通科学可视化软件无法做到的方式评估火场内的能见度。

虽然不属于 NIST 维护的 FDS/Smokeview 套件（也不受本计划的约束），但 FDS 有几个第三方和专有的 “附加组件”，这些组件可以通过商业途径获得，也可以由个人用户私人维护。最值得注意的是，有几个图形用户界面 (GUI)，可用来创建输入文件，其中包含执行模拟所需的所有必要信息。

## Model Version

FDS 第一版于 2000 年 2 月公开发布，第二版于 2001 年 12 月公开发布，第三版于 2002 年 11 月公开发布，第四版于 2004 年 7 月公开发布，第五版于 2007 年 10 月公开发布，第六版于 2013 年 10 月公开发布。

从 FDS 5 开始，实施了正式的修订管理系统来跟踪 FDS 源代码的变更。开源程序开发工具由 GitHub (https://github.com/) 提供。
由开发人员维护的维基文件（可通过 https://pages.nist.gov/fds-smv 上的维基页面按钮访问）详细记录了每个版本所做的修改。FDS 和 Smokeview 都有单独的文件。

## Model Developers

目前，FDS 由 NIST 消防研究部工程实验室与位于马里兰州哥伦比亚市的 UL 研究院消防安全研究所合作开发。NIST 和 UL FSRI 的开发人员与相关利益方建立了松散的合作关系，其中包括：

- 在本报告和其他技术手册开头鸣谢的各位撰稿人、
- 消防工程师协会 (SFPE)，该协会开设了使用消防数据系统的培训课程、
- 使用该软件的消防工程公司、
- NIST 消防研究部门颁发的外部赠款的部分受益人、
- 各大学的工程系，重点是消防。

## Intended Uses

在整个开发过程中，FDS 一直以解决消防工程中的实际火灾问题为目标，同时还为研究基本的火灾动力学和燃烧提供了工具。FDS 可用来模拟以下现象：

- 火灾中热量和燃烧产物的低速输送
- 气体和固体表面之间的辐射和对流传热
- 热解
- 火焰蔓延和火势增长
- 洒水器、热探测器和烟雾探测器启动
- 洒水器喷洒和用水或其他制剂镇压

虽然 FDS 是专为火灾模拟而设计的，但它也可用于其他不一定包括火灾或热效应的低速流体流动模拟。迄今为止，该模型约有一半的火灾应用是用于烟雾控制系统设计和自动喷水灭火/探测器启动研究。另一半用于住宅和工业火灾重建。

## Input Parameters

FDS 描述特定场景所需的所有输入参数都通过用户创建的单一文本文件传递。该文件包含数值网格、周围环境、场景几何、材料属性、燃烧动力学和所需输出量等信息。数值网格由一个或多个具有（通常）均匀单元的直线网格组成。场景中的所有几何特征都必须符合该数值网格。小于单个网格单元的物体要么被近似为单个阻塞单元或单元面，要么被剔除。场景几何体以一系列矩形块的形式输入。边界条件以矩形块的形式应用于实体表面。材料由其热导率、比热、密度、厚度和燃烧行为定义。根据所需的详细程度，这些信息有多种传达方式。

任何真实火灾场景的模拟都需要指定墙壁、地板、天花板和家具的材料属性。FDS 将所有这些对象都视为多层固体；因此，许多真实对象的物理参数只能被视为实际属性的近似值。在输入文件中描述这些材料对用户来说是最具挑战性的任务。导热系数、比热、密度和厚度等热特性可以在各种手册、制造商文献或工作台测量中找到。材料在不同热通量下的燃烧行为更难以描述，其特性也更难以获得。即使有整本书专门讨论这个问题[^5]，但仍然很难找到有关特定物品的信息。

FDS 输入文件的很大一部分内容是指示代码以各种方式输出各种量。与实际实验一样，用户必须在计算开始前决定保存哪些信息。如果计算开始时没有要求保存信息，那么计算结束后就无法恢复这些信息。

关于 FDS 所需输入参数的完整说明，请参阅《FDS 用户指南》[^3]。

## Output Quantities

FDS 在每个离散时间步计算每个数值网格单元内的温度、密度、压力、速度、化学成分和其他各种量。通常有数十万到数百万个网格单元和数千到数十万个时间步长。此外，FDS 还计算固体表面的温度、热通量、质量损失率和其他各种量。尽管只能保存一小部分计算信息，但输出结果通常由相当大的数据文件组成。气相的典型输出量包括

- 气体温度
- 气体流速
- 气体种类浓度（水蒸气、CO2、CO、烟尘、O2、N2）
- 烟雾浓度和能见度估计值
- 压力
- 单位体积热释放率
- 气体密度
- 单位体积的水滴质量

在固体表面上，FDS 预测了与气相和固相之间能量平衡相关的其他量，包括

- 表面和内部温度
- 辐射和对流热通量
- 燃烧率
- 单位面积水滴质量

该计划记录的全局量包括

- 总热量释放率 (HRR)
- 自动喷水灭火系统和探测器的启动时间
- 通过开口或固体的质量通量和能量通量

空间单点的各种数量或火灾热释放率 (HRR) 等全局数量的时间历史保存在简单的逗号分隔文本文件中，可使用电子表格程序绘制。不过，大多数现场或表面数据都存储在二进制文件中，以便使用名为 Smokeview 的程序进行可视化，该程序是专门为分析 FDS 生成的数据而设计的工具。FDS 和 Smokeview 可协同用于火灾现象的建模和可视化。Smokeview 通过显示动画示踪粒子流、计算气体变量的动画等值线切片和动画表面数据来实现可视化。Smokeview 还可显示场景中任意位置固定时间的静态数据的等值线和矢量图。参考文献[^3]列出了 FDS 输出数量和格式的完整列表。有关 Smokeview 使用的详细信息，请参阅参考文献[^6]。

## Governing Equations, Assumptions and Numerics

下文简要介绍了 FDS 的主要组成部分。与模型相关的假设和控制方程的详细信息见《FDS 技术参考指南》第 1 卷[^7]。

**Hydrodynamic Model** FDS 对纳维尔-斯托克斯方程的一种形式进行数值求解，该方程适用于低速热驱动流动，重点关注火灾产生的烟雾和热量传输。其核心算法是一种显式预测-修正方案，在空间和时间上都达到了二阶精度。湍流是通过大涡流模拟（LES）处理的。如果基础数值网格足够精细，还可以执行直接数值模拟（DNS）。LES 是默认的运行模式。

**Combustion Model** 在大多数应用中，FDS 使用的燃烧模型基于混合受限、无限快的块状物质反应。块状物质是代表混合物的反应标量，如空气是氮、氧、水蒸气和二氧化碳的混合物。与 FDS 5 一样，燃料和氧气的反应并不一定是瞬时和完全的，有几种可选方案旨在预测通风不足空间的燃烧程度。所有原始物种的质量分数都可以从集合物种的线性组合中获得。

**Radiation Transport** 辐射传热是通过求解灰色气体的辐射传输方程来实现的。在少数情况下，可以使用宽带模型代替灰气模型，以提供更好的光谱精度。**辐射方程的求解技术类似于对流传输的有限体积法，因此被称为有限体积法（FVM）**。使用约 100 个离散角，有限体积求解器需要的时间约占计算总 CPU 时间的 20%，考虑到辐射传热的复杂性，这一成本并不高。水滴可以吸收和散射热辐射。这在涉及雾状喷水器的情况下非常重要，但在所有喷水器情况下也会起作用。吸收和散射系数基于米氏理论。模型中不包括气体和烟尘的散射。

**Geometry** FDS 在一个或多个直线网格上逼近治理方程。用户指定的矩形障碍物会强制与底层网格保持一致。

**Boundary Conditions** 所有固体表面都分配有热边界条件，以及有关材料燃烧行为的信息。虽然在进行直接数值模拟（DNS）时可以直接计算热量和质量的传递，但固体表面之间的热量和质量传递通常是通过经验相关性来处理的。

**Sprinklers and Detectors** 水喷淋设施、热探测器和烟雾探测器的启动是通过相当简单的热惯性相关性来模拟的，而烟雾探测器的启动则是通过传输滞后来模拟的。自动喷水灭火装置的喷水是由拉格朗日粒子模拟的，这些粒子代表了从自动喷水灭火装置喷出的水滴样本。

## Limitations

虽然 FDS 可以应对大多数火灾情况，但其各种算法都有局限性。这里列出了该模型的一些比较突出的局限性。

**Low Speed Flow Assumption** FDS 的使用仅限于低速[^1-1] 流动，重点是火灾中的烟雾和热量传输。这一假设排除了在任何涉及流速接近音速的情况下使用该模型的可能性，例如爆炸、喷嘴处的阻塞流和爆燃。

**Rectilinear Geometry** FDS 的高效性得益于其简单的矩形数值网格和使用快速、直接的压力场求解器。这在某些情况下可能会受到限制，因为某些几何特征不符合矩形网格，尽管大多数建筑构件都符合矩形网格。对于大多数实际的大规模模拟，快速压力求解器提供的更高网格分辨率可以抵消小矩形网格单元对弯曲边界的近似。

**Fire Growth and Spread** 由于该模型最初是为分析工业规模的火灾而设计的，因此当指定了火灾的热释放率 (HRR) 并将热量和废气产物的传输作为模拟的主要目标时，该模型可以可靠地使用。在这些情况下，模型预测的流速和温度精度在实验测量值的 10% 到 20% 之间，具体取决于数值网格的分辨率[^1-2]。然而，对于预测而非指定热释放率的火灾情景，模型的不确定性较大。造成这种情况的原因有以下几点：(1) 实际材料和实际燃料的特性往往是未知的或难以获得的；(2) 燃烧、辐射和固相传热的物理过程比其在 FDS 中的数学表示更为复杂；(3) 计算结果对数值参数和物理参数都很敏感。目前的研究旨在改善这种情况，但可以肯定地说，与模拟特定火灾的烟雾和热量传播相比，模拟火灾的增长和蔓延需要更高水平的用户技能和判断力。

**Combustion** 在大多数应用中，FDS 使用混合控制的、基于块状物质的燃烧模型。混合气体是代表混合气体的反应标量。在大多数应用中，混合气体包括空气、燃料和燃烧产物。该模型的最简单形式是假设燃烧受混合控制，燃料和氧气的反应速度无限快，与温度无关。对于大规模、通风良好的火灾而言，这是一个很好的假设。但是，如果火灾发生在通风不畅的隔间内，或者引入了水雾或二氧化碳等灭火剂，根据一些基于经验的标准，燃料和氧气会混合而不会燃烧。这些现象背后的物理机制非常复杂，与火焰温度和局部应变率密切相关，而这两者在大规模火灾模拟中都无法计算。气相抑制和熄灭的亚网格尺度模型仍是一个积极研究的领域。在开发出用于建筑规模火灾模拟的可靠模型之前，可以使用简单的经验规则，当火灾周围的大气无法维持燃烧时防止燃烧发生。

**Radiation** 辐射传热是通过求解灰色气体的辐射传输方程（RTE）以及在某些有限的情况下使用宽带模型来实现的。辐射传输方程的求解方法类似于对流传输的有限体积法，因此被称为有限体积法（FVM）。该模型有几个局限性。首先，烟气的吸收系数是烟气成分和温度的复杂函数。由于燃烧模型的简化，含烟气体的化学成分，尤其是烟尘含量，会影响热辐射的吸收和发射。其次，虽然用户可以选择使用更多的角度，但辐射传输是通过大约 100 个实体角度离散的。对于远离局部辐射源的目标，如正在燃烧的火焰，离散化可能会导致辐射能量分布不均匀。这种误差被称为 “射线效应”，在表面温度的可视化中可以看到，“热点 ”显示了有限的实体角度的影响。加入更多的实体角度可以减少这一问题，但代价是需要更长的计算时间。在大多数情况下，远场目标的辐射通量不如近场目标重要，而近场目标默认角度数的覆盖范围要大得多。

****

[^1-1]:Ma数约小于0.3
[^1-2]:很少有火灾实验中的局部速度和/或温度测量值的误差估计值小于 10%。因此，与绝大多数火灾实验相比，使用 FDS 进行的最精确计算不会在这些量上产生明显更大的误差。

# Configuration Management

## Project Management

FDS 由 NIST 消防研究部工程实验室与 UL 研究所消防安全研究所合作开发。对于 NIST 工程实验室的所有项目，都有一名指定的项目负责人（目前是 NIST 工程实验室的兰德尔-麦克德莫特Randall McDermott）负责指导和优先安排模型开发、纠错和模型开发文档的准备工作。

FDS 和 Smokeview 团队成员共同承担开发和维护责任，其中包括

1. 开发新算法和改进程序功能
2. 回答用户问题
3. 回复错误报告
4. 定期更新正式发布的程序版本
5. 维护《技术参考》和《用户指南》
6. 维护一套样本案例，以演示模型的使用
7. 维护一套验证和确认案例，以测试模型的准确性和可靠性
8. 制定和更新未来发展 "路线图“

有关这些不同任务的大多数决定都是由团队成员单独或协商一致做出的。如果在技术问题上出现分歧，则由 NIST 和 UL FSRI 的主要开发人员协助解决。非技术性问题则由 NIST 消防研究部门主管或 UL FSRI 的相应人员负责解决。本文件中描述的所有政策和程序均由 NIST 在听取 UL FSRI、SFPE 和其他联邦机构意见的基础上进行审查。

软件和文件的审查与批准是 NIST 开发的任何报告或其他产品的标准审查程序的一部分。在发布报告或软件之前，至少需要进行五次审查，包括两次独立的技术同行审查、技术工作组和部门一级的技术和管理审查以及整个 NIST 一级的政策审查。NIST 标准表格 NIST 114 将记录和记载审查情况，并向产品的主要作者提供正式批准通知。

FDS/Smokeview 完全通过 NIST 专门为该模型建立的网站 (https://pages.nist.gov/fds-smv) 发布。网站内容由 FDS 项目负责人负责。网站的添加和更改通过本计划中记录的相同 SQA 流程进行。

## Document Identification and Control

文件识别和控制包括将所有项目文件放置在一个中央位置，并保存这些文件的更改记录。该中心位置被称为 “存储库”。
从 2007 年的 FDS 第 5 版开始，FDS 开发团队采用了 GoogleCode，这是一项免费的互联网服务，旨在通过提供源代码库、修订控制、程序分发、错误跟踪和其他各种非常有用的服务来协助开源软件开发。2015 年，谷歌终止了这项服务，并为其所有项目提供了向 GitHub 迁移的路径，GitHub 是一项类似的免费服务，使用 Git 而非 Subversion 作为版本控制软件。

FDS 手册使用 LATEX（特别是 pdfLATEX）排版。LATEX 文件本质上是受版本控制的文本文件。数字是 PDF（便携式文档格式）或 PNG（便携式网络图形）文件，取决于它们是矢量图像还是光栅图像。有多种 LATEX 软件包（包括 MiKTeX）可用于将 LATEX 编译成 PDF 文件。FDS 开发人员编辑手册是模型日常维护工作的一部分。不同版本的手册由特定的 Git 哈希标签区分。

### Project Repository

目前，FDS 和 Smokeview 使用 GitHub，这是一项支持开源应用软件开发的免费服务。GitHub 使用 Git 版本控制软件。在该系统下，一个包含所有项目文件的集中存储库位于外部服务器上。特定文件最后一次更改时的版本号记录会被保留下来。作为一个开放源代码程序，任何个人都可以获取版本库的副本或检索版本库的特定版本。

FDS 和 Smokeview 都位于 GitHub 上一个名为 “Fire Models ”的组织中。该组织的当前位置可通过 https://pages.nist.gov/fds-smv 上的 “在 Github 上查看 ”按钮查看。FDS 和 Smokeview 项目使用的资源库包含 6000 多个配置项，并在下面列出了简要说明：

- fds FDS 源代码、验证和确认测试、维基和文档
- smv Smokeview 源代码、集成测试和文档
- exp 用于模型验证的实验数据
- out 用于验证的 FDS 输出结果
- bot Firebot（持续集成系统）源代码
- radcal 窄带辐射模型 RadCal 的源代码和文档
- fds-smv 网页 html 源代码
- fig 在 firemodels 下的其他资源库中使用的图形和其他大型文件
- cad 可能包含在 FDS 输入文件中的 CAD 几何图形文件

开发团队的每位成员都有一个账户和密码[^2-1]来访问软件源。此外，潜在贡献者可以 fork（即复制）任何或所有版本库，并接收最新版本的源代码、手册和其他项目。只有前一章所述的团队成员才能向版本库提交更改。所有其他人都可以对其个人分叉进行更改，并提交拉取请求，然后由开发团队进行审核，将其纳入版本库。

如果 GitHub 服务和/或 FDS 资源库发生意外变更，开发团队的每位成员以及相关第三方的本地计算机上都有一份资源库副本。在 NIST，员工电脑也会定期备份。因此，项目存储库丢失的可能性很小。如有必要，可将文件转移到另一个开源软件开发站点。

有关模型使用 GitHub 的更多详情，可通过 https://pages.nist.gov/fds-smv 的维基页面按钮访问模型的维基页面。

### Version Identification and Numbering

仿真开始时，FDS 会向 Smokeview 输出文件、FDS 输出文件和 FDS 日志文件写入页眉信息。这些头信息包含用于执行该模拟的 FDS 版本。
NIST 发布的模型正式版本使用与资源库中特定修订版相关联的特定版本号进行标识，并在可与模型输出版本进行比较的模型下载页面上进行标识。例如，FDS 6.7.9 版的 FDS 下载网站包含以下信息

> Version : FDS 6.7.9
> Revision : FDS6.7.9-0-gec52dee42-release
> Revision Date : Wed Aug 24 16:29:46 2016 -0400
> Compilation Date : Aug 24, 2016 22:28:55

FDS 和 Smokeview 的新版本使用特定的编号约定进行标识，由三个以句号分隔的整数组成，其中第一个数字为主要版本，第二个数字为次要版本，第三个数字为维护版本。例如，FDS 6.7.9 表示 FDS 6，即第六个主要版本。7 表示重大升级（次要版本），但仍在 FDS 6 的框架内。9 表示 6.7 的第九个维护版本，主要是错误修复和用户的小要求。各卷 FDS/Smokeview 文档也会在每份文档的标题页上自动标注此信息，以提供文档和特定版本文档与特定版本的 FDS/Smokeview 和特定版本库修订的可追溯性。发布说明指出更改是否影响特定的模型功能。维护版本只是修复错误或增加小的增强功能（如新的输出量），不应影响代码功能。

****

[^2-1]:通过双因素身份验证进入消防模型库。

# Software Requirements Identification,Design, Implementation, and Testing
每天都会对 FDS 源代码进行修改，并通过修订控制软件进行跟踪。但是，这些日常更改并不构成版本号的更改。在开发人员确定源代码已经有足够的改动后，他们会发布维护升级，例如从 6.2.12 升级到 6.2.13。这种情况每隔几个月就会发生一次。小版本升级，例如从 6.2 升级到 6.3，可能一年只发布几次，因为模型的物理或数值方面有了重大改进。
FDS/Smokeview 的软件开发过程非常简单。该过程可定义为五个基本步骤：

1. **Identify and document the need for a change:** 对 FDS 的改进通常来自用户的询问。这些询问可能是报告软件中的错误，也可能是要求增加功能或模型输出。在现有研究路线图（见 https://pages.nist.gov/fds-smv）的指导下，FDS/Smokeview 的重大改动将根据以下标准进行，排名不分先后：
   1. **Better Physics:** 任何模型的目标都是具有预测性，但同时也必须可靠。FDS 融合了经验模型和确定性子模型，根据其稳健性、一致性和可靠性进行选择。任何新的子模型都必须证明其准确性可与其经验模型相媲美或更胜一筹。
   2. **Modest CPU Increase:** 如果建议的算法能使计算时间增加一倍，但精度却只有微不足道的提高，那么该算法很可能会被否决。此外，预计 FDS 中各种例程消耗的 CPU 时间与其总体重要性成正比（Baum法则[^3-1]）。例如，辐射传输算法消耗了约 25% 的 CPU 时间，这与约四分之一到三分之一的火灾能量是以热辐射形式发射的这一事实是一致的。
   3. **Simpler Algorithm:** 如果新算法能用较少的代码行数实现旧算法的功能，只要不降低功能性或准确性，几乎都会被接受。
   4. **Increased or Comparable Accuracy:** 本指南中的验证实验是新例程的衡量标准。新算法仅在少数情况下表现良好是不够的。它必须在整套实验中显示出明显的改进。如果准确度仅与前一版本相当，则必须满足其他一些标准。
   5. **Acceptance by the Fire Protection Community:** 特别是在消防专用设备方面，如自动喷水灭火器和烟雾探测器，消防数据系统中的算法往往是基于其在执业工程师中的认可度。
2. **Analyze, evaluate, and implement the change:** 复杂变化的算法通常通过修订《FDS 或 Smokeview 技术参考指南》来记录，而用于验证模型变化操作正确性的具体测试用例则包含在《FDS 或 Smokeview 验证和确认指南》中。然后，软件的实施将遵循相关《技术参考指南》中的公式。有关更改过程、跟踪和测试的更多详情，请参阅以下章节。
3. **Review and approval of the change:** 在将任何变更纳入资源库之前，都会进行验证和确认测试，以确保达到预期结果。软件和文档的所有更改都会在 FDS 和 Smokeview 资源库中自动跟踪。
4. **Verification and Validation:** 每晚运行一套简单的验证计算，以确保每天的错误修复没有改变任何重要算法。每晚运行一套验证计算。对结果的任何更改都会自动标记，并通过电子邮件发送给开发人员进行审查。有关该过程的更多详情，请参阅以下章节。
5. **Release of new versions:** NIST 政策要求审查和批准技术报告，其中包括所有 FDS 和 Smokeview 手册。有关审查过程的更多详情，请参阅以下章节。

****

[^3-1]:以霍华德-鲍姆（Howard Baum）命名，他是 NIST 研究员，也是 FDS 数学基础的最初开发者之一。

## Problem Reporting and Resolution

NIST 开发了一个自动报告和解决方案跟踪网站，与 FDS 模型一起使用，以便于对询问、问题和模型改进/修订进行跟踪和编目。通过 https://pages.nist.gov/fds-smv 上的 “ISSUE ”按钮，该网站已成为 FDS 网站的一部分。

## Software Change Implementation

每个开发人员负责不同的例程，并根据需要进行修改。小错误的修复无需任何沟通（开发人员在不同的地点），但更重要的更改则通过电子邮件或电话进行讨论。每晚都会进行一套简单的验证计算（包含在本文件中），以确保每天的错误修复没有改变任何重要算法。在每次重大升级时，都会例行运行一套验证计算（也包括本文件）。验证或确认结果的任何变化都会被标记并报告，以作进一步调查，确保模型输出的变化是模型代码的预期变化。

### Creating a Change Request

变更请求通过 FDS Issue Tracker 提交。问题跟踪器是 GitHub 提供的一项在线服务。变更请求通过打开一个新问题发起。问题报告包含基线标识（版本号、编译日期和修订号）、操作系统以及缺陷或改进请求的描述。可附加输入文件或其他支持文档。如果问题是由用户打开的，在开发人员审查之前，其状态将是 “新建New”。这通常需要几分钟到几小时的时间，具体取决于报告问题的时间。如果问题由开发人员打开，开发人员可以立即分配状态和所有者。

### Committing Changes

一旦开发人员处理了变更请求，修改后的文件就会提交到 FDS 资源库。变更描述将添加到变更日志中。该说明首先会确定更改的主要组件（例如：FDS 源文件或 FDS 文档）。在组件标识之后，将简要概述所做的更改。

## Software and Peer Reviews

一般来说，所有团队成员都会注意无意中提交的受版权保护的资料或算法，以及从最终用户处收集的专有数据或案例研究。FDS 本身不包括受版权保护的数据或专有数据，但偶尔会有提交错误报告的最终用户提交此类信息。

### Reviews Prior to Software Release

在最终实施新功能或重大变更之前，开发团队的其他成员会对拟议的修改和文档进行审查。这种审查包括对软件要求和设计规范的审查和同意，以及根据修改的复杂程度对代码更改进行更详细的审查。相关项目发起人或用户对软件要求和设计规范的审核和验收也可酌情包括在内。批准和/或审查的名称和日期将在 NIST 审查流程中以电子方式注明。

FDS 由内部和外部进行审查。国家标准与技术研究所发布的所有文件都由工作人员进行正式的内部审查。本文件阐述了 FDS 的理论基础，并由工作人员进行内部审查，他们不是模型开发的积极参与者，但都是火灾研究部门的成员，是火灾和燃烧领域的专家。对外，详细介绍 FDS 各部分的论文定期发表在同行评审期刊和会议论文集上。此外，世界各地的消防工程公司都在使用 FDS，他们会审查与其特定应用相关的模型技术细节。其中一些公司还在公开文献中发表报告，记录内部为验证模型的特定用途所做的努力。《FDS 技术参考指南》第 3 卷[^7]引用了其中许多研究。

### Survey of the Relevant Fire and Combustion Literature

FDS 有两本独立的手册--《FDS 技术参考指南》[^7] 和《FDS 用户指南》[^3]。《技术参考指南》分为四卷：(1) 数学模型、(2) 验证、(3) 验证和 (4) 配置管理。Smokeview 有自己的《用户指南》[^6]。FDS 和 Smokeview 用户指南仅介绍了计算机程序的使用方法。技术参考指南》则提供理论、算法细节以及验证和确认结果。

有许多资料介绍了该模型的各个部分。在 FDS 中求解的基本方程组是由 Rehm 和 Baum 在《美国国家标准局研究期刊》（Journal of Research of the National Bureau of Standards）上提出的[^8]。NIST 的基本流体力学算法在 20 世纪 80 年代和 90 年代不断发展，采用了相当著名的数值方案，这些方案记录在 Anderson、Tannehill 和 Pletcher [^9]、Peyret 和 Taylor [^10]，以及 Ferziger 和 Peri´c [^11]的著作中。最后一本书很好地描述了大涡流模拟技术，并提供了许多有关该主题的最新出版物的参考资料。Oran 和 Boris [^12]介绍了适合燃烧系统的数值技术。Poinsot 和 Veynante [^13]介绍了涡耗散概念（EDC）燃烧模型。Holman [^14] 和 Incropera [^15]提供了基本传热理论。Siegel 和 Howell [^16]介绍了热辐射理论。

目前有关消防科学与工程的许多知识都可以在 SFPE 的《消防工程手册》（SFPE Handbook of Fire Protection Engineering）[^17] 和《消防手册》（Fire Protection Handbook）[^18] 中找到。消防工程方面的流行教科书包括 Drysdale [^19] 和 Quintiere [^20]的著作。一些期刊和会议论文集中记录了正在进行的火灾和燃烧研究。国际消防安全科学协会（IAFSS）每三年组织一次会议，其论文集经常被消防研究人员参考。Interscience Communications 是一家总部位于伦敦的出版商，出版多份与火灾有关的期刊，该公司大约每三年在英国举办一次名为 Interflam 的会议。燃烧研究所（Combustion Institute）每两年举办一次燃烧问题国际研讨会，除研讨会论文集外，该组织还出版自己的期刊《燃烧与火焰》（Combustion and Flame）。刊登在 IAFSS 会议论文集、燃烧专题讨论会论文集和《Combustion and Flame》上的论文都是经过同行评审的，而刊登在 Interflam 论文集上的论文则是根据提交的简短摘要筛选出来的。消防工程师协会 (SFPE) 和美国国家防火协会 (NFPA) 出版的同行评审技术期刊分别名为《Journal of Fire Protection Engineering》和《Fire Technology》。其他经常被引用的同行评审技术期刊包括《Fire Safety Journal》、《Fire and Materials》、《Combustion Science and Technology》、《Combustion Theory and Modeling》和《Journal of Heat Transfer》。

除了工作人员向外部期刊和会议投稿外，NIST 还以各种方式记录研究工作。NIST 出版多种形式的内部报告、技术说明、特别出版物和自己的期刊《Journal of Research of NIST》。内部报告被称为 NISTIR（NIST 机构间报告），是传播信息的便捷手段，特别是当数据量超过期刊通常可接受的数量时。通常情况下，NISTIR 的部分内容会在外部发表，而 NISTIR 本身则是工作的完整记录。以前版本的《FDS 技术参考指南》和《用户指南》就是作为 NISTIR 出版的。目前的 FDS 和 Smokeview 手册是作为 NIST 特别出版物出版的，与 NISTIR 的区别在于它们是永久存档的。外部人员或组织根据 NIST 赠款或合同开展的工作以 NIST 赠款/合同报告 (GCR) 的形式出版。1993 年以后，NIST 消防研究部门工作人员所做的所有工作均以电子形式永久保存，并通过互联网免费提供。

### Review of the Theoretical Basis of the Model

该模型的技术方法和假设已在同行评议的科学文献和上一节引用的技术会议上进行了介绍。该模型的主要假设，例如大涡流模拟技术和燃烧模型，经历了大约 40 年的发展，现在已载入流行的入门教科书。而更具体的子模式，如喷淋喷雾程序或各种热解模型，则尚未发展到这种程度。因此，NIST 工作人员编写的所有文件都必须经过内部编辑审查和批准程序。这一程序旨在确保符合 NIST 所要求的技术要求、政策和编辑质量。技术审查包括对技术内容和方法、数据统计处理、不确定性分析、适当参考数据和单位的使用以及参考书目进行严格评估。FDS 和 Smokeview 手册首先由消防研究部门的一名成员进行审查，然后由文件作者的直属上司、消防研究部门的主管进行审查，最后由部门外的一名读者进行审查。直接主管和处长都是该领域的技术专家。文件经审查后，将提交编辑审查委员会（ERB），该委员会由来自 NIST 所有实验室的代表组成。委员会为每份接受审查的文件至少指定一名审阅人。最后一位读者是根据技术能力和公正性挑选的。该读者通常来自编制文件的部门之外，负责检查文件是否符合 NIST 有关单位、不确定性和范围的政策。读者不需要是火灾或燃烧方面的技术专家。

美国核管理委员会 (US NRC) 出版了一份七卷本的报告，对核电厂应用的五种不同火灾模型进行了验证和确认研究[^21]。其中两个模型基本上是以工程 “电子表格 ”为形式的一套基于经验的相关性。两个模型是经典的两区火灾模型，其中一个是 NIST 开发的 CFAST 模型。FDS 是该研究中唯一的 CFD 模型。有关该研究及其结果的更多信息，请参阅《FDS 技术参考指南》第 3 卷[^7]。

除了正式的内部审查和同行审查外，FDS 还受到持续的审查，因为它是免费向公众提供的，而且在国际上被从事消防安全设计和火灾后重建的人员所使用。FDS 和 Smokeview 用户指南的质量得到了隐性的检验，因为大多数模型用户并不需要参加专门针对 FDS 的正式培训课程，他们只需阅读辅助文件，进行一些模拟样本，然后系统地积累与其应用相适应的专业知识。开发人员每天都会收到用户对文件清晰度的反馈，并在必要时进行补充说明。在模型的新版本发布之前，会有几个月的 “beta 测试 ”期，在此期间，用户会使用更新后的文档对新版本进行测试。这一过程与大多数计算机软件程序所经历的过程类似，但不那么正式。此外，FDS 的源代码是公开发布的，并已在世界各地的多所大学中使用，既作为课堂教学工具，也用于研究。因此，理论发展和计算机程序本身的缺陷已被发现和纠正。随着 FDS 的不断发展，用户群将继续作为评估模型的手段。我们认为这一过程对于 FDS 的发展与正式的内部和外部同行评审过程同样重要。

## Model Testing

在对模型进行任何修订时，开发人员都会对模型算法进行单独测试。通常情况下，这种测试构成了未来模型版本中任何新标准测试用例的基础。模型发布前的系统发布测试包括以下内容：

- 根据对模型所做的任何适当修改，检查特定测试案例的结果。如果有简化问题的分析解决方案，最好与之进行比较。
- 检查模型发布版本中包含的标准测试用例的结果。与先前版本相比，输出结果的任何变化都会通过对模型的修改加以解释（并记录在软件测试和验证结果报告中）。
- 对于模型的主要新版本，应将一整套测试用例与模型以前版本的测试用例进行比较。这至少包括**美国核管理委员会出版物 NUREG 1824 [^22][^21]中描述的一套验证练习，但也可酌情包括许多额外的示例或验证练习**。
- 对于模型的所有改动，都采用了自动测试流程，在 FDS 修订版之间提供自动错误检查并收集性能和准确性统计数据。该过程对模型发布版本的测试结果包含在 FDS [^23][^24] 和 Smokeview [^25]的验证和确认指南中。

## Firebot: Automated Software Quality Testing

FDS 和 Smokeview 的源代码需要经过自动构建、验证、确认和回归测试流程，这类似于为项目自动构建/测试周期的持续集成系统。这一自动化流程被称为 Firebot。Firebot 构建/测试流程可在 FDS 修订版之间执行自动错误检查并收集性能和准确性统计数据，从而为 FDS-SMV 开发团队提供帮助。

自动构建/测试验证流程定期（每晚）运行，以确保 FDS 和 Smokeview 在构建/测试周期内没有编译器错误、验证错误或任何其他可能导致失败的错误。自动构建/测试验证流程通过逐组验证套件持续运行。构建/测试过程的结果会被存档，并标注所使用的相应版本号，以备将来参考。

自动构建/测试流程完成后，构建/测试流程的结果将发送给开发团队。如果出现故障，构建/测试流程会尽可能继续，并将相应的错误日志发送给开发团队。自动构建/测试流程由八个构建阶段组成，下文将对这些阶段进行介绍。

**Stage 1: Checkout of FDS-SMV codebase**

在第一阶段，FDS 和 Smokeview 源代码的最新版本将从 GitHub 上的 Fire Models 资源库中获取。在这一阶段，Firebot 脚本会确保删除所有临时文件，并在后面的阶段使用所有相关软件源的干净副本，就像最终用户第一次下载软件源一样。

**Stage 2: Compilation of FDS debug versions**

FDS 在编译时启用了调试标志。在这一阶段，源代码中的错误可以在编译/测试过程的早期被识别和跟踪。此时会记录任何编译器警告，在未发现重大编译错误后继续编译/测试过程。

**Stage 3: Run verification suite (or validation set) in debug mode**

验证套件中的所有案例都使用第 2 阶段编译的 FDS 调试版本进行调用。验证案例至少运行一个时间步长，以确保案例启动时没有错误。所有案例运行至少一个时间步后，使用 FDS 停止文件停止案例。然后检查 FDS 输出日志，看是否有 Fortran 错误、数值不稳定、验证案例文件丢失或其他 FDS 错误。

**Stage 4: Compilation of FDS release versions**

编译 FDS 的发布版本。此时会记录任何编译器警告，如果没有发现重大编译错误，则继续编译/测试过程。

**Stage 5: Run verification suite (or validation set) in release mode**

验证套件中的所有案例都使用在第 4 阶段编译的 FDS 版本调用。所有案例运行完成后，检查 FDS 输出日志是否有 Fortran 错误、数值不稳定、验证案例文件丢失或其他 FDS 错误。

**Stage 6: Compilation of Smokeview and scripted generation of figures**

Smokeview 调试和发布版本与 Smokeview 实用程序（smokezip、smokediff 和 background）一起编译。此时会记录任何编译器警告，在未发现重大编译错误后继续编译/测试过程。
此外，FDS 和 Smokeview 验证套件中的脚本可用于使用自动 Smokeview 脚本命令生成图形。这些图表用于 FDS 用户 [^3]和验证 [^24]指南以及 Smokeview 用户和验证指南。

**Stage 7: Generation of verification and validation plots and regression statistics**

FDS 验证和验证套件中的脚本可用于利用第 5 阶段的结果生成图表、回归信息和时序统计信息。FDS 用户[^3]和验证[^24]指南》以及《SMV 用户和验证指南》中使用了这些绘图、数字和统计信息。

**Stage 8: Compilation of FDS-SMV Guides**

FDS 用户[^3]、技术参考[^26]、验证[^24]和确认[^23]指南、FDS 配置管理计划以及 Smokeview 用户、技术和验证指南的编译，可确保所有图表和方程式在编译时不会出现任何 LATEX 错误。

## Issuing New Releases

更改软件版本的决定是由开发团队协商一致做出的，通常是在确定已经做出足够的更改，需要发布新版本之后。决定何时发布新版本并没有正式的流程。不过，一旦做出决定，就会给新版本编号，对其进行测试，然后发布到官方下载网站。

### Testing a New Release

每个建议发布的版本都要经过测试。用于测试新版本的输入文件有两套--验证套件和确认套件。验证套件包括一系列计算，从仅测试功能的计算到将 FDS 结果与控制方程的分析解进行比较的计算。验证套件包括各种实验的模拟。测试水平取决于基线版本的类型：维护、次要或主要版本。

维护版本每隔几周发布一次。每个维护版本都会在每晚的 Firebot 测试中通过验证套件进行测试。维护版本主要用于日常错误修复、文档说明和可用性问题。维护版本的代码功能应该不会有任何变化，尽管错误修复可能会稍微改变结果。

次要版本每三到六个月发布一次。每个小版本都要经过验证和确认套件的测试。验证案例的运行时间要长得多，但程序类似--使用自动绘图软件包绘制结果并与实验测量结果进行比较，该软件包基本上重绘了 FDS 验证指南[^23]中的所有绘图和图形。对新旧指南进行比较，以评估新版模型的精确度是否明显低于旧版。《FDS 验证指南》在 “摘要 ”一章中有一个表格，列出了所有预测量的偏差和相对标准偏差值。使用此特定次要版本的任何人都应引用这些不确定性指标。实质上，对于小规模释放，ASTM E 1355 中概述的评估程序是重复的。自动持续集成脚本会重新进行验证和确认研究。

FDS 每隔几年发布一次重大版本。顾名思义，对算法进行重大修改，需要数月的测试，并通过验证和确认套件的多次运行。预计重大版本将引入并可能删除主要算法和功能。

### Announcing a New Version

在成功完成所需的基线测试后，就会发布新版本。在发布之前，要更新 FDS 源代码中的版本标识信息。更新 FDS 文档，以包含新版本号。编译新版本，并将新的安装包上传到 FDS 下载站点。之前的版本将被归档并废弃。

# Software Risk Management

NIST 开发和发布的软件的主要风险管理工具是上文概述的 NIST 对软件、文件和 NIST 其他产品的官方审查程序。在发布模型供普遍使用之前，必须获得正式批准。将风险降至最低的其他流程如下。

## Media Control

FDS 和 Smokeview 的发布版本只能在 FDS/Smokeview GitHub 存储库结构中的 FDS 专用网站上获取。
作为模型开发的一部分，NIST 维护了一个基于网络的系统，用于对 FDS 和 Smokeview 源代码以及软件的发布前和发布后可执行文件进行版本控制和历史记录。
这些计算机系统仅供指定人员使用，包括 FDS 项目负责人和项目组成员。

## Supplier Control

NIST 目前使用英特尔 oneAPI Base 和 HPC 工具包，其中包括 Fortran 和 C++ 编译器以及各种诊断工具[^4-1]。一些英特尔可重新分发库是 FDS 安装包的一部分。在对编译器进行任何更改之前，都要对一整套测试用例进行比较，以验证模型和模型结果的运行是否一致。

## Records Collection, Maintenance, and Retention

除了 FDS/Smokeview 资源库中已确定的配置项目外，所有软件、文档和 SQA 文件均由 FDS 项目负责人保留，通常为电子形式。软件和文档也作为模型旧版本的一部分在 NIST FDS 网站上进行维护和存档。
在销毁旧的或过时的记录之前，需要获得 NIST 管理层的批准。记录通常至少保存 25 年。

## Training

没有为使用本计划确定具体的培训内容。《FDS 用户指南》中关于模型使用培训要求的详细信息也适用于模型开发人员。

****

[^4-1]: 本文件中可能会标明某些商业实体、设备或材料，以便充分描述实验程序或概念。这些标识并不意味着美国国家标准与技术研究院推荐或认可这些实体、材料或设备，也不意味着这些实体、材料或设备一定是可用于该目的的最佳产品。

# 参考文献

[^1]: Institute of Electrical and Electronics Engineers. IEEE Std 828-2005, IEEE Standard for Software Configuration Management Plans, 2005. v, 1
[^2]: American Society for Testing and Materials, West Conshohocken, Pennsylvania. ASTM E1355-12, Standard Guide for Evaluating the Predictive Capabilities of Deterministic Fire Models, 2012. v, 1
[^3]: K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, User’s Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. v, 3, 4, 13, 17
[^4]: The Institute of Electrical and Electronics Engineers. IEEE Standard for Software Quality Assurance Plans, IEEE Std 730-2002 edition, 2002. 1
[^5]: V. Babrauskas. Ignition Handbook. Fire Science Publishers, Issaquah, Washington USA, 1st edition, 2003. Co-published by the Society of Fire Protection Engineers. 3
[^6]: G.P. Forney. Smokeview, A Tool for Visualizing Fire Dynamics Simulation Data, Volume I: User’s Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, sixth edition, May 2013. 4, 13
[^7]: K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. Vol. 1: Mathematical Model; Vol. 2: Verification Guide; Vol. 3: Validation Guide; Vol. 4: Software Quality Assurance. 4, 13, 15
[^8]: R.G. Rehm and H.R. Baum. The Equations of Motion for Thermally Driven, Buoyant Flows. Journal of Research of the NBS, 83:297–308, 1978. 13
[^9]: D.A. Anderson, J.C. Tannehill, and R.H. Pletcher. Computational Fluid Mechanics and Heat Transfer. Hemisphere Publishing Corporation, Philadelphia, Pennsylvania, 1984. 13
[^10]: R. Peyret and T.D. Taylor. Computational Methods for Fluid Flow. Springer-Verlag, New York, 1983. 13
[^11]: J.H. Ferziger and M. Peri´c. Computational Methods for Fluid Dynamics. Springer-Verlag, Berlin, 2nd edition, 1999. 13
[^12]: E.S. Oran and J.P. Boris. Numerical Simulation of Reactive Flow. Elsevier Science Publishing Company, New York, 1987. 13
[^13]: T. Poinsot and D. Veynante. Theoretical and Numerical Combustion. R.T. Edwards, Inc., Philadelphia, Pennsylvania, 2nd edition, 2005. 14
[^14]: J.P. Holman. Heat Transfer. McGraw-Hill, New York, 7th edition, 1990. 14
[^15]: T.L. Bergman, A.S. Lavine, F.P. Incropera, and D.P. DeWitt. Fundamentals of Heat and Mass Transfer. John Wiley and Sons, New York, 7th edition, 2011. 14
[^16]: R. Siegel and J. R. Howell. Thermal Radiation Heat Transfer. Taylor & Francis, New York, 4th edition, 2002. 14
[^17]: M.J. Hurley, editor. SFPE Handbook of Fire Protection Engineering. Springer, New York, 5th edition, 2016. 14
[^18]: Fire Protection Handbook. National Fire Protection Association, Quincy, Massachusetts, 18th edition, 1997. 14
[^19]: D. Drysdale. An Introduction to Fire Dynamics. John Wiley and Sons, New York, 2nd edition, 2002. 14
[^20]: J.G. Quintiere. Principles of Fire Behavior. Delmar Publishers, Albany, New York, 1998. 14
[^21]: D. Stroup and A. Lindeman. Verification and Validation of Selected Fire Models for Nuclear Power Plant Applications. NUREG-1824, Supplement 1, United States Nuclear Regulatory Commission, Washington, DC, 2013. 15
[^22]: K. Hill, J. Dreisbach, F. Joglar, B. Najafi, K. McGrattan, R. Peacock, and A. Hamins. Verification and Validation of Selected Fire Models for Nuclear Power Plant Applications. NUREG-1824, United States Nuclear Regulatory Commission, Washington, DC, 2007. 15
[^23]: K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 3: Validation. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 15, 17
[^24]: K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 2: Verification. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 15, 17
[^25]: G.P. Forney. Smokeview, A Tool for Visualizing Fire Dynamics Simulation Data, Volume III: Verification Guide. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, sixth edition, May 2013. 15
[^26]: K. McGrattan, S. Hostikka, R. McDermott, J. Floyd, C. Weinschenk, and K. Overholt. Fire Dynamics Simulator, Technical Reference Guide, Volume 1: Mathematical Model. National Institute of Standards and Technology, Gaithersburg, Maryland, USA, and VTT Technical Research Centre of Finland, Espoo, Finland, sixth edition, September 2013. 17