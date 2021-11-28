# 再帰型ニューラルネットワーク　RNN について

# 再帰型ニューラルネットワークの概念
## RNNとは
時系列データに対応可能なニューラルネットワークのこと。

時系列データとは、時間的順序を追って一定間隔ごとに観察され、相互に統計的依存関係が認められるようなデータの系列のこと。

例）音声データ、テキストデータ、株価など

![スクリーンショット 2021-11-25 4 58 23](https://user-images.githubusercontent.com/85814165/143305438-ced335b9-a47c-4f36-908d-f95e3c032295.png)

上図は左右で同じことを表現している。

![スクリーンショット 2021-11-27 20 43 16](https://user-images.githubusercontent.com/85814165/143679808-956b7827-3363-49a8-b24e-d069f802ec69.png)

## RNNの特徴

時系列モデルを扱うために、初期の状態と過去の時間t-1の状態を保持し、次の時間でのtを再帰的にに求める再帰構造が必要。

## BPTTとは

RNNにおいてのパラメータ調整方法の一種（誤差逆伝搬の一種）

## BPTTの数学的記述

![スクリーンショット 2021-11-28 14 42 42](https://user-images.githubusercontent.com/85814165/143731146-45cc5758-ad0e-4ce8-877e-1c161cf7e9d0.png)

![gif latex-3](https://user-images.githubusercontent.com/85814165/143731828-0a849241-e775-4146-be16-03b8935ab311.gif)

パラメータの更新式

![スクリーンショット 2021-11-28 15 22 54](https://user-images.githubusercontent.com/85814165/143732007-f63d3f74-3aae-4e59-836a-5bf85911d48f.png)

## BPTTの全体像

![gif latex-4](https://user-images.githubusercontent.com/85814165/143732147-c7ba6ff3-9e34-4f05-81e7-e56ea5651a01.gif)

![gif latex-5](https://user-images.githubusercontent.com/85814165/143732194-ae838aac-9a7a-4552-a1d8-51c65fd34736.gif)


# 確認テスト

Q.サイズ5x5の入力画像を、サイズ3x3のフィルタで畳み込んだ時の出力画像のサイズを答えよ。なおストライドは2, パディングは1とする。

A.3x3

Q.RNNのネットワークには大きく分けて3つの重みがある。1つは入力から現在の中間層を定義する際にかけられる重み、1つは中間層から出力を定義する際にかけられる重みである。残り1つの重みについて説明せよ。

A.前回の中間層からの重み

Q.連鎖律の原理を使い、dz/dxを求めよ　z=t^2 t=x+y

dz/dx=dx/dt・dt/dx

dx/dt=2t

dt/dx=1

から、dz/dx=2t・1=2t=2(x+y)


Q.下図のy1をx,z0,w_in,w,w_outを用いて数式で表せ。

![スクリーンショット 2021-11-25 4 58 23](https://user-images.githubusercontent.com/85814165/143305438-ced335b9-a47c-4f36-908d-f95e3c032295.png)

![gif latex-2](https://user-images.githubusercontent.com/85814165/143731671-6828a8ae-d507-44ea-89dd-5a0eda43dd72.gif)

# 演習チャレンジ

![スクリーンショット 2021-11-27 21 26 37](https://user-images.githubusercontent.com/85814165/143681243-bf531ea2-18ee-4d3c-8c56-bf44e7baaf6c.png)

A.2 W.dot(np.concatencate([left, right]))


![スクリーンショット 2021-11-28 15 22 54](https://user-images.githubusercontent.com/85814165/143732515-33cb7c8b-9fed-42f0-935c-cc35b2693cc3.png)

A.2 delta_t.dot(U)

# 実装
3_1_simple_RNN.ipynb



