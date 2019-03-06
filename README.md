### tunny
---
https://github.com/Jeffail/tunny

```go
pool := tunny.New(poolSize, func() Worker {
  return newCustomWorker()
})

result, err := pool.ProcessTimed(input, time.Second*5)
if err == tunny.ErrJobTimedOut {
  http.Error(w, "Request timed out", http.StatusRequestTimeout)
}

pool.SetSize(10)
pool.SetSize(100)

package main

import ()

func main() {
  numCPUs := runtime.NumCPU()
  
  pool := tunny.NewFunc(numCPUs, func(payload interface{}) interface{} {
    var result []byte
    
    return result
  })
  defer pool.Close()
  
  http.HandleFunc("/work", func(w http.ResponseWriter, r *http.Request) {
    input, err := ioutil.ReadAll(r.Body)
    if err != nil {
      http.Error(w, "Internal error", http.StatusInternalServerError)
    }
    defer r.Body.Close()
    
    result := pool.Process(input)
    
    w.Write(result.([]byte))
  })
  
  http.ListenAndServe(":8080", nil)
}
```

```
go get github.com/Jeffail/tunny
dep ensure -add github.com/Jeffail/tunny
```

```
```


