確認テストは最後にまとめています。

# モデル

## 識別モデル
- 決定木
- ロジスティック回帰
- SVM
- NN
画像認識

## 生成モデル
- 隠れマルコフモデル
- ベイジアンネットワーク
- 変分オートエンコーダ(VAE)
- 敵対的生成ネットワーク(GAN)
画像の超解像、テキスト生成

# 識別器の開発アプローチ

## 識別モデル
p(Ck|x)を推定
決定理論に基づき識別結果を得る
- データがクラスに属する確率
- 確率的な識別

## 識別関数
入力値xを直接クラスに写像（変換）する関数f(x)を推定
-　データの属するクラスの情報のみ（確率は計算されない）
-　学習量が少ない
-　決定的な識別

## 生成モデル
p(x|Ck) p(Ck)を推定
ベイズの定期より、p(Ck|x)=p(x|Ck)p(Ck)/p(x)
ただしp(x)=Σp(x|Ck)p(Ck)
-　各クラスの生起確率
-　データのクラス条件付き密度
-　データを人工的に生成できる
-　確率的な識別

## 万能近似定理と深さ
活性化関数をもつような関数を使うことでうまいこと近似できるのではないか？

# 深層学習（NN）
入力層、中間層、出力層に分かれている。
学習を行うのは、w(weight：重み)とb(bias：バイアス)
多数の中間層を持つNNを用いて、入力値から目的とする出力値に変換する数学モデルを構築すること。

## NNでできること
- 回帰
  - 結果予測・・売上予測、株価予測
  - ランキング・・競馬順位予測、人気順位予測
- 分類
  - 猫写真の判別
  - 手書き文字認識
  - 花の種類分類

## 回帰分析
・線形回帰
・回帰木
・ランダムフォレスト
・NN

## 分類
・ベイズ分類
・ロジスティック回帰
・決定木
・ランダムフォレスト
・NN

## 4つ以上の中間層を持つものを深層学習という。
- 自動売買（トレード）
- チャットボット
- 翻訳
- 音声解釈
- 囲碁・将棋AI

# 入力層〜中間層
ノードの重要性に応じて、重みwの値を変化させて中間層に出力する。

![gif latex-76](https://user-images.githubusercontent.com/85814165/139436436-939918bb-0088-4572-82ee-f8067f2bda48.gif)


## 確認テスト
Q.ディープラーニングは、結局何をやろうとしているか。

A.中間層が多数存在する多層構造のニューラルネットワークを用いた機械学習のことで、最終的な出力層で正解が求まるように、重みとバイアスを調整する作業を行っている。（入直値から目的とする出力値に変換する数学もモデルを構築すること）

Q.どの値の最適化が最終目的か？

A.③重み[W]　④バイアス[b]　の最適化が目的

Q.次のネットワークを書け
入力層：2ノード1層
中間層：3ノード2層
出力層：1ノード1層

<img width="828" alt="スクリーンショット 2021-10-29 21 17 10" src="https://user-images.githubusercontent.com/85814165/139432868-8d1f6155-0749-42a1-bb4f-524968bab2a7.png">

Q.図式に動物分類の実例を入れてみよう

<img width="675" alt="スクリーンショット 2021-10-29 21 54 22" src="https://user-images.githubusercontent.com/85814165/139438176-95a9e67a-ada2-4fca-a3fd-6ecb98cf0e70.png">

Q.数式をPythonで書け

![スクリーンショット 2021-10-29 21 58 05](https://user-images.githubusercontent.com/85814165/139438750-01c94b9e-c73b-4055-bfe5-65576c170637.png)

Q.1-1のファイルから中間層の出力を定義しているソースを抜き出せ

![スクリーンショット 2021-10-29 22 01 34](https://user-images.githubusercontent.com/85814165/139439358-51e9660e-f15d-4654-81c5-13890dee8dd5.png)