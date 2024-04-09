# Install Python and Pip from source on Ubuntu tutorial

## Step 1: Update the Package Repository & Install Supporting Software

`sudo apt update`

`sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget`

## Step 2: Download the Desired Version of Python Source Code

Navigate to the official Python source code webpage and select the program version you want to install.

Use the wget command and the link above to download the newest release of Python Source Code:

`cd /tmp`

`wget https://www.python.org/ftp/python/3.12.1/Python-3.12.1.tgz`

extract Compressed Files:

`tar -xf Python-3.12.1.tgz`

# Step 3: Install Python

Navigate to the extracted folder:

`cd ./Python-3.12.1`

Before you install the software, make sure you test the system and optimize Python.

`./configure --enable-optimizations`

Install Python:

`sudo make install`

Verify Python Version:

`python3 --version`

# Step 4: Install Pip

Python comes with an ensurepip module, which can install pip in a Python environment.

`python3 -m ensurepip --upgrade`

Upgrade pip:

`python3 -m pip install --upgrade pip`

