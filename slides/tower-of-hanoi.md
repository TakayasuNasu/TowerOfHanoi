---
marp: true
paginate: true
theme: gaia-ex
---

<!-- _class: top -->

Algorithm Tower of Hanoi
===

- Takayasu Nasu

---

#### Agenda

- ice break
- ハノイの塔の説明
- サンプル - 1 / 2 / 3 / 10
- 解説
- コード
- 結論
- フィボナッチ

---

#### ice break

この中で中でハノイの塔はどれ?

---

ハノイの塔とは


---

Let's brain exercise.

---

1. まず5枚の円盤を柱Aから柱Bに移す
1. 次に(6枚の中で)最も大きな円盤を柱Aから柱Bに移す
1. 最後に、5枚の円盤を柱Cから柱Bに移す

---

1. まず4枚の円盤を柱Aから柱Bに移す
1. 次に(5枚の中で)最も大きな円盤を柱Aから柱Bに移す
1. 最後に、4枚の円盤を柱Cから柱Bに移す

---

つまり

n枚の円盤を、柱Aから柱Bに移すには

`n = 0`の場合
- 何もしない

`n > 0`の場合
- まず、n-1枚の円盤を、柱xから柱zへ柱yを利用して移す
- 次に、1枚の円盤を、柱xから柱yへ移す
- 最後に`n -1`枚の円盤を、柱zから柱yへ柱xを利用して移す

---

最低枚数を求める式を

```bash
H(n)
```

とすると、0枚の場合

```bash
H(0) = 0
```

---

1枚の円盤を移す方法は

```bash
H(1) = 1
```

つまり

```bash
H(n) = H(n - 1) + 1 + H(n - 1)
```

0から順番にみると

```bash
H(0) = 0
H(1) = H(0) + 1 + H(0) = 0 + 1 + 0 = 1
H(2) = H(1) + 1 + H(1) = 1 + 1 + 1 = 3
H(3) = H(2) + 1 + H(2) = 3 + 1 + 3 = 7
H(4) = H(3) + 1 + H(3) = 7 + 1 + 7 = 15
H(5) = H(4) + 1 + H(4) = 15 + 1 + 15 = 31
H(6) = H(5) + 1 + H(5) = 31 + 1 + 31 = 63
```

---

```bash
0 = 1 - 1
1 = 2 - 1
3 = 4 - 1
7 = 8 - 1
15 = 16 - 1
```

`1, 2, 4, 8` = `2^0, 2^1, 2^2, 2^3, 2^4`

---

`H(n) = 2^n - 1`

---

Do you feel lazy?
OK, I'll make the computer calculate.

---

```js
const hanoi = (n, x = 'x', y = 'y', z = 'z') => {
  if (n == 0) {
    // nothing
  } else {
    hanoi(n - 1, x, z, y)
    console.log(`${x} -> ${y}`)
    hanoi(n - 1, z, y, x)
  }
}

hanoi(3)
```

---

result

```bash
x -> y
x -> z
y -> z
x -> y
z -> x
z -> y
x -> y
```

---

Thank you very much for your attention.