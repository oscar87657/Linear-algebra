# 1.4 — 행렬 곱셈과 첫 번째 분해 (Matrix Multiplication and A = CR)

> **선생님의 한마디**: "단순한 계산을 넘어 행렬을 '조립' 하고 '해체' 하는 과정을 보여드릴게요. 특히 '조각 조립(Rank-1 Sum)' 방식은 처음엔 낯설 수 있지만, 나중에 데이터 압축이나 AI를 배울 때 보물 같은 지식이 될 거예요!"

---

## 목차

- [1. 행렬 곱셈 AB: 4가지 관점 비교 예시](#ab-multiplication)
- [2. 관점 4 집중 탐구: 랭크-1 행렬의 조립 (Rank-1 Sum)](#rank-1-sum)
- [3. A = CR 분해: 행렬 속의 뼈대와 설계도](#a-cr-decomposition)
- [요약](#summary)

---

<br>

<a id="ab-multiplication"></a>
## 1. 행렬 곱셈 AB: 4가지 관점 비교 예시

행렬 곱셈 $C = AB$ 를 계산하는 방법은 무려 4가지나 있습니다. 결과는 모두 같지만, 상황에 따라 우리가 얻을 수 있는 통찰이 다릅니다.

$$

A = \begin{bmatrix} 1 & 2 \\\\ 3 & 4 \end{bmatrix}, \quad B = \begin{bmatrix} 5 & 6 \\\\ 7 & 8 \end{bmatrix}

$$

### 1.1 성분별 방식 (Dot Product): "현미경 관찰"
가장 기초적인 방법으로, $A$ 의 행과 $B$ 의 열을 내적합니다.
- **예시**: $c\_{11} = (1)(5) + (2)(7) = 19$

### 1.2 열(Column) 방식: "기둥 섞기" ★
$B$ 의 각 열을 $A$ 의 열들의 선형 결합으로 봅니다.
- **의미**: $C$ 의 첫 번째 열은 $A$ 의 열들을 $B$ 의 첫 번째 열 성분만큼 섞은 결과입니다.

$$

5 \begin{bmatrix} 1 \\\\ 3 \end{bmatrix} + 7 \begin{bmatrix} 2 \\\\ 4 \end{bmatrix} = \begin{bmatrix} 19 \\\\ 43 \end{bmatrix} \quad (\text{C의 1번 열})

$$

### 1.3 행(Row) 방식: "줄 섞기"
$A$ 의 각 행을 $B$ 의 행들의 선형 결합으로 봅니다.
- **의미**: $C$ 의 첫 번째 줄은 $B$ 의 행들을 $A$ 의 첫 번째 행 성분만큼 섞은 결과입니다.

$$

1 \begin{bmatrix} 5 & 6 \end{bmatrix} + 2 \begin{bmatrix} 7 & 8 \end{bmatrix} = \begin{bmatrix} 5+14 & 6+16 \end{bmatrix} = \begin{bmatrix} 19 & 22 \end{bmatrix} \quad (\text{C의 1번 행})

$$

> **열 방식과 대칭**: 열 방식은 "$C$ 의 각 **열**을 $A$ 의 **열** 조합"으로 봤다면, 행 방식은 "$C$ 의 각 **행**을 $B$ 의 **행** 조합"으로 보는 것입니다. 구하는 것의 방향만 다를 뿐 같은 원리입니다.

### 1.4 블록 방식 (Outer Product): "조각 조립"
$A$ 의 각 **열** 과 $B$ 의 대응하는 **행** 을 곱하면 **랭크-1 행렬** 조각이 하나 만들어집니다. 이 조각들을 모두 더하면 $C$ 가 됩니다.

$$

C = AB = \sum_{k} (\text{A의 }k\text{번 열}) \times (\text{B의 }k\text{번 행})

$$

---

<br>

<a id="rank-1-sum"></a>
## 2. 관점 4 집중 탐구: 랭크-1 행렬의 조립 (Rank-1 Sum)

이 방식은 행렬을 거대한 데이터가 아니라 **'의미 있는 조각들의 합'** 으로 봅니다.

**[조립 과정]**

**판 1** (A의 1번 기둥 $\times$ B의 1번 줄):

$$

\begin{bmatrix} 1 \\\\ 3 \end{bmatrix} \begin{bmatrix} 5 & 6 \end{bmatrix} = \begin{bmatrix} 5 & 6 \\\\ 15 & 18 \end{bmatrix}

$$

**판 2** (A의 2번 기둥 $\times$ B의 2번 줄):

$$

\begin{bmatrix} 2 \\\\ 4 \end{bmatrix} \begin{bmatrix} 7 & 8 \end{bmatrix} = \begin{bmatrix} 14 & 16 \\\\ 28 & 32 \end{bmatrix}

$$

**최종 합체** (판 1 + 판 2):

$$

\begin{bmatrix} 5 & 6 \\\\ 15 & 18 \end{bmatrix} + \begin{bmatrix} 14 & 16 \\\\ 28 & 32 \end{bmatrix} = \begin{bmatrix} 19 & 22 \\\\ 43 & 50 \end{bmatrix} = C

$$

이것이 바로 행렬을 구성하는 '근본적인 조각' 들을 찾아내는 원리입니다.

---

<br>

<a id="a-cr-decomposition"></a>
## 3. A = CR 분해: 행렬 속의 뼈대와 설계도

모든 행렬은 독립적인 핵심 기둥들($C$) 과 그 기둥들을 어떻게 섞을지 적어둔 레시피($R$) 로 분해할 수 있습니다. 이것이 행렬 압축의 시작인 $A = CR$ 분해입니다.

$$

A = \begin{bmatrix} 1 & 0 & 2 \\\\ 2 & 1 & 4 \\\\ 0 & 1 & 0 \end{bmatrix}

$$

**Step 1: 뼈대($C$) 찾기**
- 1번 기둥: $[1, 2, 0]^{T}$ (독립)
- 2번 기둥: $[0, 1, 1]^{T}$ (독립)
- 3번 기둥: $[2, 4, 0]^{T}$ (1번 기둥의 2배 $\rightarrow$ **종속**, 버림!)

$$

C = \begin{bmatrix} 1 & 0 \\\\ 2 & 1 \\\\ 0 & 1 \end{bmatrix} \quad (\text{행렬 A의 독립적인 기둥만 모음})

$$

**Step 2: 설계도($R$) 적기**
$A$ 의 각 열이 $C$ 의 기둥들을 어떤 비율로 섞었는지 적습니다.
- $A$ 의 1번 열 = $C$ 의 1번 기둥 $\times 1$ + $C$ 의 2번 기둥 $\times 0$
- $A$ 의 2번 열 = $C$ 의 1번 기둥 $\times 0$ + $C$ 의 2번 기둥 $\times 1$
- $A$ 의 3번 열 = $C$ 의 1번 기둥 $\times 2$ + $C$ 의 2번 기둥 $\times 0$

$$

R = \begin{bmatrix} 1 & 0 & 2 \\\\ 0 & 1 & 0 \end{bmatrix}

$$

**[최종 분해 결과]**

$$

A = \underbrace{\begin{bmatrix} 1 & 0 \\\\ 2 & 1 \\\\ 0 & 1 \end{bmatrix}}_{C} \underbrace{\begin{bmatrix} 1 & 0 & 2 \\\\ 0 & 1 & 0 \end{bmatrix}}_{R}

$$

---

<br>

<a id="summary"></a>
## 요약

| 관점/개념 | 핵심 내용 |
|:-----|:-----|
| **AB의 4가지 관점** | 성분, 열 결합, 행 결합, 랭크-1 합 (상황에 따라 골라 쓰기!) |
| **Rank-1 Sum** | 행렬은 얇은 조각 행렬들의 합으로 이루어진다. |
| **A = CR** | 중복된 정보를 버리고 '뼈대'와 '설계도'로 압축하는 과정. |

---

<br>

> **다음 시간에는**: 이제 본격적으로 연립방정식을 깎아서 푸는 **소거법** 의 세계로 떠나보겠습니다. 고생하셨습니다! 👋🏻
