# Seq2seq

Sequence to Sequence；系列を出力するもの。　翻訳業務や音声データ、チャットボットに利用される。

![スクリーンショット 2021-12-15 4 58 25](https://user-images.githubusercontent.com/85814165/146070545-6c05768d-247d-4ca6-8c66-bac8ec193d71.png)

RNNの理解と言語モデルの理解が必要

言語モデルとは、単語の並びに確率を与える、時刻t-1までの情報で、時刻tの事後確率を求めることが目標で、同時確率が計算できる。

## RNN x 言語モデルまとめ
- 系列情報を内部情報に変換できる
- 文章の書く単語が現れる同時確率は、事後確率で分解できる
- 言語モデルを再現できるようにRNNの重みが学習されている。次の単語を予測することができる。

# Seq2seq

RNNが2つ連結したもの。EncoderとDecoderがある。文章がEncodeされた情報（h）がDecoderの入力に渡される。

![スクリーンショット 2021-12-15 5 10 56](https://user-images.githubusercontent.com/85814165/146072190-0068e131-eb38-4b96-afb8-e428556a46fb.png)

Decoderのoutput側に正解を当てれば教師あり学習がEnd2endで行える。

![スクリーンショット 2021-12-15 5 13 42](https://user-images.githubusercontent.com/85814165/146072522-0901057a-4ffc-4d06-affa-5575d2340ef7.png)

# Transformer

ニューラル機械翻訳は長さの弱い。

## Attention

翻訳先の各単語を選択する際に、翻訳元の文中の各単語の隠れ状態を利用する。

辞書オブジェクト。query（検索クエリ）に一致するkeyを索引し、対応するvalueを取り出す操作。

## Attetion is all you need

2017年6月に登場し、RNNを利用しない。Attentionのみ。

![スクリーンショット 2021-12-17 7 40 32](https://user-images.githubusercontent.com/85814165/146459626-08cf3e41-fe44-48bb-bb84-09e9d28f004e.png)

## Self-Attetion

入力を全て同じにして学習的に注意箇所を決めていく。

## Scaled dot product attention

全単語に関するAttentionをまとめて計算する。

## Multi Head Attention

重みパラメタの異なる8個のヘッドを使用。

8個のScaled dot product Attentionの出力をConcat


# 演習 seq2seq

![スクリーンショット 2021-12-18 21 22 13](https://user-images.githubusercontent.com/85814165/146640896-0e8ad37d-0957-4c44-9b85-04af14d42ad1.png)
![スクリーンショット 2021-12-18 21 22 32](https://user-images.githubusercontent.com/85814165/146640900-9f209bb3-c7c5-47e5-b835-f7757a7093dc.png)
![スクリーンショット 2021-12-18 21 22 40](https://user-images.githubusercontent.com/85814165/146640903-bb467b81-562c-4547-85f3-7c376bb6aae7.png)
![スクリーンショット 2021-12-18 21 22 51](https://user-images.githubusercontent.com/85814165/146640907-2d72589c-3d98-4f5c-bbe5-d098c0e2f999.png)
![スクリーンショット 2021-12-18 21 23 04](https://user-images.githubusercontent.com/85814165/146640910-ca5bef03-9440-4aee-81a0-91e818398c6b.png)
![スクリーンショット 2021-12-18 21 23 16](https://user-images.githubusercontent.com/85814165/146640912-217463f2-8cdb-49f5-8671-9d029063cc20.png)
![スクリーンショット 2021-12-18 21 23 30](https://user-images.githubusercontent.com/85814165/146640916-9a3addad-7a80-4a5f-9162-fa43c021e92d.png)
![スクリーンショット 2021-12-18 21 23 39](https://user-images.githubusercontent.com/85814165/146640925-8b5d6c05-b211-49ba-b29f-7589b4d04646.png)
![スクリーンショット 2021-12-18 21 23 48](https://user-images.githubusercontent.com/85814165/146640927-22d2a0b1-a188-41dc-8f7e-eb5d7c2748e3.png)
![スクリーンショット 2021-12-18 21 24 00](https://user-images.githubusercontent.com/85814165/146640928-50a6ef35-fe81-4c16-ae82-03f06873283b.png)

