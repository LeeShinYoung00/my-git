# 🖥️요약
쇼핑몰 데이터를 활용하여 분석을 진행하였다. 
먼저, 전체 매출액을 기준으로 상위 3개 그룹인 다우기술, 지니, 천재 태블릿을 대상으로 RFM 분석을 실시하였다. R, F, M 분석에서 모두 다우테크가 가장 높은 값을 보였고, 지니와 천재 태블릿이 그 뒤를 이었다. 이를 바탕으로 입점 기업별 판매 전략 수립을 세울 수 있다. 다음으로, 월별 매출액은 3, 5, 10월이 높게 나타났고, 연도별 매출액은 2019년부터 2022년까지 꾸준히 증가하였다. 이를 통해 월별, 연도별 판매 전략을 수립할 수 있다. 마지막으로, 결제방법과 결제금액의 연관성을 분석한 결과, 신용 거래가 현금 거래보다 거래액이 높음을 확인하였다.
본 분석 결과는 지니마켓의 마케팅 전략을 수립하는 근거로 활용될 수 있을 것이다.

# ❓연구질문
필수분석
1. 입점 기업별 RFM 분석(3그룹)
2. 매출 시각화
- 월별, 연도별 매출
- 월별 순수익 (처리 상황, 할부기간 고려)
3. 결제방법에 따른 분석
- 결제방법과 결제금액의 연관성 분석
- 결제방법은 맨 앞의 한가지만 사용한 것으로 간주

# 👩‍🔬[필수-3]에 대한 연구가설
가설: 신용 거래가 현금 거래보다 거래금액이 클 것이다.

귀무가설(H0): 신용 거래와 현금 거래의 거래금액은 같거나 차이가 없다.

대립가설(H1): 신용 거래의 평균 거래금액은 현금 거래의 평균 거래금액보다 크다.

# ✏️연구방법
## 1.	데이터 수집 방법
본 연구는 천재교육의 ‘프로젝트 기반 빅데이터 서비스 개발자 양성 과정’에서 본사로부터 제공 받은 ‘미니프로젝트-쇼핑몰 실습데이터.xlsx’ 데이터를 활용하였다.
## 2.	조사 방법 및 사용된 통계적 방법
### 가. 전처리

업체명, 상품명, 결제방법 열에서 결측치가 있는 행을 삭제하였다. 업체명 열의 ‘지니’, ‘지니 태블릿’, ‘지니 태블릿(후불집행)’은 같은 업체이므로 업체명을 ‘지니’로 통일하였다. 주문 수량과 판매금액 열의 값이 0인 경우, 해당 행을 삭제하였다. 제작 문구 내역 열은 분석 관련 내용이 없고 대부분이 결측치이므로 삭제하였다. 할부기간 열의 필드값이 없는 부분은 일시불 결제로 판단하고 ‘일시불’로 채웠다. 여러 결제방법이 사용된 경우, 첫 번째 결제방법만 사용한 것으로 간주하였다.

### 나. 입점 기업별 RFM 분석(3그룹)

총 89개의 입점 기업명을 기준으로 분류하고 이 중 총 판매금액이 가장 큰 3개의 입점 기업을 대상으로 RFM 분석을 진행하였다. R분석은 주문일자를 기준으로 2022년, 2021년, 2019~2020년으로 나누어 각 3점, 2점, 1점을 부여하여 계산하였다. F분석은 주문량 100이상, 50이상, 50미만으로 나누어 각 3점, 2점, 1점을 부여하여 계산하였다. M분석은 지출 금액 분포 75% 이상, 50% 이상, 50% 미만으로 나누어 각 3점, 2점, 1점을 부여하여 계산하였다.

### 다. 매출 시각화
1) 월별, 연도별 매출
주문일자를 각각 월별, 연도별로 추출하여 월과 연도를 기준으로 그룹화한 판매금액을 계산하였다.
2) 월별 순수익(처리 상황, 할부기간 고려)
‘처리상태’가 ‘구매확정’인 행의 판매금액만을 고려하여 순수익을 계산하였다. 이때, ‘할부기간’ 열의 값인 ‘일시불’, ‘1개월’, ‘6개월’, ‘12개월’, ‘18개월’, ‘24개월’를 고려하여 매월 순수익에 포함하여 계산하였다.

### 라. 결제방법에 따른 분석: 결제방법과 결제금액의 연관성 분석

결제방법은 맨 앞의 한 가지만 사용한 것으로 간주하였다. 신용카드, 정기결제, 후불을 신용 거래로 분류하고 웰컴마일, 포인트, 현금간편결제, 적립금, 가상계좌는 현금 거래로 분류하여 결제방법별 결제금액을 시각화 하였다. 검정 방법으로는 Mann-Whitney U Test를 사용하였다.

# 📖결과
## 1. 결과 요약

### 가.	입점 기업별 RFM 분석(3그룹)

총 매출액이 가장 큰 상위 세 그룹인 다우기술, 지니, 천재 태블릿에 대한 RFM 분석을 진행하였다. R, F, M 분석 결과 모두 다우기술이 50% 넘는 큰 값을 보였고 지니와 천재 태블릿이 그 뒤를 이었다. 이를 통해 다우기술, 지니, 천재 태블릿 순으로 최근에, 자주, 많이 판매하였음을 확인하였다.
이 결과를 바탕으로 세 그룹을 기준으로 하면 충성 고객인 다우기술에 큰 혜택을 부여하고, 지니에는 혜택과 동시에 촉진 전략을 수행하고, 큰 차이로 3순위에 위치했던 천재 태블릿에는 큰 촉진 전략을 진행할 수 있다.

### 나.	매출 시각화
1)	월별, 연도별 매출
월별로는 3월이 가장 큰 매출을 기록하였고, 다음으로 5월과 10월이 높은 매출을 보였다. 연도별로는 2019년부터 2022년까지 꾸준한 매출 상승 추세를 보였다.
매출이 급증하는 3, 5, 10월에는 많이 판매되는 상품의 프로모션을 진행하여 고객들이 다른 상품과 함께 구매할 수 있도록 유도하고, 매출이 높지 않은 월에는 꾸준히 판매되는 상품에 대한 프로모션을 진행할 수 있다. 연도별로는 매출 상승 추세를 보이고 있으나, 추후 성장이 지체될 수 있음을 고려하여 마케팅 전략을 세워야 한다. 
2)	월별 순수익 (처리 상황, 할부기간 고려)
처리 상황이 ‘구매 확정’된 행만을 대상으로 일시불, 1개월, 6개월, 12개월, 18개월, 24개월의 할부 기간을 계산하여 월별 순수익을 계산하였다. 그 결과, 10월의 할부 결제가 가장 많아 매출이 큰 폭으로 낮아졌음을 확인하였다. 이는 다음 해를 준비하며 금액이 높은 물품을 구매하면서 할부를 많이 진행했음을 유추해 볼 수 있다.

### 다.	결제방법에 따른 분석: 결제방법과 결제금액의 연관성 분석

신용 거래와 현금 거래의 결제금액 차이를 확인하기 위해 Scatterplot으로 시각화 하였다. 신용 거래는 매출 분포가 넓게 퍼져 있는 반면, 현금 거래는 낮은 금액에 몰려 있는 양상을 보였다. 
데이터 정규화를 위해 판매금액을 로그 스케일 변환했을 때 정규분포 형태가 아님을 확인하였다. 정규분포가 아니기 때문에 Mann-Whitney U Test를 진행하였고 P-value가 9.121e-07라는 작은 값으로 나타나 신용 거래와 현금 거래 간 판매금액 차이는 통계적으로 유의미함을 확인하였다. 

## 2. 한계점
본 분석의 한계는 다음과 같다. 
먼저, RFM 분석 자체의 한계가 있다. RFM 분석은 다양한 시사점을 제공하지만 R, F, M을 기준으로 분류하는 것 외에는 정해진 것이 없기 때문에 실제 서비스에 적용하기 위해서는 추가 분석이 필요하다.
다음으로 데이터로 인한 한계가 있다. ‘할부기간’을 일시불, 1개월, 6개월, 12개월, 18개월, 24개월로 구분하여 분석을 진행하였으나 1개월 할부는 일시불로 취급하는 경우도 있기 때문에 분류에서의 모호함이 있었다. 1개월을 일시불과 같다고 보고 분석을 진행하면 결과가 달라지므로 이 부분을 명확히 할 필요가 있다.
마지막으로, 선택 분석 미실시로 인한 한계가 있다. 선택 분석을 진행하면 최대 매출 상품 세 종류 집계, 주문 연도에 따른 해당 상품의 매출 증감 분석, 주문한 달과 판매금액의 상관관계 분석을 진행하였을 것이다. 그러나 시간 부족으로 선택 분석을 진행하지 못했고, 필수 분석 결과를 기반으로 시사점을 도출할 때 한계가 있었다.

## 3. 제언
본 분석은 천재교육의 ‘프로젝트 기반 빅데이터 서비스 개발자 양성 과정’에서 본사로부터 제공 받은 ‘미니프로젝트-쇼핑몰 실습데이터.xlsx’ 데이터를 활용하였다. 이 보고서는 다음의 경우 전략 수립의 근거로 활용 가능할 것으로 기대한다.
먼저, 입점 기업별 RFM 분석을 토대로 전략을 수립할 수 있다. 다음으로 매출 시각화 결과를 통한 전략을 수립할 수 있다. 마지막으로 신용 거래와 현금 거래 간 판매금액 차이를 바탕으로 신용 거래 활성화 전략과 현금 거래 유도 전략을 필요에 맞게 진행할 수 있다.
