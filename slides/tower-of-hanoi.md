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

- What is Tower of Hanoi
- サンプル - 1 / 2 / 3 / 10
- 解説
- コード
- 結論

---

#### ice break

この中で中でハノイの塔はどれ?

|  A | B  |  C |
|---|---|---|
|　![leaning_tower_of_pisa](https://www.touropia.com/gfx/d/famous-towers-in-the-world/leaning_tower_of_pisa.jpg "leaning_tower_of_pisa") |　![hanoi](https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif "hanoi") | ![cn_tower](https://www.touropia.com/gfx/d/famous-towers-in-the-world/cn_tower.jpg "cn_tower") |

---

|  A | B  |  C |
|--|:-:|---|
|　![leaning_tower_of_pisa](https://www.touropia.com/gfx/d/famous-towers-in-the-world/leaning_tower_of_pisa.jpg "leaning_tower_of_pisa") |　![hanoi](https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif "hanoi") | ![cn_tower](https://www.touropia.com/gfx/d/famous-towers-in-the-world/cn_tower.jpg "cn_tower") |
| Leaning Tower of Pisa | :smile: | CN Tower |

---

What is Tower of Hanoi

The Tower of Hanoi is a mathematical game or puzzle consisting of three rods and a number of disks of various diameters, which can slide onto any rod.

The puzzle begins with the disks stacked on one rod in order of decreasing size, the smallest at the top, thus approximating a conical shape.

The objective of the puzzle is to move the entire stack to the last rod, obeying the following rules:

---

Let's brain exercise.

---

1枚のみ
![n1](https://www.kirupa.com/data_structures_algorithms/images/toh_one_144.png)

---

![n1](https://www.kirupa.com/data_structures_algorithms/images/toh_one_final_144.png)

---

2枚
![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_144.png)

---

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_2_144.png)

---

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_3_144.png)

---

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_4_144.png)

---

3枚
![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_1_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_2_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_3_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_4_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_5_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_6_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_7_144.png)

---

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_8_144.png)

---

10枚

---

1024

---

Did you come up with a solution?
Let's think about how to solve it.

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

$H(n)$

とすると、0枚の場合

$H(0) = 0$

---

1枚の円盤を移す方法は

$H(1) = 1$

つまり


$H(n) = H(n - 1) + 1 + H(n - 1)$

---

0から順番にみると

$H(0) = 0$
$H(1) = H(0) + 1 + H(0) = 0 + 1 + 0 = 1$
$H(2) = H(1) + 1 + H(1) = 1 + 1 + 1 = 3$
$H(3) = H(2) + 1 + H(2) = 3 + 1 + 3 = 7$
$H(4) = H(3) + 1 + H(3) = 7 + 1 + 7 = 15$
$H(5) = H(4) + 1 + H(4) = 15 + 1 + 15 = 31$
$H(6) = H(5) + 1 + H(5) = 31 + 1 + 31 = 63$

---

$0 = 1 - 1$
$1 = 2 - 1$
$3 = 4 - 1$
$7 = 8 - 1$
$15 = 16 - 1$

$1, 2, 4, 8 = 2^0, 2^1, 2^2, 2^3, 2^4$

---

$H(n) = 2^n - 1$

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