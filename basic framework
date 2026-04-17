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
        <h1>Hello</h1>
        <p>my name is ~~</p>
        <p>I am interested in ~</p>
        <p>Add content</p>
    </body>
    </html>
    """
