# NN

This repository contains network files created to use for NNUE based evaluation in RubiChess engine.

Format: nn-\<first-10-hex-digits-of-sha256\>-\<yyyymmdd\>.nnue

 - nn-f21733c196-20201028.nnue:  Learned from Rubi depth 10 training positions (TB disabled) using the SF learner binary; +95 Elo +/-25 vs. HCE
 - nn-803c91ad5c-20201107.nnue:  Learned from Rubi depth 6 training using eval from last net, 6-men-TB and disabled pruning; net passed SPRT test and was slighly better in 10-engines-gauntlet
 - nn-375bdd2d7f-20210112.nnue: Learned from Rubi depth 8 training using eval from last net, 6-men-TB and disabled pruning using trainer of SV mod branch
