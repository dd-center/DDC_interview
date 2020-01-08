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
x = 0b00101100
How do we get '0b00101000' from x?
```

🎉 Answer:
```python3
x&(x-1) = 0b00101000
```

3. Extract lowest set bit
```python3
x = 0b00101100
How do we extract lowest bit from x?
```

🎉 Answer:
```python3
x&~(x-1) = 0b00000100
```

4. Show XOR concept

🎉 Answer:
```python3
if A == B, A^B = 0
if A != B, A^B = 1
```

5. Reverse Bits
```python3
Reverse bits of a given 32 bits unsigned integer.

 

Example 1:

Input: 00000010100101000001111010011100
Output: 00111001011110000010100101000000
Explanation: The input binary string 00000010100101000001111010011100 represents the unsigned integer 43261596, so return 964176192 which its binary representation is 00111001011110000010100101000000.
Example 2:

Input: 11111111111111111111111111111101
Output: 10111111111111111111111111111111
Explanation: The input binary string 11111111111111111111111111111101 represents the unsigned integer 4294967293, so return 3221225471 which its binary representation is 10111111111111111111111111111111.
```

🎉 Answer:
```python3
class Solution:
    def reverseBits(self, n: int) -> int:
        def swapbit(i, j, n):
            if n>>i & 1 != n>>j &1:
                bitmask = 1 << i | 1 << j
                n ^= bitmask
            return n
        
        for i in range(16):
            j = 31 - i
            n = swapbit(i, j, n)
        return n
```












