# Zeppelin 노트북: 화재 뉴스 기사 분류
> 2016년 10월 14일 (금) **데이터야놀자**의 세션 **Spark와 Zeppelin을 활용한 머신러닝 실전 적용기** 발표에 사용된 노트북입니다.

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
GitHub issue로 올려주셔도 되고, 아래 주소로 메일주셔도 됩니다.

김태준(i2r.jun@gmail.com)

[Data Mining Lab, University of Seoul](datamining.uos.ac.kr)
