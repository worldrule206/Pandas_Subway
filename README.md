## Pandas Database 활용
---
- Pandas를 사용하여 데이터프레임 생성, 접근, 수정, 삭제를 할 수 있다.
- 데이터프레임(Frame) : 행(Index), 열(Columns)로 구성되어 있다.


## Pandas 명령어 정리.
---

```python
    # 통계청에서 2019년도 지하철 이용객 데이터베이스를 사용.
    # pd.read_excel : Excel 파일 불러오기
    # Excel을 읽고 DataFrame에 저장, header를 사용하여 Excel의 1번째 행부터 읽는다. (header의 기본값 '0'번째 행)
    DataFrame = pd.read_excel('./2019_Seoul_Train.xlsx', header = 1)
```
```python
    # 상위 5개의 Index, DataFrame 출력.
    DataFrame.head() 
```
```python
    # DataFrame의 '역번호'열이 '222'인 값만 GangNamStation에 저장.
    GangNamStation = DataFrame[DataFrame['역번호'] == 222]

    # 저장되어 있는값 확인.
    GangNamStation.head()
    GangNamStation

    # '날짜' column의 DateTpye을 변경. (int, str => dtype: datetime64[ns]) 
    pd.to_datetime(GangNamStation['날짜'])
   
    # 강남역의 데이터의 월값을 추출.
    GangNam_M = GangNamStation['날짜'].dt.month
    
    # 강남역 1월 데이터 
    GangNam_M1 = GangNam_M[GNdt == 1]
    # 1월 데이터 확인.
    GangNam_M1

    # 날짜와 합계 데이터만 남기고 나머지 열 Drop
    # axis=0은 "각 열의 모든 행"에 적용, axis=1은 "각 행의 모든 열"에 적용.
    GangNam_M1 = drop(GangNam_M1.columns[range(1,25),], axis=1)
```
