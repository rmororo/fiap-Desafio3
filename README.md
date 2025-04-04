<div align="center">
    <img src="https://www.fiap.com.br/wp-content/themes/fiap2016/images/sharing/fiap.png" alt="Logo FIAP" width="300"/>
</div>

# 💳 Detecção de Fraudes em Cartões de Crédito - FIAP Challenge 3

[![Python Version](https://img.shields.io/badge/python-3.11-blue.svg)](https://python.org)  
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)  
[![Status](https://img.shields.io/badge/status-concluído-brightgreen)](/)  
[![Power BI](https://img.shields.io/badge/export-PowerBI-yellow)](/)  
[![AWS](https://img.shields.io/badge/cloud-AWS-orange)](/)  
[![PostgreSQL](https://img.shields.io/badge/database-PostgreSQL-blue)](https://www.postgresql.org/)  
[![SMOTE](https://img.shields.io/badge/class%20balance-SMOTE-green)](/)  

---

## 📚 Sumário

- [🎯 Objetivo](#-objetivo)  
- [🛠 Tecnologias Utilizadas](#-tecnologias-utilizadas)  
- [📁 Estrutura do Projeto](#-estrutura-do-projeto)  
- [📦 Fonte dos Dados](#-fonte-dos-dados)  
- [⚙️ Como Funciona](#️-como-funciona)  
- [💡 Decisões de Projeto](#-decisões-de-projeto)  
- [💻 Como Rodar Localmente](#-como-rodar-localmente)  
- [📊 Avaliação do Modelo](#-avaliação-do-modelo)  

---

## 🎯 Objetivo

Este projeto visa detectar automaticamente possíveis fraudes em transações com cartão de crédito com base em variáveis comportamentais, geográficas e temporais.

O projeto foi desenhado para:  
- Identificar padrões suspeitos  
- Reduzir falsos positivos  
- Ser facilmente integrado ao ambiente de produção  
- Gerar dados legíveis para análise no Power BI  

---

## 🛠 Tecnologias Utilizadas

- **Python 3.11**  
- **PostgreSQL (AWS RDS)**  
- Pandas / NumPy  
- Scikit-learn  
- Imbalanced-learn (SMOTE)  

---

## 📁 Estrutura do Projeto

```text
modelo_fraudes/
├── modelo_rf_final.pkl         # Modelo treinado
├── predict_fraudes.py          # Script de predição (pronto para produção)
├── conexao_aws.py              # Script de conexão com o banco RDS (opcional)
├── requirements.txt            # Dependências
├── dados/
│   └── novos_dados.csv         # Dados de entrada (caso local)
├── resultado_fraudes.csv       # Saída técnica
└── fraudes_powerbi.csv         # Saída legível para Power BI
```

---

## 📦 Fonte dos Dados

Utilizamos uma base pública e simulada de transações com cartões de crédito disponibilizada no Kaggle.

Para simular um ambiente de produção:  
- Os dados foram divididos entre `base_treino` e `base_teste`  
- Inseridos em um banco PostgreSQL hospedado na AWS RDS  
- A ingestão dos dados é feita diretamente via script Python utilizando a biblioteca `psycopg2`  

---

## ⚙️ Como Funciona

1. **Ingestão de dados** diretamente da AWS RDS (PostgreSQL)  
2. **Renomeação de colunas** para padronização  
3. **Criação de variáveis derivadas**:  
     - Distância cliente ↔ loja (via Geopy)  
     - Volume de transações por cartão/dia  
     - Hora e dia da semana da transação  
4. **Pré-processamento**:  
     - Label Encoding para variáveis categóricas  
     - Normalização para variáveis contínuas  
5. **Aplicação do modelo Random Forest**:  
     - Treinado com SMOTE para tratar o desbalanceamento  
     - Predição com threshold ajustado (0.6)  
6. **Exportação**:  
     - `resultado_fraudes.csv` com os resultados técnicos  
     - `fraudes_powerbi.csv` com dados amigáveis para visualização  

---

## 💡 Decisões de Projeto

- O **SMOTE** foi utilizado para rebalancear a base de treino, melhorando o recall do modelo  
- O **threshold padrão (0.5)** foi ajustado para 0.6 para reduzir falsos positivos sem perder muita sensibilidade  
- O **Random Forest** foi escolhido pela robustez e boa performance com poucos ajustes de hiperparâmetros  
- A **normalização** e o **label encoding** garantiram melhor performance e compatibilidade com o modelo  
- O pipeline completo foi pensado para ser executado em nuvem (AWS), desde a ingestão até a exportação  

---

## 💻 Como Rodar Localmente

```bash
# Clone o repositório
git clone https://github.com/anaplmiranda/modelo_fraudes.git
cd modelo_fraudes

# Crie o ambiente virtual
python -m venv venv
source venv/bin/activate       # Linux/macOS
venv\Scripts\activate          # Windows

# Instale as dependências
pip install -r requirements.txt

# Execute a predição
python predict_fraudes.py
```

---

## 📊 Avaliação do Modelo

Resultados na base de teste:  
- **Accuracy**: 96%  
- **Recall (fraudes detectadas)**: 81%  
- **Precisão**: 78%  
- **AUC-ROC**: 92%  

Com foco em recall, o modelo teve boa performance na detecção de fraudes reais, mesmo com um leve aumento nos falsos positivos.

---

## 👥 Equipe

Projeto desenvolvido por:  
- Ana Paula Miranda  
- Ariel Velardo  
- Eric Tamada  
- Ricardo Mororo  

Desenvolvido como parte do programa acadêmico da FIAP.  
