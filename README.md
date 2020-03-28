# deep-chicken-terminator
deep learning to track (and possibly kill)  chickens in minecraft :hocho: :chicken:

[![Binder](https://camo.githubusercontent.com/bfeb5472ee3df9b7c63ea3b260dc0c679be90b97/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f72656e6465722d6e627669657765722d6f72616e67652e7376673f636f6c6f72423d66333736323626636f6c6f72413d346434643464)](https://nbviewer.jupyter.org/github/Mayukhdeb/deep-chicken-terminator/tree/master/)

<img src="sample_images/mouse_automation.gif" width="120%">.


## Step 1 - collecting training data for the deep neural network 

<img src="sample_images/training_data_samples.png" width="120%">.

* This was mostly just me taking cropped screenshots of animals while playing the game, took about 40 screenshots of each animal.
* The 20 screenshots of each animal were then augmented and got 500 samples of each. 
* The dataset is very small, but it works anyways for now

## Step 2 - training a deep learning model on the samples

<img src="sample_images/training_curve.png" width="30%">.

* The architecture was kept intentionally small so that it keeps a good response time on the live feed
* The dataset had only 2000 images sized at 50*50, so training barely took any time 

## Step 3 - Collecting more training data with the trained model

<img src="sample_images/hunter_alpha.gif" width="60%">.

* this is done by saving the frames which give a probaility of over 99% on the pre trained model
* these saved images are again used for further training, which means `hunter()` is getting better and better.

## Step 4 - detecting a and tracking chicken (or any animal for that matter) with the mouse using the trained model



<img src="sample_images/pre_barbecue.png" width="60%">.

* This was done using a custom ```detect_animal_numpy()``` function which iterates through the image with a certain kernel size and a stride size, and feeds each sample to the trained NN (nicknamed hunter)
* A heatmap is then generated from the output of the NN which gives us a probability distribution over the image of a certain animal ( chicken, pig, or panda)
* why use heatmaps instead of rectangles ? because they look cooler.

<img src="sample_images/barbecue.png" width="60%">.

## Step 5 (and probably the final step) - Train `hunter()` to detect fellow villagers and wipe out whole villages

* Chickens are just an excuse, it can be easily modified to shoot arrows on anything that moves.
* This is yet to be done.



