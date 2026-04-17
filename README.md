
## FastAPI 사용법

## 1. FastAPI란?
FastAPI는 Python으로 웹 서버와 API를 빠르게 만들 수 있게 도와주는 프레임워크입니다.  
문법이 비교적 단순해서 초심자도 구조를 익히기 좋습니다.

---

## 2. 설치

먼저 FastAPI와 실행용 서버인 uvicorn을 설치합니다.

````
pip install fastapi uvicorn
````

---

## 3. 기본 코드

아래는 가장 기본적인 FastAPI 코드입니다.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello FastAPI"}
```

---

## 4. 코드 설명

### `app = FastAPI()`

FastAPI 앱 객체를 만드는 코드입니다.
이 객체를 기준으로 서버가 동작합니다.

### `@app.get("/")`

브라우저가 `/` 주소로 접속했을 때 실행할 기능을 정하는 부분입니다.
`GET` 요청을 처리합니다.

### `def home():`

해당 주소에 접속했을 때 실행되는 함수입니다.

### `return {"message": "Hello FastAPI"}`

클라이언트에게 JSON 형태의 데이터를 반환합니다.

---

## 5. 실행 방법

파일 이름이 `main.py`라면 아래 명령어로 실행합니다.

```bash
uvicorn main:app --reload
```

### 의미

* `main`: 파일 이름
* `app`: FastAPI 객체 이름
* `--reload`: 코드 수정 시 자동 재실행

실행 후 브라우저에서 아래 주소로 접속합니다.

```bash
http://127.0.0.1:8000
```

---

## 6. HTML 페이지 반환하기

FastAPI는 API만 만드는 것이 아니라 간단한 웹페이지도 반환할 수 있습니다.

```python
from fastapi import FastAPI
from fastapi.responses import HTMLResponse

app = FastAPI()

@app.get("/", response_class=HTMLResponse)
def home():
    return """
    <html>
        <head>
            <title>자기소개</title>
        </head>
        <body>
            <h1>안녕하세요</h1>
            <p>제 이름은 홍길동입니다.</p>
            <p>FastAPI로 만든 자기소개 페이지입니다.</p>
        </body>
    </html>
    """
```

---

## 7. 여러 페이지 만들기

주소별로 다른 내용을 만들 수 있습니다.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"page": "home"}

@app.get("/about")
def about():
    return {"page": "about"}

@app.get("/contact")
def contact():
    return {"page": "contact"}
```

### 결과

* `/` → home
* `/about` → about
* `/contact` → contact

---

## 8. Swagger 문서 확인

FastAPI는 자동으로 API 문서를 만들어줍니다.

실행 후 아래 주소에 접속하면 됩니다.

```bash
http://127.0.0.1:8000/docs
```

이 문서 페이지에서 API를 직접 테스트할 수 있습니다.

---

## 9. 초심자가 알아두면 좋은 점

* FastAPI는 `app = FastAPI()`부터 시작한다.
* `@app.get()`은 주소와 기능을 연결한다.
* `return`으로 JSON 또는 HTML을 보낼 수 있다.
* `uvicorn`으로 서버를 실행한다.
* `/docs`에서 API 테스트가 가능하다.

---

## 10. 간단한 자기소개 예시

```python
from fastapi import FastAPI
from fastapi.responses import HTMLResponse

app = FastAPI()

@app.get("/", response_class=HTMLResponse)
def home():
    return """
    <!DOCTYPE html>
    <html lang="ko">
    <head>
        <meta charset="UTF-8">
        <title>자기소개</title>
    </head>
    <body>
        <h1>안녕하세요</h1>
        <p>저는 Python과 보안에 관심이 있습니다.</p>
        <p>이 페이지는 FastAPI로 만들었습니다.</p>
    </body>
    </html>
    """
```

---

## 11. 정리

FastAPI를 사용할 때 가장 기본 흐름은 아래와 같습니다.

1. FastAPI 설치
2. `app = FastAPI()` 작성
3. `@app.get()`으로 주소 만들기
4. 함수에서 데이터 반환
5. `uvicorn`으로 실행
6. 브라우저 또는 `/docs`에서 확인

초심자라면 먼저
**JSON 반환 → HTML 반환 → 자기소개 페이지 만들기**
순서로 연습하는 것이 좋습니다.
