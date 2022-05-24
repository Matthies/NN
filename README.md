# NN

This repository contains network files created to use for NNUE based evaluation in RubiChess engine.

Format: nn-\<first-10-hex-digits-of-sha256\>-\<yyyymmdd\>.nnue

 - nn-f21733c196-20201028.nnue: Learned from Rubi depth 10 training positions (TB disabled) using the SF learner binary; +95 Elo +/-25 vs. HCE
 - __nn-803c91ad5c-20201107.nnue__: Default net of Rubi-1.9. Learned from Rubi depth 6 training using eval from last net, 6-men-TB and disabled pruning; net passed SPRT test and was slighly better in 10-engines-gauntlet
 - __nn-375bdd2d7f-20210112.nnue__: Default net of Rubi-2.0. Learned from Rubi depth 8 training using eval of last net, 6-men-TB and disabled pruning using trainer of SV mod branch
 - __nn-cf8c56d366-20210326.nnue__: Default net of Rubi-2.1. Learned from Rubi depth 10-12 / depth 8 multipv training data using eval of last net and some improved/fixed gensfen code. Again the trainer of SV mod was used, this time with some parameters of SV workflow like Lambda=0.5
 - nn-673bf01913-20210421.nnue: Learned from Rubi depth 11-13 / depth 9 multipv training data using eval of last net and Rubi-pre-2.1 using the old scaling factor 64. Same trainer parameters as last net. Net seems slightly stronger (5-15 Elo).
 - nn-72b4488f79-20210510.nnue: Same as last net even with same traing data but trained with Lambda=0.4. Tested nets from several epochs, this one wasn't the last accepted but the one before.
- __nn-fb50f1a2b1-20210705.nnue__: Default net of Rubi-2.2. Identical to 72b44 with just rescaled last layer to get back to trainer-compatible scaling "eval = netoutput / 16". This was supposed to lose some Elo but in fact it gained 4-6 Elo in three tests. 
- nn-e4660d9c81-20220104.nnue: Finally right after release of Rubi 2021 a new master net. Epoch 17 trained on new training data (800M positions depth 9, pruning disabled) with SV trainer starting on old master net.
- nn-555efa676e-20220105.nnue: Retraining starting with last net nn-e4660d9c81-20220104.nnue with same data. Some few more Elo.
- nn-49832fc04f-20220106.nnue: Epoch 26 of another retrain starting with nn-555efa676e-20220105.nnue. Another 10-15 Elo progress.
- nn-26119c6435-20220109.nnue: Epoch 21 of another retrain starting with nn-49832fc04f-20220106.nnue. Another 3-5 Elo progress.
- nn-e4977569c9-20220130.nnue: Epoch 51 of another retrain starting with nn-26119c6435-20220109.nnue and using nearly three billion positions, half of them created with latest net all of them well shuffled. Also using a set of mixed positions (old and new data) for validation. Progress is ~8 Elo.
- nn-7e8d2f1670-20220202.nnue: Rescaled last layer of  with a factor of 60/64 which gives another ~2 Elo.
- nn-d585174582-20220214.nnue: Another training starting from last net and using all the latest well shuffled training data (created with nn-e4977569c9-20220130) and Nodchip/Sergio trainer. The last net from epoch 59 before trainer termination was tested best and further improved by rescaling the last layer with 56/64.
- __nn-d458c5999d-20220222.nnue__:  Default net of Rubi-20220223. Another training session with well shuffled latest training data, now 3.5B positions in total. Net from epoch 82 tested best and further imroved with 56/64 scaling of last layer.
- nn-bc67e15665-20220523.nnue: First time that a net trained with nnue-pytorch beats master. This is epoche 500 from a training starting with last master, using 2G depth9 positions created with last master, first 320 epochs with default parameters (in/outscaling 361), then resuming on last checkpoint with lambda=0.75. 4-7 Elo progress.
