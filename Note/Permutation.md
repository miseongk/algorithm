# ๐ ์์ด (Permutation)
์๋ก ๋ค๋ฅธ n๊ฐ์ ์์์์ r๊ฐ๋ฅผ ์ค๋ณต์์ด ์์์ ์๊ด์๊ฒ ์ ํ ๋๋ ๋์ดํ๋ ๊ฒ

## ์์ด ๊ตฌํํ๊ธฐ
### 1. itertools ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ฌ์ฉ
```python
import itertools

data = ['a', 'b', 'c']
result = list(itertools.permutations(data)

print(result)
# [('a', 'b', 'c'), ('a', 'c', 'b'), ('b', 'a', 'c'), ('b', 'c', 'a'), ('c', 'a', 'b'), ('c', 'b', 'a')]
```
### 2. DFS ์ฌ์ฉ
```python
data = ['a', 'b', 'c']
visited = [0 for _ in range(len(data))]
result = []

def dfs(cnt, list):
    if cnt == len(data):
        result.append(list[:])
        return
    
    for i, val in enumerate(data):
        # ๋ง์ฝ ๋ฐฉ๋ฌธํ๋ค๋ฉด ๊ฑด๋ ๋ฐ๊ธฐ
        if visited[i] == 1:
            continue
            # ํ์ฌ๊น์ง์ list์ ๊ฐ์ ์ถ๊ฐํ๊ณ , ๋ฐฉ๋ฌธ ํ์ํ๊ธฐ
        list.append(val)
        visited[i] = 1

        dfs(cnt + 1, list)
        # ๋ฐฉ๊ธ ์  list์ ์ถ๊ฐํ ๊ฐ๊ณผ ๋ฐฉ๋ฌธ ํ  ๊ฒ์ ๋๋๋ ค์ฃผ๊ธฐ
        list.pop()
        visited[i] = 0

dfs(0, [])
print(result)
# [('a', 'b', 'c'), ('a', 'c', 'b'), ('b', 'a', 'c'), ('b', 'c', 'a'), ('c', 'a', 'b'), ('c', 'b', 'a')]
```
