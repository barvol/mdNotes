# Goroutine
Tags: #GO 
Date: 2022-05-21
***
### Пример использования гоурутин:
```go
func main() {
	ch := make(chan int)
	go sayHello(ch)
	for i := range ch {
		fmt.Println(i)
	}
}

func sayHello(exit chan int) {
	for i := 0; i < 5; i++ {
		time.Sleep(1 * time.Second)
		exit <- i
	}
	close(exit)
}
```

Mutex - бллокировка 
```go
type Counter struct {  
   mu sync.Mutex  
   c  map[string]int  
}  
  
func (c *Counter) Inc(key string) {  
   c.mu.Lock()  
   c.c[key]++  
   c.mu.Unlock()  
}  
  
func (c *Counter) Value(key string) int {  
   c.mu.Lock()  
   defer c.mu.Unlock()  
   return c.c[key]  
}  
  
func main() {  
   key := "test"  
   count := Counter{  
      c: make(map[string]int),  
   }  
   for i := 0; i < 100; i++ {  
      go count.Inc(key)  
   }  
  
   time.Sleep(3 * time.Second)  
   fmt.Println(count.Value(key))  
}
```

---
links: [[Fullstack GO]]