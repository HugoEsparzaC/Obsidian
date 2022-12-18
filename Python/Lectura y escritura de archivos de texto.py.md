# sys
```python
import sys
sys.stdout = open('output.tex', 'w')
sys.stdin = open('input.tex', 'r')
a = input()
print(a)
```