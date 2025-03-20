|GET|POST|
|---|----|
|서버에서 어떤 데이터를 가져와서 보여주는 용도|서버의 값이나 상태를 변경하기 위해서 또는 추가하기 위해서 사용|
|요청하는 데이터가 HTTP Request Message의 Header부분에 URL이 담겨서 전송됨|HTTP Request와 Message의 Body 부분에 데이터가 담겨서 전송|
|URL상에 '?' 뒤에 데이터가 붙여 request를 보낸다. 👉 전송할 수 있는 데이터가 제한적이다. 보안이 필요한 데이터가 그대로 URL에 노출|데이터의 크기가 GET 방식보다 크고 보안면에서 낫다.|
|브라우저에서 Caching 가능|브라우저에서 Caching 불가능|
