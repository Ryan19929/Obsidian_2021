### 1. 背景
- 量子计算机程序以电路的形式表示，通过一连串的单门或符合门的操作。
- 我们有三种方法去计算电路
		1. State Vector Simulation: 他是用当前的 state vector 顺序X每一个门对应的unitary matrix。
			好处: 零错误。
			坏处: 开销会随着规模指数级上升, 并且收到 NISQ 的限制。
		2. Quantum Device (noisy, shot-based) -> QC Evaluation.
		3. Partition large circuit into subcircuits, execute independently(noisy, shot_based) -> CutQC Evaluation.
- 第一种是BASELINE, 不需要用到量子计算机。
#### 1.1 Shot
- NISQ 设备每执行一次称作 shot, 量子计算机在很短的时间会编译很多次。所有的输出结果都会被记录下来，然后可以观察他们的全概率分布。

### 2. 截切理论
- N个量子比特(qubit)的操作可以描述为 2^N X 2^N 的 unitary matrices 矩阵。
- 每一个量子比特的操作可以被分解为一系列的正交矩阵。
1. **单个量子门**是一个 2X2 的 unitary matrices.
2. Pauli matrices 是 3 个 2X2 的 Hermitian and unitary 矩阵。
3. **I X Y Z**可以说是4个组成一个矩阵的基。I 好像代表一个单位向量, X Y Z 是上一条提到的Pauli matrices 中的 3个矩阵的基。
- 以上的信息可以说明，单个量子比特的操作可以被 Pauli matrices 分解。

#### 2.1 原文中分解任意一个 2X2 矩阵的意义
1. 通过第二节的信息，可以将 2X2 矩阵分解为四个基向量。
2. 但是下面分解的结果是量子计算机不能计算的，它接触到复杂的振幅。
$$A = \frac{Tr(AI)I+Tr(AX)X+Tr(AY)Y+Tr(AZ)Z}{2}$$
3. 为了让量子计算机可以计算，作者开始把 Pauli matrices 分解成他们的特征基，并带入上述公式，得到下面的公式
$$A = \frac{A1+A2+A3+A4}{2}$$
WHERE
$$ A1 = [Tr(AI)+Tr(AZ)|0><1|] $$
$$ A2 = [Tr(AI)-Tr(AZ)]|1><1| $$
$$ A3 = Tr(AX)[2|+><+|-|0><0|-|1><1|]$$
$$ A4 = Tr(AY)[2|+i><+i|-|0><0|-|1><1|]$$
- 左边的部分是 trace operator, 右边的部分是量子的密度矩阵(density matrices)
	1. trace operator 代表着物理上在其中一个泡利基上测量这个量子。
	2. 密度函数用来描述量子状态, 这里在它其中之一的原状态方向初始化。
- 图表 3 左边是 3 个变量，右侧是 4 个变量, 因为I 和 Z 物理上对应着相同的量子电路。
- 结果就导致他们之间出现四对 Kronecker 积，他们的和就是未切割电路的输出。
### 2.2 图三一些新的理解
- u -> v 
-  u 可以被测量 I X Y Z 上的 trace operator
-  v 通过初始化的电路状态。