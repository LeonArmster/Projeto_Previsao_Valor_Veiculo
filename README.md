
# Projeto de Machine Learning – Previsão de Preço de Veículos

## 1. Sumário Executivo

Este projeto tem como objetivo desenvolver um modelo preditivo de Machine Learning capaz de estimar o **preço de venda de veículos usados**, com base em características técnicas e histórico do veículo.

A solução foi construída seguindo boas práticas de ciência de dados, contemplando:
- Análise exploratória
- Tratamento e preparação dos dados
- Comparação de múltiplos algoritmos
- Avaliação objetiva de performance
- Persistência do modelo para uso em produção

O projeto pode ser utilizado como base para **precificação automática**, **simulações comerciais** e **apoio à tomada de decisão** em contextos corporativos.

---

## 2. Objetivo de Negócio

Automatizar a estimativa do valor de venda de veículos, reduzindo subjetividade, aumentando a precisão da precificação e permitindo escalabilidade operacional em ambientes como:

- Concessionárias
- Marketplaces automotivos
- Plataformas de compra e venda de veículos
- Análises internas de portfólio

---

## 3. Fonte de Dados

- Origem: Kaggle  
- Dataset: Car Data  
- Link: https://www.kaggle.com/datasets/athirags/car-data  

---

## 4. Descrição das Variáveis

| Variável | Descrição |
|--------|----------|
| Car_Name | Nome do veículo |
| Year | Ano de fabricação |
| Present_Price | Preço atual estimado |
| Kms_Driven | Quilometragem |
| Fuel_Type | Tipo de combustível |
| Seller_Type | Tipo de vendedor |
| Transmission | Tipo de câmbio |
| Owner | Quantidade de donos anteriores |
| Selling_Price | **Preço de venda (variável alvo)** |

---

## 5. Análise Exploratória (EDA)

Foram realizadas análises estruturais e estatísticas para:
- Verificar consistência dos dados
- Avaliar distribuição das variáveis
- Identificar possíveis outliers
- Avaliar cardinalidade e balanceamento das categorias

### Decisões tomadas:
- Não foram identificados valores nulos
- Registros com `Selling_Price >= 33` foram removidos por representarem outliers extremos

---

## 6. Pré-processamento dos Dados

### 6.1 Engenharia de Atributos
- Criação da variável `Age`:
  - `Age = Ano atual - Year`

### 6.2 Codificação de Variáveis Categóricas
- Fuel_Type: Petrol (0), Diesel (1), CNG (2)
- Seller_Type: Dealer (0), Individual (1)
- Transmission: Manual (0), Automatic (1)

### 6.3 Remoção de Colunas
- `Car_Name` foi removida por não agregar valor preditivo direto

---

## 7. Modelagem

Foram treinados e avaliados os seguintes algoritmos de regressão:

- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor
- XGBoost Regressor

Os dados foram avaliados em três cenários:
- Sem normalização
- Normalização (MinMaxScaler)
- Padronização (StandardScaler)

---

## 8. Avaliação de Performance

### Métrica utilizada:
- **R² Score**

Modelos baseados em árvores apresentaram melhor desempenho geral e menor sensibilidade à normalização.

---

## 9. Modelo Selecionado

**GradientBoostingRegressor**

Critérios:
- Melhor desempenho médio
- Boa capacidade de generalização
- Robustez frente a outliers
- Menor complexidade operacional

---

## 10. Persistência do Modelo

O modelo final foi salvo para utilização futura em ambientes produtivos:

```python
joblib.dump(modelo, 'modelo_treinado_veiculos.pk')
```

---

## 11. Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Joblib


---

## 12. Próximos Passos

- Implementação de pipeline com `sklearn.Pipeline`
- Validação cruzada
- Tuning de hiperparâmetros
- Criação de API para consumo do modelo
- Monitoramento de performance em produção

---

## 13. Observações Finais

Este projeto segue padrões corporativos de documentação e organização, sendo adequado para:
- Portfólio profissional
- Avaliação técnica
- Base para projetos produtivos

