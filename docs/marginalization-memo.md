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
>In the case where marginalized nodes comprise landmarks at infinity (or sufficiently close to infinity), or landmarks visible only in one camera from a single pose, the Hessian blocks associated with those landmarks will be (numerically) rank-deficient. We thus employ the pseudo-inverse H+ µµ, hich provides a solution for δχµ given δχλ with a zerocomponent into nullspace direction
https://www.roboticsproceedings.org/rss09/p37.pdf

このへんが参考にできそうな感じ。やはりHを足すだけなのか？
![image](https://github.com/eryeden/get-slam-to-marginalize/assets/4968978/db510296-e33a-49a7-9b99-21f90638e617)



##
https://dellaert.github.io/files/Williams14ijrr.pdf

👆結構marginalizationが登場している



##
https://wang-yimu.com/variable-elimination-smoothing-and-marginalization-explained/

👆このサイト、神。このサイトで勉強することにする。
