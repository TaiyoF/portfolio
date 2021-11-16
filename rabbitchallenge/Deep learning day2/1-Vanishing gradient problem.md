#  勾配消失問題
誤差逆伝播法が下位層に進むにつれて、勾配がどんどん緩やかになる。
そのため、勾配降下法による更新では下位層のパラメータはほとんど変わらず、訓練は最適値に収束しなくなる。

## 活性化関数：シグモイド関数
勾配消失問題を引き起こすことがあった。理由は大きな値では出力の変化が微笑なため。
シグモイド関数を微分すると0.25が最大値になってしまう。

## 活性化関数：ReLU関数
勾配消失問題の回避とスパース化に貢献。

![gif latex](https://user-images.githubusercontent.com/85814165/140504207-a57ae6c6-9101-4777-8acc-36df49cc06ec.gif)

![スクリーンショット 2021-11-05 20 27 56](https://user-images.githubusercontent.com/85814165/140503816-fcf7f1bc-bbf8-46d2-a7c2-743fdc0adb3a.png)

## 重みの初期値設定
NNを学習始める時に、何箇所かある重みは何かしらのルールに基づいて作成する。多くの場合は乱数。

シグモイド関数に対しては、Xavier（サビエル）という乱数設定方法がある。
正規分布に従った乱数の生成。
前の層のノード数のルートで除算した値

ReLU関数には、重みの要素を、前の層のノード数の平方根で除算した値に対して√2をかけた値

## バッチ正規化
ミニバッチ単位で、入力値のデータの偏りを抑制する方法。
- 中間層の重みの更新が安定化する、学習スピードが向上する。
- 過学習を抑えられる。
GPU：1-64枚
TPU：1-256枚

ミニバッチの平均

![gif latex-2](https://user-images.githubusercontent.com/85814165/140510796-33890b32-ab9b-4097-bc36-628411724558.gif)

ミニバッチの分散

![gif latex-3](https://user-images.githubusercontent.com/85814165/140510897-62da32a8-6973-4f5f-9fab-a0c3d2cc0ee1.gif)

ミニバッチの正規化

![gif latex-4](https://user-images.githubusercontent.com/85814165/140511053-9bbc9cf4-ca25-43b1-934a-17c0bf0714da.gif)

変倍・移動

![gif latex-5](https://user-images.githubusercontent.com/85814165/140511113-2c52f975-d208-4a77-8149-8f4366ecf2af.gif)

γは定数倍、βはバイアス

# 確認テスト

Q.連鎖律の原理を使い、dz/dxを求めよ。z=t^2, t=x+y

![gif latex-101](https://user-images.githubusercontent.com/85814165/140500014-a2d854b5-6ceb-4572-aec8-f2a40fbf993e.gif)

Q.シグモイド関数を微分したとき、入力値が0の時に最大値をとる。その値として正しいものを選択肢から選べ

A.0.25が最大値

Q.重みの初期値に0を設定すると、どのような問題が発生するか。簡潔に説明せよ。

A.重みを0で初期化すると正しい学習が行えない。すべての重みの値が均一に更新されるため、多数の重みを持つ意味がなくなる。

Q.一般的に考えられるバッチ正規化の効果を2点あげよ。

A1.中間層の重みの更新が安定化する、学習スピードが向上する。
A2.過学習を抑えられる。

# 実装
1.2_2_2_vanishing_gradient_modified.ipynb

![スクリーンショット 2021-11-16 21 54 59](https://user-images.githubusercontent.com/85814165/141989507-c45b67a5-2bfc-4501-8c31-e8962f04a4c9.png)
![スクリーンショット 2021-11-16 21 55 24](https://user-images.githubusercontent.com/85814165/141989523-cd06d4cb-4cac-430e-9f68-5e7fa0d33bdf.png)
![スクリーンショット 2021-11-16 21 55 34](https://user-images.githubusercontent.com/85814165/141989527-8b80021f-7317-4937-afda-238c790eb8b6.png)
![スクリーンショット 2021-11-16 21 55 47](https://user-images.githubusercontent.com/85814165/141989538-e3ee1f75-f503-42d0-a4d1-d223226ce62d.png)
![スクリーンショット 2021-11-16 21 55 56](https://user-images.githubusercontent.com/85814165/141989548-9079d0d7-203c-44a8-9da9-5cddb03c7926.png)
![スクリーンショット 2021-11-16 21 56 06](https://user-images.githubusercontent.com/85814165/141989556-fddb7a22-6c47-4690-9e9d-7c3beb805f32.png)
![スクリーンショット 2021-11-16 21 56 22](https://user-images.githubusercontent.com/85814165/141989573-d97f078d-7d39-4b7d-9f33-b358e5172896.png)
![スクリーンショット 2021-11-16 21 56 38](https://user-images.githubusercontent.com/85814165/141989579-3d870db2-daaf-48a0-988c-984bba8ec5ae.png)
![スクリーンショット 2021-11-16 21 56 52](https://user-images.githubusercontent.com/85814165/141989586-c18461b2-ff65-4767-bb80-aa79a1b7090a.png)
![スクリーンショット 2021-11-16 21 57 00](https://user-images.githubusercontent.com/85814165/141989593-7721673f-e35d-46cb-9fb3-6214fa490be1.png)
![スクリーンショット 2021-11-16 21 57 16](https://user-images.githubusercontent.com/85814165/141989607-50cfbf51-b03c-4d63-b970-4ffc17d19f5b.png)
![スクリーンショット 2021-11-16 21 57 24](https://user-images.githubusercontent.com/85814165/141989617-5746068d-5608-4bf8-b2e5-c76e70aff7b1.png)
![スクリーンショット 2021-11-16 21 57 37](https://user-images.githubusercontent.com/85814165/141989624-9d0e279c-19d1-453c-90a3-23f1df204751.png)
![スクリーンショット 2021-11-16 21 57 47](https://user-images.githubusercontent.com/85814165/141989637-d1012ea6-11f8-41e3-8a0f-df29c8905293.png)
![スクリーンショット 2021-11-16 21 57 55](https://user-images.githubusercontent.com/85814165/141989650-a3107499-53e0-47e2-b487-be002b17bf11.png)
![スクリーンショット 2021-11-16 21 58 03](https://user-images.githubusercontent.com/85814165/141989662-7784842b-8ad5-47a8-993b-4db1b7e2492a.png)
![スクリーンショット 2021-11-16 21 58 11](https://user-images.githubusercontent.com/85814165/141989671-3029b21e-c37d-4e82-b37e-6b4ab63d6fcb.png)

2.2_3_batch_normalization.ipynb

![スクリーンショット 2021-11-17 5 45 59](https://user-images.githubusercontent.com/85814165/142063171-8a186683-d92f-4148-8e4e-31af2ab162e9.png)
![スクリーンショット 2021-11-17 5 46 12](https://user-images.githubusercontent.com/85814165/142063182-41ee10f0-41d1-408a-a469-478137daafa1.png)
![スクリーンショット 2021-11-17 5 46 25](https://user-images.githubusercontent.com/85814165/142063189-e3a98340-1ec1-493e-8a73-98ce507ce58e.png)
![スクリーンショット 2021-11-17 5 46 39](https://user-images.githubusercontent.com/85814165/142063193-05c3df54-e5c1-4e2c-8b2a-aaba77ef62a4.png)

1と2の比較

sigmoid Xvaier normalizationなし

![スクリーンショット 2021-11-17 5 48 58](https://user-images.githubusercontent.com/85814165/142063411-212c7ddb-c26c-4fbf-b84a-4d4db44b25af.png)

sigmoid Xvaier normalization あり

![スクリーンショット 2021-11-17 5 50 27](https://user-images.githubusercontent.com/85814165/142063592-c545d408-d02f-4a35-8887-65c2cf1fada9.png)

normalizationをかけることで学習が向上することがわかる。
