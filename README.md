# faceswap-GAN-swap-them-all
A GAN based approach for one model to swap them all.

The following figure illustrates our priliminary faceswapping results on random identities drawn from [VGGFace2](http://www.robots.ox.ac.uk/~vgg/data/vgg_face2/) dataset (from left to right: source, target, result). We also show some failure cases, which demonstrate limitations of our model for genrerating consistent skin tone, eye-glasses, and expression.

![](https://github.com/shaoanlu/faceswap-GAN-swap-them-all/raw/master/images/result.jpg)

Our model is still very data sentitive, i.e., when feeding identities that the model had never seem before or are outside training data distribution (such as asian faces that are scarce in VGGFace2), our GAN failed at genereating faces with high fidelity.

![](https://github.com/shaoanlu/faceswap-GAN-swap-them-all/raw/master/images/result2.jpg)

## Architecture
![](https://github.com/shaoanlu/faceswap-GAN-swap-them-all/raw/master/images/sta_generator.jpg)

The above image illustrates our generator, which is a encoder-decoder based network, at test phase. Our swap-them-all approach is basically a GAN conditioned on the latent embeddings extracted from a pre-trained face recognition model. [SPADE](https://arxiv.org/abs/1903.07291) module is intrioduced in the decoder in order to inject better semantic information. On the other hand, the use of Res2Net module is purely heuristic without meaningful reason. The architecture of SPADE Res2Net block is shown below.

![](https://github.com/shaoanlu/faceswap-GAN-swap-them-all/raw/master/images/sta_SPADE_Res2Net_block.jpg)
