# 主成分分析
多変量データの持つ構造をより少数個の指標に圧縮
変量の個数を減らすことに伴う、情報の損失をなるべく小さくしたい

2次元だと1次元ベクトル上にプロットすることで圧縮する。

係数ベクトルが変われば、線形変換後の値が変化
線形変換後の変数の分散が最大となる射影軸を探索

## 制約付き最適化問題を解く

目的関数

![gif latex-54](https://user-images.githubusercontent.com/85814165/138611614-169b763d-f930-401e-a2ce-371147579576.gif)

制約条件

![gif latex-55](https://user-images.githubusercontent.com/85814165/138611664-01d200e0-3d4f-4634-946d-c8703d01ec72.gif)

ラグランジュ関数
- この関数を最大にする係数ベクトルを探索（微分して0になる点）

![gif latex-56](https://user-images.githubusercontent.com/85814165/138611709-808c44ef-3215-46eb-b320-5692a7f9ef8e.gif)

## ラグランジュ関数の微分
応用数学で学んだ固有ベクトルの解法になる

![gif latex-57](https://user-images.githubusercontent.com/85814165/138611819-5698d848-6d06-4e42-90c9-bd58dd647f1e.gif)

## 寄与率
どれぐらい圧縮したか
寄与率：第k主成分の分散の全分散に対する割合（第k主成分がもつ情報量の割合）
寄与率(Ck)=第k主成分の分散(λk)/主成分の総分散(λiの合計)

累積寄与率：第1-k主成分までの圧縮した際の情報損失量の割合
累積寄与率(rk)=第1から第kまでの主成分の分散(λjの合計)/主成分の総分散(λiの合計)

## Google Colabでの実装

![スクリーンショット 2021-10-25 7 30 09](https://user-images.githubusercontent.com/85814165/138615539-18d4ac9f-983b-4ea8-8a56-71c30001f378.png)
![スクリーンショット 2021-10-25 7 30 33](https://user-images.githubusercontent.com/85814165/138615542-237056e6-f451-445d-9986-9f09af2e7836.png)
![スクリーンショット 2021-10-25 7 30 45](https://user-images.githubusercontent.com/85814165/138615545-950cf8bc-d98e-4b85-a739-8e25cb2633f5.png)
