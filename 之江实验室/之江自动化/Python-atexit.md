## atexit
- 用处，在程序退出之前执行代码
## 方法
- 使用装饰器
```python
import atexit

@atexit.register
def f():
	print('结束')

if __name__ == '__main__':
	1/0
```