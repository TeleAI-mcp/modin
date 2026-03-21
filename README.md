[![Modin](https://github.com/modin-project/modin/raw/main/docs/img/Modin_logo.png)](https://modin.readthedocs.io)

| [Linux](https://github.com/modin-project/modin/actions?query=workflow%3ALinux) | [macOS](https://github.com/modin-project/modin/actions?query=workflow%3AmacOS) | [Windows (3.9)](https://github.com/modin-project/modin/actions?query=workflow%3AWindows-3.9) | [Coverage](https://app.codecov.io/gh/modin-project/modin) |
|:---: |:---: |:---: |:---: |
| ![Linux](https://github.com/modin-project/modin/actions/workflows/linux.yml/badge.svg) | ![macOS](https://github.com/modin-project/modin/actions/workflows/macos.yml/badge.svg) | ![Windows (3.9)](https://github.com/modin-project/modin/actions/workflows/windows.yml/badge.svg) | [![codecov](https://codecov.io/gh/modin-project/modin/branch/main/graph/badge.svg)](https://app.codecov.io/gh/modin-project/modin) |

<p align="center">
<!-- markdownlint-disable MD036 -->
<em>Scale your Pandas workflows by changing a single line of code.</em>
<!-- markdownlint-enable MD036 -->
</p>

| [Installation](https://modin.readthedocs.io/en/stable/installation.html) | [Examples](https://modin.readthedocs.io/en/stable/examples/index.html) | [Architecture](https://modin.readthedocs.io/en/stable/architecture.html) | [Development](https://modin.readthedocs.io/en/stable/development/contributing.html) | [FAQ](https://modin.readthedocs.io/en/stable/faq.html) |
|:---: |:---: |:---: |:---: |:---: |
| [![]()][installation] | [![]()][examples] | [![]()][architecture] | [![]()][development] | [![]()][faq] |

[installation]: https://modin.readthedocs.io/en/stable/installation.html
[examples]: https://modin.readthedocs.io/en/stable/examples/index.html
[architecture]: https://modin.readthedocs.io/en/stable/architecture.html
[development]: https://modin.readthedocs.io/en/stable/development/contributing.html
[faq]: https://modin.readthedocs.io/en/stable/faq.html

[pandas_api]: https://pandas.pydata.org/pandas-docs/stable/reference/index.html
[ray]: https://www.ray.io/
[dask]: https://www.dask.org/
[unidist]: https://unidist.readthedocs.io/
[spark]: https://spark.apache.org/

### Why Modin?

Every data scientist spends a huge amount of time waiting for `pandas` computations to complete. 
In recent years, the ecosystem has grown to include many libraries that seek to perform the same 
operations faster. Most of these projects seek to distribute the computation, but doing so requires 
learning entirely new APIs and concepts. The goal of Modin is to provide a seamless experience for 
users of `pandas` by distributing their code with minimal changes via the use of Modin's internal 
implementations. Modin can be used to instantly speed up your pandas workflows with zero code changes.

Modin achieves this goal by distributing pandas computations across all of your available cores. The 
primary focus of Modin is to make your existing pandas code run faster and requires minimal code changes.

```python
# Standard pandas
import pandas as pd

df = pd.read_csv("train.csv")

# Modin uses all cores in your machine
import modin.pandas as pd

df = pd.read_csv("train.csv")
```

Modin is a seed project for [Pandas API Quill](https://github.com/modin-project/pandas-api-quill).

### Ray

Modin uses [Ray](https://www.ray.io/) to provide an easy-to-use way to parallelize your pandas 
computations. Starting with Modin 0.8.0, you can use Modin with [Ray](https://www.ray.io/) 
by installing modin like this: `pip install modin[ray]` or just `pip install modin`. 
We chose [Ray](https://www.ray.io/) because it makes it simple to build and run distributed 
applications. We aim to make the switch from pandas to Modin seamless.

### Dask

Modin also supports [Dask](https://www.dask.org/) as a backend. You can install Modin 
with dask like this: `pip install modin[dask]`. We chose [Dask](https://www.dask.org/) 
because it provides advanced parallelism for analytics and we can leverage its existing 
infrastructure for parallelizing pandas computations.

### Unidist

Modin also supports [unidist](https://unidist.readthedocs.io/) as a backend. 
You can install Modin with unidist by installing from source or `pip install modin[unidist]`. 
We chose [unidist](https://unidist.readthedocs.io/) because it provides uniform 
interface for cluster and single-machine execution, and has a minimal set of dependencies.

### Multi-threading

Modin uses its own partition manager, and different compute engines may have different ways to 
handle partitions and parallelism. The user-facing pandas-like API is unchanged between the different 
partition managers.

For more information on Modin's architecture, view the [architecture doc](https://modin.readthedocs.io/en/stable/architecture.html).

### Installing Modin

Modin can be installed with pip:

```bash
# Install Modin with Ray backend (the default)
pip install "modin[ray]" 

# Install Modin with Dask backend
pip install "modin[dask]"

# Install Modin with all compute backends
pip install "modin[all]"

# Install Modin from source
pip install git+https://github.com/modin-project/modin.git
```

For more detailed instructions on how to install Modin, view the [installation doc](https://modin.readthedocs.io/en/stable/installation.html).

### SQL support

Modin supports querying pandas DataFrames via SQL. 
You can use the `read_sql` function:

```python
import modin.pandas as pd

# Read pandas DataFrame
df = pd.read_csv("train.csv")

# Read table via SQL
from modin.pandas import SQLDispatcher

sql_dispatcher = SQLDispatcher()
result = sql_dispatcher.read_sql("SELECT * FROM df WHERE Age > 30", 
                                  connection="pandas://")
```

### Contributing to Modin

We are actively working on expanding the pandas coverage. The best way to contribute and help with 
this project is to implement a missing pandas function that you need. Check out our 
[contributing guide](https://modin.readthedocs.io/en/stable/development/contributing.html) to see 
how you can implement a pandas function in Modin.

### Getting Started

You can get started with Modin in your browser with an interactive Jupyter Notebook provided 
[launch on Binder](https://mybinder.org/v2/gh/modin-project/modin-binder-notebook/main?filepath=quickstart.ipynb):

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/modin-project/modin-binder-notebook/main?filepath=quickstart.ipynb)

Here are [more Jupyter Notebook examples](https://github.com/modin-project/modin-notebooks).

### Discussion

Feel free to ask questions and discuss on our 
[developer mailing list](https://groups.google.com/forum/#!forum/modin-dev).

### Citation

If you use Modin in your research, please cite both the [paper](https://arxiv.org/abs/2101.02009) 
and [this GitHub repository](https://github.com/modin-project/modin).

```bibtex
@misc{modin2021,
    author = {Devin R. Peters and
              Romain -Francois  and
              David  and
              Weizhi  and
              Yingbo  and
              Itamar  and
              Todd  and
              Stefan  and
              Adam  and
              Michael  and
              Joshua },
    title = {Modin: Parallel pandas with Ray},
    year = {2021},
    publisher = {GitHub},
    journal = {GitHub repository},
    howpublished = {\url{https://github.com/modin-project/modin}},
}
```

### Maintainers

The following people are currently maintainers of Modin:

- [@devin-petersohn](https://github.com/devin-petersohn)
- [@vitrioil](https://github.com/vitrioil)
- [@anmyachev](https://github.com/anmyachev)
- [@mvashishtha](https://github.com/mvashishtha)
- [@YaroslavIshchenko](https://github.com/YaroslavIshchenko)
- [@dchigare](https://github.com/dchigare)
- [@Gerrrr](https://github.com/Gerrrr)
- [@tg170](https://github.com/tg170)
- [@sultan00786](https://github.com/sultan00786)
- [@Jianghai-Quantil](https://github.com/Jianghai-Quantil)

### License

[Apache License 2.0](LICENSE)

[![Copyright (c) Modin contributors](https://img.shields.io/badge/Copyright%20(c)-Modin%20contributors-blue.svg)](LICENSE)

[//]: # "Please do not edit these following lines. They are used by GitHub actions."
[image-pypi]: https://badge.fury.io/py/modin.svg
[image-conda-forge]: https://img.shields.io/conda/vn/conda-forge/modin.svg
[link-conda-forge]: https://anaconda.org/conda-forge/modin
[image-python]: https://img.shields.io/pypi/pyversions/modin.svg
[link-docs]: https://img.shields.io/badge/docs-passing-green.svg
[link-releases]: https://github.com/modin-project/modin/releases
[link-issues]: https://github.com/modin-project/modin/issues

| PyPI | Conda-Forge | Python |
|:---:|:---:|:---:|
| [![][image-pypi]][link-releases] | [![][image-conda-forge]][link-conda-forge] | [![][image-python]][link-releases] |

| Docs | License |
|:---:|:---:|
| [![][link-docs]][link-docs] | [![][image-license]][LICENSE] |

[image-license]: https://img.shields.io/github/license/modin-project/modin.svg


1. related project [pandas-dev/pandas](https://github.com/pandas-dev/pandas)
2. related project [pola-rs/polars](https://github.com/pola-rs/polars)