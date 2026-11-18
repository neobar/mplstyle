# mplstyle

`mimicIDL.mplstyle` gives Matplotlib plots the boxed axes, inward ticks,
and black first curve of [IDL Direct Graphics](https://www.nv5geospatialsoftware.com/docs/PLOT_Procedure.html).
It uses Matplotlib's bundled DejaVu Sans to approximate the look of
[IDL's Hershey Simplex Roman](https://www.nv5geospatialsoftware.com/docs/Using_Hershey_Vector_Fon.html).

## Load the style

Run the examples from the repository directory. To load the style by name
from any directory, copy it to Matplotlib's user style library.

```sh
style_dir="$(python -c 'import matplotlib; print(matplotlib.get_configdir())')/stylelib"
mkdir -p "$style_dir"
cp mimicIDL.mplstyle "$style_dir/"
```

After restarting any running Python session, use `plt.style.use("mimicIDL")`
or replace the file path in either context below with `"mimicIDL"`.

## Single plot

Automatic axis limits snap outward to round numbers, with no extra x-axis
margin before rounding. To match IDL's zero baseline for an all-positive
linear y series, set the lower y limit explicitly.

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0.13, 9.86, 300)
flux = 1.5 + np.sin(x)

with plt.style.context("./mimicIDL.mplstyle"):
    fig, ax = plt.subplots()
    ax.plot(x, flux)
    ax.set(xlabel=r"Wavelength $\lambda$ ($\mu$m)", ylabel=r"Flux $F_\lambda$")
    ax.set_ylim(bottom=0)
    fig.savefig("spectrum.png")
    fig.savefig("spectrum-tight.pdf", bbox_inches="tight")
    plt.show()
```

The PNG retains the full `8 × 6` inch canvas, giving `1200 × 900` pixels
at 150 dpi. The PDF example crops to the plotted content.

## Multiple panels

Use `layout="constrained"` to give axis labels and tick labels room between
panels. This example plots the same data on linear and logarithmic y axes.

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0.13, 9.86, 300)
flux = 1.5 + np.sin(x)

with plt.style.context("./mimicIDL.mplstyle"):
    fig, (ax_linear, ax_log) = plt.subplots(2, 1, layout="constrained")
    for ax in (ax_linear, ax_log):
        ax.plot(x, flux)
        ax.set(xlabel=r"Wavelength $\lambda$ ($\mu$m)", ylabel=r"Flux $F_\lambda$")
    ax_linear.set_title("Linear")
    ax_log.set_title("Logarithmic")
    ax_log.set_yscale("log")
    plt.show()
```

## Custom CSS

#### Use full width in jupyter-notebook
See 
* https://stackoverflow.com/questions/77030544/how-do-i-increase-the-cell-width-of-the-jupyter-version-7
* https://stackoverflow.com/questions/21971449/how-do-i-increase-the-cell-width-of-the-jupyter-ipython-notebook-in-my-browser
