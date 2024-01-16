# 이어드림스쿨 -(주)예스스탁 국내주식 외국인 수급분석 프로젝트

<br>

## 팀원 구성
| 이름 | 파트 | 역할 |
|---|---|---|
박수영| **DE** | 프로젝트 총팀장 
반민성| **DE** | 팀원
권태하| **DS** | DS파트장 기획 LSTM모델 개발
한상진| **DS** | 팀원
조민재| **DS** | 팀원 


--- 
## DS프로젝트 개요
- 국내 주식 시장 큰 영향을 미치는 요인중 하나는 외국인 투자자입니다. 
- 외국인 투자자 들은 큰 자본을 운용하므로 실시간으로 주가의 상승 및 하락에 큰 영향을 미치게 됩니다. 
- KOSPI 증권 시장의 1체결량(Tick) 단위 데이터, 실시간 프로그램 매매 데이터, 상위 거래원 데이터를 사용
- 실시간으로 외국인 수급을 추정해보려 합니다.
- 최종 결과는 매일 장이 끝나고 18:00에 발표되는 공식 결과와 비교.
---
## 데이터셋
- (주) 예스스탁 제공
- 데이터 크기 : 3TB
- 2023년 2월부터 10월까지의 KOSPI 종목에 대해 한국거래소에서 제공하는 모든 데이터.
- 증권사 API에서 제공하는 긴 시계열(Tick 기준), 압축되지 않은 데이터, 서버에서 수신한Raw 데이터.

## 기술 스택
> DS
>> python, Tensorflow, Pytorch

> DE
>> ReactJS, Hadoop, spark, node, PostgerSQL, mongoDB

## DS프로젝트 진행
1. 프로젝트 범위 결정
2. EDA
3. 기존 문제 해결방법 탐색 및 전략 수립
4. 학습 모델 결정 및 트레이닝
5. 결론 및 성능평가 (테스트셋, 실제 장 적용)
6. 데모 제작
## DS프로젝트 세부 과정
### 데이터셋 분석 
- 하우투스탁 - 주식 기본 공부(https://howtostock.kiwoom.com/lecture/contents/1/1/0)
- 도메인 지식을 학습
### EDA 
- 상위TOP 거래량을 보이는 종목 5개~10개를 지정 데이터 범위 결정
### 기존 문제 해결 방안
- 논문과 다양한 블로그를 참조 기존 시계열 모델의 성능이 51% 이상 어렵움
- CNN은 주로 이미지 처리에 사용되는데, 이미지 데이터의 특성을 잘 활용하기 위해
- Convolutional Layer등을 사용합니다.
- 그래프 데이터의 특성에 따라 모델의 구조를 설계. 
### Combine
- 실시간 체결, 상위 거래원, 프로그램 매매 데이터를 하나의 데이터로 통합
- 행 길이를 100,000으로 고정
  
### Scaling
- 외국인의 현재 매수와 매도를 파악, 음수와 양수를 유지하는 것이 중요하다고 판단
- -1 ~ 1범위(음수, 양수, 0 값은 유지)
   
## 프로젝트 결과

### 1. LSTM모델
> 장마감 데이터만을 활용 : 60일을 입력 받아서 61째의 외국인 수급 예측
- Train data : 2004년1월 ~ 2020년 2월 (3,939 set)
- Test data : 2020년 3월 ~ 2023년 10월 (792 set)
- LSTM 평가지표 MAE : 0.1179

### 2. 이미지 학습 CNN모델
> 실시간 체결데이터, 상위거래원 데이터,프로그램 매매데이터를 하나의 데이터로 통합
- Train data : 2023년 1월 ~ 9월 (7,480 set)
- Test data : 2023년 10월 (792 set)
- CNN 평가지표 MAE : 0.01171 

## 프로젝트 회고
- 빅데이터를 정제하는과정에서 기존정보 손실이 발생.
- 고성능 하드웨어를 활용 학습속도를 향상 시키면 좋을 것 같다 
- 기간 대비 다양한 모델의 시도를 해보지 못한 부분이 매우 아쉽다.


