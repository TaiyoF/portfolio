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

## 尤度関数を最大化させる（最尤推定）
対数をとると微分の計算が簡単になる。
- 同時確率の積が和に変換できる
- 指数が積の演算に変換できる
- 対数関数は単調増加のため、対数尤度関数が最大になると尤度関数が最大になる
- 尤度関数にマイナスをかけたものを最小化し、最小二乗法の最小化と合わせる

![gif latex-50](https://user-images.githubusercontent.com/85814165/138592120-5f96030d-3776-4bc0-b5c6-d53addeb26f4.gif)

## 勾配降下法
反復学習によりパラメータを逐次的に更新するアプローチの一つ。
パラメータが更新されなくなった場合、それは勾配が0になったということ、最適な解が求められたということ。

## 確率的勾配降下法（SGD）
勾配降下法のうち、データを１つずつランダムに選びパラメータを更新する方法。

## モデル評価
-TP TruePositive 真陽性　正しくPositiveと判別
-TN TrueNegative 真陰性　正しくNegativeと判別
-FP FalsePositive 偽陰性　間違えてPositiveと判別してしまった (正常な人を間違えて異常としてしまう→確認の工数がかかる）
-FN FalseNegative 偽陽性　間違えてNegativeと判別してしまった（異常な人を間違えて正常としてしまう→異常者を漏らしてしまう）

正解率がよく使われる
正解した数/全データ数

![gif latex-51](https://user-images.githubusercontent.com/85814165/138592518-82dd7e22-4f54-4135-9b42-73c2dc3628c9.gif)

課題）全データが100件で、スパム数が80件の場合、すべてスパムと判断すると正解率が80%となってしまう。

- リコール、プレシジョンを使って評価する。

## 再現率（Recall：リコール）
本当にPositiveの中からPositiveと予測できる割合
誤り（FP）が多少多くても抜け漏れが少ないという予測をしたい場合に利用
例）病気診断：陽性であるものを陰性と誤診してしまうのを避けたい。

![gif latex-52](https://user-images.githubusercontent.com/85814165/138592638-7b5b7aed-a85d-418a-8055-f1dfc5c2eb9a.gif)

## 適合率（Precision:プレシジョン）
モデルがPositiveと予測したものの中で本当にPositiveである割合
見逃し（FN）が多いことより、より正確な予測をしたい場合に利用
例）スパム診断：重要なメールがスパムと誤判別されるより、スパムと予測されたものが確実にスパムである方が便利

![gif latex-53](https://user-images.githubusercontent.com/85814165/138592827-ccee7e53-bdbe-48d8-9b15-14d7ab1521f0.gif)

## F値
理想的にはどちらも高いモデルが良いモデル。だが、トレードオフの関係。
PrecisionとRecallの調和平均：バランスを示す。

## GoogleColabで実装
- Colabのタイトルでおかしなところがありますが、保管をお願いします。

![スクリーンショット 2021-10-24 21 48 49](https://user-images.githubusercontent.com/85814165/138594963-b61d3cc8-b831-4c3e-9ee8-c9b01439e1ce.png)
![スクリーンショット 2021-10-24 21 49 00](https://user-images.githubusercontent.com/85814165/138594970-34f66f21-600f-4a43-a7cb-a05d70af8670.png)
![スクリーンショット 2021-10-24 21 49 09](https://user-images.githubusercontent.com/85814165/138594972-b6de0868-45c2-4d60-8fe1-f2deedcf64a4.png)
![スクリーンショット 2021-10-24 21 49 18](https://user-images.githubusercontent.com/85814165/138594975-0e88bb91-3c1d-46a2-b50a-19a4f148efa2.png)
![スクリーンショット 2021-10-24 21 49 24](https://user-images.githubusercontent.com/85814165/138594979-dca5b6e4-317b-4f74-9d29-8b290f635d53.png)
![スクリーンショット 2021-10-24 21 49 33](https://user-images.githubusercontent.com/85814165/138594982-c25dc96d-92f9-4f06-9bee-fe4afc5faab7.png)
![スクリーンショット 2021-10-24 21 49 44](https://user-images.githubusercontent.com/85814165/138594983-0f4f025e-0aac-4a69-b2db-e34e3007950a.png)
![スクリーンショット 2021-10-24 21 49 51](https://user-images.githubusercontent.com/85814165/138594986-b85cca03-e11a-418a-9822-33549e275ac1.png)
![スクリーンショット 2021-10-24 21 50 01](https://user-images.githubusercontent.com/85814165/138594991-26e19cfa-f933-468e-ba69-c86af31d3c46.png)


