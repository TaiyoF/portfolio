# 学習率最適化手法
optimizer
学習率の値が大きすぎる・・最適値にいつまでも到達できず、発散してしまう。
学習率の値が小さすぎる・・発散することはないが、収束するまでに時間がかかってしまう。極小点を最適と見てしまうため、大域局所最適値に収束しづらくなる。

- 初期の学習率を大きく設定し、徐々に学習率を小さくしていく。
- パラメータ毎に学習率を可変させる。

## モメンタム
メリット：局所的最適解にならず、大域的最適解となる。谷間についてから最も低い値（最適値）に到達するまでの時間が早い。

誤差をパラメータで微分したものと学習率の積を減算した後、現在の重みに前回の重みを減算した値と慣性の積を加算する。

![gif latex-6](https://user-images.githubusercontent.com/85814165/140569963-f38c4a8c-2e14-4189-9086-b6d204f7fd2d.gif)

self.v[key] = self.momentum * self.v[key] - self.learning_rate * grad[key]

![gif latex-7](https://user-images.githubusercontent.com/85814165/140569998-48463342-ede4-4c4b-aefe-3d9a45d24c3d.gif)

params[key] += self.v[key]

μは慣性

## AdaGrad
メリット：勾配の緩やかな斜面にたいして、最適値に近づける。
課題：学習率がジョジョに小さくなるので、鞍点問題（あんてんもんだい）を引き起こす。

誤差をパラメータで微分したものと再定義した学習率の積を減算する。

![gif latex-8](https://user-images.githubusercontent.com/85814165/140571338-57122eba-9a58-466a-8d8a-950a8948dfe3.gif)

θは最初適当な値を決める。上手く調整しないと上手く動かないことがある。

self.h[key] = np.zeros_like(val) #適当な値を決めれる zeros_like

![gif latex-9](https://user-images.githubusercontent.com/85814165/140571418-11bf34bf-f190-4177-862d-026121dd16ef.gif)

self.he[key] += grad[key] * grad[key]

![gif latex-10](https://user-images.githubusercontent.com/85814165/140571559-4bd23419-e2a1-4f2d-b571-b514222d07fe.gif)

params[key] -= self.learning_rate * grad[key]/(np.sqrt(self.h[key]) + 1e-7)

## RMSProp
メリット：局所最適解にならず、大域的最適解となる。ハイパーパラメータの調整が必要な場合が少ない。
誤差をパラメータで微分したものと再定義した学習率の積を減算する。θの値を上手く合わせなくても良い。

![gif latex-11](https://user-images.githubusercontent.com/85814165/140572512-97f61313-518d-46e4-a482-31cff86f83c9.gif)

self.h[key] *= self.decay_rate
self.h[key] += (1 - self.decay_rate) * grad[key] * grad[key]

![gif latex-10](https://user-images.githubusercontent.com/85814165/140572520-eba7add5-b5df-44dd-be5b-27ddd935debe.gif)

params[key] -= self.learning_rate * grad[key] / (np.sqrt(self.h[key]) + 1e-7)

## Adam
メリット：モメンタムおよびRMSPropのメリットを孕んだアルゴリズム。
モメンタム：過去の勾配の指数関数的減衰平均
RMSProp：過去の勾配の2乗の指数関数的減衰平均

# 確認テスト
Q.モメンタム・AdaGrad・RMSPropの特徴をそれぞれ簡潔に説明せよ。
A.
モメンタム：局所的最適解にならず、大域的最適解になる。
AdaGrad：勾配の緩やかな斜面に対して、最適解に近づく
RMSProp：局所的最適解にならず、大域的最適解になる。ハイパーパラメータの調整が不要な場合が多い、。

# 実装
2_4_optimizer.ipynbより

![スクリーンショット 2021-11-22 20 21 54](https://user-images.githubusercontent.com/85814165/142853333-4994406b-733a-44aa-801a-ef9f75e93411.png)
![スクリーンショット 2021-11-22 20 22 37](https://user-images.githubusercontent.com/85814165/142853345-5f6988e9-bdc9-41b2-aa99-d4f7d700955f.png)
![スクリーンショット 2021-11-22 20 22 55](https://user-images.githubusercontent.com/85814165/142853358-4803845b-38b8-45d8-babb-45b7ab5f02c8.png)
![スクリーンショット 2021-11-22 20 23 24](https://user-images.githubusercontent.com/85814165/142853370-477780d1-a6c0-48dd-98d2-0718cfb26d00.png)
![スクリーンショット 2021-11-22 20 23 35](https://user-images.githubusercontent.com/85814165/142853388-7ec97198-770c-4a09-9841-bbc8f34c0b86.png)
![スクリーンショット 2021-11-22 20 23 50](https://user-images.githubusercontent.com/85814165/142853398-4ca52fa8-5046-4108-a042-4fa53a93b011.png)
![スクリーンショット 2021-11-22 20 24 01](https://user-images.githubusercontent.com/85814165/142853407-e7e073be-cf83-41bb-a3fa-8a84de2295f3.png)
![スクリーンショット 2021-11-22 20 24 12](https://user-images.githubusercontent.com/85814165/142853418-96d0c4c8-464c-4469-920d-ed1443931cc7.png)
![スクリーンショット 2021-11-22 20 24 22](https://user-images.githubusercontent.com/85814165/142853425-6af14487-9b60-4044-85be-3a29a7673798.png)
