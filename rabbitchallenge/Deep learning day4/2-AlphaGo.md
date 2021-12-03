# Alpha Go

強化学習の注目を集めたのがAlpha Go(AlphaGo Lee, AlohaGo Zero)

![スクリーンショット 2021-12-03 15 32 00](https://user-images.githubusercontent.com/85814165/144556408-fa8b1b36-1b42-4dd1-bb82-cb3dad31dc4d.png)

![スクリーンショット 2021-12-03 15 32 12](https://user-images.githubusercontent.com/85814165/144556417-0fa60826-b07c-4ad5-8763-6488eef59553.png)

いずれもCNN。PolicyNetは方策関数。Valuenetは価値関数。

![スクリーンショット 2021-12-03 15 35 52](https://user-images.githubusercontent.com/85814165/144556744-17e5df28-a485-4d78-abd1-b4128890ab57.png)

![スクリーンショット 2021-12-03 15 36 17](https://user-images.githubusercontent.com/85814165/144556804-8a51a1a5-dd9a-43db-921c-062d6d762a9f.png)

2次元の情報から、価値関数と方策関数ができる。その後は学習させる。

# AlphaGoの学習ステップ

![スクリーンショット 2021-12-03 16 57 20](https://user-images.githubusercontent.com/85814165/144566329-a7d726ac-6400-4053-8a24-9ffbeb96a812.png)

1.教師あり学習によるRollOutPolicyとPolicy Netの学習

![スクリーンショット 2021-12-03 17 02 28](https://user-images.githubusercontent.com/85814165/144566969-5276fc3d-3051-49b6-8a15-4a437f27ed84.png)

2.強化学習によるPolicyNetの学習

3.強化学習によるValueNetの学習

# PolicyNetの強化学習

現状のPolicyNetとPolicyPoolからランダムに選択されたPolicyNetと対局シミュレーションを行い、その結果を用いて方策勾配法で学習を行った。

PoliyPoolとは、PolicyNetの強化学習の過程を500Iterationごとに記録し保存しておいたもの。

現状のPolicyNet同士の対局ではなく、PolicyPoolに保存したものとの対局を使用する理由は、対局に幅を持たせて過学習を防ぐため。この学習をmini batch size 128で1万回行った。

# ValueNetの学習

PolicyNetを使用して対局シミュレーションを行い、その結果の勝敗を教師として学習した。教師データの作成手順は、

1.SL PolicyNet（教師あり学習で作成したPolicyNet）でN手まで打つ

2.N＋1手目の手をランダムに選択し、その手で進めた局面をS（N＋１）とする。

3.S(N+1)からRL PolicyNet（強化学習で作成したPolicyNet）で終局までうち、その勝敗報酬をRとする。

S(N+1)とRを教師データ対年、損失関数を平均二乗誤差年、回帰問題として学習。この学習をmini batch size = 32で5000万回行った。

N手までとN+1手からのPolicyNetを別々にした理由は、過学習を防ぐため。

