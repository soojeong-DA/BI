# Day2 워드클라우드와 박스플롯

## 2-1. 워드클라우드 - 칼로리가 높은 메뉴명
- 워드클라우드는 핵심 키워드 표현하는데 유용하고, 상세 비교보다는 트렌드를 나타날 때 사용 

<img src="https://user-images.githubusercontent.com/35002720/143890804-7927baa4-02ae-467f-9a97-168e6c93ccef.png" width="600" height="350">

- 텍스트에 메뉴명 드로그앤 드랍
- 제주 까망 크림 프라푸치노가 칼로리가 가장 높음


## 2-2. 카테고리별 칼로리 박스플롯
- 칼로리가 낮고 카페인이 높지 않은 메뉴를 마시고 싶다면?

<img src="https://user-images.githubusercontent.com/35002720/143890977-9dd302a9-7f6d-4adf-ab1f-87cdf1506e6e.png" width="600" height="350">

- 메뉴별 칼로리 포인트에 카페인 정도에 따른 색상 지정

## 2-3. 계산된 필드 생성 - 메뉴별 지정 카페인 용량 초과 여부

<img src="https://user-images.githubusercontent.com/35002720/143891105-78585633-0ca7-400b-9a54-ca3883cf7e43.png" width="600" height="350">

- 80mg 기준으로 계산된 필드 생성
- ```tableau
	IF AVG([카페인 (Mg)]) > 80
	THEN "카페인 > 80mg"
	ELSE "카페인 <= 80mg"
	END
  ```

## 2-4. 매장별 매장운영시간

<img src="https://user-images.githubusercontent.com/35002720/143891422-9530cb54-8f49-49ea-8884-781d48a667d9.png" width="600" height="350">

- 시도 필터 추가
- ```tableau
	# 시간 차이 계산하여 매장운영시간 구하기
	
	DATEDIFF('hour', [영업시작시간], [영업종료시간])
  ``` 