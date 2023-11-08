# mplstyle


### Check the directory

```
In [2]: import matplotlib as mpl

In [3]: mpl.get_configdir()
Out[3]: '/home/foobar/.matplotlib'
```

### Copy style sheet to configuration directory

```
git clone https://github.com/neobar/mplstyle.git

cd mplstyle

mkdir -p /home/foobar/.matplotlib/stylelib

cp mimicIDL.mplstyle /home/foobar/.matplotlib/stylelib/
```

## Custom CSS

#### Use full width in jupyter-notebook
See 
* https://stackoverflow.com/questions/77030544/how-do-i-increase-the-cell-width-of-the-jupyter-version-7
* https://stackoverflow.com/questions/21971449/how-do-i-increase-the-cell-width-of-the-jupyter-ipython-notebook-in-my-browser
