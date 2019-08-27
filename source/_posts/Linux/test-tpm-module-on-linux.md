---
title: Test TPM module on Linux
toc: true
date: 2019-08-27 21:57:38
tags: [TPM,Linux]
categories: [Linux]
---



<!--more-->



```bash
#Test on Ubuntu 18.04

#Update
sudo apt update
sudo apt upgrade

#Make sure kernel version is 4.12 or higher
uname -r

#Install TPM2 tools
sudo apt install *tpm2*

#Install python2
sudo apt install python
sudo apt install python-pip
pip install -U pytest
pip install -U pytest-html
pip install -U pytest-rerunfailures

#Download TPM2 test scripts
sudo apt install git
git clone https://github.com/jsakkine-intel/tpm2-scripts
#Download tpm2_smoke.py from: https://github.com/jsakkine-intel/tpm2-scripts/tree/4398af02a90442a85751148aebf725992a2949f3

#Run test
sudo python -m pytest -v tpm2_smoke.py
```



## Reference material

> - [tpm2-scripts](https://github.com/jsakkine-intel/tpm2-scripts)
