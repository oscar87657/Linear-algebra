# 4.2 — 직선과 부분 공간으로의 사영 (Projections onto Lines and Subspaces)

> **선생님의 한마디**: "$Ax = b$ 의 해가 없을 때 포기하지 마세요. 열 공간 안에서 $b$ 에 **가장 가까운 점**을 찾으면 됩니다. 이것이 **사영(projection)** 이고, 통계, 신호 처리, 머신러닝의 핵심인 최소 제곱법의 시작입니다!"

---

## 목차

- [1. 사영이 필요한 이유](#why-projection)
- [2. 직선으로의 사영](#projection-onto-line)
- [3. 사영 행렬 P (1차원)](#projection-matrix-1d)
- [4. 부분 공간으로의 사영](#projection-onto-subspace)
- [5. 정규 방정식](#normal-equation)
- [6. 사영 행렬 P (n차원)](#projection-matrix-nd)
- [7. A 전치 A 의 가역성](#ata-invertible)
- [8. 실전 예시](#examples)
- [요약](#summary)

---

<br>

<a id="why-projection"></a>
## 1. 사영이 필요한 이유

$Ax = b$ 가 해를 가지려면 $b$ 가 $A$ 의 열 공간 $C(A)$ 에 속해야 합니다. 그런데 실제 데이터에서는 $b$ 가 $C(A)$ 밖에 있는 경우가 훨씬 흔합니다.

**해결책**: $b$ 자체를 맞추려 하지 말고, $C(A)$ 에서 $b$ 에 **가장 가까운 점** $p$ 를 찾아 $Ax = p$ 를 풉니다.

$$
e = b - p \quad \text{(오차 벡터)}
$$

- $p$: **사영(projection)** — 열 공간 안의 가장 가까운 점
- $e$: **오차(error)** — $b$ 에서 $p$ 까지의 거리 방향

> **왜 $e$ 가 열 공간에 수직이어야 할까요?**: $b$ 에서 평면까지의 최단 경로는 수직선이기 때문입니다. $e$ 가 수직이 아니라면 더 가까운 점이 존재합니다.

---

<br>

<a id="projection-onto-line"></a>
## 2. 직선으로의 사영

가장 단순한 경우 — 벡터 $b$ 를 벡터 $a$ 방향의 **직선** 위로 사영합니다.

사영 벡터 $p$ 는 $a$ 의 배수입니다:

$$
p = \hat{x} \, a
$$

$\hat{x}$ 는 구해야 할 스칼라 ("x-hat"이라 읽습니다).

<br>

**핵심 조건**: 오차 $e = b - \hat{x}a$ 가 $a$ 에 **수직** 입니다.

$$
a^{T}(b - \hat{x}a) = 0
$$

$$
a^{T}b - \hat{x}(a^{T}a) = 0
$$

$$
\hat{x} = \frac{a^{T}b}{a^{T}a}
$$

따라서 직선 위로의 사영 벡터는:

$$
\boxed{p = \hat{x} \, a = \frac{a^{T}b}{a^{T}a} \, a}
$$

<br>

**두 가지 특수 경우**:

| 경우 | $\hat{x}$ | $p$ | 의미 |
|:-----|:-----|:-----|:-----|
| $b = a$ | $1$ | $a$ | $a$ 위로 사영하면 $a$ 자신 |
| $b \perp a$ ($a^{T}b = 0$) | $0$ | $\mathbf{0}$ | 직교하면 사영은 영벡터 |

---

<br>

<a id="projection-matrix-1d"></a>
## 3. 사영 행렬 P (1차원)

$p = \frac{a^{T}b}{a^{T}a} \, a$ 를 행렬 형태로 쓰겠습니다. $a^{T}b$ 는 스칼라이므로 순서를 바꾸면:

$$
p = \frac{a \, a^{T}}{a^{T}a} \, b = P \, b
$$

**사영 행렬** ($n \times n$):

$$
\boxed{P = \frac{a \, a^{T}}{a^{T}a}}
$$

- $a$ 는 열벡터($n \times 1$), $a^{T}$ 는 행벡터($1 \times n$)
- $a a^{T}$ 는 $n \times n$ 랭크 1 행렬 (분자)
- $a^{T}a$ 는 스칼라 (분모)

<br>

**두 가지 핵심 성질**:

$$
P^{2} = P \quad \text{(두 번 사영해도 결과는 같다)}
$$

$$
P^{T} = P \quad \text{(사영 행렬은 대칭 행렬)}
$$

**증명** ($P^{2} = P$):

$$
P^{2} = \frac{a \, a^{T}}{a^{T}a} \cdot \frac{a \, a^{T}}{a^{T}a} = \frac{a \, (a^{T}a) \, a^{T}}{(a^{T}a)^{2}} = \frac{a \, a^{T}}{a^{T}a} = P \quad \blacksquare
$$

<br>

> **직교 여공간으로의 사영**: $I - P$ 는 $a$ 에 수직인 평면(직교 여공간)으로의 사영 행렬입니다.
>
> $$P + (I - P) = I$$
>
> $b$ 는 $a$ 방향 성분 $Pb$ 와 수직 성분 $(I-P)b$ 로 분해됩니다.

<br>

**예시**: $a = (1, 2, 2)^{T}$ 방향 직선으로의 사영.

$$
a^{T}a = 9, \quad P = \frac{1}{9} \begin{bmatrix} 1 \\\\ 2 \\\\ 2 \end{bmatrix} \begin{bmatrix} 1 & 2 & 2 \end{bmatrix} = \frac{1}{9} \begin{bmatrix} 1 & 2 & 2 \\\\ 2 & 4 & 4 \\\\ 2 & 4 & 4 \end{bmatrix}
$$

$b = (1, 1, 1)^{T}$ 를 사영하면:

$$
p = Pb = \frac{1}{9}(1 + 2 + 2) \begin{bmatrix} 1 \\\\ 2 \\\\ 2 \end{bmatrix} = \frac{5}{9} \begin{bmatrix} 1 \\\\ 2 \\\\ 2 \end{bmatrix}, \quad e = b - p = \frac{1}{9}\begin{bmatrix} 4 \\\\ -1 \\\\ -1 \end{bmatrix}
$$

검증: $e^{T}a = \frac{1}{9}(4 - 2 - 2) = 0$ ✓

---

<br>

<a id="projection-onto-subspace"></a>
## 4. 부분 공간으로의 사영

이제 1차원(직선)에서 **$n$차원 부분 공간**으로 확장합니다.

$A$ 의 열 공간 $C(A)$ 위로 $b$ 를 사영하는 문제입니다. $A$ 는 $m \times n$ 행렬이고 열들은 선형 독립입니다.

사영 벡터 $p$ 는 $A$ 의 열들의 선형 결합:

$$
p = A\hat{x} = \hat{x}_{1} a_{1} + \hat{x}_{2} a_{2} + \cdots + \hat{x}_{n} a_{n}
$$

**핵심 조건**: 오차 $e = b - A\hat{x}$ 가 $C(A)$ 의 모든 기저 벡터에 수직입니다.

$$
a_{1}^{T}(b - A\hat{x}) = 0, \quad a_{2}^{T}(b - A\hat{x}) = 0, \quad \ldots, \quad a_{n}^{T}(b - A\hat{x}) = 0
$$

이를 행렬 형태로 묶으면:

$$
A^{T}(b - A\hat{x}) = \mathbf{0}
$$

---

<br>

<a id="normal-equation"></a>
## 5. 정규 방정식 (Normal Equation)

위 조건을 정리하면 핵심 방정식이 나옵니다.

$$
\boxed{A^{T}A\hat{x} = A^{T}b}
$$

이를 **정규 방정식(normal equation)** 이라 합니다. $A^{T}A$ 가 가역이면:

$$
\hat{x} = (A^{T}A)^{-1}A^{T}b
$$

그리고 사영 벡터는:

$$
p = A\hat{x} = A(A^{T}A)^{-1}A^{T}b
$$

<br>

> **핵심 해석**: $A^{T}(b - p) = \mathbf{0}$ 이란 오차 $e = b - p$ 가 왼쪽 영 공간 $N(A^{T})$ 에 속한다는 뜻입니다. 4.1절에서 $N(A^{T}) \perp C(A)$ 임을 배웠으니, 오차가 열 공간에 수직이라는 사실과 완벽히 일치합니다!

---

<br>

<a id="projection-matrix-nd"></a>
## 6. 사영 행렬 P (n차원)

$p = A(A^{T}A)^{-1}A^{T}b = Pb$ 이므로, 열 공간 $C(A)$ 으로의 사영 행렬은:

$$
\boxed{P = A(A^{T}A)^{-1}A^{T}}
$$

<br>

**두 가지 핵심 성질** (1차원과 동일하게 성립):

$$
P^{2} = P \quad \text{(두 번 사영해도 결과는 같다)}
$$

$$
P^{T} = P \quad \text{(대칭 행렬)}
$$

**증명** ($P^{2} = P$):

$$
P^{2} = A(A^{T}A)^{-1}A^{T} \cdot A(A^{T}A)^{-1}A^{T} = A(A^{T}A)^{-1}(A^{T}A)(A^{T}A)^{-1}A^{T} = A(A^{T}A)^{-1}A^{T} = P \quad \blacksquare
$$

**증명** ($P^{T} = P$):

$$
P^{T} = \bigl(A(A^{T}A)^{-1}A^{T}\bigr)^{T} = A\bigl((A^{T}A)^{-1}\bigr)^{T}A^{T} = A(A^{T}A)^{-1}A^{T} = P \quad \blacksquare
$$

($A^{T}A$ 는 대칭이므로 그 역행렬도 대칭입니다.)

<br>

**1차원과 n차원 비교**:

| | 직선 위 사영 ($n=1$) | 부분 공간 위 사영 |
|:-----|:-----|:-----|
| 계수 | $\hat{x} = a^{T}b / a^{T}a$ (스칼라) | $\hat{x} = (A^{T}A)^{-1}A^{T}b$ (벡터) |
| 사영 벡터 | $p = \hat{x} \, a$ | $p = A\hat{x}$ |
| 사영 행렬 | $P = aa^{T} / a^{T}a$ | $P = A(A^{T}A)^{-1}A^{T}$ |
| 오차 조건 | $e \perp a$ | $e \perp C(A)$ |

---

<br>

<a id="ata-invertible"></a>
## 7. $A^{T}A$ 의 가역성

정규 방정식을 풀려면 $A^{T}A$ 가 가역이어야 합니다.

> **정리**: $A^{T}A$ 가 가역 $\iff$ $A$ 의 열들이 선형 독립

$$
A^{T}A \text{ 가역} \iff N(A) = \{\mathbf{0}\}
$$

**증명**:

($N(A) \subseteq N(A^{T}A)$): $Ax = \mathbf{0}$ 이면 $A^{T}Ax = A^{T}\mathbf{0} = \mathbf{0}$. 자명합니다.

($N(A^{T}A) \subseteq N(A)$): $A^{T}Ax = \mathbf{0}$ 이면, 양변에 $x^{T}$ 를 곱하면:

$$
x^{T}A^{T}Ax = (Ax)^{T}(Ax) = \|Ax\|^{2} = 0
$$

길이가 $0$ 이므로 $Ax = \mathbf{0}$, 즉 $x \in N(A)$. $\blacksquare$

따라서 $N(A^{T}A) = N(A)$. $A$ 의 열이 선형 독립 $\Leftrightarrow$ $N(A) = \{\mathbf{0}\}$ $\Leftrightarrow$ $N(A^{T}A) = \{\mathbf{0}\}$ $\Leftrightarrow$ $A^{T}A$ 가역.

<br>

> **주의**: $A$ 자체는 정방 행렬이 아니어서 역행렬이 없어도, $A$ 의 열이 선형 독립이면 $A^{T}A$ 는 가역입니다!

---

<br>

<a id="examples"></a>
## 8. 실전 예시

### 예시: 부분 공간으로의 사영 (단계별)

$$
A = \begin{bmatrix} 1 & 0 \\\\ 1 & 1 \\\\ 1 & 1 \end{bmatrix}, \quad b = \begin{bmatrix} 1 \\\\ 2 \\\\ 3 \end{bmatrix}
$$

$A$ 의 두 열은 선형 독립이므로 $A^{T}A$ 는 가역입니다.

**Step 1**: $A^{T}A$ 계산.

$$
A^{T}A = \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 \\\\ 1 & 1 \\\\ 1 & 1 \end{bmatrix} = \begin{bmatrix} 3 & 2 \\\\ 2 & 2 \end{bmatrix}
$$

**Step 2**: $A^{T}b$ 계산.

$$
A^{T}b = \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 1 \\\\ 2 \\\\ 3 \end{bmatrix} = \begin{bmatrix} 6 \\\\ 5 \end{bmatrix}
$$

**Step 3**: 정규 방정식 풀기. $\det(A^{T}A) = 6 - 4 = 2$.

$$
(A^{T}A)^{-1} = \frac{1}{2}\begin{bmatrix} 2 & -2 \\\\ -2 & 3 \end{bmatrix}, \quad \hat{x} = \frac{1}{2}\begin{bmatrix} 2 & -2 \\\\ -2 & 3 \end{bmatrix} \begin{bmatrix} 6 \\\\ 5 \end{bmatrix} = \frac{1}{2}\begin{bmatrix} 2 \\\\ 3 \end{bmatrix} = \begin{bmatrix} 1 \\\\ 3/2 \end{bmatrix}
$$

**Step 4**: 사영 벡터 $p = A\hat{x}$.

$$
p = \begin{bmatrix} 1 & 0 \\\\ 1 & 1 \\\\ 1 & 1 \end{bmatrix} \begin{bmatrix} 1 \\\\ 3/2 \end{bmatrix} = \begin{bmatrix} 1 \\\\ 5/2 \\\\ 5/2 \end{bmatrix}
$$

**Step 5**: 오차 확인.

$$
e = b - p = \begin{bmatrix} 0 \\\\ -1/2 \\\\ 1/2 \end{bmatrix}
$$

$$
A^{T}e = \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix} \begin{bmatrix} 0 \\\\ -1/2 \\\\ 1/2 \end{bmatrix} = \begin{bmatrix} 0 \\\\ 0 \end{bmatrix} \quad \checkmark
$$

오차 $e$ 가 $C(A)$ 에 수직입니다. 정규 방정식이 맞습니다!

<br>

**사영 행렬 $P$ 계산**:

$$
P = A(A^{T}A)^{-1}A^{T} = \begin{bmatrix} 1 & 0 \\\\ 1 & 1 \\\\ 1 & 1 \end{bmatrix} \frac{1}{2}\begin{bmatrix} 2 & -2 \\\\ -2 & 3 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix}
$$

$$
= \frac{1}{2}\begin{bmatrix} 2 & 0 \\\\ 0 & 1 \\\\ 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix} = \frac{1}{2}\begin{bmatrix} 2 & 2 & 2 \\\\ 0 & 1 & 1 \\\\ 0 & 1 & 1 \end{bmatrix}
$$

$$
P = \begin{bmatrix} 1 & 1 & 1 \\\\ 0 & 1/2 & 1/2 \\\\ 0 & 1/2 & 1/2 \end{bmatrix}
$$

검증: $Pb = (1, 5/2, 5/2)^{T} = p$ ✓

---

<br>

<a id="summary"></a>
## 요약: 4.2절 — 직선과 부분 공간으로의 사영

| 개념 | 핵심 내용 |
|:-----|:-----|
| 사영의 목적 | $b \notin C(A)$ 일 때 가장 가까운 $p \in C(A)$ 를 찾는다 |
| 직선 위 사영 | $\hat{x} = a^{T}b / a^{T}a$, $p = \hat{x}\,a$ |
| 사영 행렬 (1차원) | $P = aa^{T} / a^{T}a$ |
| 정규 방정식 | $A^{T}A\hat{x} = A^{T}b$ |
| 부분 공간 위 사영 | $p = A(A^{T}A)^{-1}A^{T}b$ |
| 사영 행렬 (n차원) | $P = A(A^{T}A)^{-1}A^{T}$ |
| 사영 행렬의 성질 | $P^{2} = P$, $P^{T} = P$ |
| $A^{T}A$ 가역 조건 | $A$ 의 열이 선형 독립 $\Leftrightarrow$ $N(A) = \{\mathbf{0}\}$ |

<br>

$$
\boxed{A^{T}A\hat{x} = A^{T}b \implies p = A\hat{x}, \quad P = A(A^{T}A)^{-1}A^{T}}
$$

---

<br>

> **마무리**: "사영 행렬 $P$ 는 공간을 두 조각으로 자르는 칼날입니다. $Pb$ 는 열 공간 안으로, $(I-P)b$ 는 열 공간 밖(왼쪽 영 공간)으로 — 정확히 반으로 갈라냅니다. 이 분해가 다음에 배울 최소 제곱법과 직교 행렬의 핵심 아이디어입니다!"

---

<br>

> **다음 시간에는**: 4.3절에서 사영을 이용한 **최소 제곱법(Least Squares)** 을 배웁니다. 데이터에 가장 잘 맞는 직선을 찾는 방법 — 통계와 머신러닝의 출발점입니다!
