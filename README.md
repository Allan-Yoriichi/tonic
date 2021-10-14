![tonic](tonic-logo-padded.png)
[![PyPI](https://img.shields.io/pypi/v/tonic)](https://pypi.org/project/tonic/)
[![Travis Build Status](https://travis-ci.com/neuromorphs/tonic.svg?branch=master)](https://travis-ci.com/neuromorphs/tonic)
[![codecov](https://codecov.io/gh/neuromorphs/tonic/branch/develop/graph/badge.svg?token=Q0BMYGUSZQ)](https://codecov.io/gh/neuromorphs/tonic)
[![Documentation Status](https://readthedocs.org/projects/tonic/badge/?version=latest)](https://tonic.readthedocs.io/en/latest/?badge=latest)
[![contributors](https://img.shields.io/github/contributors-anon/neuromorphs/tonic)](https://github.com/neuromorphs/tonic/pulse)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5079802.svg)](https://doi.org/10.5281/zenodo.5079802)


**Tonic** is a tool to facilitate the download, manipulation and loading of event-based/spike-based data. Have a look at the list of [supported datasets](https://tonic.readthedocs.io/en/latest/datasets.html) and [transformations](https://tonic.readthedocs.io/en/latest/transformations.html)!
It's fully compatible with PyTorch Vision/Audio for an intuitive interface, so that you spend less time worrying about how to read files and more time on things that matter.

## Documentation
You can find the full documentation on Tonic [on this site](https://tonic.readthedocs.io/en/latest/index.html).

## Install
```bash
pip install tonic
```
If you prefer conda, please check out the [forge repository](https://github.com/conda-forge/tonic-feedstock).

## Getting started
Have a look at our [introduction](https://tonic.readthedocs.io/en/latest/getting_started.html) page to see how some of the moving parts work. There are some more short examples available [here](https://tonic.readthedocs.io/en/latest/examples.html).

## Quickstart
If you're looking for a minimal example to run, this is it!

```python
import tonic
import tonic.transforms as transforms

sensor_size = tonic.datasets.NMNIST.sensor_size
transform = transforms.Compose([transforms.Denoise(filter_time=10000),
                                transforms.ToFrame(sensor_size=sensor_size, n_time_bins=3),])

testset = tonic.datasets.NMNIST(save_to='./data',
                                train=False,
                                transform=transform)

from torch.utils.data import DataLoader
testloader = DataLoader(testset, shuffle=True)

events, target = next(iter(testloader))
```

## Discussion
Have a question about how something works? Ideas for improvement? Feature request? Please get in touch here on GitHub via the [Discussions](https://github.com/neuromorphs/tonic/discussions) page!

## Contributing
Please check out the [contributions]() page for details.

## Citation
If you find this package helpful, please use the following citation:

```BibTex
@software{lenz_gregor_2021_5079802,
  author       = {Lenz, Gregor and
                  Chaney, Kenneth and
                  Shrestha, Sumit Bam and
                  Oubari, Omar and
                  Picaud, Serge and
                  Zarrella, Guido},
  title        = {Tonic: event-based datasets and transformations.},
  month        = jul,
  year         = 2021,
  note         = {{Documentation available under 
                   https://tonic.readthedocs.io}},
  publisher    = {Zenodo},
  version      = {0.4.0},
  doi          = {10.5281/zenodo.5079802},
  url          = {https://doi.org/10.5281/zenodo.5079802}
}
```
