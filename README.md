# Overview

This repo contains code for the "TensorFlow for Vehicle" series of codelabs.

There are multiple versions of this codelab depending on which version 
of the tensorflow libraries you plan on using:

* For [TensorFlow Lite](https://www.tensorflow.org/mobile/tflite/) the new, ground up rewrite targeted at mobile devices
* For the more mature [TensorFlow Mobile](https://www.tensorflow.org/mobile/mobile_intro) use 
  [this version of the codealab](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets-2).


This repo contains simplified and trimmed down version of tensorflow's example image classification apps.

* The TensorFlow Lite version, in `android/tflite`, comes from [tensorflow/contrib/lite/](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/contrib/lite).
* The Tensorflow Mobile version, in `android/tfmobile`, comes from [tensorflow/examples/android/](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android).

The `scripts` directory contains helpers for the codelab. Some of these come from the main TensorFlow repository, and are included here so you can use them without also downloading the main TensorFlow repo (they are not part of the TensorFlow `pip` installation).

# Vehicle-Detection-Using-Tensorflow-Android-Implemenation

pip install upgrade tensorflow 

Clone the repository

Now download the data set from the following link

Extract the Vehicle section where you see different vehicle category

Put these files into tf_files

Run the following command according to your version

python scripts/retrain.py --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos

python3 scripts/retrain.py --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos

It will around 4000 steps and you can also configure this step from retrain.py


## Test the newly model

python3 scripts/label_image.py --image xyz.jpg

python scripts/label_image.py --image xyz.jpg

If you see the result you're successfull

### On Android mobile 

You have already `tf_files/retrained_graph.pb` and `tf_files/retrained_labels.txt` which is retrained model graph and text file containing labels.

### Creating an Optimized model

python -m tensorflow.python.tools.optimize_for_inference \
  --input=tf_files/retrained_graph.pb \
  --output=tf_files/optimized_graph.pb \
  --input_names="Mul" \
  --output_names="final_result"

python3 -m tensorflow.python.tools.optimize_for_inference \
  --input=tf_files/retrained_graph.pb \
  --output=tf_files/optimized_graph.pb \
  --input_names="Mul" \
  --output_names="final_result"

According to your version 2 & 3

Now lets just optimize and quantize the graph

python -m scripts.quantize_graph \
  --input=tf_files/optimized_graph.pb \
  --output=tf_files/rounded_graph.pb \
  --output_node_names=final_result \
  --mode=weights_rounded

python3 -m scripts.quantize_graph \
  --input=tf_files/optimized_graph.pb \
  --output=tf_files/rounded_graph.pb \
  --output_node_names=final_result \
  --mode=weights_rounded

Setup the android studio and build the gradle which is already setup in `android/tfmobile` folder.

Now you need to add your models to project

Run the following command to copy and rename the file or you can just skip and copy paste the final and rename it manually.

cp tf_files/rounded_graph.pb android/tfmobile/assets/graph.pb
cp tf_files/retrained_labels.txt android/tfmobile/assets/labels.txt

That's it you made it end
Now build the apk and enjoy...


## Attention features

* More neural networks
* Model name and also finding axel of model
