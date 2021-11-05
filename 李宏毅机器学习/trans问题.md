- local minima: 无路可走，周围都是最低
- ![[Pasted image 20211030124915.png]]
- ![[Pasted image 20211030124949.png]]
- ![[Pasted image 20211030125156.png]]
- 如果不是local minima 可以看 H 判断
- saddle point: 还可以走
$$
Minimun ratio = \frac{Number of Positive Eigen values}{ Number of Eigen values}
$$
- 在实际情况中，特征值都是正的critical point 基本上是不存在的，就是无法判断local minima ,所以设定 Minimun ratio > 0.5 说明就是 local minima
## Optimization Fails
- ![[Pasted image 20211030151509.png]]
- Small batch is better on testing data
	- 会有flat minima 和 sharpminima
- Momentum -> local minima
	- 相当于有惯性，走到minima 继续走
	- M初始为0 , m=lamada m -n g

## learning rate
- 大的lr 会导致震荡
- 小的lr 会导致不前进了
- 需要定制lr->更改原来梯度下降生成的函数
- ![[Pasted image 20211030154555.png]]
- 可以让他随着时间越大而越小，因为随着时间的增加而接近终点，不需要太大的g
- Learning Rate Decay
- Warm up
	- 让他一开始去探索，让rate很大，再变小
### RMSProp
- ![[Pasted image 20211030164253.png]]
### Adam
- 混合体

## LOSS引起的问题
- 将目标的真实结果变成 one-hot vector