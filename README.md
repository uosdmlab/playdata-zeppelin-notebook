# Zeppelin 노트북: 화재 뉴스 기사 분류
> 2016년 10월 14일 (금) **데이터야놀자**의 세션 **Spark와 Zeppelin을 활용한 머신러닝 실전 적용기** 발표에 사용된 노트북입니다.

본 노트북은 총 1326건의 뉴스 기사들을 Spark ML을 활용해 주제가 화재인 것과 아닌 것들로 나누는 **text binary classification** 예제입니다. 아래의 ZeppelinHub Viewer 링크들을 통해 노트들을 미리 보실 수 있습니다.

## 미리 보기: ZeppelinHub Viewer

[전체 목록](https://www.zeppelinhub.com/viewer/search?q=playdata) (총 13개의 노트)

- [0.ZeppelinSetting](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS80ZjFjMGIyNGE3M2U0MTRiOGMwNWM0NmM2OGE4Y2JhYy9ub3RlLmpzb24)
- 1.Preprocessing
  - [1.DownloadDataset](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS9kMTYyYzlmNjgyYjk0N2U3ODM5YjIyNGZjZDA1NzBmNS9ub3RlLmpzb24)
  - [2.LabelingID](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS81ZDgzNWZhMmZmNmE0NzQ1ODk4YzFkNjQ4YzQ2YjhhMC9ub3RlLmpzb24)
  - [3.WordExtraction](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS8xZTc2MWRmYTE4NGU0NDhiODg0OWVmY2JlYjc0NTY5Ny9ub3RlLmpzb24)
  - [4.WordSelection](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS82ZjA0NjI2NTJmNWM0NWUyOGFjYTJlN2ViNjcxN2QyNi9ub3RlLmpzb24)
- 2.Featurize
  - [1.TF](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS82YTdhZjhhNTBkODY0NTFhODEwZDIzYjJkN2VjNmFmZS9ub3RlLmpzb24)
  - [2.IDF](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS9kNGQyYWZiYmJjNDE0MjNiOTY5ZGE4NTQ5NDA3MDI1NS9ub3RlLmpzb24)
- 3.Training
  - [1.NaiveBayesTF](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS9lNmY3NDY0MWE5YTg0ZDJkOTFlNDI2NmRlZjIwMTYxYi9ub3RlLmpzb24)
  - [2.NaiveBayesTFIDF](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS81NzBlNDc3NTY1ZDA0MWRkYjQzZmRmN2U3MDU4N2VmZS9ub3RlLmpzb24)
- 4.Evaluation
  - [1.Accuracy](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS8zNmI1OGFkZDkxYWY0ZDQyOTU2ZDFhMWFmNjI2NmJmNS9ub3RlLmpzb24)
  - [2.All](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS9hZjA1NjUwMDdmYTE0NDJkOWMxOTI0M2E5MzBhZWNkNC9ub3RlLmpzb24)
- [5.ExploratoryDataAnalysis](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS9hMjU0MzIzZjY1YjU0MmU0OTg3YWVkMmE0YzYzZGQyZS9ub3RlLmpzb24)
- [6.TuningResult](https://www.zeppelinhub.com/viewer/notebooks/bm90ZTovL2p1bi9wbGF5ZGF0YS80YTdkNWE4ZmE5NzU0OGY3YTQzZThiYjljZTU0OGI0Yy9ub3RlLmpzb24)

## 사용법
> Zeppelin은 설치하셨다고 가정합니다 ㅎㅎ

### 1. 노트북 추가하기
저장소를 원하는 곳에 복제합니다.

```bash
git clone git@github.com:uosdmlab/playdata-zeppelin-notebook.git
```

#### 방법1. 노트북 복사
복제한 저장소의 `notebook` 디렉터리 안의 내용물들을 `$ZEPPELIN_HOME/notebook/` 밑으로 복사

#### 방법2. 노트북 폴더 설정
> 기존에 사용하던 노트들과 저장소의 노트들이 섞이는 것이 싫다면 추천하는 방법!

`$ZEPPELIN_HOME/conf/zeppelin-env.sh` 파일을 열어 다음과 같은 라인 추가.

```bash
export ZEPPELIN_NOTEBOOK_DIR="<저장소경로>/notebook"
```

추가 후 Zeppelin을 재시작합니다.

```bash
$ZEPPELIN_HOME/bin/zeppelin-daemon.sh restart
```

다시 원래 노트들을 사용하려면 `$ZEPPELIN_HOME/conf/zeppelin-env.sh`에 추가한 라인을 지우거나 주석처리하고 Zeppelin을 재실행하시면 됩니다.

### 2. Dependency 추가
한국어 형태소 분석기 [spark-nkp](https://github.com/uosdmlab/spark-nkp)을 사용하기 위해 Spark interpreter dependency에 다음과 같이 추가해주세요.

**artifact** `com.github.uosdmlab:spark-nkp_2.11:0.2.1`

### Issue
GitHub issue로 올려주셔도 되고(한국어 가능), 아래 주소로 메일주셔도 됩니다.

김태준(i2r.jun@gmail.com)

[Data Mining Lab, University of Seoul](datamining.uos.ac.kr)
