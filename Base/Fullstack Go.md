# Fullstack GO
Tags: #GO
Date: 2022-05-03

## Задачи по изучению GO!
- [ ] Изучение WEB курса по GO [Ссылка Youtube][1]
- [ ] Записаться на обучение у Владилена Минина
- [ ] Изучить фреймворк [[HUGO]] [Ссылка Youtube][2]
- [ ] Создание сайта на [GO](https://www.youtube.com/watch?v=mBLpAx06l44)

## Основы:
### Массивы и слайсы:
```GO 
//Массив
var a [2]int  
a[0] = 22  
a[1] = 3232  
  
b := [4]int{4, 3, 2, 5}  
cutSlices := b[:2]  
b[0] = 77

//Слайс
letters := []string{  
   "Привет",  
   "Как дела?",  
}
letters = append(letters, "Возможно")  
  
createSlices := make([]int, 0, 4)  
createSlices = append(createSlices, 1, 2, 3, 4)

//Создаем слайс и копируем из b, емкость слайса создаем на основе массива  
s := make([]int, 0, cap(b))  
for _, i2 := range b {  
   s = append(s, i2)  
}  
//сравнение слайсов с nil  
var slicesNull []int  
if slicesNull == nil {  
   println("Они равны")  
}

```

### Функции:
```Go
//callback  
func doSomething(callback func(int, int) int, s string) int {  
   a := callback(5, 8)  
   fmt.Println(s)  
   return a  
}  
  
//Змыкания  
func totalPrice(initPrice int) func(int) int {  
   num := initPrice  
   return func(x int) int {  
      num += x  
      return num  
   }  
}  
  
func main() {  

   //добавляем в callback разную логику  
   sumCallback := func(n1, n2 int) int {  
      return n1 + n2  
   }  
   multiCallback := func(n1, n2 int) int {  
      return n1 * n2  
   }  

   //работаем с замыканием  
   orderPrise := totalPrice(10)  
   fmt.Println(orderPrise(5))  
   fmt.Println(orderPrise(5))  
  
   result := doSomething(sumCallback, "Hello World")  
   result2 := doSomething(multiCallback, "Второе значение")
```

### Мапы:
```Go
//создаем map, при создании без make, необходимо ставить фигурные скобки для инициализации map  
func main() {  
   pointsMapNew := map[string]int{  
      "xx": 88,  
      "yy": 3222,  
   }  
   pointsMap := map[int]Pointer{  
      1: {  
         X: 31,  
         Y: 2,  
      },  
   }
```

### Метод:
```Go
type Point struct {  
   X, Y int  
}  
  
func (p *Point) movePointNew(x, y int) {  
   p.X += x  
   p.Y += y  
}  
func main() {  
   p := Point{  
      X: 1,  
      Y: 2,  
   }  
   p.movePointNew(5, 8)
```

### Интерфейс:
```Go
type MathNumbers interface {  
   Sum() int  
   Min() int  
}  
  
type calculate struct {  
   X int  
   Y int  
}  
  
func (c calculate) Sum() int {  
   return c.X + c.Y  
}  
  
func (c calculate) Min() int {  
   return c.X - c.Y  
}  
  
func main() {  
   var dev = MathNumbers(  
      calculate{  
         X: 2,  
         Y: 1,  
      },  
   )  
   var i MathNumbers  
   num := calculate{  
      X: 44,  
      Y: 24,  
   }  
   i = num  
   fmt.Println(i.Sum())  
   fmt.Println(i.Min())  
   fmt.Println(dev.Min())  
}
```


## Дополнения в других заметках:
[[Обработка ошибок в GO]]
[[Программирование]]
[[Goroutine]]

***
[1]: https://www.youtube.com/watch?v=0s3Jz8Y_cq8&list=PLP19RjSHH4aE9pB77yT1PbXzftGsXFiGl&index=3
[2]: https://www.youtube.com/channel/UCtlnMUJr68ytsr11_dv_elg/videos

