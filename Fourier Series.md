
## 詳細求解步驟

### 核心觀念：利用奇偶函數簡化積分
在對稱區間 $[-\pi, \pi]$ 上，週期 $T = 2\pi$。我們可以將函數 $f(x) = x + \pi$ 拆解為奇函數與偶函數兩部分：
1. **$x$ 為奇函數**（關於原點對稱）。
2. **$\pi$ 為偶函數**（常數，關於 $y$ 軸對稱）。

利用奇偶函數在對稱區間的積分性質，可以大幅簡化接下來的係數計算。

---

### Step 1: 求解直流項係數 $a_0$
根據傅立葉係數公式：

$$
a_0 = \frac{1}{2\pi} \int_{-\pi}^{\pi} f(x) \, dx
$$

代入 $f(x) = x + \pi$，由於奇函數 $x$ 在對稱區間的積分為 0，式子簡化為：

$$
a_0 = \frac{1}{2\pi} \int_{-\pi}^{\pi} \pi \, dx = \frac{1}{2\pi} \cdot \left( \pi \cdot 2\pi \right) = \pi
$$

---

### Step 2: 求解餘弦項係數 $a_n$
根據公式：

$$
a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} (x + \pi) \cos(nx) \, dx
$$

將其拆解為兩項：

$$
a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x \cos(nx) \, dx + \frac{1}{\pi} \int_{-\pi}^{\pi} \pi \cos(nx) \, dx
$$

* **第一項**：因為 奇函數 $\times$ 偶函數 = 奇函數，所以積分結果為：
  $$\int_{-\pi}^{\pi} x \cos(nx) \, dx = 0$$
* **第二項**：餘弦波 $\cos(nx)$ 在一整個完整週期 $[-\pi, \pi]$ 上的波峰波谷會剛好抵消，所以積分結果亦為 $0$。

因此：

$$
a_n = 0
$$

---

### Step 3: 求解正弦項係數 $b_n$
根據公式：

$$
b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} (x + \pi) \sin(nx) \, dx
$$

將其拆解為兩項：

$$
b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x \sin(nx) \, dx + \frac{1}{\pi} \int_{-\pi}^{\pi} \pi \sin(nx) \, dx
$$

* **第二項**：因為 偶函數 $\times$ 奇函數 = 奇函數，所以積分結果直接為：
  $$\int_{-\pi}^{\pi} \pi \sin(nx) \, dx = 0$$
* **第一項**：因為 奇函數 $\times$ 奇函數 = 偶函數，根據對稱性質，可以簡化為 $2$ 倍的 $[0, \pi]$ 區間積分：

$$
b_n = \frac{2}{\pi} \int_{0}^{\pi} x \sin(nx) \, dx
$$

接下來使用**分部積分法 (Integration by parts)**，令 $u = x \implies du = dx$，並令 $dv = \sin(nx)dx \implies v = -\frac{\cos(nx)}{n}$：

$$
b_n = \frac{2}{\pi} \left( \left[ -x \frac{\cos(nx)}{n} \right]_{0}^{\pi} - \int_{0}^{\pi} \left( -\frac{\cos(nx)}{n} \right) \, dx \right)
$$

由於後面的 $\int_{0}^{\pi} \cos(nx)dx = 0$，我們只需要計算前項：

$$
b_n = \frac{2}{\pi} \left( -\pi \frac{\cos(n\pi)}{n} - 0 \right) = -\frac{2}{n} \cos(n\pi)
$$

已知 $\cos(n\pi) = (-1)^n$，代入後整理可得：

$$
b_n = -\frac{2}{n} (-1)^n = \frac{2}{n} (-1)^{n+1}
$$

---

## 最終答案

將求得的係數 $a_0 = \pi$、$a_n = 0$ 與 $b_n = \frac{2}{n}(-1)^{n+1}$ 代回展開式，可得 $f(x) = x + \pi$ 的傅立葉級數終解為：

$$
f(x) = \pi + \sum_{n=1}^{\infty} \frac{2}{n} (-1)^{n+1} \sin(nx)
$$

若將前幾項展開，則呈現如下級數形式：

$$
f(x) = \pi + 2 \left( \sin(x) - \frac{1}{2}\sin(2x) + \frac{1}{3}\sin(3x) - \frac{1}{4}\sin(4x) + \dots \right)
$$
