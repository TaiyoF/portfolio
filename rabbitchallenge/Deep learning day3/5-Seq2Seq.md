# Seq2Seq

![スクリーンショット 2021-11-28 19 49 54](https://user-images.githubusercontent.com/85814165/143764798-422e5b76-dcf8-4044-945c-8438ae042f0d.png)

エンコーダとデコーダからなる。

用途：機械対話や機械翻訳など

## Encoder RNN

インプットしたテキストデータを単語等のトークンに区切って渡す構造

![スクリーンショット 2021-11-28 19 52 31](https://user-images.githubusercontent.com/85814165/143764887-9aeb140e-88f0-4c20-be86-1b653ce8186d.png)

文の全体の意味が、１つのベクトル表現として保存される。

vec1をRNNに入力し、hidden_stateを出力。このhidden_stateと次の入力vec2をまたRNNに入力し、hidden_stateを出力するを繰り返す。

最後のvecを入れた時のhidden_stateをfinal_stateとして、このfinal_stateがthought_vectorと呼ばれ、入力した文の意味を表すベクトルとなる。

Taking:文章を単語等のトークンごとに分割し、トークンごとのIDに分割する

Embedding:IDからそのトークンを表す分散表現ベクトルに変換する

Encoder RNN:ベクトルを順番にRNNに入力する


## Decoder RNN

システムがアウトプットしたデータを単語ごとのトークンごとに生成する構造

![スクリーンショット 2021-11-28 19 53 28](https://user-images.githubusercontent.com/85814165/143764900-58d3a94a-a526-4425-9e77-f079897a9980.png)

1.Decoder RNN Encoder RNNのfinal_state（thought vector)から各トークンの生成確率を出力する。final_stateをDecorderRNNのinitial_stateとして設定し、Embeddingを入力

2.Sampling:生成確率に基づいてtokenをランダムに選ぶ

3.Embadding:Samplingで選ばれたtokenをEmbeddingし、Decorder RNNへの次の入力とする

4.Detokenize:1-3を繰り返し、2で得られたtokenを文字列に直す

## Seq2seq課題

一問一答しかできない。

→過去の文脈を取れないか？HRED

## HRED

過去(n-1個）の発話から次の発話を生成する。

Seq2seqでは会話の文脈無視で応答がなされたが、HREDでは前の単語の流れに即して応答されるため、より人間らしい文章が生成される。

HRED = Seq2seq + Context RNN

Context RNN:Encoderのまとめた各文章の系列をまとめ、これまでの会話コンテキスト全体を表すベクトルに変換する構造。過去の発話履歴を加味できる。

HREDの課題：確率的な多様性が地面にしかなく、会話の流れのような多様性がない。バリエーションがない。HREDは短く情報量に乏しい答えをしがち。

## VHRED

HREDにVAEの潜在変数の概念を追加したもの。

## オートエンコーダー

オートエンコーダは教師なし学習の一つ。教師データは利用しない。

入力データから潜在変数zに変換するニューラルネットワークをEncorder。逆に潜在変数zをインプットとして元画像を復元するニューラルネットワークをDecorder・

メリット：次元削減が可能。

## VAE

通常のオートエンコーダの場合、何かしら潜在変数zにデータを押し込めているもののその構造がどのような状態かわからない。

VAEは潜在変数zに確率分布z~N(0,1)を仮定したもの。データを潜在変数zを確率分布の構造に押し込めることが可能になる。

# 確認テスト

![スクリーンショット 2021-11-28 20 15 12](https://user-images.githubusercontent.com/85814165/143765523-23bf12a0-5b4d-462b-912d-5e2cf26db8e7.png)

A.2

Q.VAEに関する下記の説明文中の空欄に当てはまる言葉を答えよ

A.自己符号化器の潜在変数に確率分布を導入したもの。

# 演習チャレンジ

![スクリーンショット 2021-11-28 20 16 31](https://user-images.githubusercontent.com/85814165/143765573-bd7f7f05-c5fe-4f6b-9235-58dbd296cd2b.png)

A.1 E.dot(w)


