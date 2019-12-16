### Python iteration

请写出以下程式预计的结果：

```python3
import copy
my_test = [1, 2, 3, 4, 5]
iterator = iter(my_test)
copy_iter = iter(copy.deepcopy(my_test))
```

```python3

>>> print(next(iterator))
1
>>> print(next(iter(my_test)))
1
>>> print(next(iterator))
2
```

```python3
del my_test[0]
```

```python3
>>> print(next(iter(my_test)))
2
>>> print(next(iterator))
4
>>> print(next(copy_iter))
1
```
