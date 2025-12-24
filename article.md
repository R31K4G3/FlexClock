[TUT (powered by LinuxClub) Advent Calendar 2025](https://adventar.org/calendars/12000) 24 日目の記事(?)です (間に合いませんでした) 。

## 12時間表記や時計の「12」について
12月24日……  
12, 24 といえば 12時間表記と24時間表記ですよね。  
12時間表記について，私は気に食わないところがあります。  
24時間表記でいう 23:59 → 00:00 のところと，11:59 → 12:00 のところで「午前」と「午後」が切り替わりますよね？  
でも，時分の「時」のカウントは，24時間表記でいう 00:59 → 01:00 のところと，12:59 → 13:00 のところでリセットされます。

<img width="1348" height="169" alt="12時間表記と24時間表記についての表" src="https://github.com/user-attachments/assets/544fbaf5-c208-45d9-8e91-6e69e2c4379b" />

このズレが嫌です。  
以下のようであるべきです。

<img width="1349" height="171" alt="12時の部分が0時に置き換わった12時間表記と24時間表記についての表" src="https://github.com/user-attachments/assets/155e7592-b747-4480-95ce-57dddb453c0e" />

時計も同様です。

<img width="210" alt="時計の画像" src="https://github.com/user-attachments/assets/c06870e0-f93c-4ab6-8426-416d33e9a3d9" />

こうあるべき。 (下)

<img width="210" alt="12時の部分が0時に置き換わった時計の画像" src="https://github.com/user-attachments/assets/123ca917-c93c-4d92-93ce-ebac5b05547f" />

## 本題(?)

ということで(?)，時計の 0 or 12 を選択できるWebページ時計を作りたいなと思ったので，作りました。  
他にも 10 進法で表すのか N 進法で表すのか，１日に短針が何週するか，１週が何時間か，１時間が何分か，１分が何秒かなども変えられるようにしました。

https://r31k4g3.github.io/FlexClock/

使ったものは HTML + CSS + バニラの JavaScript で，時計の描画には Canvas API を使っています。

時計の描画について軽く書いておきます。  
00:00 を 0，24:00 を 1 として表したときの現在の時刻にあたる値を `p` とすると，  
`p` に「１日に短針が何週するか」「１週が何時間か」「１時間が何分か」を乗じたものが各針の角度です (360度を1とする) 。  
あとは $2 \pi$ をかけて `Math.sin(θ)` と `Math.cos(θ)` を使えば針を描画できますね。  
`CanvasRenderingContext2D` の `arc(...)` や `fillText(...)` などを使えば文字盤も。

## 最後に

製作途中で変なバグを見つけたので，乗せておきます。

<img width="716" height="819" alt="文字盤の文字が全てundefinedに置き換わっている時計" src="https://github.com/user-attachments/assets/78a00987-8953-497e-ba0c-6ae3a31a7b25" />

[TUT (powered by LinuxClub) Advent Calendar 2025](https://adventar.org/calendars/12000) ，次回は，すみsann です。
