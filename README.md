# ucx-py_notes
Installation notes for UCX and UCX-PY

# mpi4py
```
env MPICC=$(which mpicc) pip install --no-cache-dir mpi4py
```

# Modules
```
ml openmpi/3.1.6
```
# Install UCX
```
./autogen.sh
mkdir build
cd build

../contrib/configure-release \
  --enable-mt \
  --prefix=/home/ksayers/bin \
  --with-rdmacm \
  --with-verbs

make -j8
make install

```

# UCX-PY

```
conda create -n ucx -c conda-forge \
    automake make libtool pkg-config \
    libhwloc psutil \
    "python=3.7" setuptools "cython>=0.29.14,<3.0.0a0"
```

```
CC=gcc python setup.py build_ext --inplace
pip install .
```
