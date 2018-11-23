# Anaconda Tips

## Using pip in Ananconda

There are packages which are available in `pip` but not in `Anaconda`. Here is how you can use pip in your anaconda environment to install the packages available in pip [source](https://stackoverflow.com/questions/41060382/using-pip-to-install-packages-to-anaconda-environment)

```python
conda create -n venv_name # venv_name is your virtual environment name; replace it with your virtual env name
source activate venv_name
conda install -yn venv_name -c anaconda pip
```

Now run the command `which pip` in your terminal (Linux or Mac), and the result would be the path to your `pip` in your venv_name. Which should look like `/anaconda3/envs/venv_name/bin/pip`. Assuming that this is the path to your `venv_name` then run the following command:

```python
/anaconda3/env/venv_name/bin/pip install <package_name>
```

As of Nov. 23, 2018, an example of a package which does not exist in anaconda repository but does exist in pip is `wikidata`. 