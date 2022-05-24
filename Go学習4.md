5月24日　水曜日　Go言語学習
- 学んだこと
- 標準パッケージ
- fmt.Printf
- 文字列の書式
- データ型の不一致
- 改行文字
- for
- rand

- 詳細　
- 標準パッケージ
  プログラムを書くとき、すべての処理を自分で書く必要はない<br>
  Goには標準パッケージと呼ばれるものがあり、100種類以上の便利な機能がはじめから用意されている<br>これらを自分たちのプログラム内で自由に用いることができる<br>
  
- 例　 <br>
　　　　fmt コンソールに出力できる<br>
  math/rand ランダムな数値を生成できる<br>
  time 時間に関する処理ができる<br>
  [参考になるパッケージサイト](https://y-hiroyuki.xyz/go/package/what-is-package)<br>
  
- パッケージのインポート<br>
  標準パッケージを自分のプログラムで使うためには、インポートする必要がある<br>インポートは、「package main」の下に「import "パッケージ名"」と記述する<br>
  例えば、コンソールへの出力機能などを持つfmtパッケージは「import "fmt"」と書く<br>
　　　　※パッケージ名をダブルクォーテーションで囲むことに注意※<br>
 
- 例<br>
   ```　　　　
   package main
     inport "fmt" ← [fmt]という標準パッケージをインポート
     ```
- パッケージの使い方<br>
  標準パッケージの機能を使うには、パッケージ名.機能名とします。<br>fmtパッケージのPrintlnという機能は、コンソールに()内の値を出力<br>
  「fmt.Println」の方が表示できるデータ型が多いため、今後はこちらを使うように!<br>
  
- 例<br>
```　　
package main
import "fmt"
func main(){
  fmt.Println("Hello,World") //Println 「パッケージ名、機能名」で使いたい機能を呼び出す　
}　　　　　　　　　　//Pは大文字なので注意

Hello,Worldが出力される
```

- 使用していないパッケージ<br>
Goでは、インポートしたパッケージは必ず使う必要がある<br>
fmtパッケージをインポートしているのに使っていない場合、エラーが発生<br>

- 例<br>
```　　
package main
import "fmt"
func main(){
  Println("Hello,World") 　//fmtパッケージを使ってないとエラーになる
```

- fmt.Printfについて<br>
  fmtパッケージのPrintfという機能を用いると、書式を指定してコンソールに出力することができる<br>
  書式とは、出力する文字列の形<br>  
  パッケージの使い方<br>
  1つめに書式、2つめに出力に用いる値を指定<br>
  
- 例
  ```　　
  fmt.Printf（書式、出力に用いる値）
  ```
 
  
- 文字列の書式<br>
書式（出力する文字列の形式<br>
"Hello, %sさん"のように%sを文字列の中に含めると、「fmt.Printf」の2つめに指定した文字列が%sの部分に挿入されて出力される<br> 
変数nameの値が「にんじゃワンコ」であるため、「Hello, にんじゃワンコさん」とコンソールに出力<br>

- 例 <br>

```
func main(){
  name := "にんじゃワンコ" 
  fmt.Printf("Hello,%sさん",name) //%sの部分には、変数nameに入っている文字列が使用される
}

Hello,にんじゃワンコさん　←nameの値が％sの部分に挿入されている
```

- 複数の値を埋め込む<br>
%sは書式中にいくつでも用いることができる<br>
下図のように%sを2回用いる場合、それぞれの%sに挿入する文字列を指定する必要がある<br>
書式中の1つめの%sに「fmt.Printf」の2つめで指定した「Hello」が、2つめの%sに「fmt.Printf」の3つめで指定した変数nameの値（にんじゃわんこ）が挿入される<br>

- 例<br>
```
func main(){
  name := "にんじゃ　ワンコ"
  fmt.Printf("%s,%sさん","Hello",name) //%sにはHello %sさんにはname
} 

Hello,にんじゃワンコさんと出力される
```

- 整数を埋め込む<br>
書式には、文字列だけでなく数値も挿入することができる<br>
数値の場合には%dを使う<br>
%sと同じように、挿入する数値を「fmt.Printf」の2つめに指定する<br>
下のコードでは"%d歳です"の%dの部分に、変数ageの値１８が挿入されている

- 例<br>
```
func main() {
  age := 18
  fmt.Printf("%d歳です",age) //%dの部分には、変数ageに入ってる整数が使用される
}
18歳ですと出力される
```

- データ型の不一致<br>
「fmt.Printf」では文字列に%sや%dで値を挿入することができる。<br>このとき、%sは文字列、%dは数値を挿入するために用いる。<br>
指定する値のデータ型が文字列にも関わらず、書式には%dを使ったり、その逆を行ったりした場合、エラーとなる<br>

- 例<br>
```
func main() {
  age := "18" ←　文字列
  fmt.Printf("%d歳です",age) //書式は％dだが、ageは文字列
  
  %!d(string=18)歳です　//%dなのに文字列の"18"が指定されたというエラー
```

- 改行文字<br>
- PrintfとPrintlnの違い<br>
fmt.Printf」は、「fmt.Println」と違い、出力した文字列のあとで改行を行ってくれない<br>
複数の「fmt.Printf」を行うと、出力は同じ行の末尾から続けて行われてしまう<br>

- 例<br>
```
func main() {
  fmt.Printf("Hello,%さん","ニンジャワンコ")
  fmt.Printf("Hello,%さん","ニンジャ仙人")
}

Hello,ニンジャワンコさん　　Hello,ニンジャ
仙人さん　←一つ目のPrintfで改行されない
```
- \nについて<br>
文字列中で\nを用いると、出力される文字列が改行される（\n自体は出力されない<br>
文字列の末尾に\nを書くと、出力した文字列の最後で改行が行われ、次の出力は次の行から行われる<br>
※\nはどこでも使うことができる※

- 例<br>
```
func main() {
  fmt.Printf("Hello,%さん \n","ニンジャワンコ")
  fmt.Printf("Hello,%さん \n","ニンジャ仙人") // \nは改行されるという意味の特殊な文字
}

Hello,ニンジャワンコさん　　
Hello,ニンジャ仙人さん　// \nの部分で改行される　("\n"という文字列自身は出力されない)
```

- forについて<br>
繰り返し処理とは、一定の処理を自動で繰り返し行う処理のこと<br>

- 例<br>
 ```
 func main() {
 fmt.Printf("Hello")
 fmt.Printf("Hello")
 ↓
 fmt.Printf("Hello")　//何度も書くのが大変
 
 Hello
 Hello
 ↓
 Hello
 ```
 
- for文
Goでは、繰り返し処理のためにfor文を使う<br>
for文では、変数の初期化、繰り返しの条件、変数の更新の3つを指定し、{}の中の処理を繰り返すことができる<br>
例ではまず変数iに1が代入され、「iが4以下」を満たす間{}内の処理が繰り返され、終わるたびに変数の更新「i++」が実行される<br>
その結果、"Hello"が4回表示される<br>

- 例
```
for i := 1; i <= 4; i++ { // i := 1は変数の初期化 i <= 4は繰り返しの条件　i++は変数の更新
  fmt.Println("Hello")　//繰り返したい処理
} 

Hello
Hello
Hello
Hello
```

- 処理の流れ<br>
処理の流れを図解して確認<br>
繰り返しの1周目は変数iは1だが、forの{}の中の処理（③）が終わるたびに、<br>
変数iが更新（④）され1,2,3,4,5と変化していく<br>そしてi <= 5（②）が成立しなくなると自動的に繰り返しが終了する<br>
for文の記述は難しく感じますが、頻繁に使う　<br>

1 変数の変化　→ ２　条件　→ 3 繰り返すの処理　→ ４　→ 変数の更新　２に戻る

- 例　<br>
```
for (1)i := 1; (2)i <= 5; (4)i++ { 
(3)fmt.Println(i)　
}
1
2
3
4
5
```

- 複数の処理<br>
forで繰り返す処理は1つでなくてもOK。forの{}の中に複数の処理を書くとそれを書いた順に繰り返してくれる<br>

- 例<br>
```
func main(){
 for i := 1; i <= 3; i++ {
 fmt.Println("Hello")
 fmt.Println(i)
 }
}

Hello //１回目
1
Hello //2回目
2
Hello　//3回目
3
```

- for文の変数定義の注意点<br>
for文の変数定義では、varを使うことは出来ず、:=を用いた変数定義しか出来ません。varを用いると、エラーが発生する。
※これはGoの決まりなので覚えておく必要がある※

- 例<br>
```
for var int= 1; i <= 3; i++ { //var を用いて変数を定義はfor文では使えない
 fmt.Println("Hello")
```

- rand　パッケージ<br>
プログラムは決められた処理をすることが多い<br>
今回のようにランダムな処理をしたい場合がある。G
oにはランダムな数を扱うためのmath/randというパッケージがある<br>
またランダムな数のことを日本語で乱数と呼ぶ<br>


- 例<br>
```
package main
import "math/rand" ←fmtと同じように""で囲む
```
- 乱数の生成<br>
乱数を使うには、まずmath/randパッケージを、import "math/rand"のようにインポート<br>
そして、 「rand.Intn(10)」と書くことで、0~9までの10個の整数の乱数を生成することができる<br>

- 例<br>
```
package main
import "fmt"
import "math/rand"

func main() {
fmt.Println(){
  fmt.Println(rand.Intn(10)) 0~9の乱数を生成
  fmt.Println(rand.Intn(10))　0~9の乱数を生成
}
※Iは大文字のiなので注意※

1 違う数字
5　違う数字
```

- 乱数の注意点<br>
実は単に「rand.Intn(10)」のように呼び出すだけでは、実行する度に、毎回同じ乱数が生成される

- 例<br>
```
package main
import "fmt"
import "math/rand"

func main() {
  for i:=1; i<= 5; i++ {
   fmt.Println(rand.Intn(10))　0~9の乱数を生成
  }
}
1  毎回同じ順番にランダムになる
３
6
4
7
```
- 完全な乱数を生成する<br>
完全な乱数を生成するために、「rand.Seed(time.Now().Unix())」という1行を追加する必要がある<br>
また、このコードを使うためには「time」パッケージをインポートする必要がある<br>

- 例<br>
```
import "math/rand"
import "time" ←timeパッケージをインポート

func main(){
  rand.Seed(time.Now().Unix())←完全な乱数を生成するためのコード
  for i:=1; i<= 5; i++ {
  fmt.Println(rand.Intn(10))
  }
}
１回目　2回目
１　　　　　　　　３
3    6
４    8 
６    1
９    5
```
