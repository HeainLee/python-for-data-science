**스마트시티 분석모듈**

**오픈 API 명세서**

**Version 0.1**

Document Information

| **Project Name:**   | 스마트시티 국가전략프로젝트 사업 |                     |            |
|---------------------|----------------------------------|---------------------|------------|
| **Project Agency:** | 다음소프트                       | **Version Number:** | V 0.1      |
| **Project Manger:** | \-                               | **Version Date:**   | 2019.09.00 |
| **Auther:**         | 이혜인                           | **Written Date:**   | 2019.09.00 |
| **Reviewer:**       | \-                               | **Reviewed Date:**  | 2019.09.00 |

Document Distribution

| Copy Number | Name(Role, Title) | Date | Contact (Phone/email) |
|-------------|-------------------|------|-----------------------|
|             |                   |      |                       |
|             |                   |      |                       |
|             |                   |      |                       |
|             |                   |      |                       |

Revision History

| Version | Version Date | Author | Description |
|---------|--------------|--------|-------------|
| 0.1     | 2019.09.00   | 이혜인 | 초안 작성.  |
|         |              |        |             |
|         |              |        |             |
|         |              |        |             |
|         |              |        |             |
|         |              |        |             |
|         |              |        |             |
|         |              |        |             |

1.  **오픈 API 목록**

    1.  **API URI 맵**

| **기능구분**      | **HTTP 메서드** | **URI**                   | **출력포맷** | **설명**                                 |
|-------------------|-----------------|---------------------------|--------------|------------------------------------------|
| 알고리즘조회      | GET             | /algorithm                | json         | 분석 가능한 알고리즘 리스트 조회         |
|                   | GET             | /algorithm/{id}           | json         | 분석 가능한 알고리즘 개별 조회           |
| 파일조회          | GET             | /localFiles               | json         | 샌드박스 안의 로컬 파일 리스트 조회      |
| 원본데이터 관리   | GET             | /originalData             | json         | 데이터 원본 리스트 조회                  |
|                   | POST            | /originalData             | json         | 데이터 원본 설정                         |
|                   | GET             | /originalData/{id}        | json         | 데이터 원본 개별 조회                    |
|                   | PATCH           | ​/originalData​/{id}        | json         | 데이터 전처리 테스트                     |
|                   | DELETE          | /originalData/{id}        | json         | 데이터 원본 삭제                         |
| 전처리기능 조회   | GET             | /preprocessFunctions      | json         | 사용 가능한 전처리 기능 리스트 조회      |
|                   | GET             | ​/preprocessFunctions​/{id} | json         | 사용 가능한 전처리 기능 개별 조회        |
| 전처리데이터 관리 | GET             | /preprocessedData         | json         | 전처리된 데이터 리스트 조회              |
|                   | POST            | /preprocessedData         | json         | 전처리 데이터 생성                       |
|                   | GET             | /preprocessedData{id}     | json         | 전처리된 데이터 개별 조회                |
| 모델 관리         | GET             | /models                   | json         | 학습된 모델 리스트 조회                  |
|                   | POST            | /models                   | json         | 모델 생성                                |
|                   | GET             | /models/{id}              | json         | 학습된 모델 개별 조회                    |
|                   | PATCH           | /models/{id}              | json         | 모델 로드, 언로드, 학습중지 및 모델 적용 |
|                   | DELETE          | /models/{id}              | json         | 학습된 모델 삭제                         |
| 헬스체크          | GET             | /healthCheck              | json         | 헬스체크                                 |

2.  **오픈 API 명세**

    1.  **알고리즘 조회**

>   스마트시티 분석모듈에서 사용 가능한 알고리즘 조회 요청. 지원하는 알고리즘은
>   Scikit-learn, LigthGBM, Keras에서 지원하는 머신러닝/딥러닝 모델입니다.
>   현재는 Scikit-learn에서 지원하는 일부 알고리즘을 지원합니다.

1.  **요청 메시지 URL**

| **메서드** | **요청 URL**    | **출력 포맷** | **설명**                         |
|------------|-----------------|---------------|----------------------------------|
| GET        | /algorithm      | json          | 분석 가능한 알고리즘 리스트 조회 |
| GET        | /algorithm/{id} | json          | 분석 가능한 알고리즘 개별 조회   |

2.  **요청 변수**

    1.  **분석 가능한 알고리즘 리스트 조회**

>   해당없음.

1.  **분석 가능한 알고리즘 개별 조회**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                             |
|-----------------|----------|---------------|------------|--------------------------------------|
| Id              | Integer  | Y             |            | 개별 조회를 희망하는 알고리즘의 ID값 |

2.  **출력 결과**

    1.  **분석 가능한 알고리즘 리스트 조회**

| **필드**                     | **타입** | **설명**                 |
|------------------------------|----------|--------------------------|
| ALGORITHM_SEQUENCE_PK        | Integer  | 알고리즘번호             |
| ALGORTHM_NAME                | string   | 알고리즘이름             |
| LIBRARY_NAME                 | string   | 라이브러리이름           |
| LIBRARY_VERSION              | string   | 라이브러리버전           |
| LIBRARY_DOCUMENT_URL         | string   | 라이브러리문서URL        |
| LIBRARY_OBJECT_NAME          | string   | 라이브러리객체이름       |
| LIBRARY_FUNCTION_NAME        | string   | 라이브러리함수이름       |
| LIBRARY_FUNCTION_DESCRIPTION | string   | 라이브러리 함수설명      |
| LIBRARY_FUNCTION_USAGE       | string   | 라이브러리 함수 활용용도 |
| MODEL_PARAMETERS             | string   | 모델파라미터             |
| \--name                      | string   | 파라미터 이름            |
| \--default                   | string   | 파라미터 기본값          |
| \--type                      | string   | 파라미터 데이터 타입     |
| \--note                      | string   | 파라미터 설명            |
| TRAIN_PARAMETERS             | string   | 학습파라미터             |
| \--name                      | string   | 파라미터 이름            |
| \--default                   | string   | 파라미터 기본값          |
| \--type                      | string   | 파라미터 데이터 타입     |
| \--note                      | string   | 파라미터 설명            |
| SUPPORT_DATA_TYPE            | string   | 지원데이터종류           |
| CREATE_DATETIME              | Datetime | 생성일시                 |
| WRITER                       | string   | 작성자                   |
| USE_FLAG                     | Boolean  | 사용가능여부             |

3.  **분석 가능한 알고리즘 개별 조회**

| **필드**                     | **타입** | **설명**                 |
|------------------------------|----------|--------------------------|
| ALGORITHM_SEQUENCE_PK        | Integer  | 알고리즘번호             |
| ALGORTHM_NAME                | string   | 알고리즘이름             |
| LIBRARY_NAME                 | string   | 라이브러리이름           |
| LIBRARY_VERSION              | string   | 라이브러리버전           |
| LIBRARY_DOCUMENT_URL         | string   | 라이브러리문서URL        |
| LIBRARY_OBJECT_NAME          | string   | 라이브러리객체이름       |
| LIBRARY_FUNCTION_NAME        | string   | 라이브러리함수이름       |
| LIBRARY_FUNCTION_DESCRIPTION | string   | 라이브러리 함수설명      |
| LIBRARY_FUNCTION_USAGE       | string   | 라이브러리 함수 활용용도 |
| MODEL_PARAMETERS             | string   | 모델파라미터             |
| \--name                      | string   | 파라미터 이름            |
| \--default                   | string   | 파라미터 기본값          |
| \--type                      | string   | 파라미터 데이터 타입     |
| \--note                      | string   | 파라미터 설명            |
| TRAIN_PARAMETERS             | string   | 학습파라미터             |
| \--name                      | string   | 파라미터 이름            |
| \--default                   | string   | 파라미터 기본값          |
| \--type                      | string   | 파라미터 데이터 타입     |
| \--note                      | string   | 파라미터 설명            |
| SUPPORT_DATA_TYPE            | string   | 지원데이터종류           |
| CREATE_DATETIME              | Datetime | 생성일시                 |
| WRITER                       | string   | 작성자                   |
| USE_FLAG                     | Boolean  | 사용가능여부             |

4.  **에러코드**

| **HTTP 코드** | **에러 메시지** | **조치 방안**                |
|---------------|-----------------|------------------------------|
| 404           | Not Found       | 조회 가능한 id를 입력합니다. |

5.  **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 [ { "ALGORITHM_SEQUENCE_PK": 1, "ALGORITHM_NAME": "RandomForestRegressor", "LIBRARY_NAME": "sklearn", "LIBRARY_VERSION": "0.21.3", "LIBRARY_DOCUMENT_URL": "https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html", "LIBRARY_OBJECT_NAME": "ensemble", "LIBRARY_FUNCTION_NAME": "RandomForestRegressor", "LIBRARY_FUNCTION_DESCRIPTION": "A random forest classifier", "LIBRARY_FUNCTION_USAGE": "regression", "MODEL_PARAMETERS": “[ { "name": "n_estimators", "default": "warn", "type": "int", "note": "Tree의 수 " }, { "name": "criterion", "default": "mse", "type": "string", "note": "분할의 질을 측정하는 함수 " }, { "name": "max_depth", "default": "None", "type": "int", "note": "Tree의 최대 깊이 " }, { "name": "min_samples_split", "default": "2", "type": "int, float", "note": "내부 노드를 분할 하는데 필요한 최소 샘플 수 " }, ],” "TRAIN_PARAMETERS": “[ { "name": "X", "default": " ", "type": "array-like, sparse matrix", "note": "학습용 입력 데이터 [n_samples, n_features]" }, { "name": "y", "default": " ", "type": "array-like", "note": "대상 값 [n_samples], [n_samples, n_outputs]" }, { "name": "sample_weight", "default": "None", "type": "array-like", "note": "샘플의 가중치 [n_samples], None" } ],” "SUPPORT_DATA_TYPE": "numeric, string", "CREATE_DATETIME": "2019-09-06T09:59:24.962309+09:00", "WRITER": "daumsoft", "USE_FLAG": true } ] \* 실패할 경우 응답 예시 { "detail": "Not Found", "status_code": "404" } |

6.  **파일 조회**

>   샌드박스 내부의 특정 경로(../result)의 하위 디렉토리에서 파일 리스트를
>   조회합니다. 조회 가능한 파일 유형은 json과 csv입니다. .

1.  **요청 메시지 URL**

| **메서드** | **요청 URL** | **출력 포맷** | **설명**                            |
|------------|--------------|---------------|-------------------------------------|
| GET        | /localFiles  | json          | 샌드박스 안의 로컬 파일 리스트 조회 |

2.  **요청 변수**

>   해당 없음.

1.  **출력 결과**

| **필드**      | **타입** | **설명**                |
|---------------|----------|-------------------------|
| file_info_1   | string   | 조회된 파일 리스트 내역 |
| ALGORTHM_NAME | string   | 파일 이름               |
| LIBRARY_NAME  | string   | 파일 경로               |

2.  **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                  |
|-----------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 { "file_info_1": { "filename": "D_1.json", "path": "../result/original_data" } } |

3.  **원본데이터 관리**

>   모델 분석을 위한 원본 데이터를 관리합니다. 데이터 원본 생성, 조회, 삭제 및
>   전처리 테스트를 요청할 수 있습니다.

1.  **요청 메시지 URL**

| **메서드** | **요청 URL**       | **출력 포맷** | **설명**                |
|------------|--------------------|---------------|-------------------------|
| GET        | /originalData      | json          | 데이터 원본 리스트 조회 |
| POST       | /originalData      | json          | 데이터 원본 설정        |
| GET        | /originalData/{id} | json          | 데이터 원본 개별 조회   |
| PATCH      | ​/originalData​/{id} | json          | 데이터 전처리 테스트    |
| DELETE     | /originalData/{id} | json          | 데이터 원본 삭제        |

2.  **요청 변수**

    1.  **데이터 원본 리스트 조회**

>   해당없음.

1.  **데이터 원본 설정**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                  |
|-----------------|----------|---------------|------------|---------------------------|
| data_path       | string   | Y             |            | 원본 데이터를 가져올 경로 |

2.  **데이터 원본 개별 조회**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                              |
|-----------------|----------|---------------|------------|---------------------------------------|
| Id              | integer  | Y             |            | 개별 조회를 희망하는 원본데이터의ID값 |

3.  **데이터 전처리 테스트**

| **요청 변수명**                     | **타입** | **필수 여부** | **기본값** | **설명**                              |
|-------------------------------------|----------|---------------|------------|---------------------------------------|
| Id                                  | integer  | Y             |            | 전처리 테스트를 수행할 원본데이터의ID |
| request_dict                        | object   | Y             |            | 전처리 요청 정보                      |
| \--preprocess_functions_sequence_pk | Integer  | Y             |            | 전처리 기능 ID                        |
| \--field_name                       | string   | Y             |            | 전처리 수행할 컬럼명                  |
| \--condition                        | string   | N             |            | 변경할 전처리 기능의 알고리즘         |

4.  **데이터 원본 삭제**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                          |
|-----------------|----------|---------------|------------|-----------------------------------|
| Id              | integer  | Y             |            | 삭제를 희망하는 원본데이터의 ID값 |

5.  **출력 결과**

    1.  **데이터 원본 리스트 조회**

| **필드**                  | **타입** | **설명**            |
|---------------------------|----------|---------------------|
| ORIGINAL_DATA_SEQUENCE_PK | Integer  | 원본데이터번호      |
| NAME                      | string   | 원본데이터이름      |
| FILEPATH                  | string   | 파일경로            |
| FILENAME                  | string   | 파일이름            |
| EXTENTION                 | string   | 확장자              |
| CREATE_DATETIME           | string   | 생성일시            |
| DELETE_FLAG               | boolean  | 원본데이터 삭제여부 |

6.  **데이터 원본 설정**

| **필드**                  | **타입** | **설명**            |
|---------------------------|----------|---------------------|
| ORIGINAL_DATA_SEQUENCE_PK | Integer  | 원본데이터번호      |
| NAME                      | string   | 원본데이터이름      |
| FILEPATH                  | string   | 파일경로            |
| FILENAME                  | string   | 파일이름            |
| EXTENTION                 | string   | 확장자              |
| CREATE_DATETIME           | string   | 생성일시            |
| DELETE_FLAG               | boolean  | 원본데이터 삭제여부 |

7.  **데이터 원본 개별 조회**

| **필드**                  | **타입** | **설명**            |
|---------------------------|----------|---------------------|
| ORIGINAL_DATA_SEQUENCE_PK | Integer  | 원본데이터번호      |
| NAME                      | string   | 원본데이터이름      |
| FILEPATH                  | string   | 파일경로            |
| FILENAME                  | string   | 파일이름            |
| EXTENTION                 | string   | 확장자              |
| CREATE_DATETIME           | string   | 생성일시            |
| DELETE_FLAG               | boolean  | 원본데이터 삭제여부 |

8.  **데이터 전처리 테스트**

| **필드**    | **타입** | **설명**                    |
|-------------|----------|-----------------------------|
| field_name  | string   | 전처리 테스트 수행한 컬럼명 |
| test_result | list     | 전처리 테스트 수행 결과     |

9.  **데이터 원본 삭제**

| **필드**                  | **타입** | **설명**            |
|---------------------------|----------|---------------------|
| ORIGINAL_DATA_SEQUENCE_PK | Integer  | 원본데이터번호      |
| NAME                      | string   | 원본데이터이름      |
| FILEPATH                  | string   | 파일경로            |
| FILENAME                  | string   | 파일이름            |
| EXTENTION                 | string   | 확장자              |
| CREATE_DATETIME           | string   | 생성일시            |
| DELETE_FLAG               | boolean  | 원본데이터 삭제여부 |

10. **에러코드**

| **HTTP 코드** | **에러 메시지**    | **조치 방안**                                           |
|---------------|--------------------|---------------------------------------------------------|
| 400           | Bad Request        | 올바른request 메시지를 사용합니다.                      |
| 404           | Not Found          | 조회 가능한 id를 입력합니다.                            |
| 405           | Method Not Allowed | 파일 조회를 통해 데이터가 경로에 존재하는지 확인합니다. |

11. **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 { "ORIGINAL_DATA_SEQUENCE_PK": 1, "NAME": "parking_data", "FILEPATH": "result/original_data/D_1.json", "FILENAME": "D_1.json", "EXTENSION": "json", "CREATE_DATETIME": "2019-09-24T02:11:51Z", "DELETE_FLAG": false } \* 데이터 전처리 테스트 성공할 경우 응답 예시 [ { "field_name": "temperature", "test_result": [ "0.6035", "0.1206", "0.6897", "0.5862", "0.2586" ] }, { "field_name": "season", "test_result": [ "[0. 0. 1. 0.]", "[0. 0. 1. 0.]", "[0. 0. 1. 0.]", "[0. 0. 1. 0.]", "[1. 0. 0. 0.]" ] } ] |

12. **전처리기능 조회**

>   스마트시티 분석모듈에서 사용 가능한 전처리 기능 조회 요청. 지원하는
>   알고리즘은 Scikit-learn, LigthGBM, Keras에서 지원하는 전처리 기능입니다.
>   현재는 Scikit-learn에서 지원하는 일부 기능을 지원합니다.

1.  **요청 메시지 URL**

| **메서드** | **요청 URL**              | **출력 포맷** | **설명**                            |
|------------|---------------------------|---------------|-------------------------------------|
| GET        | /preprocessFunctions      | json          | 사용 가능한 전처리 기능 리스트 조회 |
| GET        | ​/preprocessFunctions​/{id} | json          | 사용 가능한 전처리 기능 개별 조회   |

2.  **요청 변수**

    1.  **사용 가능한 전처리 리스트 조회**

>   해당없음.

1.  **사용 가능한 전처리 개별 조회**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                                |
|-----------------|----------|---------------|------------|-----------------------------------------|
| Id              | Integer  | Y             |            | 개별 조회를 희망하는 전처리 기능의 ID값 |

2.  **출력 결과**

    1.  **사용 가능한 전처리 리스트 조회**

| **필드**                        | **타입** | **설명**                 |
|---------------------------------|----------|--------------------------|
| PREPROCESS_FUNCTION_SEQUENCE_PK | Integer  | 전처리함수사전번호       |
| PREPROCESS_FUNCTION_NAME        | string   | 전처리함수이름           |
| LIBRARY_NAME                    | string   | 라이브러리이름           |
| LIBRARY_VERSION                 | string   | 라이브러리버전           |
| LIBRARY_DOCUMENT_URL            | string   | 라이브러리문서URL        |
| LIBRARY_OBJECT_NAME             | string   | 라이브러리객체이름       |
| LIBRARY_FUNCTION_NAME           | string   | 라이브러리함수이름       |
| LIBRARY_FUNCTION_DESCRIPTION    | string   | 라이브러리 함수설명      |
| LIBRARY_FUNCTION_USAGE          | string   | 라이브러리 함수 활용용도 |
| PARAMETERS                      | string   | 파라미터                 |
| \--name                         | string   | 파라미터 이름            |
| \--default                      | string   | 파라미터 기본값          |
| \--type                         | string   | 파라미터 데이터 타입     |
| \--note                         | string   | 파라미터 설명            |
| SUPPORT_DATA_TYPE               | string   | 지원데이터종류           |
| CREATE_DATETIME                 | string   | 생성일시                 |
| WRITER                          | string   | 작성자                   |
| USE_FLAG                        | string   | 사용가능여부             |

3.  **사용 가능한 전처리 개별 조회**

| **필드**                        | **타입** | **설명**                 |
|---------------------------------|----------|--------------------------|
| PREPROCESS_FUNCTION_SEQUENCE_PK | Integer  | 전처리함수사전번호       |
| PREPROCESS_FUNCTION_NAME        | string   | 전처리함수이름           |
| LIBRARY_NAME                    | string   | 라이브러리이름           |
| LIBRARY_VERSION                 | string   | 라이브러리버전           |
| LIBRARY_DOCUMENT_URL            | string   | 라이브러리문서URL        |
| LIBRARY_OBJECT_NAME             | string   | 라이브러리객체이름       |
| LIBRARY_FUNCTION_NAME           | string   | 라이브러리함수이름       |
| LIBRARY_FUNCTION_DESCRIPTION    | string   | 라이브러리 함수설명      |
| LIBRARY_FUNCTION_USAGE          | string   | 라이브러리 함수 활용용도 |
| PARAMETERS                      | string   | 파라미터                 |
| \--name                         | string   | 파라미터 이름            |
| \--default                      | string   | 파라미터 기본값          |
| \--type                         | string   | 파라미터 데이터 타입     |
| \--note                         | string   | 파라미터 설명            |
| SUPPORT_DATA_TYPE               | string   | 지원데이터종류           |
| CREATE_DATETIME                 | string   | 생성일시                 |
| WRITER                          | string   | 작성자                   |
| USE_FLAG                        | string   | 사용가능여부             |

4.  **에러코드**

| **HTTP 코드** | **에러 메시지** | **조치 방안**                |
|---------------|-----------------|------------------------------|
| 404           | Not Found       | 조회 가능한 id를 입력합니다. |

5.  **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 [ { "PREPROCESS_FUNCTIONS_SEQUENCE_PK": 1, "PREPROCESS_FUNCTIONS_NAME": "MinMaxScaler", "LIBRARY_NAME": "sklearn", "LIBRARY_VERSION": "0.21.3", "LIBRARY_DOCUMENT_URL": "https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html", "LIBRARY_OBJECT_NAME": "preprocessing", "LIBRARY_OBJECT_NAME": "preprocessing", "LIBRARY_FUNCTION_NAME": "MinMaxScaler", "LIBRARY_FUNCTION_DESCRIPTION": "Transforms features by scaling each feature to a given range.", "LIBRARY_FUNCTION_USAGE": "numerical feature scaling", "PARAMETERS": { "name": "feature_range", "default": "(0, 1)", "type": "tuple", "note": "변형된 데이터의 원하는 범위 [min, max]" }, "SUPPORT_DATA_TYPE": "numerical", "CREATE_DATETIME": "2019-09-06T10:05:15.818890+09:00", "WRITER": "daumsoft", "USE_FLAG": true } ] \* 실패할 경우 응답 예시 { "detail": "Not Found", "status_code": "404" } |

6.    
    **전처리데이터 관리**

>   원본 데이터와 전처리 기능을 사용해서 전처리된 데이터를 생성하고 조회합니다.

1.  **요청 메시지 URL**

| **메서드** | **요청 URL**          | **출력 포맷** | **설명**                    |
|------------|-----------------------|---------------|-----------------------------|
| GET        | /preprocessedData     | json          | 전처리된 데이터 리스트 조회 |
| POST       | /preprocessedData     | json          | 전처리 데이터 생성          |
| GET        | /preprocessedData{id} | json          | 전처리된 데이터 개별 조회   |

2.  **요청 변수**

    1.  **전처리된 데이터 리스트 조회**

>   해당없음.

1.  **전처리 데이터 생성**

| **요청 변수명**                     | **타입** | **필수 여부** | **기본값** | **설명**                      |
|-------------------------------------|----------|---------------|------------|-------------------------------|
| original_data_sequence_pk           | integer  | Y             |            | 원본데이터 ID값               |
| request_dict                        | object   | Y             |            | 전처리 요청 정보              |
| \--preprocess_functions_sequence_pk | Integer  | Y             |            | 전처리 기능 ID                |
| \--field_name                       | string   | Y             |            | 전처리 수행할 컬럼명          |
| \--condition                        | string   | N             |            | 변경할 전처리 기능의 알고리즘 |

2.  **전처리된 데이터 개별 조회**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                                    |
|-----------------|----------|---------------|------------|---------------------------------------------|
| Id              | Integer  | Y             |            | 개별 조회를 희망하는 전처리된 데이터의 ID값 |

3.  **출력 결과**

    1.  **전처리된 데이터 리스트 조회**

| **필드**                      | **타입** | **설명**                             |
|-------------------------------|----------|--------------------------------------|
| PREPROCESSED_DATA_SEQUENCE_PK | integer  | 전처리데이터번호                     |
| FILEPATH                      | string   | 파일경로                             |
| FILENAME                      | string   | 파일이름                             |
| FILESIZE                      | string   | 파일크기                             |
| SUMMARY                       | string   | 작업결과요약                         |
| \--field_name                 | string   | 전처리를 수행한 컬럼명               |
| \--function_name              | string   | 전처리 기능 이름                     |
| \--function_pk                | integer  | 전처리 기능 ID                       |
| \--file_name                  | string   | 변환기 저장 이름                     |
| \--origianl_classes           | string   | (인코딩인 경우만) 원본 데이터 값     |
| \--encoded_classes            | string   | (인코딩인 경우만) 인코딩된 데이터 값 |
| CREATE_DATETIME               | datetime | 생성일시                             |
| PROGRESS_STATE                | string   | 작업상태                             |
| PROGRESS_START_DATETIME       | datetime | 작업시작일시                         |
| PROGRESS_END_DATETIME         | datetime | 작업종료일시                         |
| DELETE_FLAG                   | string   | 전처리데이터 삭제여부                |
| ORIGINAL_DATA_SEQUENCE_FK1    | integer  | 원본데이터번호                       |

4.  **전처리 데이터 생성**

| **필드**                      | **타입** | **설명**                             |
|-------------------------------|----------|--------------------------------------|
| PREPROCESSED_DATA_SEQUENCE_PK | integer  | 전처리데이터번호                     |
| FILEPATH                      | string   | 파일경로                             |
| FILENAME                      | string   | 파일이름                             |
| FILESIZE                      | string   | 파일크기                             |
| SUMMARY                       | string   | 작업결과요약                         |
| \--field_name                 | string   | 전처리를 수행한 컬럼명               |
| \--function_name              | string   | 전처리 기능 이름                     |
| \--function_pk                | integer  | 전처리 기능 ID                       |
| \--file_name                  | string   | 변환기 저장 이름                     |
| \--origianl_classes           | string   | (인코딩인 경우만) 원본 데이터 값     |
| \--encoded_classes            | string   | (인코딩인 경우만) 인코딩된 데이터 값 |
| CREATE_DATETIME               | datetime | 생성일시                             |
| PROGRESS_STATE                | string   | 작업상태                             |
| PROGRESS_START_DATETIME       | datetime | 작업시작일시                         |
| PROGRESS_END_DATETIME         | datetime | 작업종료일시                         |
| DELETE_FLAG                   | string   | 전처리데이터 삭제여부                |
| ORIGINAL_DATA_SEQUENCE_FK1    | integer  | 원본데이터번호                       |

5.  **전처리된 데이터 개별 조회**

| **필드**                      | **타입** | **설명**                             |
|-------------------------------|----------|--------------------------------------|
| PREPROCESSED_DATA_SEQUENCE_PK | integer  | 전처리데이터번호                     |
| FILEPATH                      | string   | 파일경로                             |
| FILENAME                      | string   | 파일이름                             |
| FILESIZE                      | string   | 파일크기                             |
| SUMMARY                       | string   | 작업결과요약                         |
| \--field_name                 | string   | 전처리를 수행한 컬럼명               |
| \--function_name              | string   | 전처리 기능 이름                     |
| \--function_pk                | integer  | 전처리 기능 ID                       |
| \--file_name                  | string   | 변환기 저장 이름                     |
| \--origianl_classes           | string   | (인코딩인 경우만) 원본 데이터 값     |
| \--encoded_classes            | string   | (인코딩인 경우만) 인코딩된 데이터 값 |
| CREATE_DATETIME               | datetime | 생성일시                             |
| PROGRESS_STATE                | string   | 작업상태                             |
| PROGRESS_START_DATETIME       | datetime | 작업시작일시                         |
| PROGRESS_END_DATETIME         | datetime | 작업종료일시                         |
| DELETE_FLAG                   | string   | 전처리데이터 삭제여부                |
| ORIGINAL_DATA_SEQUENCE_FK1    | integer  | 원본데이터번호                       |

6.  **에러코드**

| **HTTP 코드** | **에러 메시지**    | **조치 방안**                                           |
|---------------|--------------------|---------------------------------------------------------|
| 400           | Bad Request        | 올바른request 메시지를 사용합니다.                      |
| 404           | Not Found          | 조회 가능한 id를 입력합니다.                            |
| 405           | Method Not Allowed | 파일 조회를 통해 데이터가 경로에 존재하는지 확인합니다. |

7.  **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 [ { "PREPROCESSED_DATA_SEQUENCE_PK": 1, "FILEPATH": "result/preprocessed_data/P_1.json", "FILENAME": "P_1.json", "SUMMARY": "[{'field_name': 'atemp', 'function_name': 'MinMaxScaler', 'function_pk': 1, 'file_name': 'T_1_1.pickle', 'original_classes': None, 'encoded_classes': None}, {'field_name': 'season', 'function_name': 'OneHotEncoder', 'function_pk': 2, 'file_name': 'T_1_2.pickle', 'original_classes': [1.0, 2.0, 3.0, 4.0], 'encoded_classes': [[1.0, 0.0, 0.0, 0.0], [0.0, 1.0, 0.0, 0.0], [0.0, 0.0, 1.0, 0.0], [0.0, 0.0, 0.0, 1.0]]}]", "CREATE_DATETIME": "2019-09-19T09:21:42.102769+09:00", "PROGRESS_STATE": "success", "PROGRESS_START_DATETIME": "2019-09-19T09:21:42.164546+09:00", "PROGRESS_END_DATETIME": "2019-09-19T09:21:42.543532+09:00", "DELETE_FLAG": false, "ORIGINAL_DATA_SEQUENCE_FK1": 1 } ] |

8.  **모델 관리**

>   기계학습/딥러닝 모델을 관리합니다. 모델 생성, 조회, 삭제 및 적용을 요청할 수
>   있습니다.

1.  **요청 메시지 URL**

| **메서드** | **요청 URL** | **출력 포맷** | **설명**                                 |
|------------|--------------|---------------|------------------------------------------|
| GET        | /models      | json          | 학습된 모델 리스트 조회                  |
| POST       | /models      | json          | 모델 생성                                |
| GET        | /models/{id} | json          | 학습된 모델 개별 조회                    |
| PATCH      | /models/{id} | json          | 모델 로드, 언로드, 학습중지 및 모델 적용 |
| DELETE     | /models/{id} | json          | 학습된 모델 삭제                         |

2.  **요청 변수**

    1.  **학습된 모델 리스트 조회**

>   해당없음

>   .

1.  **모델 설정(모델 학습 요청)**

| **요청 변수명**        | **타입** | **필수 여부** | **기본값** | **설명**                                                                 |
|------------------------|----------|---------------|------------|--------------------------------------------------------------------------|
| algorithms_sequence_pk | Integer  | Y             |            | 모델 학습에 사용할 알고리즘 ID 값                                        |
| train_data             | object   | Y             |            | 모델 학습에 사용할 데이터 ID 값 (원본 데이터 또는 전처리된 데이터 ID 값) |
| model_parameters       | object   | N             |            | 변경할 알고리즘의 파라미터 값                                            |

2.  **학습된 모델 개별 조회**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                                |
|-----------------|----------|---------------|------------|-----------------------------------------|
| Id              | integer  | Y             |            | 개별 조회를 희망하는 학습된 모델의 ID값 |

3.  **모델 수정 요청(모델 로드, 언로드, 학습중지 및 모델 적용)**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                                                                 |
|-----------------|----------|---------------|------------|--------------------------------------------------------------------------|
| Id              | integer  | Y             |            | 수정할 모델의 ID 값                                                      |
| mode            | string   | Y             |            | 수정모드((STOP, LOAD, UNLOAD, TEST 중 선택)                              |
| test_data       | object   | N             |            | 모델 적용에 사용할 데이터 ID 값 (원본 데이터 또는 전처리된 데이터 ID 값) |

4.  **학습된 모델 삭제**

| **요청 변수명** | **타입** | **필수 여부** | **기본값** | **설명**                           |
|-----------------|----------|---------------|------------|------------------------------------|
| Id              | integer  | Y             |            | 삭제를 희망하는 학습된 모델의 ID값 |

5.  **출력 결과**

    1.  **학습된 모델 리스트 조회**

| **필드**                       | **타입** | **설명**                 |
|--------------------------------|----------|--------------------------|
| MODEL_SEQUENCE_PK              | Integer  | 모델번호                 |
| FILEPATH                       | string   | 파일경로                 |
| FILENAME                       | string   | 파일이름                 |
| FILESIZE                       | string   | 파일크기                 |
| TRAIN_SUMMARY                  | string   | 학습결과요약             |
| \--model_name                  | string   | 학습한 알고리즘 이름     |
| \--model_param                 | string   | 학습한 알고리즘 파라미터 |
| \--model_train_columns         | string   | 학습한 데이터 컬럼명     |
| VALIDATION_SUMMARY             | string   | 모델검증요약             |
| CREATE_DATETIME                | datetime | 생성일시                 |
| PROGRESS_STATE                 | string   | 작업상태                 |
| PROGRESS_START_DATETIME        | datetime | 작업시작일시             |
| PROGRESS_END_DATETIME          | datetime | 작업종료일시             |
| LOAD_STATE                     | string   | 모델로드상태             |
| DELETE_FLAG                    | boolean  | 모델 삭제여부            |
| ORIGINAL_DATA_SEQUENCE_FK1     | integer  | 원본데이터번호           |
| PREPROCESSED_DATA_SEQUENCE_FK2 | Integer  | 전처리데이터번호         |
| JOB_ID                         | String   | 작업 ID                  |

6.  **모델 설정(모델 학습 요청)**

| **필드**                       | **타입** | **설명**                 |
|--------------------------------|----------|--------------------------|
| MODEL_SEQUENCE_PK              | Integer  | 모델번호                 |
| FILEPATH                       | string   | 파일경로                 |
| FILENAME                       | string   | 파일이름                 |
| FILESIZE                       | string   | 파일크기                 |
| TRAIN_SUMMARY                  | string   | 학습결과요약             |
| \--model_name                  | string   | 학습한 알고리즘 이름     |
| \--model_param                 | string   | 학습한 알고리즘 파라미터 |
| \--model_train_columns         | string   | 학습한 데이터 컬럼명     |
| VALIDATION_SUMMARY             | string   | 모델검증요약             |
| CREATE_DATETIME                | datetime | 생성일시                 |
| PROGRESS_STATE                 | string   | 작업상태                 |
| PROGRESS_START_DATETIME        | datetime | 작업시작일시             |
| PROGRESS_END_DATETIME          | datetime | 작업종료일시             |
| LOAD_STATE                     | string   | 모델로드상태             |
| DELETE_FLAG                    | boolean  | 모델 삭제여부            |
| ORIGINAL_DATA_SEQUENCE_FK1     | integer  | 원본데이터번호           |
| PREPROCESSED_DATA_SEQUENCE_FK2 | Integer  | 전처리데이터번호         |
| JOB_ID                         | String   | 작업 ID                  |

7.  **학습된 모델 개별 조회**

| **필드**                       | **타입** | **설명**                 |
|--------------------------------|----------|--------------------------|
| MODEL_SEQUENCE_PK              | Integer  | 모델번호                 |
| FILEPATH                       | string   | 파일경로                 |
| FILENAME                       | string   | 파일이름                 |
| FILESIZE                       | string   | 파일크기                 |
| TRAIN_SUMMARY                  | string   | 학습결과요약             |
| \--model_name                  | string   | 학습한 알고리즘 이름     |
| \--model_param                 | string   | 학습한 알고리즘 파라미터 |
| \--model_train_columns         | string   | 학습한 데이터 컬럼명     |
| VALIDATION_SUMMARY             | string   | 모델검증요약             |
| CREATE_DATETIME                | datetime | 생성일시                 |
| PROGRESS_STATE                 | string   | 작업상태                 |
| PROGRESS_START_DATETIME        | datetime | 작업시작일시             |
| PROGRESS_END_DATETIME          | datetime | 작업종료일시             |
| LOAD_STATE                     | string   | 모델로드상태             |
| DELETE_FLAG                    | boolean  | 모델 삭제여부            |
| ORIGINAL_DATA_SEQUENCE_FK1     | integer  | 원본데이터번호           |
| PREPROCESSED_DATA_SEQUENCE_FK2 | Integer  | 전처리데이터번호         |
| JOB_ID                         | String   | 작업 ID                  |

8.  **모델 수정 요청(모델 로드, 언로드, 학습중지 및 모델 적용)**

    1.  **모델 수정 요청 – mode = STOP**

| **필드**    | **타입** | **설명**         |
|-------------|----------|------------------|
| request_id  | integer  | 테스트 수행 결과 |
| delete_flag | boolen   | 모델 삭제 여부   |

9.  **모델 수정 요청 – mode = LOAD**

| **필드**          | **타입** | **설명**                  |
|-------------------|----------|---------------------------|
| load_model_id     | List     | 로드된 모델 ID 값         |
| load_state        | string   | 로드 상태                 |
| model_expiry_date | Datetime | 로드된 모델 타임아웃 시간 |

10. **모델 수정 요청 – mode = UNLOAD**

| **필드**        | **타입** | **설명**            |
|-----------------|----------|---------------------|
| unload_model_id | integer  | 언로드한 모델 ID 값 |
| load_state      | string   | 로드 상태           |

11. **모델 수정 요청 – mode = TEST**

| **필드**   | **타입** | **설명**         |
|------------|----------|------------------|
| test_score | integer  | 테스트 수행 결과 |

12. **학습된 모델 삭제**

| **필드**                       | **타입** | **설명**                 |
|--------------------------------|----------|--------------------------|
| MODEL_SEQUENCE_PK              | Integer  | 모델번호                 |
| FILEPATH                       | string   | 파일경로                 |
| FILENAME                       | string   | 파일이름                 |
| FILESIZE                       | string   | 파일크기                 |
| TRAIN_SUMMARY                  | string   | 학습결과요약             |
| \--model_name                  | string   | 학습한 알고리즘 이름     |
| \--model_param                 | string   | 학습한 알고리즘 파라미터 |
| \--model_train_columns         | string   | 학습한 데이터 컬럼명     |
| VALIDATION_SUMMARY             | string   | 모델검증요약             |
| CREATE_DATETIME                | datetime | 생성일시                 |
| PROGRESS_STATE                 | string   | 작업상태                 |
| PROGRESS_START_DATETIME        | datetime | 작업시작일시             |
| PROGRESS_END_DATETIME          | datetime | 작업종료일시             |
| LOAD_STATE                     | string   | 모델로드상태             |
| DELETE_FLAG                    | boolean  | 모델 삭제여부            |
| ORIGINAL_DATA_SEQUENCE_FK1     | integer  | 원본데이터번호           |
| PREPROCESSED_DATA_SEQUENCE_FK2 | Integer  | 전처리데이터번호         |
| JOB_ID                         | String   | 작업 ID                  |

13. **에러 코드**

| **HTTP 코드** | **에러 메시지**              | **조치 방안**                      |
|---------------|------------------------------|------------------------------------|
| 400           | Bad Request                  | 올바른request 메시지를 사용합니다. |
| 400           | Model State is SUCCESS       |                                    |
| 400           | Model State is FAIL          |                                    |
| 400           | Model is Not Loaded          | 모델을 로드합니다.                 |
| 400           | Number of Features Not Match |                                    |
| 400           | Test Data is Not Provided    | 테스트 데이터를 요청합니다.        |
| 404           | Not Found                    | 조회 가능한 id를 입력합니다.       |
| 405           | Method Not Allowed           |                                    |

14. **응답 메시지 형태 (샘플 JSON 예제)**

| **JSON**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \* 성공할 경우 응답 예시 [ { "MODEL_SEQUENCE_PK": 1, "FILEPATH": "result/model/M_1.pickle", "FILENAME": "M_1.pickle", "TRAIN_SUMMARY": "{'model_name': 'RandomForestRegressor', 'model_param': {'bootstrap': True, 'criterion': 'mse', 'max_depth': None, 'max_features': 'log2', }, 'model_train_columns': ['holiday', 'workingday', 'weather', 'atemp', 'humidity', 'windspeed', 'casual', 'registered', 'season_0', 'season_1', 'season_2', 'season_3']}", "VALIDATION_SUMMARY": "{'validation_score': [0.9827, 0.9818, 0.9810, 0.9801, 0.9824], 'holdout_score': 0.9746915817925598}", "CREATE_DATETIME": "2019-09-23T16:45:03.155842+09:00", "PROGRESS_STATE": "success", "PROGRESS_START_DATETIME": "2019-09-23T16:45:03.213688+09:00", "PROGRESS_END_DATETIME": "2019-09-23T16:45:04.370592+09:00", "LOAD_STATE": "load_available", "DELETE_FLAG": true, "ORIGINAL_DATA_SEQUENCE_FK1": 1, "PREPROCESSED_DATA_SEQUENCE_FK2": 2, "JOB_ID": "48666569-13ea-4b30-9b7e-f7bf7750562f" } ] \* 모델 적용(테스트) 성공할 경우 응답 예시 { "test_score": 0.7577241571 } |
