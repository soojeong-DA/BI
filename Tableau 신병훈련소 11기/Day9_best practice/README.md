# Day9 Best Practice

- 모범 사례에 설명된 원칙 요약
	1. 질문으로 시작하기
	2. 적합한 차트 유형 선택	
	3. 효과적인 뷰 만들기
	4. 총체적인 대시보드 디자인
	5. 작업을 완벽하게

## 9. Best Practice 적용 대시보드
- covid19 확진자 및 사망자 데이터로 생성한 대시보드
- 아래 질문에 대한 답을 구하기 위해 만들어짐
	- Q1. 국가별 확진자 및 사망자 수는 얼마나 되는가? 어느 나라가 더 많은가?
	- Q2. 지역(대륙)별 확진자 분포는 어떠하며, 어떤 특징을 보이는가?
	- Q3. 국가별 확진자는 증가세인가 감소세인가?

<img src="01. best practice.png" width="600" height="350">

- 국가별 확진자수 막대그래프에서 confirmed 대비 deaths값의 크기가 작아 제대로 표현되지 않음
	- 축 편집 > **각 행 또는 열에 독립적인 축 범위** 지정
- **영역차트와 라인차트 다른 사용성 이해**
	- 영역차트는 개별 국가의 숫자보다는 전체 합의 트렌드가 강조되는 차트 유형
- 관심 있는 몇 개 국가에만 색상 지정 action (나머지 기타 국가들은 회색으로)
	- Country Region으로 집합 생성
	- 계산된 필드 생성 (country color)
		- ```Tableau
			IF [관심 국가] THEN [Country Region] ELSE '기타' END
		  ```
	- 워크시트 > 동작 > 동작 추가 (집합 값 변경) > ...
- New Cases, Total Cases `측정값` 전환하며 볼 수 있게
	- 매개변수 (Select Metric) 생성 및 계산된 필드 생성
		- ```Tableau
			IF [Select Metric] = 1 THEN [Total Cases]
			ELSE [New Cases] END
		  ```
- 대시보드 필터 생성
	- '국가별 확진자수' 막대를 클릭하면, '일자별 확진자 및 사망자수'에 국가 필터가 적용되게
		- 필터 범위: 대상필터 > 선택한 필드 > Country Region
- 대시보드 하이라이터 생성
	- 툴바의 하이라이트 버튼에서 country region 선택
	