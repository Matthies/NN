# NN

This repository contains network files created to use for NNUE based evaluation in RubiChess engine.

Format: nn-\<first-10-hex-digits-of-sha256\>-\<yyyymmdd\>.nnue

 - nn-f21733c196-20201028.nnue: Learned from Rubi depth 10 training positions (TB disabled) using the SF learner binary; +95 Elo +/-25 vs. HCE
 - nn-803c91ad5c-20201107.nnue: Default net of Rubi-1.9. Learned from Rubi depth 6 training using eval from last net, 6-men-TB and disabled pruning; net passed SPRT test and was slighly better in 10-engines-gauntlet
 - nn-375bdd2d7f-20210112.nnue: Default net of Rubi-2.0. Learned from Rubi depth 8 training using eval of last net, 6-men-TB and disabled pruning using trainer of SV mod branch
 - nn-cf8c56d366-20210326.nnue: Default net of Rubi-2.1. Learned from Rubi depth 10-12 / depth 8 multipv training data using eval of last net and some improved/fixed gensfen code. Again the trainer of SV mod was used, this time with some parameters of SV workflow like Lambda=0.5
 - nn-673bf01913-20210421.nnue: Learned from Rubi depth 11-13 / depth 9 multipv training data using eval of last net and Rubi-pre-2.1 using the old scaling factor 64. Same trainer parameters as last net. Net seems slightly stronger (5-15 Elo).
 - nn-72b4488f79-20210510.nnue: Same as last net even with same traing data but trained with Lambda=0.4. Tested nets from several epochs, this one wasn't the last accepted but the one before.
- nn-fb50f1a2b1-20210705.nnue: Default net of Rubi-2.2. Identical to 72b44 with just rescaled last layer to get back to trainer-compatible scaling "eval = netoutput / 16". This was supposed to lose some Elo but in fact it gained 4-6 Elo in three tests. 
- nn-e4660d9c81-20220104.nnue: Finally right after release of Rubi 2021 a new master net. Epoche 17 trained on new training data (800M positions depth 9, pruning disabled) with SV trainer starting on old master net.
