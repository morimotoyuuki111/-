5月28日　土曜日　Go学習

- 学んだこと<br>
- アドレス
- ポインタ
- 別の関数でポインタを利用
- 引数の仕組み

- 詳細<br>
　
 - アドレスとは<br>
 コンピュータにはメモリと呼ばれる作業場所のような物が存在する<br>
 変数にはそのメモリに記憶されており、その場所をアドレスと呼ぶ<br>
 
 例　「0xc420010230」のように16進数で表現されることが多い<br>
   　16進数とは、数学を数えるときに16で繰り上げるようにする数え方<br>
   
- アドレスを取得してみる<br>
変数のアドレスを取得する為には、＆変数名とする<br>
メモリ上の記憶する場所はコンピュータによって変わるため、<br>プログラムを実行する度に違う
アドレスを出力する場合もある<br>
 　

- 例　<br>
```
func main(){
  fmt.Println(name) // nameで値を取得
  fmt.Println(&name)　// &nameでアドレスを取得できる
}

コンソール
johon //値が出力される
0xc420010230 アドレスが出力される
```

- ポインタとは<br>
 アドレスは値<br>
 整数や文字列のように操作したり変数に代入することができる<br>
 Goではアドレスをポインタと呼び扱っている<br>
 またポインタが代入された変数をポインタ型変数と呼ぶ
 
- ポインタ型変数の定義
ポインタ型変数を定義するには、変数のデータに*をつけて宣言する<br>

- 例<br>
```
func main() {
 name : "john" //nameの値がstring型なので*string型になる
 var namePtr *string = &name 　// nameのポインタをnemePtrに代入
 fmt.Println(namePrt)
}

コンソール
0xc420010230　ポインタが出力される
```

- ポインタからアクセスする<br>
ポインタ型変数に対して「*(アスタリスク)変数名」とすることで、そのポインタが示す変数の値を取り出すことができる<br>

- 例<br>
```
func main(){
 name := "joho"
 var namePtr *string = &name
 fmt.Println(*namePtr) //namePtrが示す変数の値を出力
}

コンソール
john //値が出力される
```
- ポインタを使って値を更新する<br>
ポインタ型変数をしようして、値を直接更新することもできる<br>
更新するには「*変数名 = 更新する値」と記述する<br>

- 例<br>
```
 func main() {
  name :="john"
  var namePtr*string = &name
  *namePtr = "Kate" //namePtrが示す変数の値を更新
  fmt.Println(name)
 }
```

コンソール
kate 更新した値が出力される

- ポインタのおさらい
```
name :="john"
var namePtr*string = &name　ポインタ型は*変数の型で定義できる
```

```
fmt.Println(◯○)
name john  　　　　　　　
&name 0xc
namePtr 0xc
*namePrtjohn
```

- 引数にポインタを指定する<br>
ポインタを別の関数に引数として指定する場合、受け取る関数には対応したポインタ型の引数を用意する必要がある<br>

- 例
```
func main(){
 name := "john"
 changeName(&name) //&name　ポインタを引数に指定する　↓
} 
func changeName(namePtr *string){ //namePtr *string stringのポインタ型で受け取る
}
```

- 別の関数でポインタを使って値を更新<br>
ポインタを引数として指定することで、別の関数からでもポインタを使って元の変数を更新することができる<br>

- 例
```
func main(){
 name := "john"
 changeName(&name) //ポインタを引数に指定
 fmt.Println(name)
}
func changeNname(namePtr *string){
 *namePtr = "Kate"　//ポインタを使って元の変数を更新　”john”⇨"kate"
}

コンソール
Kate
```

- 引数の仕組み<br>
変数を引数に指定<br>
変数totalScoreを引数に指定する場合、その変数自体が渡されるわけではない<br>
実際には変数totalScoreの値がコピーされ、新しい変数に代入される<br>

- 例
```
func main(){
 fn(totalScore)//totalScoreを引数に指定する
}
func fn(totalScore int){ //int型で受け取る
}
```

- 渡した値を更新する<br>
 main関数とfn関数のそれぞれの変数totalScoreは、別の変数<br>
そのため、fn関数のtotalScoreを更新しても、fn関数のtotalScoreのみ値が更新される<br>

- 例
```
func main(){
 totalScore := 0
 fn(totalScore)
 fmt.Ptintln(totalScore)//totalScoreの値を出力
}
func fn(totalScore int){
 totalScore += 10 //fn関数のtotalScoreのみ値を更新
 
コンソール
0 元の値が出力される
 ```
