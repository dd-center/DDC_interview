# Bitwise operation

1. Bit shift
```python3
x = 2
x >> 1 = ?
x << 1 = ?
```

🎉 Answer:
```python3
x >> 1 = 1
x << 1 = 4
```

2. Erase lowest set bit
```python3
x = '0b00101100'
How do we get '0b00101000' from x?
```

🎉 Answer:
```python3
x&(x-1) = '0b00101000'
```
