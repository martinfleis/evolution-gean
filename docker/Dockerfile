FROM jupyter/minimal-notebook:latest

LABEL maintainer="Martin Fleischmann <martin@martinfleischmann.net>"

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN conda install mamba \
    && conda config --add channels conda-forge \
    && conda config --set channel_priority strict \
    && mamba install --yes --quiet \
    'geopandas==0.8.2' \
    'momepy==0.4.2' \
    'seaborn==0.11.1' \
    'pygeos==0.8' \
    'scikit-learn==0.24.1' \
    'contextily==1.1.0' \
    'legendgram==0.0.3' \
    'pysal==2.3.0' \
    'osmnx==1.0.1' \
    'scipy==1.6.0' \
    'clustergram==0.3.0' \
    'dask==2021.1.1' \
    && conda clean --all --yes --force-pkgs-dirs \
    && find /opt/conda/ -follow -type f -name '*.a' -delete \
    && find /opt/conda/ -follow -type f -name '*.pyc' -delete \
    && find /opt/conda/ -follow -type f -name '*.js.map' -delete

#--- Jupyter config ---#
USER root
RUN echo "c.NotebookApp.default_url = '/lab'"\
    >> /home/$NB_USER/.jupyter/jupyter_notebook_config.py \
    && jupyter lab build -y \
    # Clean cache up
    && jupyter lab clean -y \
    && conda clean --all -f -y \
    && npm cache clean --force \
    && rm -rf $CONDA_DIR/share/jupyter/lab/staging \
    && rm -rf "/home/${NB_USER}/.node-gyp" \
    && rm -rf /home/$NB_USER/.cache/yarn \
    # Fix permissions
    && fix-permissions "${CONDA_DIR}" \
    && fix-permissions "/home/${NB_USER}" \
    # Build mpl font cache
    && python -c "import matplotlib.pyplot;"
USER $NB_UID

#--- htop ---#

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends htop \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Switch back to user to avoid accidental container runs as root
USER $NB_UID