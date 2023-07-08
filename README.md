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
