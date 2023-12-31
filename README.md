# stock_er


# Assumption
  - IPO 이후 상장 폐지가 되지 않는다면 2년 뒤에는 무조건 수익이 나고 있을 것이다 (IPO ETF 참고)
  - IPO 종목들의 수익률은 상장 당시 시가총액 or 상장 가격과 정비례할 것이다.

# Potential Approach
  - 상장 후 n일 동안 가격 및 거래량 변화 + financial statement 정보 기반으로 매수 타이밍 예측
  - 1.과 동일한 컨셉으로 clustering 혹은 pair trading 구성
    
# Current Consideration

    
  쿼터 마지막 날짜는 주말끼는거 생각해서 다시 조정해야함 
  매달 가격으로 그냥 분석하는것도 괜찮아 보임 
  
  1. 19년도부터 지금까지 생존한 친구들
  2. 1년 매달 혹은 분기별 마지막날 가격, 볼륨 추출 3년치     -> 구간별 가격 변동폭도 사용 가능할듯? 
  3. 그걸로 multiple regression으로 distribution 만들어서 1차 예측 
  4. 분명히 IPO 달력인데, 차트로 보면 예전부터 가격대가 있는애들은 private 이었다가 올라온건가?

  
# Dongwoo
  - Profile에 있는 정보 one-hot 가지고 예측모델 만들어보려고함 
  - 예측모델은 multiple regression으로 distribution 예측모델로 만들고 mean + std 했을때 최저가 기준으로 주가 상승률 예측해보려고 함 (아니면 그냥 point estimate로 해도 좋을듯)
  - 지금은 19년도부터 22년도까지 모든 데이터가 있는애들만 생존 시켜놨는데 좀더 세밀한 분석이 필요함
  - 우리가 원하는건 (일단) 4가지 케이스 인것 같음
    1. 언제 사야 하는지
    2. 언제 뺴야 하는지 (폭락 방지선)
    3. 언제 팔아도 되는지 (이쯤이면 그냥 정리각)
    4. 누굴 사야 하는지
  - 지금 지표를 가지고 (feature 몇개 더 넣어서) 머신러닝까지 한번 쭉 만들어 보고 그리고 처음부터 3년후까지의 임의의 t에 대해서 세부분석 필요해 보임
  - 절대적인 시간 말고 IPO listing후 주식시작 몇일후에 가격변동으로 틀어도 좋다고 생각함
  - 그리고 그렇게 애들 나열해놓고 clustering 해도 좋은데
  - 하나 유의할 점은, 국제 정세나 그 절대적 시간대에는 모든 주식이 영향을 받음 (ex. 코로나, 우크라이나-러 전쟁)

# SeungJae
  - 위에 언급된 세밀한 분석을 진행할 예정 -> 모델링 하기 전에
    1. 언제 사야 하는지? 예를 들면
      1) 거래량이 받쳐 주면서 주가가 상승하는 경우 -> 거래량 및 상승폭 or 추세에 대한 베이스라인 파악
      2) 차트 및 지표 비교? -> 클래식하게 7일 이평선이 60일 이평선을 돌파하는 경우 등등
      3) 상장 직후라 정보가 부족하겠지만, 그럼에도 재무제표 확인 -> 매출, 이익, 현금 보유 등

# Meeting Minutes
## July 9th
-  IPO에 없는애들은 merger로 한애들임, 이거 고려해야됌
-  Features: 나라, 섹터,  volume, income statement
-  Cohort analysis
-  ~~동우: Master Table 만들기~~ -> 수정은 필요할수도 있음?
-  ~~승재: IPO csv 만들기~~
  > new IPO Calendar: `./IPO/ipo_calendar.csv` updated on Jul 10, 2023 (Data source: [Investing.com](https://kr.investing.com/ipo-calendar/))
-  추가적으로 더 시간나면 하기.

-  예측모델은 multiple regression으로 distribution 예측하고 -> MCS로 close price 예측하기


## 다음미팅 
-  master table 가지고 연구해볼게 많은것 같음
-  현재 performance 분석은 단순계산이므로, 테이블 가지고 공부하면 괜찮은 지표가 나올거 같음
-  그냥 평균값, 중간값으로 볼땐 당장 상장주식 사서 행복회로 돌리고 싶음 ㅇㅇ 
