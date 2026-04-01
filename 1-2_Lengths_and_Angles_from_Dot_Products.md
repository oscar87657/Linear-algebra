# 1.2 — 내적과 각도 (Lengths and Angles from Dot Products)

> **선생님의 한마디**: "내적은 단순히 숫자를 곱하고 더하는 계산이 아니에요. 두 벡터가 얼마나 같은 방향을 향하고 있는지, 혹은 얼마나 수직인지를 알려주는 아주 강력한 도구랍니다. 오늘 이 도구를 마스터해 봅시다!"

---

## 1. 내적 (Dot Product) 이란?

**내적** 은 두 벡터의 대응하는 성분끼리 곱한 뒤 그 결과들을 모두 합산한 값입니다. 두 벡터 $\mathbf{v}$ 와 $\mathbf{w}$ 의 내적은 $\mathbf{v}\cdot\mathbf{w}$ 로 표기합니다.

$$
\mathbf{v} = \begin{bmatrix} v\_{1} \\ v\_{2} \end{bmatrix}, \quad \mathbf{w} = \begin{bmatrix} w\_{1} \\ w\_{2} \end{bmatrix} \implies \mathbf{v}\cdot\mathbf{w} = v\_{1}w\_{1} + v\_{2}w\_{2}
$$

**예시**:
$$
\mathbf{v} = \begin{bmatrix} 4 \\ 2 \end{bmatrix}, \quad \mathbf{w} = \begin{bmatrix} -1 \\ 2 \end{bmatrix} \implies \mathbf{v}\cdot\mathbf{w} = (4)(-1) + (2)(2) = -4 + 4 = 0
$$
내적값이 $0$ 이 나왔네요? 이것이 무엇을 의미하는지는 잠시 후에 '직교' 섹션에서 다루겠습니다.

---

## 2. 벡터의 길이와 단위 벡터

### 2.1 벡터의 길이 (Length or Norm)
벡터 $\mathbf{v}$ 의 길이는 $\|\mathbf{v}\|$ 로 표기하며, 자기 자신을 내적한 값에 루트를 씌워 계산합니다. 이것은 피타고라스 정리의 확장판이라고 생각하면 쉽습니다.

$$
\|\mathbf{v}\| = \sqrt{\mathbf{v}\cdot\mathbf{v}} = \sqrt{v\_{1}^{2} + v\_{2}^{2} + \dots + v\_{n}^{2}}
$$

### 2.2 단위 벡터 (Unit Vector)
길이가 $1$ 인 벡터를 **단위 벡터** 라고 부릅니다. 어떤 벡터 $\mathbf{v}$ 를 그 벡터의 길이 $\|\mathbf{v}\|$ 로 나누면, 방향은 같으면서 길이는 $1$ 인 단위 벡터 $\mathbf{u}$ 를 얻을 수 있습니다.

$$
\mathbf{u} = \frac{\mathbf{v}}{\|\mathbf{v}\|}
$$

---

## 3. 두 벡터 사이의 각도

내적은 기하학적으로 두 벡터 사이의 각도 $\theta$ 와 아주 밀접한 관련이 있습니다.

$$
\mathbf{v}\cdot\mathbf{w} = \|\mathbf{v}\| \|\mathbf{w}\| \cos\theta
$$

위 공식에서 우리는 $\cos\theta$ 를 다음과 같이 구할 수 있습니다.

$$
\cos\theta = \frac{\mathbf{v}\cdot\mathbf{w}}{\|\mathbf{v}\| \|\mathbf{w}\|}
$$

**각도에 따른 내적의 의미**:
- $\cos\theta \gt 0$: 각도가 $90^{\circ}$ 보다 작음 (예각, 같은 방향성)
- $\cos\theta = 0$: 각도가 정확히 $90^{\circ}$ 임 (**직교**, Perpendicular)
- $\cos\theta \lt 0$: 각도가 $90^{\circ}$ 보다 큼 (둔각, 반대 방향성)

---

## 4. 직교 (Orthogonality)

두 벡터 $\mathbf{v}$ 와 $\mathbf{w}$ 의 내적이 $0$ 이면, 두 벡터는 서로 **수직** 또는 **직교** 한다고 말합니다.

$$
\mathbf{v} \perp \mathbf{w} \iff \mathbf{v}\cdot\mathbf{w} = 0
$$

이것은 선형대수학에서 가장 중요한 개념 중 하나입니다. $0$ 벡터는 모든 벡터와 직교한다는 점도 기억해 두세요!

---

## 5. 두 가지 중요한 부등식

선형대수학의 기하학적 구조를 지탱하는 두 가지 핵심 부등식이 있습니다.

### 5.1 코시-슈바르츠 부등식 (Schwarz Inequality)
내적의 절대값은 항상 두 벡터의 길이의 곱보다 작거나 같습니다.

$$
|\mathbf{v}\cdot\mathbf{w}| \le \|\mathbf{v}\| \|\mathbf{w}\|
$$

이 식은 $|\cos\theta| \le 1$ 이라는 사실로부터 자연스럽게 도출됩니다.

### 5.2 삼각 부등식 (Triangle Inequality)
두 벡터를 더한 합벡터의 길이는 각 벡터의 길이를 더한 것보다 항상 작거나 같습니다.

$$
\|\mathbf{v} + \mathbf{w}\| \le \|\mathbf{v}\| + \|\mathbf{w}\|
$$

삼각형의 두 변의 길이 합은 나머지 한 변의 길이보다 길다는 기하학적 원리와 같습니다.

---

## 요약

1. **내적**: $\mathbf{v}\cdot\mathbf{w} = \sum v\_{i}w\_{i}$ (성분끼리 곱해서 합산)
2. **길이**: $\|\mathbf{v}\| = \sqrt{\mathbf{v}\cdot\mathbf{v}}$
3. **직교**: $\mathbf{v}\cdot\mathbf{w} = 0$ 이면 두 벡터는 수직임.
4. **부등식**: 내적은 길이의 곱을 넘지 못하며($\le$), 합의 길이는 길이의 합을 넘지 못함($\le$).

---

> **다음 시간에는**: 행렬과 벡터의 곱셈을 통해, 벡터들의 선형 결합이 어떻게 공간을 채워나가는지 알아보겠습니다.
