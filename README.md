# MVP — Previsão de Churn em Telecomunicações

MVP individual da disciplina de Machine Learning & Analytics: um projeto
completo de classificação binária para prever cancelamento (*churn*) de
clientes de uma operadora de telecomunicações.

## Contexto e problema

Empresas de telecom perdem receita quando clientes cancelam seus serviços.
Este projeto constrói um modelo de **classificação binária supervisionada**
que estima a probabilidade de um cliente cancelar (`Churn = Yes`), a partir
de dados cadastrais, contratuais e de consumo, para apoiar ações proativas
de retenção.

Cinco hipóteses de negócio guiaram a análise exploratória (ver seção 1 e 4
do notebook):

1. Contrato mensal aumenta a chance de churn.
2. Clientes com menor tempo de casa (`tenure`) cancelam mais.
3. Clientes com internet via fibra óptica cancelam mais.
4. Clientes que pagam por cheque eletrônico cancelam mais.
5. Clientes com mensalidade mais alta cancelam mais.

Todas as cinco hipóteses foram **confirmadas** na análise exploratória, com
intensidades diferentes — os detalhes e evidências (gráficos, tabelas e
recapitulação final) estão no notebook.

## Dataset

- **Fonte:** [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
  (IBM Sample Data Sets), 7.043 clientes e 21 atributos.
- **Arquivo:** `telco_churn.csv`, neste repositório.
- **Carregamento:** o notebook lê o dataset diretamente via URL *raw* deste
  repositório — não é necessário baixar nada manualmente.

## Como executar

1. Abra o notebook `MVP_Churn_Analysis.ipynb` no [Google Colab](https://colab.research.google.com/).
2. Execute todas as células em ordem (**Ambiente de execução → Executar tudo**).
3. Não é necessário login, chave de API ou upload manual — o CSV é
   carregado automaticamente via URL pública deste repositório.

## Estrutura do notebook

1. Apresentação do problema e hipóteses
2. Configuração do ambiente (imports e seeds)
3. Apresentação dos dados
4. Análise exploratória (uma seção por hipótese, H1 a H5, + análise de skew)
5. Preparação dos dados (tratamento de nulos, encoding, log + padronização)
6. Divisão treino/teste
7. Modelagem (baseline + Regressão Logística + Random Forest + Gradient Boosting)
8. Otimização de hiperparâmetros (GridSearchCV + validação cruzada)
9. Avaliação dos resultados (métricas, matriz de confusão, curvas ROC)
10. Recapitulação das hipóteses com evidências
11. Conclusão
12. Checklist do MVP respondido

## Principais resultados

- Todas as hipóteses de negócio (H1–H5) foram confirmadas na análise
  exploratória, com `Contract` e `tenure` como os atributos de maior poder
  discriminativo.
- O melhor modelo foi o **Gradient Boosting com hiperparâmetros
  otimizados** (via `GridSearchCV`, validação cruzada de 5 folds),
  avaliado por F1-score e AUC-ROC em dados de teste não vistos.
- Métricas, matriz de confusão e comparação completa entre modelos estão
  na seção 9 do notebook.

## Limitações e próximos passos

Ver seção 11 (Conclusão) do notebook para a discussão completa de
limitações (ausência de dimensão temporal, ausência de dados de
atendimento/satisfação) e possíveis melhorias futuras (balanceamento de
classes, busca de hiperparâmetros mais ampla, novas fontes de dados).

## Autor

Larice Freitas Mourão
