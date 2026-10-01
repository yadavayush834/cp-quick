# Matrix Diagonals

Main diagonal: `j == i`, so the element at row `i` is `mat[i][i]`.
Anti diagonal: `i + j == n - 1`, so the element at row `i` is `mat[i][n - 1 - i]`.

$$\text{main} = \sum_{i=0}^{n-1} a_{i,i} \qquad\qquad \text{anti} = \sum_{i=0}^{n-1} a_{i,\, n-1-i}$$

## Sum of both diagonals

| n | ans |
| :--- | :--- |
| even | `main + anti` |
| odd | `main + anti - mat[n / 2][n / 2]` |

For odd `n` both diagonals contain the centre cell `mat[n / 2][n / 2]`, so the loop below
adds it twice; subtract it once.

## Code

```cpp
long long ans = 0;
for (int i = 0; i < n; i++) {
    ans += mat[i][i];               // main diagonal
    ans += mat[i][n - 1 - i];       // anti diagonal
}
if (n % 2 == 1) {
    ans -= mat[n / 2][n / 2];       // centre, added twice above
}
```

Complexity: `O(n)`.

## Notes

- Rectangular `r x c` matrix: anti diagonal is `mat[i][c - 1 - i]`, loop `i = 0 .. min(r, c) - 1`.
- 1-based indexing: anti diagonal is `mat[i][n + 1 - i]`.
- Use `long long` for `ans`, large values overflow `int`.
