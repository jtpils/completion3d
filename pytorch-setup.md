Below are instructions on how to setup completion3d training in pytorch.
New networks can be added following the template in pytorch/models/PointNetFCAE.py 
and adding corresponding import statements in pytorch/main.py and 
pytorch/utils/train_utils.py Feel free to submit new model additions to the 
benchmark as a pull request.

## Clone Repository

```
git clone git@github.com:lynetcha/completion3d.git
```

## Install CUDA and CUDNN

Instructions below assume CUDA 9.0 is installed in /usr/local/cuda

```
export PATH=/usr/local/cuda/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

## Pytorch Python Environment

```
cd completion3d/pytorch
PYTHON_BIN=/path/to/python3.6
virtualenv -p $PYTHON_BIN comp3d_pth_venv
source comp3d_pth_venv/bin/activate
pip install -r ../requirements/pytorch-requirements.txt

```

## Build Chamfer module ([Grouiex et al.](https://github.com/ThibaultGROUEIX/AtlasNet/tree/master/extension))

```
cd utils/chamfer
python setup.py install
cd ../../
```

## Build EMD module ([Xia et al.](https://github.com/fxia22/pointGAN/tree/master/emd) - KNOWN ISSUES FOR SETUPS OTHER THAN Python 2.7 + Pytorch 0.1.11 - Feel free to submit a pull request with fixes for other setups)

```
cd utils/emd/src
chmod +x make.sh
./make.sh
python setup.py install
cd ../
python build.py
cd ../../../
```

## Run Pytorch Training/Testing

```
cd pytorch
```

Link data (see data-setup.md)

```
ln -s /path/to/data data
```

Modify parameters in *run.sh*

```
chmod +x run.sh
./run.sh
```
