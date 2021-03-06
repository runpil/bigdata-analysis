## Part 02. 빅데이터 탐색

데이터 관련 정의
- 데이터(Data) : 이론을 세우는 기초가 되는 사실 또는 자료를 지칭, 컴퓨터와 연관되어 프로그램을 운영할 수 있는 형태로 기호화·수치화한 자료
- 단위(Unit) : 관찰 되는 항목 또는 대상을 지칭
- 관측값(Observation) : 각 조사 단위별 기록정보 또는 특성
- 변수(Variable) : 각 단위에서 측정된 특성 결과
- 원자료(Raw Data) : 표본에서 조사된 최초의 자료

데이터의 종류
- 단변량자료(Univariate Data) : 자료의 특성을 대표하는 특성 변수가 하나인 자료
- 다변량자료(Multivariate Data) : 자료의 특성을 대표하는 특성 변수가 두 가지 이상인 자료
- 질적자료(Qualitative Data) : 정성적 자료라고도 하며 자료를 범주의 형태로 분류한다. 분류의 편의상 부여된 수치의 크기자체에는 의미를 부여하지 않는 자료이며 명목자료, 서열자료 등 이질적자료로 분류된다.
  - 명목자료(Nominal Data) : 측정대상이 범주나 종류에 대해 구분되어지는 것을 수치 또는 기호로 분류되는 자료
    - ex) 전화번호상의 국번·지역번호
  - 서열자료(Ordinal Data) : 명목자료와 비슷하나 수치나 기호로 서열을 나타내는 자료
    - ex) 기록경기의 순위 등 일반적은 순위를 나타내는 대부분의 자료를 지칭
- 수치자료(Quantitative Data) : 수치의 크기에 의미를 부여할 수 있는 자료를 나타내며 구간자료, 비율자료가 여기에 속한다.
  - 구간자료(Interval Data) : 명목자료, 서열자료의 의미를 포함하면서 숫자로 표현된 변수에 대해서 변수 간의 관계가 산술적인 의미를 가지는 자료
    - ex) 온도
  - 비율자료(Ratio Data) : 명목자료, 서열자료, 구간자료의 의미를 다 가지는 자료로서 수치화된 변수에 비율의 개념을 도입할 수 있는 자료
    - ex) 무게
  - 시계열자료(Time Series Data) : 일정한 시간간격 동안에 수집된 자료
    - ex) 일별 주식 가격
  - 횡적자료(Cross Sectional Data) : 횡단면자료라고도 하며 특정 단일시점에서 여러 대상으로부터 수집된 자료. 즉 한 개의 시점에서 여러 대상으로부터 취합하는 자료
  - 종적자료(Longitudianl Data) : 시계열자료와 횡적자료의 결합으로 여러 개체를 여러 시점에서 수집한 자료
  
결측 데이터의 종류
- 완전 무작위 결측(MCAR: Missing Completely At Random) : 어떤 변수상에서 결측 데이터가 관측된 혹은 관측되지 않는 다른 변수와 아무런 연관이 없는 경우
- 무작위 결측(MAR: Missing At Random) : 변수상의 결측데이터가 관측된 다른 변수와 연관되어 있지만 그 자체가 비관측값들과는 연관되지 않은 경우
- 비 무작위 결측(NMAR: Not Missing At Random) : 어떤 변수의 결측 데이터가 완전 무작위 결측(MCAR) 또는 무작위 결측(MAR)이 아닌 결측데이터로 정의하는 즉, 결측변수값이 결측여부(이유)와 관련이 있는 경우
  - ex) 지역 가구소득 조사 시 소득이 적은 가구에 대한 소득값 결측이 쉽다(소득이 적은 가구는 소득을 밝히기 싫어함을 가정)
  
단순 대치법(Simple Imputation)
- 기본적으로 결측치에 대하여 MCAR 또는 MAR로 판단하고 이에 대한 처리를 하는 방법
- Completes Analysis : 불완전 자료는 완전하게 무시하고 분석을 수행한다. 분석의 용이성을 보장하나 효율성 상실과 통계적 추론의 타당성에 문제발생 가능성이 있다.
- 평균 대치법(Mean Imputation) : 관측 또는 실험으로 얻어진 데이터의 평균으로 결측치를 대치해서 사용. 평균에 의한 대치는 효율성의 향상 측면에서는 장점이 있으나 통계량의 표준오차가 과소 추정되는 단점이 있다. 비조건부 평균 대치법이라고도 한다.
- 회귀 대치법(Regression Imputation) : 회귀분석(regression)에 의한 결측치를 대치하는 방법으로 조건부 평균 대치법이라고도 한다.
- 단순확률 대치법(Single Stochastic Imputation) : 평균대치법에서 추정량 표준오차의 과소 추정을 보완하는 대치법으로 Hot-deck 방법이라고도 한다. 확률추출에 의해서 전체 데이터 중 무작위로 대치하는 방법이다.
- 최근방 대치법(Nearest-Neighbor Imputation) : 전체표본을 몇 개의 대체군으로 분류하여 각 층에서의 응답자료를 순서대로 정리한 후 결측값 바로 이전의 응답을 결측치로 대치한다. 응답값이 여러 번 사용될 가능성이 단점이다.

변수의 선택 방법
- 전진 선택법(Forward Selection)
  - 영 모형에서 시작, 모든 독립변수 중 종속변수와 단순상관계수의 절댓값이 가장 큰 변수를 분석모형에 포함시키는 것을 말한다.
  - 부분 F 검정(F test)를 통해 유의성 검증을 시행, 유의한 경우는 가장 큰 F 통계량을 가지는 모형을 선택하고 유의하지 않은 경우는 변수선택 없이 과정을 중단한다.
  - 한번 추가된 변수는 제거하지 않는 것이 원칙이다.
- 후진 선택법(Backward Selection)
  - 전체모델에서 시작, 모든 독립변수 중 종속변수와 단순상관계수의 절댓값이 가장 작은 변수를 분석모형에서 제외시킨다.
  - 부분 F 검정을 통해 유의성 검증을 시행, 유의하지 않은 경우는 변수를 제거하고 유의한 경우는 변수제거 없이 과정을 중단한다.
  - 한번 제거된 변수는 추가하지 않는다.
- 단계적 선택법(Stepwise Selection)
  - 전진 선택법과 후진 선택법의 보완방법이다.
  - 전진 선택법을 통해 가장 유의한 변수를 모형에 포함 후 나머지변수들에 대해 후진 선택법을 적용하여 새롭게 유의하지 않은 변수를 제거한다.
  - 제거된 변수는 다시 모형에 포함하지 않으며 유의한 설명변수가 존재하지 않을 때까지 과정을 반복한다.