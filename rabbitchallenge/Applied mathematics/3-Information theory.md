# 応用数学　第三章　情報理論

## 自己情報量
P(x)の確率で起きる自称ｘの自己情報量は以下の式で表される。

![gif latex-30](https://user-images.githubusercontent.com/85814165/138554739-8356f835-de5d-4b8a-be80-5aea103a923d.gif)

logの底が2の時、単位はビット(bit)←通常はこちら
logの底がネイピア数（e)の時、単位はnat

## シャロンエントロピー
自己情報量の期待値のこと。

![gif latex-31](https://user-images.githubusercontent.com/85814165/138554804-7b0f3a06-961f-47e6-ae80-c7754ea08173.gif)

## カルバック・ライブラー情報量（KLダイバージェンス）
2つの確率分布がどの程度似ているかを表す尺度のこと。

![gif latex-32](https://user-images.githubusercontent.com/85814165/138554951-f81012ac-5dc5-4e11-bc9e-a7c0f1b970b5.gif)

## 交差エントロピー（Cross-entropy Loss)
機械学習における予測の誤差として使われることが多い。
正解の分布P、予測の分布Qとした場合、QがPに似ているほど、PとQの交差エントロピーが小さくなる。

![gif latex-34](https://user-images.githubusercontent.com/85814165/138555172-a396a277-b0cf-4911-a691-80bd778e094b.gif)

# 演習問題

## 問7.5
離散的な事象の確率分布をP(x)とした時、シャロンエントロピーはどれか。

解.

![gif latex-35](https://user-images.githubusercontent.com/85814165/138555232-384a7128-59f8-4af8-ba90-2e0ea5dba89f.gif)


