FROM jupyter/minimal-notebook:latest
MAINTAINER chapmanbe <brian.chapman@utah.edu>
USER root

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
      tree \
      graphviz\
      less \
      openssh-client \
      gcc \
      libcurl4-openssl-dev \
      libexpat1-dev \
      libnetcdf-dev \
      locales-all \
      libxrender-dev \
      libfontconfig-dev \
      libffi-dev \
      rsync \
      mongodb-clients \
      libmariadb-client-lgpl-dev \
      vim \
      curl \
  && rm -rf /var/lib/apt/lists/*


WORKDIR /home/jovyan

# Set default editor to nano
RUN update-alternatives --set editor /bin/nano

USER jovyan


RUN conda update conda -y && conda install -y \
    pip \
    gensim \
    biopython \
    altair \
    vega \
    nb_conda_kernels

RUN conda install -c conda-forge jupyter_contrib_nbextensions nbstripout

RUN pip install pydicom \
    textblob \
    ipythonblocks \
    pydotplus \
    pycontextnlp \
    radnlp \
    pytest \
    matplotlib_venn \
    wordcloud \
    nbstripout


WORKDIR /home/jovyan

ADD media media
ADD decart_welcome.ipynb decart_welcome.ipynb

# RUN nbstripout --install
CMD ["start-notebook.sh"]
