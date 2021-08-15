# go-rest-api

I developed rest api which include CRUD operations.
You can check for detail my medium account.

```shell
POST http://localhost:8090/api/books
BODY:
    {
    "isbn": "45812273",
    "title": "Stream processing using apache pulsar",
    "author":{"firstname":"Theophilus","lastname":"Siameh"}
    
    }
    
RESPONSE:
  {
    "InsertedID": "6119938dcc56a324ec60bfb9"
  }


curl --location --request POST 'http://localhost:8090/api/books' \
--header 'Content-Type: application/json' \
--data-raw '{
    "isbn": "45812273",
    "title": "Stream processing using apache pulsar",
    "author":{"firstname":"Theophilus","lastname":"Siameh"}
    
}'


```
```shell
curl --location --request GET 'http://localhost:8090/api/books/6119938dcc56a324ec60bfb9' \
--header 'Content-Type: application/json' \
--data-raw '{
    "isbn": "45812273",
    "title": "Stream processing using apache pulsar",
    "author":{"firstname":"Theophilus","lastname":"Siameh"}
    
}'
```

```shell
curl --location --request PUT 'http://localhost:8090/api/books/6119938dcc56a324ec60bfb9' \
--header 'Content-Type: application/json' \
--data-raw '{
    "isbn": "9999999",
    "title": "Stream processing using apache pulsar",
    "author":{"firstname":"Theophilus","lastname":"Siameh"}

}'
```
```shell
curl --location --request DELETE 'http://localhost:8090/api/books/611994efcc56a324ec60bfba' \
--header 'Content-Type: application/json' \
--data-raw '{
    "isbn": "123456",
    "title": "Introduction to data science",
    "author":{"firstname":"Theophilus","lastname":"Siameh"}

}'
```

```shell
curl --location --request GET 'http://localhost:8090/api/books'
```

## Go Code
```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "http://localhost:8090/api/books/6119938dcc56a324ec60bfb9"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```




