# Обработка ошибок в GO
Tags: #GO 
Date: 2022-05-15
***
### Пример создания custom ошибки
```GO
type AppErrors struct {  
   Err    error  
   Custom string  
   Field  int  
}  
  
func (e *AppErrors) Error() string {  
   fmt.Println(e.Custom)  
   return e.Err.Error()  
}  
  
func main() {  
   var m = error(  
      &AppErrors{  
         Err:    fmt.Errorf("my error"),  
         Custom: "value 44",  
         Field:  444,  
      },  
   )  
  
   err := m2  
   if err != nil {  
      fmt.Println(err().Error())  
   }  
   if m != nil {  
      fmt.Println(m.Error())  
   }  
}  
  
func m2() error {  
   return &AppErrors{  
      Err:    fmt.Errorf("my Error"),  
      Custom: "value Y-Y",  
      Field:  3,  
   }  
}
```

Интерфейс используется error который уже описан в GO


---
links: [[Fullstack GO]]