# 応用数学　第一章　線形代数

## スカラー
- スカラーとは大きさを表す値
- 四則演算（+ - × ÷)の処理が可能
- ベクトルの係数になれる

## ベクトル
- ベクトルとは、大きさと向きを持つ
- 図示する際は矢印で表す
- スカラーとのセットで表示される

## 行列
- 行列とは、スカラーを表にしたもの、ベクトルを並べたもののこと。
- 
![CodeCogsEqn](https://user-images.githubusercontent.com/85814165/138547835-4e9ebe4e-e3e3-45c8-a457-7efc522958c0.gif)

## 行列の積
行列の積を行うためには、1つ目の列数と2つ目の行数が一致していないといけない。

![gif latex](https://user-images.githubusercontent.com/85814165/138548178-cd3bdc05-76f9-4b0d-94bf-a24bca855f87.gif)

![gif latex-2](https://user-images.githubusercontent.com/85814165/138548268-d14ddbba-fb3d-4ec7-95ce-b4d0d86a65bd.gif)

## 単位行列
単位行列とは、n行n列の行列かつn行n列目のみ1のある行列のこと。

![gif latex-3](https://user-images.githubusercontent.com/85814165/138548384-98bc850c-837f-4208-b463-66d8e2b7b8be.gif)

## 逆行列
逆行列とは、以下の関係になる行列![gif latex-4](https://user-images.githubusercontent.com/85814165/138548414-3bba5c62-a1a4-440f-bffd-e90f1abc8661.gif)のこと

![gif latex-5](https://user-images.githubusercontent.com/85814165/138548441-29bed48b-7b49-4970-92e3-d18749140ada.gif)

例）

![gif latex-6](https://user-images.githubusercontent.com/85814165/138548493-3fbfc6f9-a0ec-4709-bd29-47e45a4d6afa.gif)

## 逆行列の求め方
基本的には二次関数を解く方法に近い.n倍して1行目や2行目を足し引きし、左の行列を単位行列にする。

例）

![gif latex-7](https://user-images.githubusercontent.com/85814165/138548906-d5ed2773-bf3b-49d6-89dd-f9a7d65912a6.gif)

## 逆行列が存在しない条件
ベクトルの方向が同一の場合もしくは1つの行列が0の場合、逆行列が存在しない。

## 行列式の求め方
正方行列（n×nの行列）には、ある一つの数値が対応する。＝正方行列の大きさみたいなもの。

2×2行列の場合
![gif latex-8](https://user-images.githubusercontent.com/85814165/138549163-d2cd86cd-de88-4289-abff-78e6cf9d2112.gif)

3×3行列の場合

![gif latex-9](https://user-images.githubusercontent.com/85814165/138549255-6978a867-388b-4482-aee9-49448e015624.gif)

## 固有値と固有ベクトル
ある行列Aと特殊なベクトル![gif latex-11](https://user-images.githubusercontent.com/85814165/138549328-998a64e5-3214-4ecc-857e-af2f8065983a.gif)の積は、スカラーであるλと特殊なベクトル![gif latex-11](https://user-images.githubusercontent.com/85814165/138549342-bd5b3185-0161-4126-afe3-751df9a15516.gif)の積とイコールになる。

- λが固有値
- 特殊なベクトル![gif latex-11](https://user-images.githubusercontent.com/85814165/138549377-72fdad4f-372f-4de1-81ee-3e4f5e84f841.gif)が固有ベクトル

![gif latex-10](https://user-images.githubusercontent.com/85814165/138549299-661c756c-de7f-43be-a5ef-12696728c478.gif)

例）

![gif latex-12](https://user-images.githubusercontent.com/85814165/138552768-2a263ac5-c804-4eaf-b0d7-fabd1e20e24f.gif)

## 固有値分解
n行n列の正方行列Aにおいて、固有値λ1,λ2,,λn及び固有ベクトル![gif latex-13](https://user-images.githubusercontent.com/85814165/138552843-17b9fc94-35a8-45fe-8209-18d392e185f8.gif)1,![gif latex-13](https://user-images.githubusercontent.com/85814165/138552843-17b9fc94-35a8-45fe-8209-18d392e185f8.gif)2,,![gif latex-13](https://user-images.githubusercontent.com/85814165/138552843-17b9fc94-35a8-45fe-8209-18d392e185f8.gif)nを持つ場合、この固有値を対角線上に並べた行列Λとそれに対応する固有ベクトルを並べた行列Vの関係は以下式。

![gif latex-14](https://user-images.githubusercontent.com/85814165/138552940-32d9bf68-5ee6-44fa-8b62-e0ae2006c596.gif)

解き方は、固有値を求め→固有ベクトルを求め→固有値がA→固有ベクトルをVに設定する。
最後に、![gif latex-15](https://user-images.githubusercontent.com/85814165/138553007-06cde37d-af29-4c1a-938d-aff15d0b64ce.gif)を逆行列の解き方により求める。

## 特異値分解
n行n列の正方行列ではない行列（長方形の行列）においても、固有値分解が可能＝特異値分解

![gif latex-16](https://user-images.githubusercontent.com/85814165/138553214-029c44e8-b356-455b-9780-ee8c5c26a037.gif)

![gif latex-17](https://user-images.githubusercontent.com/85814165/138553225-26f1f064-05bb-4ae0-8992-0e30607e2f3d.gif)を固有値分解すると、左特異ベクトルちと特異値の2乗が求められる。
Tは転置のこと。

# 演習問題
行列の四則演算は問題ないので、演習問題にある固有ベクトル問題について解法をまとめた。

# 問7.2
行列![gif latex-18](https://user-images.githubusercontent.com/85814165/138553391-c1606448-4bdf-4fe9-a0f6-8a93ffa72c3a.gif)の固有ベクトルを求めたところ、![gif latex-19](https://user-images.githubusercontent.com/85814165/138553414-242ff9a5-5fc9-455a-9965-1db3f3f27513.gif)の定数倍であることがわかった。この固有ベクトルに対する固有値を求めよ。

![gif latex-12](https://user-images.githubusercontent.com/85814165/138553459-8c7cdc04-8556-4689-b28a-e39ed0fe8b2e.gif)

上記の計算により、固有値λ=5の時、設問の固有ベクトルになるため、求める固有値λ=5であることがわかる。


