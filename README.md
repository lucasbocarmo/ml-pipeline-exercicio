# Pipeline de Machine Learning com GitHub Actions

Este é um projeto de exercício para demonstrar a automação de uma pipeline de Machine Learning usando GitHub Actions.

## Objetivo

O objetivo deste projeto é ter um workflow automatizado que, a cada `push` na branch `main`, executa um script de treino de Machine Learning e disponibiliza o relatório de performance do modelo como um artefato.

## O Workflow: ML Pipeline

O fluxo de trabalho (`.github/workflows/ml.yml`) realiza os seguintes passos:

1.  **Trigger (Gatilho):** O workflow é acionado automaticamente a cada `push` no repositório.
2.  **Checkout:** O código do repositório é baixado para a máquina virtual do GitHub.
3.  **Setup (Configuração):** O ambiente Python (versão 3.11) é configurado.
4.  **Instalação:** As dependências do projeto (listadas no `requirements.txt`, como `pandas` e `scikit-learn`) são instaladas.
5.  **Execução do Treino:** O script `train.py` é executado. Este script:
    * Carrega os dados do `data/sample.csv`.
    * Treina um modelo de Regressão Logística.
    * Gera um relatório de classificação (`report.txt`) com métricas de acurácia, precisão, recall e F1-score.
6.  **Upload do Artefato:** O arquivo `report.txt` gerado é salvo como um artefato no GitHub chamado `classification-report`, que pode ser baixado para análise.