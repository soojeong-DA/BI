# Day5 Map
## 5-1. 일별 평균 승하차 승객수 (2호선)
- 내 출퇴근 길에 항상 사람이 붐비는 강남.. 강남이 가장 사람이 많을까? 
<img src="./image/01. 일별 평균 승하차 승객수 with subway map.png" width="600" height="350">

- custom map
	- image size로 x, y 축 범위 설정
	- x: 0 ~ 2040
	- y: - ~ 1654
- 매개변수 목록 형태 생성 (측정값 선택) 후, 계산된 필드 생성 -> 색상, 크기에 할당
	- ```Tableau
		IF [측정값 선택] = '평균 승차총승객수' THEN AVG([승차총승객수])
		ELSEIF [측정값 선택] = '평균 하차총승객수' THEN AVG([하차총승객수])
		END
	  ```
- 역명을 상세정보에 할당하여 2호선 역별로 표시되게!     
-> 강남의 평균 승하차승객수가 가장 많은 것으로 보임


## 5-2. Flight Path Map
<img src="./image/02. airport path map.png" width="600" height="350">

- MakePoint
	- ```Tableau
		MAKEPOINT([Latitude (Arrival)],[Longitude (Arrival)]) # arrival
		MAKEPOINT([Latitude (Departure)], [Longitude (Departure)]) # departure
	  ```
- MakeLine
	- ```Tableau
		MAKELINE([Arrival],[Departure]) # 시작, 끝 점 연결하는 line
	  ```
- flight path, arriving airport 세부 정보에 할당!


## 5-3. Buffer를 이용한 공간 분석
<img src="./image/03. buffer를 이용한 공간분석.png" width="600" height="350">

- 거리 선택 매개변수 생성 (범위)
- Buffer
	- 점을 중심으로 지정된 거리의 버퍼를 반환
	- ```Tableau
		BUFFER(MAKEPOIN([Latitude], [Longitude]), [거리 선택], 'm') # 'km'..
	  ```
	- 생성된 계산된 필드를 세부 정보에 할당
- 시군구 필터 시 '데이터베이스틔 모든 값'이 아닌, '관련된 값만' 선택
	- 모든 시군구가 목록에 나올 필요가 없고, 서울시의 시군구만 나오면 됨
- 상표 정보 색상, 라벨에 할당
