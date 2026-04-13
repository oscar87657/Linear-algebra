# 1.2 — 내적과 각도 (Lengths and Angles from Dot Products)

> **선생님의 한마디**: "내적은 단순히 숫자를 곱하고 더하는 계산이 아니에요. 두 벡터가 얼마나 같은 방향을 향하고 있는지, 혹은 얼마나 수직인지를 알려주는 아주 강력한 도구랍니다. 오늘 이 도구를 마스터해 봅시다!"

---

## 목차

- [1. 내적 (Dot Product) 이란?](#dot-product)
- [2. 벡터의 길이와 단위 벡터](#length-unit)
  - [2.1 벡터의 길이 (Length or Norm)](#length)
  - [2.2 단위 벡터 (Unit Vector)](#unit-vector)
- [3. 두 벡터 사이의 각도](#angles)
- [4. 직교 (Orthogonality)](#orthogonality)
- [5. 두 가지 중요한 부등식](#inequalities)
  - [5.1 코시-슈바르츠 부등식 (Schwarz Inequality)](#schwarz)
  - [5.2 삼각 부등식 (Triangle Inequality)](#triangle)
- [요약](#summary)

---

<a id="dot-product"></a>
## 1. 내적 (Dot Product) 이란?

**내적** 은 두 벡터의 대응하는 성분끼리 곱한 뒤 그 결과들을 모두 합산한 값입니다. 두 벡터 $\mathbf{v}$ 와 $\mathbf{w}$ 의 내적은 $\mathbf{v}\cdot\mathbf{w}$ 로 표기합니다.

$$
\mathbf{v} = \begin{bmatrix} v\_{1} \\ v\_{2} \end{bmatrix}, \quad \mathbf{w} = \begin{bmatrix} w\_{1} \\ w\_{2} \end{bmatrix} \implies \mathbf{v}\cdot\mathbf{w} = v\_{1}w\_{1} + v\_{2}w\_{2}
$$

**예시**:

$$
\mathbf{v} = \begin{bmatrix} 4 \\\\ 2 \end{bmatrix}, \quad \mathbf{w} = \begin{bmatrix} -1 \\\\ 2 \end{bmatrix} \implies \mathbf{v}\cdot\mathbf{w} = (4)(-1) + (2)(2) = -4 + 4 = 0
$$

내적값이 $0$ 이 나왔네요? 이것이 무엇을 의미하는지는 잠시 후에 '직교' 섹션에서 다루겠습니다.

---

<a id="length-unit"></a>
## 2. 벡터의 길이와 단위 벡터

<a id="length"></a>
### 2.1 벡터의 길이 (Length or Norm)
벡터 $\mathbf{v}$ 의 길이는 $\|\mathbf{v}\|$ 로 표기하며, 자기 자신을 내적한 값에 루트를 씌워 계산합니다. 이것은 피타고라스 정리의 확장판이라고 생각하면 쉽습니다.

$$
\|\mathbf{v}\| = \sqrt{\mathbf{v}\cdot\mathbf{v}} = \sqrt{v\_{1}^{2} + v\_{2}^{2} + \dots + v\_{n}^{2}}
$$

<a id="unit-vector"></a>
### 2.2 단위 벡터 (Unit Vector)
길이가 $1$ 인 벡터를 **단위 벡터** 라고 부릅니다. 어떤 벡터 $\mathbf{v}$ 를 그 벡터의 길이 $\|\mathbf{v}\|$ 로 나누면, 방향은 같으면서 길이는 $1$ 인 단위 벡터 $\mathbf{u}$ 를 얻을 수 있습니다.

$$
\mathbf{u} = \frac{\mathbf{v}}{\|\mathbf{v}\|}
$$

---

<a id="angles"></a>
## 3. 두 벡터 사이의 각도

내적은 기하학적으로 두 벡터 사이의 각도 $\theta$ 와 아주 밀접한 관련이 있습니다.

$$
\mathbf{v}\cdot\mathbf{w} = \|\mathbf{v}\| \|\mathbf{w}\| \cos\theta
$$

위 공식에서 우리는 $\cos\theta$ 를 다음과 같이 구할 수 있습니다.

$$
\cos\theta = \frac{\mathbf{v}\cdot\mathbf{w}}{\|\mathbf{v}\| \|\mathbf{w}\|}
$$

**[실전 예시]** $\mathbf{v} = [1, 0]^{T}$ 와 $\mathbf{w} = [1, 1]^{T}$ 사이의 각도를 구해봅시다.

$$
\mathbf{v}\cdot\mathbf{w} = (1)(1) + (0)(1) = 1
$$

$$
\|\mathbf{v}\| = \sqrt{1^{2} + 0^{2}} = 1, \quad \|\mathbf{w}\| = \sqrt{1^{2} + 1^{2}} = \sqrt{2}
$$

$$
\cos\theta = \frac{1}{1 \cdot \sqrt{2}} = \frac{1}{\sqrt{2}} \implies \theta = 45^{\circ}
$$

오른쪽을 가리키는 벡터와 오른쪽 위 45도를 가리키는 벡터 사이의 각도가 $45^{\circ}$ 라는 것이 직관과 일치하죠?

**각도에 따른 내적의 의미**:
- $\cos\theta \gt 0$: 각도가 $90^{\circ}$ 보다 작음 (예각, 같은 방향성)
- $\cos\theta = 0$: 각도가 정확히 $90^{\circ}$ 임 (**직교**, Perpendicular)
- $\cos\theta \lt 0$: 각도가 $90^{\circ}$ 보다 큼 (둔각, 반대 방향성)

---

<a id="orthogonality"></a>
## 4. 직교 (Orthogonality)

두 벡터 $\mathbf{v}$ 와 $\mathbf{w}$ 의 내적이 $0$ 이면, 두 벡터는 서로 **수직** 또는 **직교** 한다고 말합니다.

$$
\mathbf{v} \perp \mathbf{w} \iff \mathbf{v}\cdot\mathbf{w} = 0
$$

이것은 선형대수학에서 가장 중요한 개념 중 하나입니다. $0$ 벡터는 모든 벡터와 직교한다는 점도 기억해 두세요!

---

<a id="inequalities"></a>
## 5. 두 가지 중요한 부등식

선형대수학의 기하학적 구조를 지탱하는 두 가지 핵심 부등식이 있습니다.

<a id="schwarz"></a>
### 5.1 코시-슈바르츠 부등식 (Schwarz Inequality)
내적의 절대값은 항상 두 벡터의 길이의 곱보다 작거나 같습니다.

$$
|\mathbf{v}\cdot\mathbf{w}| \le \|\mathbf{v}\| \|\mathbf{w}\|
$$

이 부등식은 사실 앞에서 본 $\cos\theta$ 공식에서 바로 나옵니다. $|\cos\theta| \le 1$ 이니까 $|\mathbf{v}\cdot\mathbf{w}| = \|\mathbf{v}\|\|\mathbf{w}\||\cos\theta| \le \|\mathbf{v}\|\|\mathbf{w}\|$ 가 되는 것이죠. 쉽게 말해 **"두 벡터의 내적이 아무리 커봤자 각각의 길이를 곱한 것보다 크긴 불가능하다"** 는 뜻입니다.

<a id="triangle"></a>
### 5.2 삼각 부등식 (Triangle Inequality)
두 벡터를 더한 것의 길이는 각각의 길이를 더한 것보다 항상 작거나 같습니다.

$$
\|\mathbf{v}+\mathbf{w}\| \le \|\mathbf{v}\| + \|\mathbf{w}\|
$$

> **비유**: 서울에서 부산을 갈 때 직선으로 가는 거리(왼쪽) 는 대구를 경유해서 가는 거리(오른쪽) 보다 항상 짧거나 같습니다. 두 지점을 잇는 직선이 가장 짧은 경로이기 때문입니다!

---

<a id="summary"></a>
## 요약

| 개념 | 공식 | 기하학적 의미 |
|:-----|:-----|:-----|
| **내적** | $\mathbf{v}\cdot\mathbf{w}$ | 방향의 일치성 측정 |
| **길이** | $\|\mathbf{v}\| = \sqrt{\mathbf{v}\cdot\mathbf{v}}$ | 원점에서의 거리 |
| **단위 벡터** | $\mathbf{u} = \mathbf{v}/\|\mathbf{v}\|$ | 방향만 남긴 벡터 (길이 1) |
| **직교** | $\mathbf{v}\cdot\mathbf{w} = 0$ | 두 벡터가 수직임 |
| **코시-슈바르츠** | $|\mathbf{v}\cdot\mathbf{w}| \le \|\mathbf{v}\| \|\mathbf{w}\|$ | $\cos\theta$ 가 1을 넘을 수 없음 |

---

<br>

> **다음 시간에는**: 벡터의 묶음인 **행렬(Matrix)** 과 그 행렬이 만드는 새로운 영토인 **열 공간(Column Space)** 에 대해 알아보겠습니다. 수고하셨습니다! 👋🏻
