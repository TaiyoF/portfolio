# AlexNet
AlexNetは3つの畳み込み層、2つのプーリング層、3つの全結合層から構成されているモデル。

入力画像は224x224サイズの正方形で、出力は1,000個の要素を持つ1次元ベクトル。

現在はVGGNetやResNetが主流。（AlexNetはCNNの火付け役）

![スクリーンショット 2021-11-23 16 30 09](https://user-images.githubusercontent.com/85814165/142985306-3044ed27-7b39-4615-aa07-baa0223e19bb.png)

入力:224x224に正規化した3channelカラー画像

Conv1:畳み込み層　[11x11]カーネルx96channel, stride=4, padding=2

活性化関数:Relu+局所応答正規化

P1:プーリング層 重なりあり最大値プーリング,[3x3]カーネル, stride=2

Conv2:畳み込み層　[5x5]カーネルx256channel, stride=1, padding=2

活性化関数:Relu+局所応答正規化

P2:プーリング層 重なりあり最大値プーリング,[3x3]カーネル, stride=2

Conv3:畳み込み層　[3x3]カーネルx96channel, stride=1, padding=1

Conv4:畳み込み層　[3x3]カーネルx96channel, stride=1, padding=1

Conv5:畳み込み層　[3x3]カーネルx96channel, stride=1, padding=1

P3:プーリング層 重なりあり最大値プーリング,[3x3]カーネル, stride=2

*学習時のみDropout

FC6:全結合層　9216(=256x6x69) v.s. 4096

活性化関数:Relu

*学習時のみDropout

FC6:全結合層　4096 v.s. 4096

活性化関数:Relu

FC6:全結合層　4096 v.s. 1000

出力:softmax関数で確率化した1000次元ベクトル（各次元の出力確率）

