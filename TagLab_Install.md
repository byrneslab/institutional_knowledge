# How to Install TagLab

TagLab is a wonderful image segmentation and AI piece of software. It can 
be a bit wonky to install. Here are some torubleshooting steps.

The main URL for TagLab is http://taglab.isti.cnr.it/ and the instructions 
for installing it are at 
https://github.com/cnr-isti-vclab/TagLab#installing-taglab

This should work fine for a PC running Windows or Linux.

A Mac might take more work, as one has to make sure to get the version of 
python3 right.

### Here are notes from Jarrett's installation of TagLab on his M1 
Macbook.

1. Install miniconda3 from https://docs.conda.io/en/latest/miniconda.html 
using the proper installer for your chip architecture. Note, TagLab wants 
python3 to be in the 3.10 family, NOT 3.11 at the time of writing this 
(2023-04-09).

2. Make sure you have installed homebrew from https://brew.sh/

3. Using homebrew, install qt, qt5, gdal, and cmake. I suppose you could 
skip the above installation of miniconda if you can install a version of 
python3 that is in the 3.10 family, but currently homebrew is installing 
in the 3.11 family by default.

4. Check what version of python is your default by opening a new terminal 
window and typing `python3 --version` and make sure if it is running the 
3.10.* version. You will likely have multiple versions on your computer. 
type `where python3` to see which ones. Try each, and see which gives you 
the right version. You can alias this to python3 in ~/bin or just remember 
to type out the full path from this point forward. Alternatley, you can 
likely muck about in your .zshrc to get the path you want set to be your 
primary python3 version. Your call. I'm happy to work with you on this, as 
it's a PITA.

5. Once you've got everything set so that you're running the right version 
of python3 and using the right architecture, install pyqt5 with the 
following 

```
pip3 install pyqt5 --config-settings --confirm-license= --verbose
```

as otherwise it will make your installation of TagLab hang.

6. While you're at it, get the right version of tensorflow and torch 
installed for the M1/arm64 architecture

```
conda install pytorch torchvision torchaudio -c pytorch-nightly

pip3 install --pre torch torchvision torchaudio --index-url 
https://download.pytorch.org/whl/nightly/cpu

conda install -c apple tensorflow-deps

pip3 install tensorflow-macos

pip3 install tensorflow-metal
```

You can read more about this on 
https://towardsdatascience.com/installing-pytorch-on-apple-m1-chip-with-gpu-acceleration-3351dc44d67c 
and 
https://betterprogramming.pub/installing-tensorflow-on-apple-m1-with-new-metal-plugin-6d3cb9cb00ca 
or just googling "install torch m1 osx"

7. In the TagLab directory, you should be OK from terminal now to run

```
python3 install.sh
```

and if it installs, you should be able to run

```
python3 TagLab.py
```

And away you go! Check out http://taglab.isti.cnr.it/docs for how to use 
it.
