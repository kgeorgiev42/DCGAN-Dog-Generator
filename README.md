# DCGAN-Dog-Generator
DCGAN model (and tutorial) for generating fake images of dogs based on the [Generative Dog Images Kaggle Competition (2019)](https://www.kaggle.com/c/generative-dog-images).

## Google Colab version
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1LUP_dymfwS5_yvZ_IeS_jmNyZhSyHz-5)

To run this example locally or using Colab, you will need a <b>Kaggle account</b>, in order to retrieve its API key and use the provided datasets. Full tutorial is available [here](https://medium.com/@yvettewu.dw/tutorial-kaggle-api-google-colaboratory-1a054a382de0). 

[Nbviewer link of the Kaggle notebook (better readability)](https://nbviewer.jupyter.org/github/JadeBlue96/DCGAN-Dog-Generator/blob/master/dcgans-and-techniques-to-optimize-them.ipynb)


## Visualizing the generation over epochs (~9 hrs of training)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![DCGAN gif](https://media.giphy.com/media/TL0HO5ikb99YMbF0uv/giphy.gif)

## Model architecture
My DCGAN model uses the standard <b>DCGAN</b> generator and discriminator structure from the official [paper](https://arxiv.org/pdf/1511.06434.pdf)(with some modifications) shown below:

## Generator
![DCGAN generator](https://miro.medium.com/max/875/1*KvMnRfb76DponICrHIbSdg.png)

## Discriminator
![DCGAN discriminator](https://user-images.githubusercontent.com/37034031/43060075-47f274d0-8e8a-11e8-88ff-3211385c7544.png)

### Model improvements for this task include:
- <b>Weight initialization (Truncated normal distribution)</b>
- <b>Spectral Normalization for each Conv layer in the discriminator</b>
- <b>2 Dropout layers after the first 2 TP_Conv layers in the generator</b>
- <b>Label smoothing</b>
- <b>Instance noise</b>
- <b>Cosine learning rate decay for Adam</b>
- <b>Data Augmentation (horizontal flips)</b>

### Final scores:
Evaluation was based on the <b>MIFID(Memorization Informed Frechet Inception Distance) metric</b>, where the lower the distance score is, the better the quality of the images will be. During the competition, submissions were evaluated on a public test set of dog images, while the final scoring was based on a private dataset.
- [First submission](https://www.kaggle.com/jadeblue/dogdcgan-v7-ksize-dropout-sub) - <b>Public - 59.05, Private - 122.55</b>
- [Second submission](https://www.kaggle.com/jadeblue/dogdcgan-v6-ksize?scriptVersionId=18694459) - <b>Public - 55.87, Private - 125.34</b>

## My References

- The official tutorial [kernel](https://www.kaggle.com/jadeblue/dcgans-and-techniques-to-optimize-them)
- My best [submission](https://www.kaggle.com/jadeblue/dogdcgan-v7-ksize-dropout-sub) for this competition)
- Blog post (coming soon)

## Resources

[1]. [Generative Adversarial Networks official paper](https://arxiv.org/pdf/1406.2661.pdf)

[2]. [Understanding Generative Adversarial Networks (GANs)](https://towardsdatascience.com/understanding-generative-adversarial-networks-gans-cd6e4651a29)

[3]. [A Gentle Introduction to Generative Adversarial Networks (GANs)](https://machinelearningmastery.com/what-are-generative-adversarial-networks-gans/)

[4]. [DCGAN official paper](https://arxiv.org/pdf/1511.06434.pdf)

[5]. [GAN — DCGAN (Deep convolutional generative adversarial networks)](https://medium.com/@jonathan_hui/gan-dcgan-deep-convolutional-generative-adversarial-networks-df855c438f)

[6]. [Weight Initialization Techniques in Neural Networks](https://towardsdatascience.com/weight-initialization-techniques-in-neural-networks-26c649eb3b78)

[7]. [Spectral Normalization for Generative Adversarial Networks paper](https://arxiv.org/pdf/1802.05957.pdf)

[8]. [Spectral Normalization implemented in Keras](https://github.com/IShengFang/SpectralNormalizationKeras)

[9]. [Spectral Normalization Explained](https://christiancosgrove.com/blog/2018/01/04/spectral-normalization-explained.html)

[10]. [GAN — Ways to improve GAN performance](https://towardsdatascience.com/gan-ways-to-improve-gan-performance-acf37f9f59b)

[11]. [How to Implement GAN Hacks in Keras to Train Stable Models](https://machinelearningmastery.com/how-to-code-generative-adversarial-network-hacks/)

[12]. [Tricks of GANS](https://lanpartis.github.io/deep%20learning/2018/03/12/tricks-of-gans.html)

[13]. [Instance Noise: A trick for stabilising GAN training](https://www.inference.vc/instance-noise-a-trick-for-stabilising-gan-training/)

[14]. [GAN — RSGAN & RaGAN (A new generation of cost function.)](https://medium.com/@jonathan_hui/gan-rsgan-ragan-a-new-generation-of-cost-function-84c5374d3c6e)

[15]. [A simple explanation of the Inception Score](https://medium.com/octavian-ai/a-simple-explanation-of-the-inception-score-372dff6a8c7a)

[16]. [GAN — How to measure GAN performance?](https://medium.com/@jonathan_hui/gan-how-to-measure-gan-performance-64b988c47732)

[17]. [All you need is GAN Hacks](https://www.kaggle.com/c/generative-dog-images/discussion/98595#latest-582912)

[18]. [How to train your touchy GANs - Things that seem to work.](https://www.kaggle.com/c/generative-dog-images/discussion/102155#latest-599429)

[19]. [Explaining the metric FID](https://www.kaggle.com/c/generative-dog-images/discussion/97809#latest-591866)
