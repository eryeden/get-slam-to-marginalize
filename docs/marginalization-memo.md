# Marginalization memo
## 16.485: VNAV - Visual Navigation for Autonomous Vehicles
- Resources: https://vnav.mit.edu/material/24-SLAM2-FactorGraphsAndMarginalization-slides.pdf

復習。Marginalizeし、Factor graphから変数を除去すると、以下が発生する。
- 除去した変数に接続されていた変数間に、新しい接続が生まれる。
- この影響で線形化したHessianが密になる。

ここまでは知っていた内容。
疑問：
- Marginalizeした変数、Hessianは、次の最適化ステップではどう活用されるのか？

## Google Bardより
```math
H_0 = H_{-1} - \frac{\partial x}{\partial z} \frac{\partial x}{\partial z}^T
```

- $H_0$ : 今回のHessian
- $H_{-1}$ 前回のHessian

という天啓を得た。たしかにどっかで見たことがある気がする。OKVISなどFixed lagsmoothingの初期の文献から基本的な処理を調査するのがいいかもしれない。


##
https://github.com/pangfumin/marginalization

## OKVIS
