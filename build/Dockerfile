FROM google/cloud-sdk:slim

RUN apt update && apt install -y wget

# (Optional) Install and configure Miniconda3.
ENV CONDA_HOME=/opt/conda
ENV PATH=${CONDA_HOME}/bin:${PATH}
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-py39_23.1.0-1-Linux-x86_64.sh
RUN bash Miniconda3-py39_23.1.0-1-Linux-x86_64.sh -b -p ${CONDA_HOME} \
  && ${CONDA_HOME}/bin/conda config --system --set always_yes True \
  && ${CONDA_HOME}/bin/conda config --system --set auto_update_conda False \
  && ${CONDA_HOME}/bin/conda config --system --prepend channels conda-forge \
  && ${CONDA_HOME}/bin/conda config --system --set channel_priority strict

COPY requirements.txt .
RUN ${CONDA_HOME}/bin/pip install -r requirements.txt