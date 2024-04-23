# Install Python and Pip from source on Ubuntu tutorial

In this tutorial I will show you how to install a desired version of python alongside with pip on Linux/Ubuntu.

We will build python from its offical source codes.

## Step 1: Update the Package Repository & Install Supporting Software

Update the package repository to ensure you get the latest available program version. Run the following command:

```bash
sudo apt update
```

compiling a package from source code requires additional software. Run the following command to install the required packages for Python:

```bash
sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget
```

## Step 2: Download the Desired Version of Python Source Code

Navigate to a folder that you want to download the python source into it:

(Here, I'm using /tmp folder)

```bash
cd /tmp
```

Navigate to the <a href="https://www.python.org/downloads/source/">official Python source code webpage</a> and copy the download link of the .tgz file.

Use the wget command to download the desired release of Python Source Code: 

(In this example I've used python3.8.13 but you can choose any version you need)


```bash
wget https://www.python.org/ftp/python/3.8.13/Python-3.8.13.tgz
```

Extract the compressed Files:

```bash
tar -xf Python-3.8.13.tgz
```

# Step 3: Install Python

Navigate to the extracted folder:

```bash
cd ./Python-3.8.13
```

Before you install the software, make sure you test the system and optimize Python.

```bash
./configure --enable-optimizations --with-ensurepip=install --prefix=/home/<username>/<path-to-my-python-installations>/Python3.8.13
```

Install Python: (make sure you're in the extracted folder)

```bash
sudo make install
```

Python is installed now. Verify Python Version:

```bash
python3 --version
```

you should get 'Python 3.8.13' as output.


# Step 4: Install Pip

Try to see if the pip is installed:

```bash
python3 -m pip --version
```

if pip is already install, you're good to go. 

Otherwise, Python comes with an ensurepip module, which can install pip in a Python environment.

```bash
python3 -m ensurepip --upgrade
```

Upgrade pip:

```bash
python3 -m pip install --upgrade pip
```

Now pip should be installed.

# Additional Notes

## Need sqlite3 package?

when building python from source, the sqlite3 package won't install automatically. To solve this issue we need to follow this instruction:

- Before installing python (step 3) we need to install this package on ubuntu:
  ```bash
  sudo apt install libsqlite3-dev
  ```
- then in the step 3, use this:
  ```bash
  ./configure --enable-optimizations --enable-loadable-sqlite-extensions --with-ensurepip=install --prefix=/home/<username>/<path-to-my-python-installations>/Python3.8.13
  ```
- then `sudo make install` then follow the next steps already described.

