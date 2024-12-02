## 内置函数zip
zip函数能更快捷的将两个序列类型创建成字典
```python 
>>> zip(Iterator_1, Iterator_2...)
	一个迭代器((Iterator_1[0], Iterator_2[0]), (Iterator_1[1], Iterator_2[1])...)
# 在字典创建中，可以将两个相同长度的序列合并成字典
>>> dict(zip(Iterator_1, Iterator_2...))
	{Iterator_1[0]: Iterator_2[0], Iterator_1[0]: Iterator_2[0], ...} 
```
同样，zip能提供一种节省代码量的**同时遍历多个序列**的办法
```python
>>> for x, y, z in zip(Iterator_1, Iterator_2, Iterator_3):
>>> print(x, y, z)
	x_0, y_0, z_0
	x_1, y_1, z_1
	...
```
