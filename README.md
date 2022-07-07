# Restaurant review adjustment
#식당 리뷰 별점 재조정
<div align="center">
    <img src="https://github.com/SeungVictor/restaurantreviewadjustment/blob/main/1.png" alt="Logo" width="300">
    <br>
    <h3 align="center">Sogang AIBI 2기 프랙티컴 경진대회 우등상 <캠퍼스봄날씨></h3>
</div>

## 캠퍼스봄날씨 팀원

| [박승](https://github.com/SeungVictor) | [배진성](baejinsung0126@gmail.com) | [빈준영](binjunyoung@u.sogang.ac.kr) | [안덕성](dsahn95@gmail.com) | [오성현](ffcf77@gmail.com) | [이재열](coramdeojy@gmail.com) |
| :---:|:---:|:---:|:---:|:---:|:---:|
<hr><br>

<a href="https://github.com/SeungVictor/restaurantreviewadjustment/blob/main/%ED%94%84%EB%9E%99%ED%8B%B0%EC%BB%B4_%EC%82%AC%EC%97%85%EA%B3%84%ED%9A%8D%EC%84%9C_%ED%95%A9%EB%B3%B8_%EC%B5%9C%EC%A2%85.pdf">제출본pdf
    </a>
    
 
    
## 개요
- 식당을 선택함에 있어 별점이나 리뷰를 참고하지만 리뷰내용과 실제 별점은 잘맞지 않는 경우가 많음 <br>
- 리뷰를 내용에 맞게 재조정하여 신뢰성 있는 별점 제공 및 별점 내용과 시간정보를 활용하여 소비자에게 유용한 대시보드 제공 <br>

## 개발과정
### 크롤링
- 합정, 이태원, 성수, 강남, 홍대 등 서울 주요플레이스에 대하여 네이버, 다음, 구글, 카카오등 총 17만개의 식당 리뷰 크롤링 <br>
### 사전구축
- 불용어사전 및 감성(긍부정)사전, 표제어사전을 구축 <br>
### 학습데이터 구축
- 리뷰데이터 17만건과 별도로 제작한 감성사전을 이용한 학습데이터 구축 <br>
1) 별점이 5개인 리뷰는 부정단어 모두삭제 <br>
2) 별점이 1개인 리뷰는 긍정단어 모두삭제 <br>
3) 별점 2~4점인 리뷰는 긍정,부정단어 비율에 맞춰 조정 <br>
### 학습
- KOBERT, ROBERT-Base, Small, Large 4가지 모델을 Ensemble, k-fold(n=5)로 학습 <br>
- 트레인셋 정확도 75%, 검증셋 70% <br>
### 시계열 데이터분석
- 최근 36개월간의 리뷰 및 데이터를 분석하여 최근 리뷰동향을 그래프로 시각화(plotly사용) <br>
### SNA 분석
- Python networkx패키지 사용 bi-gram, 가중치는 pagerankg적용, layout은 kamda_kawai적용하여 SNA시각화
### 대표리뷰 산정
- 식당의 긍정, 부정을 대표하는 리뷰를 선정하여 보여줌 <br>
- 2021년 이후, 표제어가 10개 이상, 전체 표제어 중 긍정,부정 단어 비중이 높은 리뷰를 선정하는 알고리즘 구현 <br>
### 파워랭킹 대시보드
- 리뷰의 수가 많고 최근(2021년 이후)의 평점이 지역의 평균보다 높은 곳을 선정하는 알고리즘을 구현하여 파워랭킹 대시보드 작성 <br>

