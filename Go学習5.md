５月２5日~26日　木曜日　Go言語学習
- 学んだこと
- 文字列の入力
- 関数
- 引数
- 戻り値
- 値を渡す　

- 詳細<br>
- 文字列の入力<br>
fmt.Scan(&変数名)を使うとコンソールでの入力ができる<br>

- 例<br>
 ```　
 var input string
 fmt.Scan(&input) ←①fmt.Scan(&変数名)でコンソールへ文字入力ができる
 
 ② コンソール画面　dog　(文字列を入力)
 ③②のdogが変数inputに代入される
```

- 流れ<br>
```　
① fmt.Println("次の単語を入力してください:dog")
②fmt.Scan(&input) ←ユーザーが入力してEnterキーを押すまで、ここで止まる
③fmt.Printf("%sと入力されました",input)
```

- 関数<br>
関数とはいくつかの処理をまとめたもの<br>
処理を関数にまとめると、何度でも使える<br>

-　例<br>
```
func main () {
 var input string
 fmt.Println("次の単語を入力してください　:dog")
 fmt.Scan(&input)
 fmt.Printf("%sと入力されました", input)
}　ask関数にまとめると何度でも使える
```

- 関数の定義<br>
関数はfunc 関数名()と書く<br>
その後ろの{}の中にまとめたい処理を書くことで関数を用意可能<br>
このように関数を用意することを『関数を定義する』と言う<br>

- 例<br>
```
関数の定義
func 関数名（）{
まとめたい処理を書く
}
```

- 関数の呼び出し<br>
関数を定義しただけでは、その中の処理は実行されない<br>
「関数名()」と書くことで関数の中の処理を実行できる<br>
このことを「関数を呼び出す」という<br>

-　例<br>
```
func main(){
 ask() ←ask関数を呼び出す
}
func ask(){
 var input string
 fmt.Println("次の単語を入力してください：dog")
 fmt.Scan(&input)
 fmt.Printf("%sと入力されました",input)
}
```

- main関数<br>
 今まで処理を書いてたfunc　main(){}の部分もmain関数と呼ばれる関数<br>
 main関数はプログラムが実行されると最初に呼び出される特別な関数<br>
 
- 例<br>
```
func main(){
 ask()
}
func ask(){
 var input string
 fmt.Println("次の単語入力してください:dog")
 fmt.Scan(&input)
 fmt.Printf("%sと入力されました",input)
}
```

- 関数を書く順番<br>
 関数を定義する順番に特に決まりはない<br>
 
- 関数を複数回呼び出す<br>
 　１度定義すれば同様の処理を何度でも実行できるのが関数のメリット<br>
  
- 例<br>
```
func main(){
 ask () ←複数回呼び出せる
 ask ()　　←複数回呼び出せる
}
func ask() {
```

- 関数に値を渡す　引数<br>
関数を呼び出す際に、()の中に値を書くことで、値を渡すことができる<br>
この値のことを引数という<br>

- 例<br>
```
func main(){
 ask("dog") （）の中に値を書くことで
 ask("cat")　値を渡すことができる
}
```

- 引数を受け取る<br>
渡した値を使うためには、受け取るための変数を用意する必要がある<br>

- 例<br>
```
func main(){
ask("cat") //"cat"を引数として渡している
}

func ask(question string){　 //question は変数名　stringは型
}
```

- 引数を使う
渡された値は受け取った変数名を用いて使うことができる<br>

- 例<br>

```
 func main()　{
  ask("dog") //引数として"dog"を渡している
  ask("cat") //引数として"cat"を渡している
 }
 func ask(question string){ //この段落のquestionは↓のquestion
 
 fmt.Printf("次の単語を入力してください　：%s\n",question)
 }
```

- 変数の値を渡す<br>
 関数には変数の値を引数として渡すこともできる<br>
 変数textを引数として、ask関数の変数questionに渡している<br>
 
- 例
```
func main(){
 texe :="cat"
 ask(text) // 変数textを引数としてquestionに渡している
 
func ask(question string){

 fmt.Printf("次の単語を入力してください　:%s\n,question)
 }
```

- 問題番号を出す<br>
　引数はコンマ（,）区切りで複数を受け取ることができる<br>
 
- 例<br>
```
func ask(number int,questioon string){
                   →コンマで引数ごとに区切る

fmt.Printf("[質問%d]次の単語を入力してください:%s\n",number,question)
```

- 複数の引数の渡し方<br>
複数の引数を使うとき、渡す順番に注意<br>
 
- 例<br>
```
func main() {
 ask(1,"dog")
 ask(2,"cat")  //問題番号、問題文の順で渡す
 ask(3,"fish") //1,2,3はnumberへ　"dog","cat","fish"はquestionへ
}
func ask(number int,question string) {
 fmt.Printf("[質問%d]次の単語を入力してください:%s\n",number,question)
}
```

- 戻り値<br>
戻り値を使うことで呼び出し元に値を返すことが出来る<br>

- 戻り値のある関数の定義<br>
ask関数は処理の終わりに戻り値10を返している<br>
「return 10」のように書くことで呼び出し元に10が返る<br>

- 戻り値のある関数の定義
```
func 関数名（引数名　引数の型）戻り値の型{
　 処理
}
```

- 戻り値の受け取り方<br>
  関数の戻り値は変数に代入するなどして受け取ることができる<br>
  
