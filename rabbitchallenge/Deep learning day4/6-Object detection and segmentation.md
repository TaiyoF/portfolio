# 物体検知

入力は画像で、モノクロかカラーかは問わない。

- 分類：クラスラベル
- 物体検知：Bounding Box[BB]どこに何があるか
- Semantic Segmentation（意味領域分割）：各ピクセルに対してクラスラベル
- Instance Segmentation（個体領域分割）：各ピクセルに対してラベルを与えて、各々も区別される

難易度は下に行くほど高くなる

## 代表的データセット
物体検出コンペティションで用いられたデータセット

- VOC12：クラス数20,Train+Val 11,540 ,Box/画像 2.4
- ILSVRC17：クラス数200,Train+Val 476,668 ,Box/画像 1.1 (ImageNetのサブセット）
- MS COCO18：クラス数80,Train+Val 123,287 ,Box/画像 7.3
- OICOD18：クラス数500,Train+Val 1,743,042 ,Box/画像 7.0 (Open Images V4のサブセット）

その他もDSはある：CIFAR-10、CIFAR-100、Food-101、楽天データなど。

Box/画像が少ないとアイコン的な写りで現実とはかけ離れている

Box/画像が多いと部分的な重なりもあり、現実に近くなる

| 真値\予測 | Positive | Negative |
| ------------- | ------------- | ------------- |
| Positive  | TP  | FN |
| Negative  | FP  | TN |

Precision = TP/(TP+FP)

Recall = TP/(TP+FN)

物体検出においては、クラスラベルだけではなく、物体位置の予測精度も評価したい。

→IoU = Area of Overlap/ Area of Union

confidenceの閾値だけでなく、IoUの閾値も準備する。

## 物体検知のフレームワーク

- ２段階検出器；検出とクラス推定を別々に行う。相対的に精度が高い傾向。計算量が多く推論も遅い傾向。
- １段階検出器：検出とクラス推定を同時に行う。相対的に精度が低い。計算量が小さく推論も早い。

# Semantic Segmentation

ConvとPoolingを行うことで解像度が落ちていく。

落ちた解像度をどのようにして元の解像度まで戻すのか、Up-samplingを行う。

- Deconvolution/Transposed convolution
- 
![スクリーンショット 2021-12-15 4 41 30](https://user-images.githubusercontent.com/85814165/146068251-4daa9b15-2267-460b-a10e-a0a7577e100b.png)

特徴マップのピクセル感覚をストライド分空ける

特徴マップの周りに（カーネルサイズー１）ーパディング分余白を空ける

畳み込み演算を行う

→逆演算ではない。そのためプーリングで失われた情報が復元される訳ではない。

## Unpooling

プーリングした時の位置情報を保持しておく。

どこが最大の値を持っているかの情報を保持しておく。
