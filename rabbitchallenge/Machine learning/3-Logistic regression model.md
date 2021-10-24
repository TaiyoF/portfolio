# ロジスティック回帰モデル
分類問題（クラスに分類する問題）
出力は0 or 1 # タイタニックやIRIS

![gif latex-43](https://user-images.githubusercontent.com/85814165/138582791-8b99ab35-69ab-4812-8b8c-b22e78f63e12.gif)

### ロジスティック線形回帰モデル
入力とm次元パラメータの線形結合をシグモイド関数に入力
- シグモイド関数とは実数かつ0~1の間の値を出力する。
- 単調増加関数（ｘが増える毎にｙが増える）
- aを増加させると、x=0付近で曲線の勾配が増加する。
- ![gif latex-44](https://user-images.githubusercontent.com/85814165/138582852-3c78afbd-939f-49df-a6f7-e4352bff0da5.gif)

### シグモイド関数の性質
シグモイド関数の微分は、シグモイド関数の式となるため。

![gif latex-45](https://user-images.githubusercontent.com/85814165/138590049-799cc73d-0470-4414-a87f-4f4e945b465b.gif)

### ロジスティック回帰の考え方
Y=1になる確率を求めたい.xとｗは線形回帰になる。

![gif latex-46](https://user-images.githubusercontent.com/85814165/138591268-7de14122-2298-48c6-89a6-c52784a43ca3.gif)

## 最尤推定（さいゆう推定）
ロジスティック回帰モデルはベルヌーイ分布を利用する。
- ex)様々な確率分布がある.正規分布、t分布、ガンマ分布、一様分布、ディリクレ分布・・・

![gif latex-47](https://user-images.githubusercontent.com/85814165/138591445-2fc59b08-1b3d-40c9-8b2a-b1f7ecebe8da.gif)

もっともらしい（尤もらしい）分布を推定したい。

## 同時関数
あるデータが得られた時、それが同時に得られる確率
- コイントスの確率（確率変数は独立であるため、前回の試行が今回の試行に影響しないため）
既知の確率pから、未知のyを求める。

## 尤度関数（ゆうど関数）
p（確率）を未知とし、既知なyから求める。

![gif latex-48](https://user-images.githubusercontent.com/85814165/138591748-beeeca73-22a8-4d47-a30f-8961f9979fc1.gif)

![gif latex-49](https://user-images.githubusercontent.com/85814165/138591959-7649a85a-58b8-43a9-a99c-9b3b75cc5833.gif)

対数をかけたものを最大化させる。

## 尤度関数を最大化させる
対数をとると微分の計算が
