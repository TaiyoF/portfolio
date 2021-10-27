# サポートベクターマシーン(SVM)
SVMとは教師あり学習の一つ、分類と回帰で優れた性能をもつアルゴリズム。
2クラス分類問題の手法の一つ、未知データに対して高い予測精度を持つ関数を構築できる。
現在では、回帰問題や教師なし問題などにも応用されている。

## マージン最大化
データを2クラスに分類したときに、両クラスのデータ点から最も遠い位置に境界線を引くこと。
マージンが大きいほど良い分類境界となる。なるべく大きいマージンを持つ分類境界を探索することをマージン最大化という。

![gif latex-58](https://user-images.githubusercontent.com/85814165/138866014-425a1e2a-01f9-4485-a8e3-c8575a188bc8.gif)

||w||はwのL2ノルムを表す。

![gif latex-59](https://user-images.githubusercontent.com/85814165/138866195-98722be6-d35e-4fc0-a446-c81b0ff6fe3a.gif)

![gif latex-60](https://user-images.githubusercontent.com/85814165/138866967-2024e72c-e31d-459b-afd6-d17fded738eb.gif)

この右辺のM(w,b)を大きくすると良いが、次の制約条件を満たせなくなる。

![gif latex-61](https://user-images.githubusercontent.com/85814165/138867970-15bb2a8f-ef2d-4558-b29c-e5e0cb0eeafd.gif

式変形し、最終的には以下式となる。
![gif latex-62](https://user-images.githubusercontent.com/85814165/138868378-8689860b-7b4e-4616-8d32-12b043dde88a.gif)

分類境界![gif latex-64](https://user-images.githubusercontent.com/85814165/138868684-53ae8076-89ae-487a-b220-b85f07b12986.gif)と分類境界から最も近くにある![gif latex-63](https://user-images.githubusercontent.com/85814165/138868599-87233ca4-231c-4cfd-bff2-9947c84878a3.gif)との距離の最大化。

また、分類境界に最も近いデータ以外を取り除いてしまってもSV分類によって得られる分類境界は変化しないため、分類境界に最も近いデータ![gif latex-63](https://user-images.githubusercontent.com/85814165/138868906-441fd119-934b-4a61-a6c1-4c6d4576f60c.gif)が分類境界を支えていると考えられるため、この![gif latex-63](https://user-images.githubusercontent.com/85814165/138869006-0e87fb9a-d974-4582-8313-2b0db80326cc.gif)のことをサポートベクターと呼ぶ。

## 線形サポートベクトル分類（ソフトマージン）
上記の式を元に、多少の分類誤りを許容する。ξはマージン内に入るデータや誤分類データに対する誤差を表す変数のことで、スラック変数と呼ばれる。

![gif latex-65](https://user-images.githubusercontent.com/85814165/138873497-a225da00-9bb0-4e43-9276-a81b4732e4f7.gif)

ハードマージンでは分類境界とその分類境界に最も近い![gif latex-63](https://user-images.githubusercontent.com/85814165/138873575-9a8e1f08-172c-47ba-bccd-116c7f1d740c.gif)との距離を用いた。ソフトマージンでは、![gif latex-66](https://user-images.githubusercontent.com/85814165/138873729-c03551e2-7028-4307-b9a4-a4193c6f4f0c.gif)の間の距離をマージンと解釈する。

このマージンを最大化しつつ、分類の誤差ξを最小化するように分類境界を決定する。

![gif latex-68](https://user-images.githubusercontent.com/85814165/138875488-3f778de8-36b4-4a45-a0b9-610cf1be9cf1.gif)

係数Cは正則化係数で、学習前に値を与える必要のあるハイパーパラメータ。正則化係数Cがξがなるべく小さくなるように抑制する度合いを調整するパラメータ。
Cが大きいほどハードマージンに近づく。Cが小さいとより誤分類が許容されやすくなる。ちょうど良いCの値を調整する必要がある。

## カーネル法（カーネルトリック）
2つの特徴量を3,4,5,...と増やしてトリックのように高次元にし、2次元では線、3次元では面、高次元なら超平面で境界を作る。
線形分離でうまく分類できないケースがあり、特徴ベクトルを非線形変換して非線形分離を行うことも。

高次元への拡張は、写像（map）という。

![gif latex-69](https://user-images.githubusercontent.com/85814165/138878425-f876a8a0-d86b-4e07-8816-ab0b61e838ad.gif)

xは元の特徴ベクトルを表す。
![gif latex-70](https://user-images.githubusercontent.com/85814165/138878711-4069202f-313c-4057-a7db-92efb717b60e.gif)

xから高次元データへ写像する関数を上記のφ(x)とする。

カーネル関数という関数で、難解な最適化問題を置き換えることが可能。

![gif latex-71](https://user-images.githubusercontent.com/85814165/138879703-10fffff6-32f4-4c41-9f79-5ff31c604c29.gif)

このカーネル関数（内積なのでスカラー）を用いることで、2つのφ(x)を直接計算することなく内積を見積もることが可能になる。

![gif latex-72](https://user-images.githubusercontent.com/85814165/138880054-f3b412ff-5eba-4526-ba66-e0e319d570c1.gif)

多項式カーネル

![gif latex-73](https://user-images.githubusercontent.com/85814165/138880285-88984926-6d4e-46af-82c6-44039dc3a23a.gif)

ガウスカーネル

![gif latex-74](https://user-images.githubusercontent.com/85814165/138880349-6462eff4-5191-4436-abb3-35585fe0ef38.gif)

シグモイドカーネル

![gif latex-75](https://user-images.githubusercontent.com/85814165/138880593-27658ee9-6983-49db-bb0d-e4b4f49802b6.gif)

c,d,γはハイパーパラメータで事前に決める必要がある。

## 実装演習
np_svm.ipynbを参考にコーディングする

![スクリーンショット 2021-10-27 21 03 17](https://user-images.githubusercontent.com/85814165/139062097-306f7726-3435-4b28-944d-a46daebc6809.png)
![スクリーンショット 2021-10-27 21 03 31](https://user-images.githubusercontent.com/85814165/139062108-6634e8c8-5624-4909-a1cb-50265b7e7e72.png)
![スクリーンショット 2021-10-27 21 03 45](https://user-images.githubusercontent.com/85814165/139062114-4a878911-9587-483a-aeb9-77346ecdaab0.png)
![スクリーンショット 2021-10-27 21 03 54](https://user-images.githubusercontent.com/85814165/139062123-e0b6ec6d-3403-4e51-ae47-fd016697fdac.png)
![スクリーンショット 2021-10-27 21 04 04](https://user-images.githubusercontent.com/85814165/139062127-ee1b6f37-d3bb-4513-8bcf-e63a74ecb5a7.png)
![スクリーンショット 2021-10-27 21 04 12](https://user-images.githubusercontent.com/85814165/139062134-0e58b0b8-7f06-444d-bdfa-c1901d598176.png)
![スクリーンショット 2021-10-27 21 04 23](https://user-images.githubusercontent.com/85814165/139062151-489ea5e1-b7df-4fac-b58d-2bbd30b37e90.png)
