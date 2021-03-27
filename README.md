# NN

This repository contains network files created to use for NNUE based evaluation in RubiChess engine.

Format: nn-\<first-10-hex-digits-of-sha256\>-\<yyyymmdd\>.nnue

 - nn-f21733c196-20201028.nnue:  Learned from Rubi depth 10 training positions (TB disabled) using the SF learner binary; +95 Elo +/-25 vs. HCE
 - nn-803c91ad5c-20201107.nnue:  Learned from Rubi depth 6 training using eval from last net, 6-men-TB and disabled pruning; net passed SPRT test and was slighly better in 10-engines-gauntlet
 - nn-375bdd2d7f-20210112.nnue: Learned from Rubi depth 8 training using eval of last net, 6-men-TB and disabled pruning using trainer of SV mod branch
 - nn-cf8c56d366-20210326.nnue: Learned from Rubi depth 10-12 / depth 8 multipv training data using eval of last net and some improved/fixed gensfen code. Again the trainer of SV mod was used, this time with some parameters of SV workflow like Lambda=0.5

Score of ms-20210327 vs 2.0.1: 669 - 103 - 1228  [0.641] 2000
Elo difference: 101.1 +/- 9.1, LOS: 100.0 %, DrawRatio: 61.4 %
