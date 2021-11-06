# 過学習（overfitting)
テスト誤差と訓練後とで学習曲線が乖離すること。

原因
- パラメータ数が多い
- パラメータの値が適切ではない
- ノードが多い
→ネットワークの自由度が高い（層数、ノード数、パラメータの値が多い）

過学習の原因ー重みが大きい値をとることで、過学習が発生することがある。
→学習させていくと重みにバラツキが発生する。重みが大きい値は、学習において重要な値であり、重みが大きいと過学習が起こる。過大評価された重みに基づいてNNが学習してしまう。

過学習の解決策ー誤差に対して正則化を加算することで、重みを抑制する。
→過学習がおこりそうな重みの大きさ以下で重みをコントロールし、かつ重みの大きさにバラツキを出す。

## 正則化
自由度を抑えて、過学習を抑える方法。

![gif latex-12](https://user-images.githubusercontent.com/85814165/140589490-664112e4-23b0-47fc-9bc5-f31cf276a576.gif)

![gif latex-13](https://user-images.githubusercontent.com/85814165/140589573-133c1111-ad5b-431c-8683-1895cc24b543.gif)

誤差関数にpノルムを加える。ノルムは距離を表す。
p = 1の場合、L1正則化（ラッソ回帰）
p = 2の場合、L2正則化（リッジ回帰）という

p1ノルム：x+y：マンハッタン距離
p2ノルム：√(x^2+y^2)：ユーグリット距離

## 正則化の計算

![gif latex-14](https://user-images.githubusercontent.com/85814165/140589977-026c7795-fb25-4e36-8957-d3e8f838d2a4.gif)

![gif latex-15](https://user-images.githubusercontent.com/85814165/140590217-b5b210dd-30c6-45a3-8c7c-20afec3cccaa.gif)

![gif latex-16](https://user-images.githubusercontent.com/85814165/140590269-a5079ede-762d-4c91-af3b-87ee24cbd53a.gif)

![gif latex-17](https://user-images.githubusercontent.com/85814165/140590273-d514d3ca-30db-4057-8e2e-f630ddd0e505.gif)

## コード

![gif latex-13](https://user-images.githubusercontent.com/85814165/140589573-133c1111-ad5b-431c-8683-1895cc24b543.gif)

np.sum(np.abs(network.params["W"+str(idx)]))

![gif latex-14](https://user-images.githubusercontent.com/85814165/140589977-026c7795-fb25-4e36-8957-d3e8f838d2a4.gif)

weight_decay += weight_decay_lambda * np.sum(np.abs(network.params["W"+str(idx)]))

loss = network.loss(x_batch, d_batch) + weight_decay

## ドロップアウト

# 確認テスト
Q.L1正則化を表しているグラフはどちらか答えよ。

![スクリーンショット 2021-11-06 9 10 22](https://user-images.githubusercontent.com/85814165/140590919-ec2bddaf-686f-4039-ae2c-9e75771c775f.png)


Q.サイズ6x6の入力画像をサイズ2x2のフィルタで畳み込んだ時の出力画像のサイズを答えよ。なおストライドとパディングは1とする。

