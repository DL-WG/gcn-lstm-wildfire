# Explainable Global Wildfire Prediction Models using Graph Neural Networks

## About The Project


Wildfire prediction has become increasingly crucial due to the escalating impacts of climate change. Traditional CNN-based wildfire prediction models struggle with handling missing oceanic data and addressing the long-range dependencies across distant regions in meteorological data. In this paper, we introduce an innovative Graph Neural Network (GNN)-based model for global wildfire prediction. We propose a hybrid model that combines the spatial prowess of Graph Convolutional Networks (GCNs) with the temporal depth of Long Short-Term Memory (LSTM) networks. Our approach uniquely transforms global climate and wildfire data into a graph representation, addressing challenges such as null oceanic data locations and long-range dependencies inherent in traditional models. Benchmarking against established architectures using an unseen ensemble of JULES-INFERNO simulations, our model demonstrates superior predictive accuracy. Furthermore, we emphasise the model’s explainability, unveiling potential wildfire correlation clusters through community detection and elucidating feature importance via Integrated Gradient analysis. Our findings not only advance the methodological domain of wildfire prediction but also underscore the importance of model transparency, offering valuable insights for stakeholders in wildfire management.


## Getting Started

### Hardware requirement

*   Programming language: Python (3.5 or higher)
*   Platform: Google Colab Pro
*   GPU: T4
*   Google Drive space: 50GB

### Software requirement

| Package Requirement                        |
|--------------------------------------------|
| os                                         |
| pandas                                     |
| math                                       |
| numpy                                      |
| netCDF4                                    |
| seaborn                                    |
| matplotlib                                 |
| pytorch                                    |
| sklearn                                    |
| pytorch-geometric                          |
| networkx                                   |



## Dataset
Data used for this project are from JULES-INFERNO. URL:
(https://imperiallondon-my.sharepoint.com/:f:/r/personal/mk1812_ic_ac_uk/Documents/Data/JULES-INFERNO?csf=1&web=1&e=3YXM21)


Four climate variables from 1961 to 1990: 
temperature (``LGM/drive/climate/CRU-NCEP-v7-LGM-n96e/tair``), humidity (``LGM/drive/climate/CRU-NCEP-v7-LGM-n96e/qair``), rainfall (``LGM/drive/climate/CRU-NCEP-v7-LGM-n96e/rain``) and lightning (``LGM/drive/lightning``).  JULES-INFERNO was implemented at a resolution of 1.25° latitude by 1.875° longitude, with each snapshot spanning 144 latitude units and 192 longitude units, resulting in a snapshot size of 144 × 192.


Five wildfire (Burnt area fraction) simulation ensembles from 1961 to 1990: P1(``LGM/output/p1``), P2(``LGM/output/p2``), P2(``LGM/output/p2``), P3(``LGM/output/p1``), P4(``LGM/output/p4``) and P5(``LGM/output/p5``). All ensemble members were simulated for the same timeframe (1961 to 1990) and with the same detrended meteorological conditions. Still, different initial internal states were implemented to cover a variety of model internal variabilities. As a result, the number of latitude units covered by the fire snapshots Pi,t, i = 1, 2, ..., 5, t = 1, 2, ..., 360 was reduced to 112, yielding a snapshot size of 112 × 192. As our work focused on the wildfire predictions, we shifted and clipped the meteorological data to align with the wildfire area data shape.


## Implementation
### Model structure
![model_structure](![model_structure](https://github.com/DL-WG/gcn-lstm-wildfire/assets/71702130/618820ae-76d8-48b0-a923-a06707ec9ce4))

### Data Processing

The `/Dataset/' directory illustrates the compressed graph data formulation process.


### Main Models

'Final_benchmarking.ipynb' contains implementations and benchmarking processes of GCN-LSTM models with the baseline models
'GCN_LSTM_v21_final.ipynb' contains the model implementation and training results

### Explainability

The overarching theme of our research, as encapsulated in the title, is the explainability of our GNN-based wildfire prediction model. The Explainability section delves into the primary facets that bolster our model’s interpretability: the inherent characteristics of the GNN, insights from community detection, and the significance of feature and node attributions.

The `/Explainability/' contains the Louvain Community Detection and Integrated Gradients implementation and results.

### Output

`/output_figure/` folder stores the metric comparison results and visual illustrations.


## License

MIT License. For more information see `LICENSE`


## Contact

Dayou Chen - dc421@ic.ac.uk<br>
Sibo Cheng - sibo.cheng@imperial.ac.uk<br>
Matthew Kasoar - m.kasoar12@imperial.ac.uk<br>
