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
