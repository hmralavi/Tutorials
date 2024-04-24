# Install Tensorflow GPU on Ubuntu Tutorial

## Install Tensorflow

According to https://www.tensorflow.org/install/pip#linux install tensorflow using pip:

```bash
python3 -m pip install tensorflow[and-cuda]
```

run the following command in terminal to see if your gpu is detected by tensorflow:

```bash
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

if you see a list of gpu name, the gpu is detected successfully. you don't need to do anything else.

however, if the gpu is not detected properly, you should get a warning like this:

`W tensorflow/core/common_runtime/gpu/gpu_device.cc:2251] Cannot dlopen some GPU libraries. Please make sure the missing libraries mentioned above are installed properly if you would like to use GPU. Follow the guide at https://www.tensorflow.org/install/gpu for how to download and setup the required libraries for your platform.
Skipping registering GPU devices...`

in this case, to enable gpu for tensorflow, follow the next section.

## Enable GPU support

for some reason, tensorflow cannot detect cuda libraries. so we need to add them to environmental variable.

to do so, run this in the terminal:

```bash
python3 -c "import nvidia.cudnn;print(nvidia.cudnn.__file__)"
```

you will get a path, something like this:

`/home/hmralavi/Programs/Python/venv/tensorflow-venv/lib/python3.11/site-packages/nvidia/cudnn/__init__.py`

copy it.

now run this:

```bash
gedit ~/.bashrc
```

now add these line at the end of the ".bashrc":\
(make sure to use your own path)

```
# enable gpu support for tensorflow
NVIDIA_PACKAGE_DIR="/home/hmralavi/Programs/Python/venv/tensorflow-venv/lib/python3.11/site-packages/nvidia"
for dir in $NVIDIA_PACKAGE_DIR/*; do
    if [ -d "$dir/lib" ]; then
        export LD_LIBRARY_PATH="$dir/lib:$LD_LIBRARY_PATH"
    fi
done
```

now save and close the texteditor and run this:

```bash
source ~/.bashrc
```

now close all terminals.

now open a new terminal and check if the gpu is detected by tensorflow:

```bash
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

if you followed the instructions correctly, the gpu support should be enabled for tensorflow now.

## Additional Notes

### Disable Tensorflow warnings:
```python
import os
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "2"

import tensorflow as tf
print(tf.config.list_physical_devices("GPU"))
```
