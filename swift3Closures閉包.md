# Swift3閉包

模擬C 或 Objective-C的block

> 已知參數function

```
func test(_ value:Int,_ fun:(Int)->Int)->Int{
      return fun(value)
}

test(2,{value in value*10})
// Int = 20

test(2){value in
     value*100+12
}
//  Int = 212

test(4){$0*200}
//Int = 800

test(3,{$0*100})
// Int = 300
```

> 簡化閉包參數流程

```
//  定義sort閉包function
extension Array{
    func mySort(clo:(_ s1: String, _ s2: String)-> Bool)-> [Element]{
        var tempArray = self
        for i in 0...tempArray.count - 1{
            for j in i...tempArray.count - 1{
                if clo(tempArray[i] as! String, tempArray[j] as! String){
                    let temp = tempArray[i]
                    tempArray[i] = tempArray[j]
                    tempArray[j] = temp
                }
            }
        }

        return tempArray
    }
}

func numSort(n1:String, n2:String)->Bool{
    return n1<n2
}

//  1.
let num = ["a","b","c","d"]
let number = num.mySort(clo: numSort)
// number is equal to ["d", "c", "b", "a"].

//  2.
let numberb = num1.mySort{(a,b)->Bool in
    return a<b
}

//當 closure 作為函數的最後一個參數時，在調用函數時，可以省去小括號，並把 closure 寫在外面。官方文件裡稱之為 Trailing Closures 。

//  3.
let numberc = num.mySort(clo:<)
```

> 標記 closure 參數的類型

@noescape和@autoclosure屬性現在必須寫在參數類型之前，而不是參數名稱之前

```
func doSomething(withParameter parameter: Int, completion: @escaping () -> ()) {
    // ...
}
```

用 @autoclosure 標記 clousre 參數的類型後，在函數呼叫的時候就可以去掉 closure 的大括號{}，把 closure 以其返回值的形式傳入函數中

```
var customersInLine = ["Alex", "Ewa", "Barry", "Daniella"]

func serve(customer customerProvider: () -> String) {
     print("Now serving \(customerProvider())!")
}

serve(customer: { customersInLine.remove(at: 0) } )
// Prints "Now serving Alex!
```

>  Swift 3 closure 作為函數的參數，默認是 @noescaping 類型

>  @escaping 標記:
>>  表示 closure 在函數運行結束後再執行

> @noescaping 標記:
>>  表示 closure 必須在函數運行結束前執行。

> 一個常見的例子是常見的 completion handle ，它們在函數運行完成後才執行。

_-_-_-_-_-_-_-

> 當 closure 的類型用 @escaping 標記之後，在 closure 內使用類的屬性或方法時，需要用 self 標明。

```
class SomeClass {
    var x = 10
    func doSomething() {

        //  use @escaping function
        someFunctionWithEscapingClosure { self.x = 100 }

        //  use @noescaping function
        someFunctionWithNonescapingClosure { x = 200 }
    }
}
```
