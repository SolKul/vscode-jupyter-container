# vscode-notebook-devcontainer
simple vscode project for development python and jupyter notebook in docker

# Usage

## Install Remote Container

Install Extensino for Visual Studio Code. 
[Remote - Containers - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)


## clone repository

clone this repository

## Open in Container

1. open Command Palette in Visual Studo Code.
2. Exec `Remote-Containers: Reopen Folder in Container`
3. wait until docker-compose build

# 追加したモジュール

選択中の文字を強調するために、`jupyter_contrib_nbextensions`をインストール。
(まだ`jupyter-lab`は選択中の文字を強調する機能がないので使わない。)