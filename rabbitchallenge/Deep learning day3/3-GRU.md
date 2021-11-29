# GRU

LSTMの課題：LSTMではパラメータ数が多く、計算負荷が高くなる。

→GRUでは、そのパラメータを大幅に削減し、精度は同等またはそれ以上を望めるようになった構造

メリット：計算負荷が低い

![スクリーンショット 2021-11-28 19 25 38](https://user-images.githubusercontent.com/85814165/143764121-e7285643-6a33-47e0-a81e-f7890d55ad8e.png)

入力ゲート・出力ゲート・忘却ゲートがなくなり→リセットゲートと更新ゲート

# 確認テスト

LSTMとCECが抱える課題についてそれぞれ簡潔に述べよ。

LSTM：勾配消失が発生する

CEC:パラメータ数が多く、計算負荷が高くなる。


LSTMとGRUの違いを簡潔に述べよ

LSTM：パラメータ数が多い。計算負荷が高い。入力ゲート・忘却ゲート・出力ゲート・CECがある。

GRU：パラメータ数が少ない。計算負荷が抑えられている。精度はLSTMより同等以上。リセットげーと・更新ゲートがある。

# 演習テスト

![スクリーンショット 2021-11-28 19 35 31](https://user-images.githubusercontent.com/85814165/143764377-6a39d245-1dfd-44d3-ac9d-4b1d08ae972a.png)

A.4 (1-z)*h +z*h_bar

# 実装
predict_word.ipynb

![スクリーンショット 2021-11-30 5 30 54](https://user-images.githubusercontent.com/85814165/143939039-f3da322f-1527-4733-9926-1fcf510f5233.png)
![スクリーンショット 2021-11-30 5 32 05](https://user-images.githubusercontent.com/85814165/143938957-3dceecb4-7202-468f-8c92-e643cfb40ea6.png)
![スクリーンショット 2021-11-30 5 32 24](https://user-images.githubusercontent.com/85814165/143938966-44cfe6ac-179b-4854-8d58-f0dd65991bd5.png)
![スクリーンショット 2021-11-30 5 32 34](https://user-images.githubusercontent.com/85814165/143938973-6e8612f1-4475-42e1-b4ca-7b13ceecb765.png)
![スクリーンショット 2021-11-30 5 33 39](https://user-images.githubusercontent.com/85814165/143938978-96502db5-d71b-4ab7-be0c-ddcd16487161.png)
![スクリーンショット 2021-11-30 5 36 07](https://user-images.githubusercontent.com/85814165/143939237-7cb6e1c2-95f8-4824-ad18-9e8868c246e6.png)

