# 1.4 — 행렬 곱셈과 첫 번째 분해 (Matrix Multiplication and A = CR)

> **선생님의 한마디**: "단순한 계산을 넘어 행렬을 '조립' 하고 '해체' 하는 과정을 보여드릴게요. 특히 '조각 조립(Rank-1 Sum)' 방식은 처음엔 낯설 수 있지만, 나중에 데이터 압축이나 AI를 배울 때 보물 같은 지식이 될 거예요!"

---

## 목차

- [1. 행렬 곱셈 AB: 4가지 관점 비교 예시](#1-행렬-곱셈-ab-4가지-관점-비교-예시)
- [2. 관점 4 집중 탐구: 랭크-1 행렬의 조립 (Rank-1 Sum)](#2-관점-4-집중-탐구-랭크-1-행렬의-조립-rank-1-sum)
- [3. A = CR 분해: 3x3 행렬 실전 예시](#3-a--cr-분해-3x3-행렬-실전-예시)
- [이번 챕터 요약](#요약)

---

<br>

## 1. 행렬 곱셈 $AB$: 4가지 관점 비교 예시

$$
A = \begin{bmatrix}1&2\\\\3&4\end{bmatrix}, \quad B = \begin{bmatrix}5&6\\\\7&8\end{bmatrix}
$$

**[핵심 관점 결과]**

1. 성분별(내적): $c_{11}=19$
2. 기둥 섞기 (1번 기둥):

$$
5\begin{bmatrix}1\\\\3\end{bmatrix}+7\begin{bmatrix}2\\\\4\end{bmatrix}=\begin{bmatrix}19\\\\43\end{bmatrix}
$$

3. 줄 섞기 (1번 줄):

$$
1\begin{bmatrix}5&6\end{bmatrix}+2\begin{bmatrix}7&8\end{bmatrix}=\begin{bmatrix}19&22\end{bmatrix}
$$

---

<br>

## 2. 관점 4 집중 탐구: 랭크-1 행렬의 조립 (Rank-1 Sum) 🚀

행렬 $AB$ 를 얇은 판데기(Rank-1 행렬) 들의 합으로 조립해 봅시다.

**[조립 과정]**

판 1 (A의 1번 기둥 x B의 1번 줄):

$$
\begin{bmatrix}1\\\\3\end{bmatrix}\begin{bmatrix}5&6\end{bmatrix}=\begin{bmatrix}5&6\\\\15&18\end{bmatrix}
$$

판 2 (A의 2번 기둥 x B의 2번 줄):

$$
\begin{bmatrix}2\\\\4\end{bmatrix}\begin{bmatrix}7&8\end{bmatrix}=\begin{bmatrix}14&16\\\\28&32\end{bmatrix}
$$

최종 합체 (판 1 + 판 2):

$$
\begin{bmatrix}5&6\\\\15&18\end{bmatrix}+\begin{bmatrix}14&16\\\\28&32\end{bmatrix}=\begin{bmatrix}19&22\\\\43&50\end{bmatrix}=C
$$

---

<br>

## 3. $A = CR$ 분해: $3 \times 3$ 행렬 실전 예시

뼈대($C$) 와 설계도($R$) 를 찾아봅시다.

$$
A = \begin{bmatrix}1&0&2\\\\2&1&4\\\\0&1&0\end{bmatrix}
$$

**Step 1: 독립 기둥 뽑기 (C)**
- 1번 기둥과 2번 기둥은 서로 독립입니다.
- 3번 기둥은 **1번 기둥의 2배** 입니다. (중복이라 버림)

$$
C = \begin{bmatrix}1&0\\\\2&1\\\\0&1\end{bmatrix}
$$

**Step 2: 조합 비율 적기 (R)**

$$
R = \begin{bmatrix}1&0&2\\\\0&1&0\end{bmatrix}
$$

**[최종 분해 결과]**

$$
A = \underbrace{\begin{bmatrix}1&0\\\\2&1\\\\0&1\end{bmatrix}}_{C}\underbrace{\begin{bmatrix}1&0&2\\\\0&1&0\end{bmatrix}}_{R}
$$

---

<br>

## 요약

| 개념 | 실제 예시의 교훈 |
|:-----|:-----|
| **Rank-1 Sum** | 전체 행렬은 조각 행렬들의 합이다. |
| **A = CR** | 독립 기둥만 모아 행렬을 압축할 수 있다. |
| **정보량** | Rank 는 행렬의 진짜 실력을 나타낸다. |

---

<br>

> **다음 시간에는**: 이제 본격적으로 연립방정식을 깎아서 푸는 **소거법** 의 세계로 떠나보겠습니다. 고생하셨습니다! 👋
