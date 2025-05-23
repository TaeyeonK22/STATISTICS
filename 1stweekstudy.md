# 통계학 1주차 정규과제

📌통계학 정규과제는 매주 정해진 분량의 『*데이터 분석가가 반드시 알아야 할 모든 것*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **Statistics_1st_TIL**에 나열된 분량을 읽고 `학습 목표`에 맞게 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 추가자료와 교재를 다시 참고하여 보완하는 것이 좋습니다.

1주차는 `1부. 데이터 기초체력 기르기`를 읽고 새롭게 배운 내용을 정리해주시면 됩니다.


## Statistics_1st_TIL

### 1부. 데이터 기초체력 기르기
### 01. 통계학 이해하기
### 02. 모집단과 표본추출
### 03. 변수와 척도
### 04. 데이터의 기술 통계적 측정
### 05. 확률과 확률변수

## Study Schedule

|주차 | 공부 범위     | 완료 여부 |
|----|----------------|----------|
|1주차| 1부 p.2~56     | ✅      |
|2주차| 1부 p.57~79    | 🍽️      | 
|3주차| 2부 p.82~120   | 🍽️      | 
|4주차| 2부 p.121~202  | 🍽️      | 
|5주차| 2부 p.203~254  | 🍽️      | 
|6주차| 3부 p.300~356  | 🍽️      | 
|7주차| 3부 p.357~615  | 🍽️      | 

<!-- 여기까진 그대로 둬 주세요-->

# 01. 통계학 이해하기

```
✅ 학습 목표 :
* 통계학의 필요성에 대해 인식한다.
* 기술통계와 추론통계의 특성을 구분할 수 있다.
```

> <통계학의 필요성>
<br> 1. 데이터 과학은 기초 통계로부터 발전하였고, 의미해석에도 기초 통계가 활용된다. 
<br><br>2. 머신러닝과 딥러닝 역시 통계학의 일부 특성을 활용한 응용과학 분야이다.
<br><br>3. 다만, 통계학은 가설 검증과 데이터의 해석을 목적으로 하고 있고, 머신러닝은 학습과 예측 프로세스를 설계하는 과정하는 것이 목적이므로 차이가 있으며, 이에 따라 접근 방향에서 차이가 있다.(가설 검증과 데이터의 확인 순서의 차이)

><기술통계와 추론통계의 특성>
<br>1. 기술통계는 주어진 데이터의 특성을 묘사하는 것으로서, 일반적으로 평균, 중앙값, 최빈값을 의미한다. 또한, 데이터 과학에서는 기술 통계를 내는 것을 EDA라고 한다. 또한 기술 통계는 일반적으로 시각화를 많이 사용한다.
<br><br>2. 추론 통계의 목적은 표본 집단으로부터 모집단의 특성을 추론하는 것이다. 신뢰 구간을 구하거나, 머신러닝을 통해 모델을 만들고 이를 구동하는 것이 추론 통계에 해당한다.
<br><br>3. 추론 통계가 기술 통계보다 중요하다고 단정지을 수 없다. 물론 추론 통계가 데이터 과학의 주축을 맡고 있지만, 기술 통계를 확실히 했을 때 추론 통계를 통한 정확한 인사이트 도출이 가능하다.

<!---새롭게 배운 내용을 자유롭게 정리해주세요.-->


# 02. 모집단과 표본추출

```
✅ 학습 목표 :
* 모집단과 표본의 정의와 관계를 설명할 수 있다.
* 편향과 분산의 차이를 설명할 수 있다.
```

> <모집단과 표본의 정의와 관계>
<br>1. 모집단은 분석 대상 전체의 집합을 말하고, 그 모집단의 일부를 추출한 것을 표본이라한다.
<br><br>2.일반적인 상황에서는 모집단 데이터를 모으는 것부터 쉽지가 않고, 또한 이를 모두 활용하느 것은 무리가 있다. 따라서 적은 표본만으로 최대한 높은 정확도를 이끌어내는 것이 중요하며, 이 과정에서 표본 추출이 상당한 중요도를 차지한다.
<br><br>3. 데이터과학 적용 시에도 빅데이터 분석이 트렌드가 되면서 표본추출이 필요 없을 것이라고 생각하지만, 실제로는 그렇지 않다.
<br><br>4. 최종 분석에는 전체 데이터를 사용하더라도, 분석 모델이 완료될 때까지는 표본 데이터를 활용하는 것이 경제적, 시간적으로 유리하다. 또한, 전수 데이터를 활용한다고 하더라도 이상치 제거 및 결측값 처리와 같은 정제 과정이 필요하다.

> <편향과 분산의 차이>
<br>1. 편향이란 표본에서 나타나는 모집단과의 체계적인 차이로서, 비표본 오차의 한 원인이다. 표본오차는 모집단과 표본과의 자연적인 차이로 인해 발생하는 오차를 표본 오차라고 하고, 이외의 오차를 비표본 오차라고 한다.
<br><br>2. 표본 편향은 확률화 등의 방법을 통해 최소화하거나 없앨 수 있다. 
<br><br>3. 인지적 편향은 분석가의 성향이나 상황에 따라 비논리적인 추론을 내리는 편향으로, 확증 편향, 기준점 편향, 선택 지원 편향, 분모 편향, 생존자편향 등이 있다.
<br><br>4. 분산은 주어진 데이터 포인트에 대한 모델 예측의 가변성을 뜻하고, 편향과는 상충관계에 있다.

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->


# 03. 변수와 척도
```
✅ 학습 목표 :
* 독립변수, 종속변수의 관계를 파악할 수 있다.
* 척도(변수의 데이터적 속성)의 종류를 설명할 수 있다.
```

> <독립변수, 종속변수의 관계>
<br>1. 독립변수와 종속변수는 원인과 결과의 관계이다. 이는 인과관계를 의미하는 것으로, 상관관계(두 변수의 수치가 상관성을 갖는 것)의 하위개념에 해당한다. 참고로, 독립변수 간 상관관계가 있으면 다중공선성의 문제가 발생하므로, 상관관계가 없는 것이 바람직하다.
<br><br>2. 새롭게 알게 된 변수 관계의 종류
<br>&ensp;1) 의사관계는 변수 간에 상관관계는 있지만 그 상관성이 다른 변수에 의해 나타난 관계이다. 
<br>&ensp;&ensp;ex) 일별 아이스크림 판매량과 익사사고 발생 수에 높은 상관관계가 있는데, 이는 '기온'이라는 제3변수와의 관게 때문이다.
<br>&ensp;2) 매개관계는 독립변수와 종속변수의 중간에서 매개변수가 개입되어 독립변수의 영향을 종속변수에 전달하는 관계이다. 따라서, 시간적 차원이 포함되어 있다. 매개관계는 조절관계와 달리 독립변수 종속변수와 직접 영향을 주고받는다.

><척도의 종류>
<br>1. 질적 척도에는 명목 척도와 서열 척도가, 양적 척도에는 등간 척도와 비율 척도가 있다. 명목 척도와 서열 척도는 속성값인지, 순위로 나타내는지에 따라 구분되며, 등간 척도와 비율 척도는 영점이 존재하는가에 따라 나뉜다.
<br><br>2. 명목척도는 순서, 거리 및 원점의 개념이 없기 때문에 숫자로 변환한다 해도 순서나 크기에 의미가 없다. 예시로, 운동선수의 등번호 숫자나 숫자로 변환한 혈액형 정보 등이 있다.
<br><br>3. 서열척도는 명목척도와 같이 대상을 서로 구분할 수 있는 정보를 포함하면서, 대상 간의 순서관계를 측정하는 척도이다. 다만, 해당 순서 사이의 간격에 대한 정보는 가지고 있지 않아서 둘 간의 차이는 알 수 없다.
<br><br>4. 등간척도는 서열척도에 더하여 해당 정보 간 차이를 비교할 수 있는 정보를 가지고 있다. 다만, 절대적인 기준점(영점)이 없다.
<br><br>5. 비율척도는 가장 많은 정보를 담을 수 있는 척도로, 절대적 기준(영점)을 통한 비율 정보를 담고 있다. 즉, 사칙연산이 모두 가능하다.

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->


# 04. 데이터의 기술 통계적 측정

```
✅ 학습 목표 :
* 산포도의 의미를 설명하고 측정방법을 나열할 수 있다.
* 정규분포의 왜도값과 첨도값이 얼마인지 답할 수 있다.
```

> <산포도의 의미, 측정방법>
<br>1. 산포도는 대푯값을 중심으로 자료들이 흩어져 있는 정도를 의미하며, 분산도라고도 불린다. 산포도를 측정하는 방법으로는 범위, 분산, 표준편차, 사분위수 범위, 변동계수 등이 있다.
<br><br>2. 변동계수는 표준편차를 산술평균으로 나누어준 값으로, 변동계수를 이용해 서로 다른 두 자료의 산포도를 비교할 수 있다. 
<br>&ensp;ex) 발 사이즈와 키의 산포도를 비교하려 한다면, 표준편차만으로는 비교할 수 없다. scale이 다르기 때문이다. 이를 변동계수를 구하여 비교하면 변동 값이 표준화되기 때문에 서로의 산포도를 비교할 수 있게 된다.

>정규분포의 왜도값과 첨도값>
<br>1. 왜도란 데이터 분포의 좌우 비대칭도를 표현하는 척도이다. 정규분포처럼 분포가 좌우대칭을 이룰수록 왜도값을 작아지고, 한쪽으로 몰려 있으면 왜도값의 절대값이 증가한다. 일반적으로, 피어슨의 비대칭 계수를 통해 측정한다.
<br><br>2. 첨도는 분포가 정규분포보다 얼마나 뾰족하거나 완만한지의 정도를 나타내는 분포이다.
<br><br>3. 정규분포의 왜도는 0이고, 첨도는 3이다.(다만, 해석의 편의성 0을 기준 값으로 하는 경우도 있다.)

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->


# 05. 확률과 확률변수

```
✅ 학습 목표 :
* 확률변수의 개념과 종류를 설명할 수 있다.
* 심슨의 역설을 설명하고, 발생 원인을 식별하며, 이를 해결하기 위한 방안을 도출할 수 있다.
```

> <확률변수의 개념과 종류>
<br>1. 확률변수는 확률과 변수의 개념이 합쳐진 것으로, 측정 값이 변할 수 있는 확률이 주어진 변수를 의미한다. 표본추출에 따라 달라지는 표본평균이나 표본분산과 같은 것이 대표적인 확률변수라 할 수 있다.
<br><br>2. 확률변수는 이산확률변수와 연속확률변수로 구분할 수 있다. 이산확률변수는 변수가 가질 수 있는 값이 셀 수 있는 변수로, 변수가 각 실숫값을 가질 수 있는 확률이 계산가능하다. 반면에 연속확률변수는 연속형 값을 가지기 때문에 나올 수 있는 값들의 개수를 셀 수 없고, 이에 따라 특정한 값을 가질 수 있는 확률을 계산하지 않고 그 대신에 특정 구간이 나올 수 있는 확률을 구하는 방법으로 접근한다.


> <심슨의 역설 의미, 발생 원인, 해결방안>
<br>1. 심슨의 역설이란 데이터를 어떻게 나누고 결합하고 가공하는가에 따라 정반대의 결과로 해석될 수 있음을 나타내는 현상이다.
<br><br>2. 이는 모든 데이터를 풀어서 보여주지 않고 압축해서 보여주는 편의 때문에 발생하는 현상이다. <br><br>3. 확률의 특성을 올바르게 고려한다면 잘못된 결과의 도출을 방지할 수 있다.


<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->


<br>
<br>

# 확인 문제

## 문제 1.

> **🧚Q. 한 대형 병원이 두 명의 외과 의사(A와 B)의 수술 성공률을 비교하려고 한다. 과거 1년간의 데이터를 보면, A 의사의 전체 수술 성공률은 80%, B 의사의 전체 수술 성공률은 90%였다. 이 데이터를 본 병원 경영진은 A 의사의 실력이 B 의사보다 별로라고 판단하여 A 의사의 수술 기회를 줄이는 방향으로 정책을 조정하려 한다.
그러나 일부 의료진은 이 결론에 의문을 제기했다.
그들은 "단순한 전체 성공률이 아니라 더 세부적인 데이터를 분석해야 한다"고 주장했다.**

> **-A 의사의 실력이 실제로 B 의사보다 별로라고 결론짓는 것이 타당한가?   
-그렇지 않다면, 추가로 확인해야 할 정보는 무엇인가?**

<!--심슨의 역설을 이해하였는지 확인하기 위한 문제입니다-->

<!--학습한 개념을 활용하여 자유롭게 설명해 보세요. 구체적인 예시를 들어 설명하면 더욱 좋습니다.-->

```
1. 타당하지 않다. 
2. 추가로 확인해 보아야 할 상황은 다음과 같다.
 - A의사와 B의사의 수술 횟수. A의사는 노련한 의사여서 많은 수술을 담당했고, 그 과정에서 성공률이 평균에 수렴하였는데, B는 신입 의사라 10건의 수술만을 담당하여 그 중 9개를 성공한 것일 수 있다. 
 - 수술 세부 분야. A의사는 수술 성공률이 낮은 세부 분야의 수술을 더 맡아서 평균적인 성공률이 낮고, B의사는 수술 성공률이 높은 분야의 수술을 더 많이 맡아서 평균적인 성공률이 높을 수 있다. 따라서, 세부 분야 별로 더 자세한 성공률을 확인해 보아야 한다.
```

### 🎉 수고하셨습니다.