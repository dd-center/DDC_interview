# Batch normalization
试给出Batch normalization的公式

🎉 Answer
1. 首先，计算mini-batch的平均值与方差，并按以下公式更新：
```python3
new_x = (x - E[x]) / sqrt(var(x))
```
2. 然后，按以下公式更新。beta与gamma属于参数，将会被自动学习：
```python3
final_x = gamma * new_x + beta
```
