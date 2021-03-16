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

# メモ

## nbextensionsについて

選択中の文字を強調するために、`jupyter_contrib_nbextensions`をインストール。`jupyter-lab`は選択中の文字を強調する機能がないので使わない。ただ、`docker-compose.yml`で、

```docker-compose.yml
- JUPYTER_ENABLE_LAB=yes
```

としているが、`loaclhost:8888/tree`にアクセスすれば、`notebook`は使える。

## 権限について

普通に立ち上げるとユーザーは`jovyan`になってしまい、`apt-get`もできないが、

`Dockerfile`中で

```Dockerfile
USER root
```

として終われば`bash`は`root`で起動する。また上記のことをした上で、`docker-compose.yml`で、

```docker-compose.yml
- GRANT_SUDO=yes
```

としていれば、`jovyan`も`sudo`が使えるようになる。

つまり`GRANT_SUDO=yes` かつ`USER root`なら`jovyan`は`sudo`を使えるということ

https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html

参照