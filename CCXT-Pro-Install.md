# How To Install

Installing CCXT Pro requires visiting the https://ccxt.pro website and obtaining a CCXT Pro license. The license gives you the access to the CCXT Pro codebase in a private GitHub repository.

```diff
- this part of the doc is currenty a work in progress
- there may be some issues here and there
- feedback and pull requests appreciated
```

## JavaScript

```shell
# in your project directory

# if you're using Git/HTTPS authentication
npm install git+https://github.com/kroitor/ccxt.pro.git

# if you are connecting to GitHub with SSH
npm install git@github.com/kroitor/ccxt.pro.git
```

## Python

```shell
# if you're using Git/HTTPS authentication
pip3 install git+https://github.com/kroitor/ccxt.pro.git#subdirectory=python

# if you are connecting to GitHub with SSH
pip3 install git+ssh://git@github.com/kroitor/ccxt.pro.git#subdirectory=python
```

## PHP

```shell
# in your project directory
composer config repositories.ccxtpro '{"type": "git", "url": "https://github.com/kroitor/ccxt.pro.git"}'
composer require ccxt/ccxtpro
```