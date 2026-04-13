# 1.1 — 벡터와 선형 결합 (Vectors and Linear Combinations)

> **선생님의 한마디**: "벡터는 단순히 숫자의 묶음이 아니라, 공간을 자유롭게 가로지르는 **'화살표'** 입니다. 화살표 두 개로 세상의 모든 점을 찍을 수 있을까요? 아니면 한 직선에 갇혀 버릴까요? 숫자로 직접 증명해 봅시다!"

---

## 목차

- [1. 시작하기 전에: 왜 벡터를 배울까요?](#intro)
- [2. 벡터의 두 가지 날개: 스칼라 곱과 덧셈](#wings)
  - [2.1 스칼라 곱 (Scalar Multiplication)](#scalar-mult)
  - [2.2 벡터 덧셈 (Vector Addition): 평행사변형 법칙](#vec-add)
- [3. 선형 결합 (Linear Combination): 공간을 만드는 마법](#linear-comb)
  - [3.1 독립적인 벡터 (평면 생성)](#independent)
  - [3.2 종속적인 벡터 (직선에 갇힘)](#dependent)
- [4. 확인 문제: 직접 해보기](#problems)
- [요약](#summary)

---

<br>

<a id="intro"></a>
## 1. 시작하기 전에: 왜 벡터를 배울까요?

벡터는 공간 상의 **'이동 명령서'** 입니다. 예를 들어, $[3, 2]$ 라는 벡터는 "오른쪽으로 3칸, 위로 2칸 가세요" 라는 명령과 같습니다. 이러한 명령들을 조합하여 우리는 우주(공간) 의 어디든 도달할 수 있게 됩니다.

---

<br>

<a id="wings"></a>
## 2. 벡터의 두 가지 날개: 스칼라 곱과 덧셈

<a id="scalar-mult"></a>
### 2.1 스칼라 곱 (Scalar Multiplication)

벡터 $\mathbf{v}$ 에 숫자(스칼라) $c$ 를 곱하면 길이는 변하지만 방향은 유지(또는 정반대) 됩니다.

**[예시: 반대 방향으로 2배 늘리기]**

$$

\mathbf{v} = 
\begin{bmatrix}
  2 \\
  -1
\end{bmatrix}, \quad 
-2\mathbf{v} = 
\begin{bmatrix}
  -4 \\
  2
\end{bmatrix}

$$

- **해석**: 오른쪽으로 2, 아래로 1 가던 화살표가 이제 **왼쪽으로 4, 위로 2** 가는 화살표로 변했습니다.

<a id="vec-add"></a>
### 2.2 벡터 덧셈 (Vector Addition): 평행사변형 법칙

두 벡터를 더하는 것은 두 이동 명령을 **연달아 수행** 하는 것과 같습니다.

> **평행사변형 법칙**: $\mathbf{v}$ 만큼 이동한 뒤 $\mathbf{w}$ 만큼 이동한 도착점 — 그것이 바로 $\mathbf{v} + \mathbf{w}$ 입니다. 어느 방향을 먼저 가든($\mathbf{v}$ 먼저든 $\mathbf{w}$ 먼저든) 도착점은 같습니다. 두 화살표가 평행사변형을 이루고, 대각선이 합벡터입니다.

**[2차원 실전 예시]**

$$

\mathbf{v} = \begin{bmatrix} 2 \\\\ 1 \end{bmatrix}, \quad \mathbf{w} = \begin{bmatrix} 1 \\\\ 3 \end{bmatrix} \implies \mathbf{v} + \mathbf{w} = \begin{bmatrix} 3 \\\\ 4 \end{bmatrix}

$$

$\mathbf{v}$ 를 따라 오른쪽으로 2, 위로 1 이동한 뒤, $\mathbf{w}$ 를 따라 오른쪽으로 1, 위로 3 이동하면 최종 위치는 오른쪽 3, 위 4 입니다.

**[3차원 확장 예시]**

$$

\mathbf{v} = 
\begin{bmatrix}
  1 \\
  0 \\
  3
\end{bmatrix}, \quad 
\mathbf{w} = 
\begin{bmatrix}
  2 \\
  1 \\
  -1
\end{bmatrix} \rightarrow 
\mathbf{v} + \mathbf{w} = 
\begin{bmatrix}
  3 \\
  1 \\
  2
\end{bmatrix}

$$

---

<br>

<a id="linear-comb"></a>
## 3. 선형 결합 (Linear Combination): 공간을 만드는 마법

가장 중요한 개념입니다. 여러 벡터를 늘리고($c \mathbf{v}$) 줄여서 더하는($d \mathbf{w}$) 모든 행위를 **선형 결합** 이라고 합니다.

$$

c \mathbf{v} + d \mathbf{w}

$$

<a id="independent"></a>
### 3.1 독립적인 벡터 (평면 생성)

두 벡터의 방향이 다르면($\mathbf{v} \ne k \mathbf{w}$), 이들의 선형 결합은 광활한 **평면** 을 만듭니다.

$$

\mathbf{v}_{1} = 
\begin{bmatrix}
  1 \\
  0
\end{bmatrix}, \quad 
\mathbf{v}_{2} = 
\begin{bmatrix}
  0 \\
  1
\end{bmatrix}

$$

목표 지점 $\mathbf{b}$ 가 $[5, 3]$ 일 때, 우리는 $5\mathbf{v}\_{1}+3\mathbf{v}\_{2}$ 라는 레시피로 정확히 그 지점에 도달할 수 있습니다.

<a id="dependent"></a>
### 3.2 종속적인 벡터 (직선에 갇힘) 🚨

두 벡터의 방향이 같으면(어느 하나가 다른 하나의 배수면), 아무리 선형 결합을 해도 **직선 밖으로 나갈 수 없습니다.**

$$

\mathbf{v} = 
\begin{bmatrix}
  1 \\
  1
\end{bmatrix}, \quad 
\mathbf{w} = 
\begin{bmatrix}
  2 \\
  2
\end{bmatrix}

$$

- **문제**: $\mathbf{w} = 2\mathbf{v}$ 입니다. $\mathbf{w}$ 가 $\mathbf{v}$ 의 2배짜리 복사본이라, 아무리 $c\mathbf{v} + d\mathbf{w}$ 를 계산해도 결국 $(c + 2d)\mathbf{v}$ 가 될 뿐입니다. 한 가지 화살표 방향 위에서만 머뭅니다.
- **결과**: 목표 $[1, 2]$ 는 이 직선($y = x$ 방향) 위에 없으므로 **절대 도달할 수 없습니다.** 두 벡터가 같은 방향이라 2차원 평면을 만들지 못하고 1차원 직선에 갇혀버린 것입니다.

---

<br>

<a id="problems"></a>
## 4. 확인 문제: 직접 해보기

**Q1. 다음 벡터들의 선형 결합으로 $[4, 5]$ 에 도달하기 위한 $c$ 와 $d$ 를 구해보세요.**

$$

\mathbf{v} = 
\begin{bmatrix}
  1 \\
  1
\end{bmatrix}, \quad 
\mathbf{w} = 
\begin{bmatrix}
  0 \\
  1
\end{bmatrix}

$$

**[정답 확인]**
$c=4, d=1$ 입니다. ($4 \mathbf{v} + 1 \mathbf{w} = [4, 4] + [0, 1] = [4, 5]$)

---

<br>

<a id="summary"></a>
## 요약

| 조합 방식 | 기하학적 모습 | 공간의 크기 (Dimension) |
|:-----|:-----|:-----|
| $c \mathbf{v}$ (한 벡터의 배수) | 원점을 지나는 **직선** | 1차원 |
| $c \mathbf{v} + d \mathbf{w}$ (독립적) | 무한히 뻗은 **평면** | 2차원 |
| $c \mathbf{v} + d \mathbf{w}$ (종속적) | 여전히 하나의 **직선** | 1차원 (손실 발생!) |

---

<br>

> **다음 시간에는**: 벡터의 길이와 각도를 측정하는 **내적(Dot Product)** 에 대해 알아보겠습니다. 수고하셨습니다! 👋🏻
