# Modification of the file tensorflow-notebook of Jupyter Development Team.
# original to be found in https://github.com/jupyter/docker-stacks/tree/master/tensorflow-notebook

FROM lisaeick/dockerjupyter-middle

LABEL maintainer="Lisa Eick <>"

#Install important packages
RUN conda install --quiet --yes \
    -c conda-forge xgboost \
    openpyxl 
RUN conda install --quiet --yes \
    scikit-learn=0.23
#   -c free scikit-learn
RUN conda install --quiet --yes \
    -c conda-forge scikit-optimize 
RUN conda install --quiet --yes \
    -c conda-forge shap
RUN conda install --quiet --yes \
    -c conda-forge eli5
RUN mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

