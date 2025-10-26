Official setup page for tensorflow:
https://www.tensorflow.org/install/docker

Unfortunately, with the settings from there, the container did not see my GPU.

Command to run docker:
docker run --gpus all -it tensorflow/tensorflow:latest-gpu bash
And with this code:
import tensorflow as tf;
print(tf.config.list_physical_devices('GPU'))
Output: []

So I found out that we have new cuda version (13.0) and tensorflow not supprot it yet(last supported cuda version is 12.5) in oficial site:
https://www.tensorflow.org/install/source

So I try to use not last version of docker container:
docker run --gpus all -it tensorflow/tensorflow:2.13.0-gpu python

As result everything is working.
Container can see my GPU.
