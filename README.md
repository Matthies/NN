# NN

This repository contains network files created to use for NNUE based evaluation in RubiChess engine.

Format: nn-\<first-10-hex-digits-of-sha256\>-\<yyyymmdd\>.nnue

History of the network files that made it to master net at some point:

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
- nn-bc67e15665-20220523.nnue: First time that a net trained with nnue-pytorch beats master. This is epoch 500 from a training starting with last master, using 2G depth9 positions created with last master, first 320 epochs with default parameters (in/outscaling 361), then resuming on last checkpoint with lambda=0.75. 4-7 Elo progress.
- nn-d3b95fbbeb-20220524.nnue: Rescaled last layer of  with a factor of 56/64 which gives another ~4 Elo.
- __nn-b1c332ae1d-20220613.nnue__: Default net of Rubi-20220813. Some few Elo with this net trained with Nodchip/SV trainer on 1.8B fresh positions (epoch 104) and rescaled with 56/64 afterwards.
- nn-df29ab9d61-20220831.nnue: This is a HalfKAv2_hm^ feature set network with 512x32x32x1 architecture (besides the smaller input layer identical to SFv5 https://github.com/glinscott/nnue-pytorch/blob/master/docs/nnue.md#historical-stockfish-evaluation-network-architectures) trained 210 epochs with a slightly tweaked nnue-pytorch on all 12.5 billion positions created with RubiChess in the last months. Training took 5 days using a GTX 1050Ti. Network is zipped with zlib to save some space and bandwidth.
- __nn-5e6b321f90-20221001.nnue__: Default net of Rubi-20221120. Took another 5 days training on 14 billion positions including additional data from latest master.
- nn-5e38b8ddf1-20221228.nnue: Continued training on last checkpoint (epoch 400) with additional training data from last two months (latest net, no tb usage). This net is epoch 522 and tested quite well at OpenBench.
- nn-0cea604698-20230119.nnue: First network with layer 1 dimension 768. This net is epoch 439 of training with same training positions as last net and using lambda=0.8. Fixed nodes tests (nodes=400000) showed +35Elo versus master while STC/LTC suffer from lower speed of this network and give 6-8 Elo. Switching to different lambda 0.7 or 1.0 at epoch 400 both regressed compared to 0.8.
- en-ep06-la025.nnue: Special network that solves Ede's testsuit but plays like shit. Details [here](https://github.com/Matthies/RubiChess/wiki/Madness-in-computer-chess#destroying-the-faith-to-testsuite-results).
- __nn-fdccaaabd3-20230314.nnue__: Default net of Rubi-20230410. Continued training beginning from checkpoint of last master net using complete binpack including latest training positions.
- nn-d901a1822f-20230606.nnue: This is epoch 509 of training a net with input layer 1024 from scratch using latest training position and usual parameters. Training took 10 days on my GTX 1050Ti. Net seems equal to current 768 master on STC and +5 Elo at LTC. Expected a little more.
- nn-1701a2eb23-20230619.nnue: This is functional identical to last net but supports the sparse propagation of first level in the sense of neurons are ordered by the activation statistics of a depth 36 search on start position. I like the first 5 letters of the sha256 so maybe I should release and finish project here :-)
- nn-8add7b5546-20230619.nnue: Compressed version of nn-1701a2eb23-20230619.nnue.
- __nn-c257b2ebf1-20230812.nnue__: Default net of Rubi-20230918 and Rubi-20240112. Continued training starting from snapshot 509 of last training for another 100 epochs. Removed oldest 25% training data and added the same amount of new data so that training still based on ~40GB binpacks. Finally sorted first layer for sparse propagation on a depth 36 startpos bench.
- __nn-bc638d5ec9-20240730.nnue__: Trained from scratch for 400 epochs on 55GB binpack data, replaced oldest 13GB of data with 26GB of new data compared to last training.
- __nn-6627982c33-20250106.nnue__: SPSA-tuned last layer of bc638d5ec9.
- __nn-f05142b28f-20250520.nnue__: Epoch 614 of latest training from scratch with latest set of training data (almost identical to the set used for bc638d5ec9) and first layer ordered for sparse propagation. Used lambda 0.8 up to epoch 614 and failed to improve trying different values for lambda 0.6..0.9 starting from checkpoint of 614.
