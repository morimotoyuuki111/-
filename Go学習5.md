５月２5日~26日　木曜日　Go言語学習
- 学んだこと
- 文字列の入力
- 関数
- 引数
- 戻り値
- 値を渡す　

- 詳細
- 文字列の入力
fmt.Scan(&変数名)を使うとコンソールでの入力ができる

- 例
 ```　
 var input string
 fmt.Scan(&input) ←①fmt.Scan(&変数名)でコンソールへ文字入力ができる
 
 ② コンソール画面　dog　(文字列を入力)
 ③②のdogが変数inputに代入される
```

- 流れ
```　
① fmt.Println("次の単語を入力してください:dog")
②fmt.Scan(&input) ←ユーザーが入力してEnterキーを押すまで、ここで止まる
③fmt.Printf("%sと入力されました",input)
```

- 関数
関数とはいくつかの処理をまとめたもの
処理を関数にまとめると、何度でも使える。

-　例
```
func main () {
 var input string
 fmt.Println("次の単語を入力してください　:dog")
 fmt.Scan(&input)
 fmt.Printf("%sと入力されました", input)
}
```
