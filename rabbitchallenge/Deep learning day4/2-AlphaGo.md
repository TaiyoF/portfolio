# Alpha Go

強化学習の注目を集めたのがAlpha Go(AlphaGo Lee, AlohaGo Zero)

![スクリーンショット 2021-12-03 15 32 00](https://user-images.githubusercontent.com/85814165/144556408-fa8b1b36-1b42-4dd1-bb82-cb3dad31dc4d.png)

![スクリーンショット 2021-12-03 15 32 12](https://user-images.githubusercontent.com/85814165/144556417-0fa60826-b07c-4ad5-8763-6488eef59553.png)

いずれもCNN。PolicyNetは方策関数。Valuenetは価値関数。

![スクリーンショット 2021-12-03 15 35 52](https://user-images.githubusercontent.com/85814165/144556744-17e5df28-a485-4d78-abd1-b4128890ab57.png)

2次元の情報から、価値関数と方策関数ができる。その後は学習させる。

# AlphaGoの学習ステップ

![スクリーンショット 2021-12-03 16 57 20](https://user-images.githubusercontent.com/85814165/144566329-a7d726ac-6400-4053-8a24-9ffbeb96a812.png)

1.教師あり学習によるRollOutPolicyとPolicy Netの学習

![スクリーンショット 2021-12-03 17 02 28](https://user-images.githubusercontent.com/85814165/144566969-5276fc3d-3051-49b6-8a15-4a437f27ed84.png)

2.強化学習によるPolicyNetの学習

3.強化学習によるValueNetの学習

# 1.PolicyNetの教師あり学習

ネット囲碁対局サイトの棋譜データ3000万局分の教師データを準備し、教師と同じ着手を予測できるよう学習。

教師が着手した手を1とし、残りを0とした19x19次元の配列を教師とし、分類問題として学習。精度は57%。

# 2.PolicyNetの強化学習

現状のPolicyNetとPolicyPoolからランダムに選択されたPolicyNetと対局シミュレーションを行い、その結果を用いて方策勾配法で学習を行った。

PoliyPoolとは、PolicyNetの強化学習の過程を500Iterationごとに記録し保存しておいたもの。

現状のPolicyNet同士の対局ではなく、PolicyPoolに保存したものとの対局を使用する理由は、対局に幅を持たせて過学習を防ぐため。この学習をmini batch size 128で1万回行った。

# 3.ValueNetの学習

PolicyNetを使用して対局シミュレーションを行い、その結果の勝敗を教師として学習した。教師データの作成手順は、

1.SL PolicyNet（教師あり学習で作成したPolicyNet）でN手まで打つ

2.N＋1手目の手をランダムに選択し、その手で進めた局面をS（N＋１）とする。

3.S(N+1)からRL PolicyNet（強化学習で作成したPolicyNet）で終局までうち、その勝敗報酬をRとする。

S(N+1)とRを教師データ対年、損失関数を平均二乗誤差年、回帰問題として学習。この学習をmini batch size = 32で5000万回行った。

N手までとN+1手からのPolicyNetを別々にした理由は、過学習を防ぐため。

# モンテカルロ木探索

Alpha Goのモンテカルロ木探索は、選択・評価・バックアップ・成長という４つのステップで構成される。

![スクリーンショット 2021-12-04 8 50 33](https://user-images.githubusercontent.com/85814165/144687016-9e4a9100-d857-4b47-89a3-9144b9f46933.png)

# AlphaGo LeeとZeroの違い

Zero

1.教師あり学習を行わず、強化学習のみ

2.特徴入力からヒューリスティックな要素を排除し、石の配置のみにした

3.PolicyNetとValueNetを１つのネットワークに統合した

4.ResidualNetを導入した

5.モンテカルロ木探索からRollOutシミュレーションを無くした

# PolicyValueNet

二股に情報を分けて、Policy出力とValue出力を出す。ResidualBlockまでは共通。

![スクリーンショット 2021-12-04 9 01 42](https://user-images.githubusercontent.com/85814165/144687773-c77d3980-bbc0-4323-8354-767a7e013ba4.png)

# Residual Network

ネットワークが増えると勾配消失問題が起こるので、ショートカットを追加して勾配消失や爆発を抑える。

また、Residual Networkを使うことで（ショートカットがあるため）、層数の異なるNetworkのアンサンブル効果が得られる。

![スクリーンショット 2021-12-04 9 03 29](https://user-images.githubusercontent.com/85814165/144687881-77dbe164-43ff-4191-8868-da727df645f4.png)

# Residual Networkの派生形

![スクリーンショット 2021-12-04 9 09 02](https://user-images.githubusercontent.com/85814165/144688227-7a2d4961-7c70-4c4c-9e98-800b2b9db2b4.png)

