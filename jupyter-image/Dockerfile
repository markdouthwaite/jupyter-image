FROM ubuntu:17.10

# Based on the Jupyter Notebook from Daniel Baptista.
LABEL maintainer="Mark Douthwaite <mark@douthwaite.io>"

# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Update the apt-get and installs curl
RUN apt-get update \
  && apt-get install -y curl

# Update node version on apt-get
RUN curl -sL https://deb.nodesource.com/setup_9.x | bash -


# Installs node.js, python, pip and setup tools
RUN apt-get install -y \
    python3 \
    python3-pip \
    python3-setuptools \
    nodejs \
    build-essential \
    libzmq3-dev

# Setup python language
ENV LANG en_US.UTF-8
ENV LC_CTYPE en_US.UTF-8

# Upgrade pip
RUN pip3 install --upgrade pip

# Upgrade npm
RUN npm install npm@latest -g

# Install Mark's Python tools.
RUN pip3 install --upgrade scipy \
                            numpy \
                            sklearn \
                            torch \
                            keras \
                            matplotlib \
                            tensorflow \
                            seaborn \
                            bs4 \
                            boto3 \
                            pandas \
                            bokeh \
                            django \
                            nltk \
                            gensim \
                            scrapy \
                            pymc3 \
                            pystan \
                            statsmodels \
                            pillow \
                            theano \
                            werkzeug \
                            tornado \
                            lightfm \
                            virtualenv \
                            xgboost \
                            sagemaker

# Install jupyter notebook
RUN pip3 install \
  jupyter==1.0.0 \
  jupyterlab==0.31.12

# Fix ipython kernel version
RUN ipython3 kernel install

RUN apt-get install -y r-base
RUN Rscript -e "install.packages(c(\"devtools\", \"testthat\", \"roxygen2\"), repos = c(\"http://irkernel.github.io/\", \"http://cran.rstudio.com\"))"

# Install nodejs kernel
RUN npm config set user 0 \
 && npm config set unsafe-perm true \
 && npm install ijavascript -g

RUN ijsinstall --hide-undefined --install=global
