
### 숙제 1  : WEEK5 수업 과정 따라하기
- 트랜젝션 ( Transaction ) 실습 따라하기
- Name Gender 실습 따라하기
  - 스키마를 자신의 스키마로 꼭 변경하기
  
  
### 숙제 2 : Weather_Forecast DAG 구현해보기 
- 앞서 설명한 Open Weather DAG 를 실제로 구현하기
   - full refresh 형태로 구현해보기. -> incremental update 로 바꿔보기 (옵션)
   - api key는 어디에 저장해야할까?
   - dw상의 테이블은 아래처럼 정의


```sql
crate table 스키마.weather_forcast(
    date date primary key
    temp float
    min_temp float
    max_temp float
    created_date timestamp default GETDATE(). # 이 필드를 통해서, 중복처리를 해줄것 
    );
```

- API를 json 형태로 가져오기

```python
f = requests.get(link)
f_js = f.json()
```

- datetime변경
```python
datetime
```

 ### 숙제 3 : airflow 환경 설정 변경
 1. airflow 환경 설정이 들어있는 파일이름은? airflow.cfg
 2. 이 파일에서 airflow 를 api 형태로 외부에서 조작하고 싶다면 어느 섹션을 변경해야하는가?
   - api 색션의 auth_backend를 airflow.api.auth.backend.basic_auth로 변경
 3. variable 에서 변수의 값이 encrypted 가 되려면, 변수의 이름에 어떤 단어들이 들어가야 하는데 , 이단어들은 무엇인가?
   - password , token, secret, passwd, authorization, api_key, apikey, access_token
 4. 이 환경 설정 파일이 수정되었다면, 이를 실제로 반영하기 위해서 해야하는 일은?
   - sudo systemctl restart airflow-webserver
   - sudo systemctl restart ariflow-scheduler
 5. dags 폴더에 새로운 dag를 만들면, 언제 실제로 airflow시스템에서 이를 알게 되나? 이 스캔 주기를 결정해주는 키의 이름이 무엇인가?
  - dat_dir_list-interval
 
