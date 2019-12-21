# mplstyle


### Check the directory

```
In [2]: import matplotlib as mpl

In [3]: mpl.get_configdir()
Out[3]: '/home/foobar/.config/matplotlib'
```

### Copy style sheet to configuration directory

```
git clone https://github.com/neobar/mplstyle.git

cd mplstyle

mkdir -p /home/foobar/.matplotlib/stylelib

cp mimicIDL.mplstyle /home/foobar/.matplotlib/stylelib/
```
