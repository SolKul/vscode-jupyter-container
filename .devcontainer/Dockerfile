FROM jupyter/scipy-notebook
# apt-getを使う場合は次4行をコメントアウトする。
# USER root
## 高速化のため、リポジトリに日本のサーバを指定。
# RUN sed -i.org -e 's|archive.ubuntu.com|jp.archive.ubuntu.com|g' /etc/apt/sources.list
# RUN apt-get update
# jupyterのパスワードをここで設定。詳しいやり方については調べてください。
# (c.NotebookApp.token=''としてパスワードなしでログインできるようにしてもいいが、セキュリティ的に心配)
RUN echo "c.NotebookApp.password='sha1:3547cc032fbb:d6fae6e88035ebd5062fd982b0d8bdd8e11b9ec6'" >> ~/.jupyter/jupyter_notebook_config.py
RUN conda install -y jupyter_contrib_nbextensions