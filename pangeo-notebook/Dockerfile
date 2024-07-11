# ONBUILD instructions in base-image/Dockerfile are used to
# perform certain actions based on the presence of specific
# files (such as conda-linux-64.lock, start) in this repo.
# Refer to the base-image/Dockerfile for documentation.
ARG PANGEO_BASE_IMAGE_TAG=master
FROM pangeo/base-image:${PANGEO_BASE_IMAGE_TAG}

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gdal-bin \
    libgdal-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
RUN conda install -c conda-forge \
    ipykernel \
    numpy \
    argparse \
    matplotlib \
    gdal \
    && conda clean -afy

# Install acolite from GitHub
RUN pip install git+https://github.com/yourusername/acolite.git

# Create a new Jupyter kernel for this environment
RUN python -m ipykernel install --name acolite --display-name "Python (acolite)"