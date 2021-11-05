## 架构
- 阈值的单位是字节
- 拥塞窗口增大一个MSS, 每一轮次就会加倍
- 该代码是负责拥塞控制的
- tcp_common_congestion_exp: 转 -> fast_retransmit
- tcp_reno_do_fast_retransmit: 快重传
- tcp_reno_slow_retransmit: 慢启动
- tcp_reno_fast_retransmit_newack: 在快恢复的时候收到一个新的newack
- tcp_reno_newack: 遇到新的ack 是否会指数上升 or ABC 算法

1. 当在慢开始的时候收到新的 ack 调用 tcp_reno_newack, tcp_reno_newack 会判断是否使用 ABC 算法。
2. 当遇到三次ack的时候, 会先启动快重传, 调用tcp_reno_do_fast-retransmit, 在快重传结束后会进入快恢复状态, 调用tcp_common_congestion_exp, 在快恢复收到第一个 ack 的时候, 会调用 tcp-reno_fast_retransmit_newack, 离开快恢复模式, 之后如果再收到 ack 就会调用 tcp_reno_newack。
3. 遇到超时的情况, 调用tcp_reno_slow_transmit, 进入慢启动模式。



## 通用部分
### 遇到超时部分
- 这一部分有 snd_recover = tp->snd_max; 通常是在快重传的时候使用 
- 该源码将 reno, newreno 和 cubic 统一使用一个超时处理的函数处理
- 通过传入 \*tp, betaa 和 betab 来实现不同算法的处理。
```C
static void tcp_common_congestion_exp(struct tcpcb *tp, int betaa, int betab)
{
 // betaa, betaab 是控制窗口变小的比率
 u_long win;
 /*

 * Reduce the congestion window and the slow start threshold. 减少拥塞窗口, 满开始

 */

 win = ulmin(tp->snd_wnd, tp->snd_cwnd) * betaa / betab / tp->t_segsz; // snd_wnd: 当前发送窗口, snd_cwnd: 当前拥塞窗口  窗口减小到当前

 if (win < 2)

 	win = 2;
 
 tp->snd_ssthresh = win * tp->t_segsz; // 上面 / t_segsz, 现在*上去了

 tp->snd_recover = tp->snd_max; // snd_recover for use in NewReno Fast Recovery  这个应该是将最高的 sequence 告诉recovery 

 tp->snd_cwnd = tp->snd_ssthresh; // ?


 /*

 * TCP ECN 显示拥塞通知 在ECN成功协商的情况下，ECN感知路由器可以在IP头中设置一个标记来代替丢弃数据包，以标明阻塞即将发生。数据包的接收端回应发送端的表示，降低其传输速率，就如同在往常中检测到包丢失那样。

 * When using TCP ECN, notify the peer that

 * we reduced the cwnd.

 */

 if (TCP_ECN_ALLOWED(tp))

 tp->t_flags |= TF_ECN_SND_CWR;

}
```
- 参数 win 应该是窗口大小值, win会取 snd_wnd, snd_cwnd 的最小值, 
- betaa, betab 是为了适应不同算法的变量
```c
win = ulmin(tp->snd_wnd, tp->snd_cwnd) * betaa / betab / tp->t_segsz;
```
- win < 2 -> win = 2 这一步 ssthresh 的最小值是 2 个数据报大小。
- 还有提到TCP ENC 显示拥塞通知

#### ENC

## RENO
### tcp_reno_do_fast_retransmit
