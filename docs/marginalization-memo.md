# Marginalization memo
## 16.485: VNAV - Visual Navigation for Autonomous Vehicles
- Resources: https://vnav.mit.edu/material/24-SLAM2-FactorGraphsAndMarginalization-slides.pdf

復習。Marginalizeし、Factor graphから変数を除去すると、以下が発生する。
- 除去した変数に接続されていた変数間に、新しい接続が生まれる。
- この影響で線形化したHessianが密になる。

ここまでは知っていた内容。
疑問：
- Marginalizeした変数、Hessianは、次の最適化ステップではどう活用されるのか？