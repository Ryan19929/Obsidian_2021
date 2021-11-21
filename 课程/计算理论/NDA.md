# NFA
- 不确定有限自动机的特点是走全部的路线，只要有一条路可以接受，那么就代表接受。
- NFA可以转化为DFA
- 会有tree of possibilities
q222222
# 结构
- Formal definition of a NFA: **5-tuple**
	1. set of states
	2. alphabet
	3. transition function: Q X alphabet -> P(Q) ，**P(Q) is the subsets of Q**
	4. start state
	5. set of accept states
# 优点
- Easy to present the process.

# 缺点
- 无法描述简单的语言{1^n0^n}
- 证明上面的语言不是正则的原理[[泵原理]]
