# *Game of Thrones* Social Network Analysis

A project developed for the **Information and Neural Networks (IRN)** course within the **Complex Network Management (GRC)** unit.

The project analyses the social network of the characters in the television series *Game of Thrones* using graph theory, complex network analysis, community detection, and Graph Convolutional Networks.

> **Institution:** ISCTE-Sintra  
> **Academic year:** 2025/2026  
> **Group:** 24

---

## About the project

In this study, each *Game of Thrones* character is represented as a node in the network. Two characters are connected when they appear in the same scene, and the weight of the connection corresponds to the number of co-occurrences between them.

The analysis covers all eight seasons of the series, making it possible to study how the network evolves over time and to identify the most important characters, communities, and connections.

The project combines:

- Construction of social networks from co-occurrence data;
- Temporal analysis of the networks from Seasons 1 to 8;
- Centrality and connectivity metrics;
- Community detection;
- The Girvan–Newman algorithm;
- Modularity analysis;
- Clustering and small-world network analysis;
- Degree-distribution and power-law analysis;
- From-scratch implementations of classical algorithms;
- Graph Convolutional Networks (GCNs);
- Ablation studies;
- Analysis of the impact of removing the most central characters;
- Static and interactive visualisations.

## Research objectives

The main objectives of this project are to:

1. Build a character network from shared scene appearances;
2. Compare the structure of the network across seasons;
3. Identify the most important characters in the narrative;
4. Detect communities and possible narrative groups;
5. Evaluate the robustness of the network after removing central characters;
6. Apply a Graph Convolutional Network to the character network;
7. Compare custom algorithm implementations with library-based methods;
8. Present the results through charts, tables, and an interactive dashboard.

## Repository structure

```text
.
├── Entregavel3_IRN_Grupo24/
│   ├── Projeto_IRN_Entrega3_Grupo24.ipynb
│   ├── bridges_summary.csv
│   ├── season_1_fragmentacao.png
│   ├── season_2_fragmentacao.png
│   ├── season_3_fragmentacao.png
│   ├── season_4_fragmentacao.png
│   ├── season_5_fragmentacao.png
│   ├── season_6_fragmentacao.png
│   ├── season_7_fragmentacao.png
│   └── season_8_fragmentacao.png
│
├── data/
├── Relatório_IRN_Entrega3_Grupo24.pdf
├── requirements.txt
├── LICENSE
└── README.md
```

The main notebook contains the complete analysis, including data loading, network construction, metric calculation, GCN training, experimental studies, and visualisation of the results.

The `season_X_fragmentacao.png` files show the network fragmentation analysis for each season. The `bridges_summary.csv` file contains summary information about the bridge edges identified during the network analysis.

## Dataset

The dataset represents the characters and their interactions throughout the eight seasons of *Game of Thrones*.

The network is constructed according to the following model:

- **Node:** character;
- **Edge:** two characters appear in the same scene;
- **Edge weight:** number of co-occurrences between the two characters;
- **Network:** weighted, undirected graph.

The data used in this project are based on the following repository:

[Game of Thrones Network Data](https://github.com/mathbeveridge/gameofthrones)

The data should be organised approximately as follows:

```text
data/
├── nodes/
│   ├── got-s1-nodes.csv
│   ├── got-s2-nodes.csv
│   └── ...
│
├── edges/
│   ├── got-s1-edges.csv
│   ├── got-s2-edges.csv
│   └── ...
│
└── houses_titles.csv
```

The notebook automatically searches for the `data` directory in the current directory and in its parent directories. The file names and column names must match the paths and variables used in the notebook.

## Requirements

- Python 3.10 or later;
- Jupyter Notebook or JupyterLab;
- Git, optionally;
- A virtual environment is recommended.

The main libraries used in the project include:

- `pandas`;
- `numpy`;
- `networkx`;
- `matplotlib`;
- `seaborn`;
- `plotly`;
- `scikit-learn`;
- `scipy`;
- `torch`;
- `torch-geometric`, when available.

The complete list of dependencies is available in [`requirements.txt`](requirements.txt).

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/IlieIftime/Network-of-Thrones.git
cd Network-of-Thrones
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

#### Windows — PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

#### Windows — Command Prompt

```cmd
.venv\Scripts\activate.bat
```

#### macOS or Linux

```bash
source .venv/bin/activate
```

### 4. Install the dependencies

```bash
pip install -r requirements.txt
```

If `torch-geometric` is not installed automatically, it may need to be installed according to the installed PyTorch version:

```bash
pip install torch-geometric
```

The notebook also includes a from-scratch GCN implementation, allowing the main analysis to run even when `torch-geometric` is unavailable.

## Running the project

The main notebook is located at:

```text
Entregavel3_IRN_Grupo24/Projeto_IRN_Entrega3_Grupo24.ipynb
```

To launch Jupyter Notebook:

```bash
jupyter notebook
```

Then:

1. Open `Projeto_IRN_Entrega3_Grupo24.ipynb`;
2. Select the virtual environment created above;
3. Run the cells in the displayed order;
4. To reproduce all results, select **Kernel → Restart & Run All**.

JupyterLab can also be launched with:

```bash
jupyter lab
```

## Notebook contents

### 1. Data loading and preparation

- Importing character and edge files;
- Cleaning and transforming the data;
- Constructing one graph per season;
- Building the aggregated network;
- Preparing adjacency matrices and node features;
- Running data-integrity checks.

The aggregated network produced by the notebook contains 363 characters and 2,594 edges after preprocessing. Its giant component contains 360 characters and 2,591 edges. These values may change if the source data or preprocessing steps are modified.

### 2. Temporal analysis

- Comparing the networks from Seasons 1 to 8;
- Tracking the evolution of the number of nodes and edges;
- Studying changes in density and connectivity;
- Identifying the most relevant characters in each season;
- Applying the Girvan–Newman algorithm;
- Analysing the evolution of modularity and community structure.

### 3. Network metrics and properties

The notebook calculates several network-analysis metrics, including:

- Node degree;
- Weighted degree;
- Degree centrality;
- Betweenness centrality;
- Closeness centrality;
- Eigenvector centrality;
- Clustering coefficient;
- Average shortest-path length;
- Network density;
- Modularity;
- Connected components;
- Degree distribution;
- Small-world properties;
- Power-law analysis.

Whenever relevant, manually calculated results are compared with the output of NetworkX implementations.

### 4. Community detection

The network is analysed to identify groups of characters with stronger internal cohesion.

The Girvan–Newman algorithm is used to progressively remove bridge edges. This analysis helps identify:

- Which edges are most important for keeping the network connected;
- How the network fragments;
- Which communities emerge in each season;
- Which characters act as bridges between different groups.

The bridge-edge results are summarised in:

```text
Entregavel3_IRN_Grupo24/bridges_summary.csv
```

### 5. Graph Convolutional Network

The project includes an application of Graph Convolutional Networks to the character network.

The analysis includes:

- Construction of the adjacency matrix;
- Adjacency-matrix normalisation;
- Preparation of node features;
- Manual implementation of the main GCN operations;
- Neural-network training;
- Performance evaluation;
- Comparison with a library-based implementation;
- An ablation study to evaluate the importance of the different model components.

### 6. Removal of central characters

The project studies the impact of removing the most important characters from the network.

The analysis evaluates:

- Changes in the number of connected components;
- Reduction in global connectivity;
- Changes in the size of the giant component;
- Increase in network fragmentation;
- Structural importance of central characters;
- Network robustness under targeted removals.

The fragmentation plots for each season are available at:

```text
Entregavel3_IRN_Grupo24/season_1_fragmentacao.png
...
Entregavel3_IRN_Grupo24/season_8_fragmentacao.png
```

### 7. Visualisations and dashboard

The results are presented through:

- Temporal-evolution plots;
- Network visualisations;
- Statistical distributions;
- Season-to-season comparisons;
- Centrality plots;
- Community visualisations;
- An interactive dashboard developed with Plotly.

## Main findings

The notebook provides a comprehensive view of the evolution of the *Game of Thrones* character network.

Among the analysed results are:

- The characters with the greatest structural importance;
- The characters that act as bridges between communities;
- The evolution of connectivity across seasons;
- The presence and evolution of narrative communities;
- The fragmentation caused by removing central characters;
- The relationship between network structure and narrative events;
- The performance of the GCN for the task defined in the notebook.

For the executed results and detailed conclusions, consult the report:

```text
Relatório_IRN_Entrega3_Grupo24.pdf
```

## Technologies

- **Python** — main programming language;
- **Jupyter Notebook** — development and presentation environment;
- **Pandas** — data manipulation;
- **NumPy** — numerical and matrix operations;
- **NetworkX** — graph construction and analysis;
- **Matplotlib and Seaborn** — statistical visualisation;
- **Plotly** — interactive visualisations and dashboard;
- **SciPy** — scientific computing;
- **Scikit-learn** — metrics and machine-learning utilities;
- **PyTorch** — neural-network implementation and training;
- **PyTorch Geometric** — graph-specific operations, when available.

## Authors

- **Ilie Iftime** — 112779
- **Inês Cruz** — 123557
- **Sofia Quintino** — 123554
- **Tomás Manarte** — 122090

## License

This project is distributed under the license specified in [`LICENSE`](LICENSE).

The data used in this project are intended for academic and research purposes.
