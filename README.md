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
  --with-rdmacm --with-verbs \
  --with-rc --with-ud --with-dc \
  --with-mlx5-dv \
  --with-cm \
  --with-dm \
  --enable-debug \
  --enable-compiler-opt=3 \
  --enable-optimizations

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

# Resources
* https://github.com/openucx/ucx/wiki/UCX-environment-parameters
* https://github.com/rapidsai/ucx-py/issues/361
* https://github.com/dask/distributed/pull/3759
* https://www.mellanox.com/related-docs/prod_acceleration_software/HPC-X_Toolkit_User_Manual_v2.1.pdf
