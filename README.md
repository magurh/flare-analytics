[![python](https://img.shields.io/badge/Python-3.11-3776AB.svg?style=flat&logo=python&logoColor=white)](https://www.python.org) [![jupyter](https://img.shields.io/badge/Jupyter-Lab-F37626.svg?style=flat&logo=Jupyter)](https://jupyterlab.readthedocs.io/en/stable) [![Flare](https://img.shields.io/badge/flare-network-e62058.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAAAXNSR0IArs4c6QAAAn1JREFUOE+1VEtIVFEY/v5zznU07QVSSmNCDzOKkhb2hGgzREQUSbgRJSPBXaDtgtkEYbRpVblSkiCLRLRFEYIKtrVcFBEZPmYoGTSbIZ17/lPnzqNxmqIR/Bf3nnse3//9//fdQ8iIyNX7G79Eptvixj0kIEAGADMgvJEXdkAggjEG9uG9SbvEXLB3x1NKbRyrqAtVfqMyVoByFFgziNLLmXk9UJOxZNMJzRjbJuu86YGdF8L7YkVbfZrBBIgkkxRK6myKZppucoNdZyVRMdNDZIJDKnK3Mx71MQpdgDOyW3AbIhshBZSs3CiB8vb6Frp27gEN1zZf2fVuvtOnFL4XAA4nQC0ICQFO9HBFybaTtkwFgbCOIXZ8T+BIf8dLuyl3k7KO5/O59oCmf2T73Gxki+OoNDEnvpKjAyDqyPjm5tPj2ezTDCcbb7WZVxO3i12GcTVISmitE97LqkOAsFS+6WPlm3u7cgKOnm9/Uj0yczFaYOBwQtJMYY21clIoO+8IwqdAVUNtd/DhH4DmsZEzLZdcn5RYklamhIJpxazaIGhKMJUMTK3TODzZm7P/NHygoX73V/3I2sMkwbwS2UAmmUEpLLtxKAbe+qLxwPSAj35ZOJf6NNR6s0a9D500xtCyZAEQ2b/4x1K8aGF+3hECUELB7/fP1V6/3EUnqhf/ZaO1t00+Js5Zsp3srTzrnlookbpQIHy0qvHgs2D3aoFptKbpjH8qNlgiJBYdxnouRGm4a9WtoPFAW3vp+GyHZPa8xiRQ1tojKUj2jsg7yDz/sCHUdGNBK0Aw4TMt41jo98WbL6JXmrnTV/F64EVfSVHxxP7Bjqa/eex/wH8Cb5jx4nKk/dAAAAAASUVORK5CYII=&colorA=FFFFFF)](https://dev.flare.network/)

# Flare Metrics

A set of tools for web-scrapping  and analysing Flare Network's data providers.

1. [flaremetrics.io](flaremetrics.io):
    - [x] Validator data
    - [x] FTSO data
    - [x] Songbird compatibility for FTSO data
2. [Flare systems explorer](https://songbird-systems-explorer.flare.rocks/entities/ftsoDataProvider)
    - [x] Songbird FTSO data
3. [FTSO monitor](https://flare-ftso-monitor.flare.network/data-providers)
    - [ ] FTSO data
    - [ ] Songbird compatibility

Note: Staking is currently live only on Flare. The data of the FTSO providers from [flare-metrics.io](flaremetrics.io) does not include C-chain addresses. As such, matching FTSO addresses with validator nodes can be done only based on the names. An alternative is to use a different source for extracting FTSO data, such as the [FTSO monitor](https://flare-ftso-monitor.flare.network/data-providers), which only includes FTSO data.

### Setup
----------------------------

1. Create and Activate Virtual Environment
On Windows:

```
python -m venv venv
venv\Scripts\activate
```

On MacOS/Linux:
```
python3 -m venv venv
source venv/bin/activate
```

2. Install dependencies:
```
pip install -r requirements.txt
```


### Web scrapping
----------------------------

There are two types of data that one can import: validator data which refers to the validator nodes on the P-chains, and FTSO data for the data providers on the C-chains. To import validator data, navigate to the root directory and run:
```
python data_scripts/flare_metrics_validator.py
```

This will create a dataframe within the `data` sub-directory, with information about all current validators on Flare.

For FTSO data, there are multiple available sources: [flaremetrics.io](flaremetrics.io), [Flare systems explorer](https://songbird-systems-explorer.flare.rocks/entities/ftsoDataProvider) (currently supporting only Songbird and testnets), and [FTSO monitor](https://flare-ftso-monitor.flare.network/data-providers). Run one of the following from the root directory:
```
python data_scripts/flare_metrics_ftso.py
python data_scripts/sys_explorer_ftso.py
```
Note that the `flare_metrics_ftso.py` script will import Flare network data by default. If songbird data is needed instead, the `network` parameter within `flare_metrics_ftso.py` should be changed before running the script.


