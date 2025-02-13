
# Installation

GluonTS is available from PyPi via:

```sh
pip install gluonts
````

```{attention}
**GluonTS uses a minimal dependency model.**

This means that to use most models and features additional dependencies need to
be installed. See the next section for more information.

```

## Optional and Extra Dependencies

Python has the notion of [extras](https://peps.python.org/pep-0508/#extras)
-- dependencies that can be optionally installed to unlock certain features of
a pacakge.

When installing a package, they are passed via ``[...]`` after the package
name:

```sh
pip install some-package[extra-1,extra-2]
````

We make extensive use of optional dependencies in GluonTS to keep the amount of
required dependencies minimal. To still allow users to opt-in to certain
features, we expose many extra dependencies.

For example, we offer support for reading and writing Arrow and Parquet based
datasets using [Apache Arrow](https://arrow.apache.org/). However, it is a
hefty dependency to require, especially if one has no need for it. Thus, we
offer the ``arrow``-extra, which installs the required packages and can be
simply enabled using:

```sh
pip install gluonts[arrow]
````

### Models


#### PyTorch

Models written using [PyTorch](https://pytorch.org/) are available via the
``gluonts.torch`` subpackage.

In addition to PyTorch we require [PyTorch Lightning](https://www.pytorchlightning.ai/)
to be installed as well.

Both required dependencies are included in the ``torch``-extra:

```sh
pip install gluonts[torch]
````


#### MXNet

MXNet based models require a version of ``mxnet`` to be installed.

```{note}

MXNet provives different package for CPU and GPU usages. Please refer to its
[documentation](https://mxnet.apache.org/versions/1.9.1/get_started?) to
select the right version fitting your use-case.

```

The ``mxnet``-extra will install a CPU-only version:

```sh
pip install gluonts[mxnet]

````


#### 3rd Party

##### R-Forecast

GluonTS includes a thin wrapper for calling the ``R`` `forecast` package.

In order to use it you need to install [``R``](https://www.r-project.org/) and
install the `forecast` package:

```sh
R -e 'install.packages(c("forecast", "nnfor"), repos="https://cloud.r-project.org")'
```

In addition, we require rpy2 to be installed:

```sh
pip install 'rpy2>=2.9.*,<3.*'
````

##### Prophet

The [Prophet](https://facebook.github.io/prophet/) forecasting library is
available via `gluonts.model.prophet` and requires the ``prophet`` package to
be installed.

The ``prophet``-extra also depends on it:

```sh
pip install gluonts[prophet]
```


### Datasets

#### JSON

Since Python's build in ``json`` package is known to be relatively slow, we use
faster implementations if available: ``orjson`` (recommended) and ``ujson``.

You can install ``orjson`` via:

```sh
pip install orjson
```

```{hint}
GluonTS will emit a warning if neither ``orjson`` nor ``ujson`` are installed.
There is no functional difference between the different implementations, but
especially when working with larger datasets, performance can be notably
impacted when relying on the default ``json`` package.
```

#### Arrow

GluonTS support [Parquet](https://en.wikipedia.org/wiki/Apache_Parquet) files
using [``PyArrow``](https://arrow.apache.org/docs/python/index.html).

Further, [arrow's custom data formats](https://arrow.apache.org/docs/python/ipc.html)
are also supported.

To utilise these, either install the ``pyarrow`` package or use the
``arrow``-extra:

```sh
pip install gluonts[arrow]
```

### Other

#### Shell

The ``shell`` module offers integration with Amazon SageMaker and is available
through:

```sh
pip install gluonts[shell]
```
