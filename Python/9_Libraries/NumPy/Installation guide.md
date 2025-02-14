


```
sudo apt update
# To update the package informations

python3 --version
pip3 --version
```

```
sudo apt install ipython3

sudo apt install jupyter-notebook
jupyter notebook

sudo apt install jupyterlab
jupyter-lab
```

If there is restriction on installation by pip, then create a virtual environment and install there.
```
sudo apt install python3-venv

python3 -m venv myenv

source myenv/bin/activate

pip install ipython jupyter notebook jupyterlab

jupyter notebook
# or
jupyter-lab

deactivate

```

```
pip3 install notebook
# for installing Jupyter notebook

pip3 install ipython
# Integrated terminal for Jupyter

pip3 install jupyterlab
# Advanced Notebook if needed
```