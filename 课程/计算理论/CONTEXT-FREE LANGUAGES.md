# CONTEXT-FREE LANGUAGUES
## 1. 形式
```txt
	A -> 0A1
	A -> B
	B -> #
```
- A grammar consists of a collection of **substitution rules**, also called producetions.

## 2.描述语言
- Steps:
	1. 写下起始变量，没有具体说明，就是top rules
	2. 找到左边的变量，然后用该变量的规则替换掉该变量
	3. 重复上述步骤，直到没有变量存在
- Example:
	- A => 0A1 => 00A11 => 000A111 => 000B111=>000#111