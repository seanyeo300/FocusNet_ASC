<h1>FocusNet</h1>

<h2>Description</h2>

This repository outlines the implementation of FocusNet by [Zhang et al.](https://arxiv.org/abs/2110.07307) [1]. FocusNet seeks to improve a deep learning teacher model in the knowledge distillation framework by focussing the model's attention on classes with high confusion.

The model backbone uses the Patchout faSt Spectrogram Transformer ([PaSST](https://arxiv.org/abs/2110.05069)) [2] model pre-trained with AudioSet [3].

<br />


<h2>Languages and Utilities Used</h2>

The important packages and libraries required for reproducing this experiment are:

- <b>Python = 3.7.9 </b> 
- <b>Pytorch = 1.13.1+cu117 </b>

For exact requirements, see [here](https://github.com/fschmid56/cpjku_dcase23).

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>Datasets Used</h2>

- <b>TAU 2022 Urban Acoustic Scenes Mobile Development [4] </b> 
- <b>AudioSet</b>

<h2>Getting Started:</h2>


Follow the setup instructions for the PaSST models found [here](https://github.com/fschmid56/cpjku_dcase23).

Train a PaSST model to act as the template model:  <br/>

- Set the default value of --ckpt_id to None
- Set the default value of --subset between 5 to 100
- Set the default value of --n_classes to 10
- Set the default value of --resample_rate to 44100
- Set the default value of --batch_size to 256 or 128, depending on size of GPU memory
- For windows users, set the default value of num_workers to 0

 Evaluate the model using the training dataset to obtain logits
 
 - Create a separate instance of [dcase23.py](https://github.com/fschmid56/cpjku_dcase23/blob/main/datasets/dcase23.py) for use on FocusNet.
 - Edit the new dcase23.py file to take evaluation files from the training files csv

![Add FocusNet loss computation](https://github.com/seanyeo300/FocusNet_ASC/blob/main/images/FocusNet_loss.png)
  
 - use the --evaluate flag when running the run_passt_training.py script from the terminal to obtain logits when inferring on training data


<h2>References:</h2>

[1] Zhang, X., Sheng, Z., & Shen, H. L. (2022). FocusNet: Classifying better by focusing on confusing classes. Pattern Recognition, 129, 108709.

[2] Koutini, K., Schlüter, J., Eghbal-Zadeh, H., & Widmer, G. (2021). Efficient training of audio transformers with patchout. arXiv preprint arXiv:2110.05069.

[3] Gemmeke, J. F., Ellis, D. P., Freedman, D., Jansen, A., Lawrence, W., Moore, R. C., ... & Ritter, M. (2017, March). Audio set: An ontology and human-labeled dataset for audio events. In 2017 IEEE international conference on acoustics, speech and signal processing (ICASSP) (pp. 776-780). IEEE.

[4] T. Heittola, A. Mesarosand T. Virtanen, “TAU Urban Acoustic Scenes 2022 Mobile, Development dataset”. Zenodo, Mar. 08, 2022. doi: 10.5281/zenodo.6337421.






<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
