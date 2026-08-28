# Análise da Rede Social de Game of Thrones

Projeto GRC & IRN | ISCTE-Sintra | 2025/2026

Análise da rede de coocorrências das personagens de Game of Thrones (T1–T8)
usando teoria de grafos, redes complexas e Graph Convolutional Networks.

## Setup

### 1. Abrir o projeto

Abre a pasta no VSCode ou no Jupyter.

### 2. Criar o ambiente virtual

```bash
python -m venv .venv
```

Ativar:

- **Windows (PowerShell):** `.venv\Scripts\Activate.ps1`
- **Windows (CMD):** `.venv\Scripts\activate.bat`
- **Mac/Linux:** `source .venv/bin/activate`

### 3. Instalar dependências

```bash
pip install -r requirements.txt
```

O `torch-geometric` pode precisar de instalação separada dependendo da versão do PyTorch:

```bash
pip install torch-geometric -f https://data.pyg.org/whl/torch-2.7.0+cpu.html
```

Se não instalar, o notebook funciona na mesma — usa a GCN from-scratch.

### 4. Dataset

O ficheiro `data/houses_titles.csv` está incluído no entregável.

Os CSVs de nós e arestas por temporada devem ser descarregados de:
https://github.com/mathbeveridge/gameofthrones

Depois de descarregar, colocar em `data/nodes/` e `data/edges/`.

### 5. Correr o notebook

Abre `entregavel_3/IRN_projeto_fase3_V10_final.ipynb` e usa
**Kernel → Restart & Run All**.

## Estrutura do notebook

- **Etapa 1** — Dados e construção da rede
- **Etapa 2** — Análise temporal com Girvan-Newman (T1–T8)
- **Etapa 3** — Métricas da rede (clustering, mundo pequeno, lei de potência, modularidade, algoritmos from-scratch)
- **Etapa 4** — Rede neuronal GCN (cálculos manuais, treino, ablation study)
- **Etapa 5** — O que acontece quando removemos as personagens centrais?
- **Etapa 6** — Avaliação final e conclusões
- **Dashboard** — Painel interativo (Plotly)

## Grupo

Ilie Iftime (112779) · Inês Cruz (123557) · Sofia Quintino (123554) · Tomás Manarte (122090)
