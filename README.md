# DeepMindBreak
*Decensoring Hentai with Deep Neural Networks*

This project applies an implementation of [Globally and Locally Consistent Image Completion](http://hi.cs.waseda.ac.jp/%7Eiizuka/projects/completion/data/completion_sig2017.pdf) to the problem of hentai decensorship. Using a deep fully convolutional neural network, DeepMindBreak can replace censored artwork in hentai with plausible reconstructions. The user needs to only specify the censored regions.

This project is LIMITED in capability. It is a proof of concept of ongoing research.

The decensorship works ONLY with color hentai images that have minor bar censorship of the penis or vagina.

# Dependencies

- Python 2/3
- TensorFlow 1.5
- Pillow
- tqdm
- scipy (only needed if poisson blending is enabled in decensor.py)
- pyamg (only needed if poisson blending is enabled in decensor.py)
- matplotlib (only for running test.py)

No GPU required! Tested on Ubuntu 16.04 and Windows.

Poisson blending is disabled by default since it has little effect on output quality.

Pillow, tqdm, scipy, pyamg, and matplotlib can all be installed using pip.

# Model
The pretrained model can be downloaded from https://drive.google.com/open?id=1mWHYSj0LDSbJQQxjR4hUMykQkVve2U3Q.

Unzip the contents into the /models/ folder.

# Usage

Using image editing software like Photoshop or GIMP, paint the areas you want to decensor the color with RGB values of (0,255,0). For each censored region, crop 128 x 128 size images containing the censored regions from your images and save them as new ".png" images.

Move the cropped images to the "decensor_input_images" directory. Decensor the images by running

```
$ python decensor.py
```

Decensored images will be saved to the "decensor_output_images" directory. Paste the decensored images back into the original image.

## II. Train the pretrained model on custom dataset

Put your custom dataset for training in the "data/images" directory and convert images to npy format.

```
$ cd training_data
$ python to_npy.py
```

Train pretrained model on your custom dataset.

```
$ python train.py
```

# To do
- ~~Add Python 3 compatibility~~
- Retrain for arbitrary shape censors
- Add a user interface
- Incorporate GAN loss into training

Contributions are welcome!

# License
