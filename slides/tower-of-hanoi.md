---
marp: true
paginate: true
theme: gaia-ex
math: katex
---

<!-- _class: first -->

Tower of Hanoi Puzzle Algorithm
===

- Takayasu Nasu

---

## Agenda

- What is Tower of Hanoi
- Use case
- Explanation
- Conclusion
- Sample code

---

## ice break

Which of these towers is in Hanoi? A, B or C?

|  A | B  |  C |
|---|---|---|
|　![leaning_tower_of_pisa](https://www.touropia.com/gfx/d/famous-towers-in-the-world/leaning_tower_of_pisa.jpg "leaning_tower_of_pisa") |　![hanoi](https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif "hanoi") | ![cn_tower](https://www.touropia.com/gfx/d/famous-towers-in-the-world/cn_tower.jpg "cn_tower") |

---

### Correct answer is B.

|  A | B  |  C |
|--|:-:|---|
|　![leaning_tower_of_pisa](https://www.touropia.com/gfx/d/famous-towers-in-the-world/leaning_tower_of_pisa.jpg "leaning_tower_of_pisa") |　![hanoi](https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif "hanoi") | ![cn_tower](https://www.touropia.com/gfx/d/famous-towers-in-the-world/cn_tower.jpg "cn_tower") |
| Leaning Tower of Pisa | :smile: | CN Tower |

---

## What is Tower of Hanoi

The Tower of Hanoi is a mathematical game or puzzle consisting of three rods and a number of disks of various diameters, which can slide onto any rod.

---

The puzzle begins with the disks stacked on one rod in order of decreasing size, the smallest at the top, thus approximating a conical shape.


The objective of the puzzle is to move the entire stack to the last rod, obeying the following rules:

1. Only one disk may be moved at a time.
1. Each move consists of taking the upper disk from one of the stacks and placing it on top of another stack or on an empty rod.
1. No disk may be placed on top of a disk that is smaller than it.

---

## Let's brain exercise.

---

## Use case

Let's consider How many times we have to move, in the case of 1 disk, 2 disks, and 3 disks.

---

## 1 disk

![n1](https://www.kirupa.com/data_structures_algorithms/images/toh_one_144.png)

---

### only 1 time

![n1](https://www.kirupa.com/data_structures_algorithms/images/toh_one_final_144.png)

---

## 2 disks

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_144.png)

---

### 1

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_2_144.png)

---

### 2

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_3_144.png)

---

### 3 times

![n2](https://www.kirupa.com/data_structures_algorithms/images/two_toh_4_144.png)

---

## 3 disks

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_1_144.png)

---

### 1

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_2_144.png)

---

### 2

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_3_144.png)

---

### 3

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_4_144.png)

---

### 4

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_5_144.png)

---

### 5

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_6_144.png)

---

### 6

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_7_144.png)

---

### 7 times

![n3](https://www.kirupa.com/data_structures_algorithms/images/three_toh_8_144.png)

---

<!-- _class: ten -->

## How about 10 disks case?

---

<!-- _class: ten -->

- 1023 times

---

## Did you come up with a solution?
## Let's think about how to solve it.

---

## Explanation

### For example 6 disks case.

1. First, move 5 disks from rod A to rod C
1. Next, move the largest disk (of the 6) from rod A to rod B
1. Finally, move the 5 disks from rod C to rod B.

---

### For example 5 disks case.

1. First, move 4 disks from rod A to rod C
1. Next, move the largest disk (of the 5) from rod A to rod B
1. Finally, move the 4 disks from rod C to rod B.

---

## That's mean

### To move n disks from rod A to rod B

case of `n = 0`
:arrow_right: Nothing

case of `n > 0`
:arrow_right: First, move `n - 1` disks from rod A to rod C using rod B
:arrow_right: Next, 1 disk move from fod A to rod B
:arrow_right: Finally, move `n - 1` disks from rod C to rod B using rod A

---

The Calculation Formula for determining the minimum number of disks is

$H(n)$

Then, if there are 0 disk

$H(0) = 0$

---

Way of move 1 disk

$H(1) = 1$

That's mean

$H(1) = H(1 - 1) + 1 + H(1 - 1)$

$H(1) = H(0) + 1 + H(0) = 1$

---

Way of move 2 disks

$H(2) = 3$

That's mean

$H(2) = H(2 - 1) + 1 + H(2 - 1)$

$H(2) = H(1) + 1 + H(1) = 3$

---

## Let's see from 0 disk

$H(0) = 0$
$H(1) = H(0) + 1 + H(0) = 0 + 1 + 0 = 1$
$H(2) = H(1) + 1 + H(1) = 1 + 1 + 1 = 3$
$H(3) = H(2) + 1 + H(2) = 3 + 1 + 3 = 7$
$H(4) = H(3) + 1 + H(3) = 7 + 1 + 7 = 15$
$H(5) = H(4) + 1 + H(4) = 15 + 1 + 15 = 31$
$H(6) = H(5) + 1 + H(5) = 31 + 1 + 31 = 63$

---

### In other words

$0 = 1 - 1$
$1 = 2 - 1$
$3 = 4 - 1$
$7 = 8 - 1$
$15 = 16 - 1$

Look at the second number.

$1, 2, 4, 8, 16 = 2^0, 2^1, 2^2, 2^3, 2^4$

---

## Conclusion

It can be obtained how many times moving disks from the following formula.

$H(n) = 2^n - 1$

### How about 10 disks case?

$2^{10} = 1024$

$H(10) = 1024 - 1 = 1023$

---

### This is the solution code.

```js
const H = (n, x = 'x', y = 'y', z = 'z') => {
  if (n == 0) {
    // nothing
  } else {
    H(n - 1, x, z, y)
    console.log(`${x} -> ${y}`)
    H(n - 1, z, y, x)
  }
}

H(3)
```

---

## result

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
<!-- _class: end -->

## Thank you very much for your attention.
