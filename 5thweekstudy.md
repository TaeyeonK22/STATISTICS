# 통계학 5주차 정규과제

📌통계학 정규과제는 매주 정해진 분량의 『*데이터 분석가가 반드시 알아야 할 모든 것*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **Statistics_5th_TIL**에 나열된 분량을 읽고 `학습 목표`에 맞게 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 추가자료와 교재를 다시 참고하여 보완하는 것이 좋습니다.

5주차는 `2부. 데이터 분석 준비하기`를 읽고 새롭게 배운 내용을 정리해주시면 됩니다.


## Statistics_5th_TIL

### 2부. 데이터 분석 준비하기
### 11.데이터 전처리와 파생변수 생성



## Study Schedule

|주차 | 공부 범위     | 완료 여부 |
|----|----------------|----------|
|1주차| 1부 p.2~56     | ✅      |
|2주차| 1부 p.57~79    | ✅      | 
|3주차| 2부 p.82~120   | ✅      | 
|4주차| 2부 p.121~202  | ✅      | 
|5주차| 2부 p.203~254  | ✅      | 
|6주차| 3부 p.300~356  | 🍽️      | 
|7주차| 3부 p.357~615  | 🍽️      | 

<!-- 여기까진 그대로 둬 주세요-->

# 11.데이터 전처리와 파생변수 생성

```
✅ 학습 목표 :
* 결측값과 이상치를 식별하고 적절한 방법으로 처리할 수 있다.
* 데이터 변환과 가공 기법을 학습하고 활용할 수 있다.
* 모델 성능 향상을 위한 파생 변수를 생성하고 활용할 수 있다.
```


## 11.1. 결측값 처리
- 개요
  - 실제 데이터에서는 결측값과 이상값이 없는 경우가 드묾.
  - 분석 환경에 따라 `.`, `NA`, `NaN` 등으로 표시됨.
  - 결측값 처리 방법을 결정하기 전에 고려해야 할 사항
    - 결측값의 비율
    - 한 변수에 결측값이 몰려 있는지 여부
  - 주의사항: 빈 문자열이 입력되어 있어서 결측값으로 인식되지 않는 값이 있는지 확인 필요

- 결측치가 발생하는 특성에 따른 분류
  1. 완전 무작위 결측(MCAR: Missing Completely at Random)
     - 이름 그대로 순수하게 결측값이 무작위로 발생한 경우를 말한다.
     - 따라서 결측값을 제거하더라도 편향(bias)가 거의 발생하지 않는다.
  2. 무작위 결측(MAR: Missing at Random)
     - 다른 변수의 특성에 의해 해당 변수의 결측치가 <span style="color: blue;">**체계적으로**</span> 발생한 경우를 뜻한다.
     - 예시: A마트의 전국 체인 매출 정보 중, 특정 체인점의 POS기기에 오류가 나서 해당 체인점에 해당하는 매출 정보에 결측값이 많이 나타난 경우.
     - 위 예시의 경우, 결측값은 해당 체인점 여부에 따른 특성에 **체계적으로** 영향을 받음.
  3. 비무작위 결측(NMAR: Missing at Not Random)
     - 결측값들이 해당 변수 자체의 특성을 가지고 있는 경우
     - 예시: A마트의 고객정보 데이터의 `고객 소득`변수에서 결측값들 대부분이 소득이 적어서 공개하기 꺼려해서 결측이 발생한 경우.

- 결측값의 처리 방법(연속형 변수 전제)
  1. 표본 제거 방법: 결측값이 심하게 많은 변수를 제거하거나 결측값이 포함된 행을 제외하고 데이터 분석
     - 결측값이 10% 미만일 경우 이 방법을 사용하는 경우가 많음.
     - 다만, 실무의 자료들은 높은 비율의 결측값이 있는 경우가 많다.
  2. 평균 대치법(Mean Imputation)
     - 방법: 결측값을 제외한 온전한 값들의 평균을 구한 후, 그 평균 값을 결측값들에 대치하는 것.
     - 평균 대신 최빈값, 중앙값, 최대값, 최솟값 활용 가능
     - 단점
       - 관측된 데이터의 평균을 사용하기 때문에 통계량의 표준오차가 축소(왜곡)되어 나타남.
       - 따라서, p-value가 부정확한 값이 산출됨.
     - 따라서, 결측치가 완전 무작위 결측이 아닌 경우 적절하지 않은 방법임.
  3. 보간법
     - 활용: 데이터가 시계열적 특성을 가지고 있을 때 활용하면 효과적임.
     - 방법: 전 시점 혹은 다음 시점의 값으로 대치하거나 전 시점과 다음 시점의 평균 값으로 대치하기
       - 시점 인덱스의 간격이 불규칙하거나 결측값이 두 번 연달아 있는 경우, 선형적인 수치 값을 계산해 보간한다.
     - 단순 순서 보간법과 시점 고려 보간법이 있다.
  4. 회귀대치법
     - 단순하게 평균값 등을 대치하는 것에서 나아가 해당 변수와 다른 변수 사이의 관계성을 고려하여 결측값을 계산하는 방법
     - 예시: 수입이 많아질수록 연령이 높아지는 상관관계를 가지고 있다면, 결측치를 포함하는 관측치의 연 수입이 높으면 높은 연령을 추정하여 결측값을 대치함
     - 논리: 추정하고자 하는 결측값을 가진 변수를 종속변수로 하고, 나머지를 독립변수로 하여 추정한 회귀식을 통해 결측값을 대치함.
     - 단점: 이 경우에도 여전히 표본오차를 과소 추정하는 문제를 가지고 있음.
       - 이러한 문제를 해결하기 위해 **확률적 회귀대치법**을 사용하여 변동성을 조정하기도 함.(인위적으로 회귀식에 확률 오차항을 추가) 다만, 이 방법도 여전히 표본오차를 과소 추정하는 문제를 가지고 있음.
  5. 다중 대치법(multiple imputation)
     - 의의: 표본오차의 과소 추정 문제를 해결하기 위하여 최근 많이 사용되는 방법
     - 개요: 단순대치를 여러 번 수행하여 n개의 가상적 데이터를 생성하여 이들의 평균으로 결측값을 대치함.
     - 단계
       1. 대치 단계(imputation step): 가능한 대치 값의 분포에서 추출된 서로 다른 값으로 결측치를 처리한 n개의 데이터셋 생성
       1. 분석 단계(Analysis Step): 생성된 각각의 데이터셋을 분석하여 모수의 추정치와 표준오차 계산
       1. 결합 단계(Pooling Step): 계산된 각 데이터셋의 추정치와 표준오차를 결합하여 최종 결측 대치값 산출
     - 결측값의 비율이 증가할수록 가상데이터도 많이 검증해야 검정력이 증가한다.

## 11.2. 이상치 처리
- 개요
  - 이상치란? 일부 관측치의 값이 전체 데이터의 범위에서 크게 벗어나 극단적인 값을 갖는 것.
  - 데이터의 모집단 평균이나 총합을 추정하는 것에 문제를 일으키며, 분산을 과도하게 증가시켜 분석이나 모델링의 정확도를 감소시킴.
  - 일반적으로 제거하는 것이 좋으나, 데이터의 특성에 따라 전체 데이터의 양이 많아 해당 이상치가 통계값에 미치는 영향력이 작을 경우 제거의 필요성이 낮아진다.
  - 다만 실제 분석용 데이터에서는 영향력 있는 이상치들이 많이 존재하는 경우가 대다수이기 때문에 이상치 처리 단계를 거치고 분석 모델링에 들어가는 것이 일반적이다.

- 이상치 처리 방법
  - 일반적: 이상치를 제거한다
    - 이렇게 하면 추정치의 분산은 감소하지만 실젯값을 과장하여 편향을 발생시키는 문제 때문에, 다른 방법들이 존재함.
  - 관측값 변경: 하한 값과 상한 값을 결정한 후 하한 값보다 작으면 하한 값으로 대체하고 상한 값보다 크면 상한 값으로 대체
  - 가중치 조정: 이상치의 영향을 감소시키는 가중치를 부여

- 이상치를 확인하는 방법(복습+추가)
  - 박스플롯 상에서 분류된 극단치를 이상치로 간주
  - 평균(중위수)로부터 &plusmn;n 표준편차 이상 떨어져 있는 값을 이상치로 간주
    - 보통 n은 3으로 설정하나, 분포가 비대칭인 경우 -n과 +n을 다르게 설정하기도 한다.
  - 중위수&중위수 절대 편차(MAD: Median Absolute Deviation): 평균은 이상치에 민감하기 때문에 이상치에 보다 강건한 중앙값을 활용하는 방법

- 이상치 확인 시 주의해야 할 부분
  - 통계치를 통한 무조건적인 이상치 탐색은 위험할 수 있으므로, 해당 데이터 변수들의 의미와 비즈니스 도메인을 먼저 이해하고 이상치가 생긴 원인을 생각하여 데이터를 바라보아야 한다.
  - **분석 도메인에 따라** 이상치가 중요한 분석 요인일 수 있다.
    - 예시: 제조 공정 데이터 분석의 경우 제품의 불량 원인을 찾아내기 위해 공정의 센서 데이터 변화를 분석하는 경우, 데이터 **이상치 자체가 분석의 주요한 요소에 해당함.**

## 11.3. 변수 구간화
- 개요
  - 목적: 데이터 분석의 성능 향상&해석의 편리성
  - 방법: 이산형 변수를 범주형 변수로 변환하기

- 변수 구간화 종류
  - 이산형 변수를 범주형 변수로 변환하기
  - 이산 값을 평활화하여 단순한 이산 값으로 변환시키기
    - 설명: 변수의 값을 일정한 폭이나 빈도를 기준으로 나눈 후, 각 구간 안에 속한 데이터 값을 평균, 중앙값, 경계값 등으로 변환하는 방법이다.
  - 클러스터링, 의사결정나무와 같은 머신러닝 기법 활용하기
    - 클러스터링: 타깃 변수의 설정 필요 없이(비교사적 방법이므로) 구간화할 변수의 값을 유사한 수준끼리 묶어줌
    - 의사결정나무: 타깃 변수를 설정해(교사적 방법이므로) 구간화할 변수의 값을 타깃 변수 예측에 가장 적합한 구간으로 나누어 줌.

- 구간화 효과성 검증 방법
  - WOE(Wieght of Evidece)값, 혹은 IV(Information Value)값 등을 통해 측정
  - 이 두 값은 로지스틱 회귀분석에서 파생된 개념으로, 종속변수 대비 독립변수가 예측력이 얼마나 강한지를 나타내는 지표.
  - IV값이 높을수록 종속변수의 True와 False를 잘 구분할 수 있는 정보량이 많다는 뜻이다. 일반적으로, **IV값이 0.3보다 큰 경우는 예측력이 우수한 변수인 것으로 판단**한다.

    | IV값 기준| 해석|
    | ---|---|
    |0~0.02|의미 없음|
    |0.02~0.1|약한 예측|
    |0.1~0.3|중간 예측|
    |0.3~0.5|강한 예측|
    |0.5~1|과도한 예측(확인 필요)|

## 11.4. 데이터 표준화와 정규화 스케일링
- 데이터 표준화와 정규화 스케일링이란?
  - 언제? 독립 변수들이 서로 단위가 다르거나 편차가 심할 때 스케일을 일정한 수준으로 변환시켜주는는 표준화나 정규화 스케일링을 한다.
  - 필요성
    - 독립변수 간 단위가 다른 것은 대부분의 데이터 마이닝 모델의 분석 결과에 별다른 영향을 미치지 않지만, 특정 머신러닝 모델의 학습 효율을 증가시키기 때문에 많이 사용된다.
      - k-Nearest Neighbor, SVM(서포트 벡터 머신), 범주화 알고리즘 인공신경망(Neural network)모델
    - 또한, 해석적 관점에서 데이터 표준화와 정규화는 매우 유용하다.

- 표준화(Z-score)
  - 각 **관측치의 값이 전체 평균을 기준으로 어느 정도 떨어져 있는지** 나타낼 때 사용한다.
  - 평균은 0으로 변환되고, 1 표준편차 거리는 &plusmn;1, 2표준편차 거리는 &plusmn;2로 변환된다.
  - Zero-mean으로부터 얼마나 떨어져 있는지를 나타내기 때문에 Z-score라고 표현한다.
  - 장점: 서로 다른 변수 간 값의 크기를 직관적으로 비교할 수 있다.

- 정규화
  - 데이터의 범위를 0부터 1까지로 변환하여 데이터 분포를 조정하는 방법이다. 전체 데이터 중에서 해당 값이 어떤 위치에 있는지 파악하는 데에 유용하다.
  - 0에 가까울수록 작은 값이고, 1에 가까울수록 큰 값이다.

- 표준화와 정규화의 차이 이해하기
  - 표준화는 평균에서 얼마나 떨어져 있는지를 나타내기 때문에 가장 큰 값이 1이 될 수도 있고 3.5도 될 수 있다.
  - 하지만 정규화는 가장 큰 값은 1, 가장 작은 값은 0으로 직관적으로 표현된다. 따라서, 평균으로부터 어느 정도 떨어져 있는지는 알기 힘들다.
  - 비슷하지만 다른 특성을 가지므로, 필요와 목적에 따라 선택하면 된다.

- 이외 방법: RobustScaler
  - 등장 배경: 기본 표준화, 정규화 방식은 평균을 활용하므로 이상치에 민감하다는 단점이 있음.
  - 방법: 중앙값(Q2)을 0으로 잡고 Q1(25%)와 Q3(75%) 사분위수와의 IQR 차이를 1이 되도록 하는 스케일링함.
  - 장점: 이상치의 영향력을 최소화하므로 일바적으로 표준화, 정규화보다 성능이 우수하다고 평가함.

## 11.5. 모델 성능 향상을 위한 파생 변수 생성
- 파생변수란?<br>원래 있던 변수들을 조합하거나 함수를 적용하여 새로 만들어낸 변수

- 예시
  - X1, X2 두 변수의 평균값으로 만들어낸 X3
  - 데이터 구간화, 표준화 및 정규화 등도 파생변수라고 할 수 있음.
  - 기존 값에 로그나 제곱근 등을 취해 변동성을 완화하거나 지수함수를 사용하여 분산을 증폭시키는 것
  - 시점을 고려하여 과거 시점 대비 변화 정도를 파생변수로 만드는 것

- 파생변수 생성 시 주의사항
  - 파생변수는 데이터의 특성을 이용하여 분석 효율을 높이는 것이기 때문에 전체 데이터에 대한 파악과 비즈니스 도메인에 대한 충분한 이해가 수반되어야 한다.
  - 기존 변수를 활용해서 만들어 낸 변수이기 대문에 다중공선성 문제가 발생할 가능성이 높다. 따라서, 파생변수를 만든 다음에는 상관분석을 통해 변수 간의 상관성을 확인해야 한다.
  - 파생 변수를 생성하는 대신 변수들 조합의 주요 속성만 추출해 내는 주성분 분석(PCA) 등을 활용할 수 있다.

<br>
<br>

# 확인 문제

## 문제 1. 데이터 전처리

> **🧚 한 금융회사의 대출 데이터에서 `소득` 변수에 결측치가 포함되어 있다. 다음 중 가장 적절한 결측치 처리 방법은 무엇인가?**

> **[보기]   
1️⃣ 결측값이 포함된 행을 모두 제거한다.  
2️⃣ 결측값을 `소득` 변수의 평균값으로 대체한다.  
3️⃣ `연령`과 `직업군`을 독립변수로 사용하여 회귀 모델을 만들어 `소득` 값을 예측한다.  
4️⃣ 결측값을 보간법을 이용해 채운다.**

> **[데이터 특징]**     
    - `소득` 변수는 연속형 변수이다.  
    - 소득과 `연령`, `직업군` 간에 강한 상관관계가 있다.  
    - 데이터셋에서 `소득` 변수의 결측 비율은 15%이다.

```
3️⃣ `연령`과 `직업군`을 독립변수로 사용하여 회귀 모델을 만들어 `소득` 값을 예측한다.  
이유
1. 결측 비율이 15%이므로 표본 제거 방법은 적절치 않다.
2. 해당 변수와 다른 변수 간 관계성이 있으므로 회귀분석법을 활용하면 보다 합리적으로 결측값을 처리할 수 있다. 
```

## 문제 2. 데이터 스케일링

> **🧚 머신러닝 모델을 학습하는 과정에서, `연봉(단위: 원)`과 `근속연수(단위: 년)`를 동시에 독립변수로 사용해야 합니다. 연봉과 근속연수를 같은 스케일로 맞추기 위해 어떤 스케일링 기법을 적용하는 것이 더 적절한가요?**

<!--표준화와 정규화의 차이점에 대해 고민해보세요.-->

```
정규화를 사용하는 것이 적절하다.
이유는 잘 모르겠습니다.
```
좋은 질문이야! 머신러닝에서 **정규화(normalization)** 와 **표준화(standardization)** 는 모두 **스케일이 서로 다른 변수들을 같은 기준으로 맞추기 위해 사용하는 전처리 기법**이지만, 적용해야 하는 상황에는 차이가 있어. 아래에서 비교 설명하고, 어떤 것이 더 적절한지도 판단해볼게.

---

## ✅ 정규화 vs 표준화 비교

| 항목              | **정규화 (Normalization)**                         | **표준화 (Standardization)**        |
| --------------- | ----------------------------------------------- | -------------------------------- |
| 정의              | 데이터를 **0과 1 사이**로 조정                            | 데이터를 **평균 0, 표준편차 1**로 변환        |
| 수식              | $x' = \frac{x - x_{\min}}{x_{\max} - x_{\min}}$ | $x' = \frac{x - \mu}{\sigma}$    |
| 사용 시기           | **최댓값과 최솟값의 범위가 중요**할 때 (예: 이미지 픽셀, 거리 기반 모델)   | **정규분포 가정, 이상치 영향 제거**가 중요할 때    |
| 민감도             | 이상치(outlier)에 **민감**                            | 이상치에 상대적으로 **강건(robust)**        |
| 대표 사용 모델        | **KNN, SVM, Neural Network** 등 거리 기반 모델         | **회귀, 로지스틱 회귀, PCA**, 선형 기반 모델 등 |
| 변수 스케일이 매우 다를 때 | 적용 가능                                           | 적용 가능                            |

---

## 🧠 문제 상황 분석

> ✨ **"연봉(단위: 원)"과 "근속연수(단위: 년)"는 단위가 매우 다르고, 머신러닝 모델에 동시에 투입된다.**

* `연봉`은 값의 범위가 **수백만\~수천만 원 이상**인 반면
* `근속연수`는 보통 **1\~30년** 수준의 상대적으로 좁은 범위

따라서, **두 변수는 스케일 차이가 크고, 단위도 완전히 다름**

---

## ✅ 어떤 스케일링이 적절한가?

| 조건                               | 해석                |
| -------------------------------- | ----------------- |
| 변수의 단위 차이가 큼                     | 둘 다 후보 가능         |
| 이상치 존재 가능성 (연봉은 고소득자가 이상치일 수 있음) | **표준화 유리**        |
| 대부분의 머신러닝 모델에서 사용하는 일반적인 방법      | **표준화가 더 보편적**    |
| 거리 기반 알고리즘이면 정규화도 고려             | (예: KNN, SVM 등에서) |

---

## ✅ 결론: **표준화(Standardization)** 가 더 적절함

> 이유:

* `연봉`은 이상치(고소득자)에 민감할 수 있으므로 정규화는 위험함
* 변수 간 **해당 값이 몇 표준편차만큼 떨어져 있는지**를 비교하는 것이 더 유리
* 대부분의 모델에서 **표준화된 스케일**이 더 안정적 성능을 제공함

---

## 💡 보너스 팁:

실전에서는 보통 `StandardScaler` (표준화)를 먼저 적용해보고, 성능이 나쁘거나 모델 특성상 정규화가 더 맞다고 판단되면 `MinMaxScaler` (정규화)를 고려하는 방식이 일반적이야.

---


### 🎉 수고하셨습니다.