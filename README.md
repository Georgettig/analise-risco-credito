# Análise e Previsão de Risco de Crédito

Projeto de análise exploratória de dados e aplicação de técnicas de Machine Learning para identificação de clientes com maior risco de inadimplência.

## Sobre o projeto

A concessão de crédito envolve riscos financeiros, especialmente quando existe a possibilidade de inadimplência por parte dos clientes.

Nesse contexto, a análise de dados e o Machine Learning podem auxiliar na identificação de padrões associados ao comportamento dos consumidores, contribuindo para uma avaliação mais criteriosa do risco de crédito.

Este projeto tem como objetivo analisar uma base de dados de clientes, identificar características relacionadas à inadimplência e desenvolver modelos de Machine Learning capazes de prever a probabilidade de um cliente não cumprir suas obrigações financeiras.

## Problema de negócio

**É possível identificar clientes com maior risco de inadimplência utilizando informações como renda, idade e valor do empréstimo?**

Para responder a essa pergunta, foram realizadas análises exploratórias, preparação dos dados, desenvolvimento de modelos de classificação e avaliação dos resultados.

## Objetivos

- Explorar e compreender as características dos clientes presentes na base de dados.
- Identificar padrões associados à inadimplência.
- Analisar a relação entre renda, idade, valor do empréstimo e inadimplência.
- Desenvolver e comparar diferentes modelos de Machine Learning.
- Avaliar o desempenho dos modelos e identificar aquele com melhores resultados.

## Base de dados

A base utilizada contém 2.000 registros de clientes e cinco variáveis:

| Variável | Descrição |
|---|---|
| `clientid` | Identificador do cliente |
| `income` | Renda do cliente |
| `age` | Idade do cliente |
| `loan` | Valor do empréstimo |
| `default` | Indicador de inadimplência (0 = Não / 1 = Sim) |

A variável `default` foi definida como variável-alvo dos modelos preditivos.

## Etapas do projeto

### 1. Exploração e análise dos dados

Inicialmente, foi realizada uma análise exploratória para compreender a estrutura da base e identificar possíveis inconsistências.

Foram avaliados:
- Dimensões e tipos das variáveis.
- Estatísticas descritivas.
- Valores ausentes e registros duplicados.
- Distribuição de clientes inadimplentes e não inadimplentes.

Também foram desenvolvidas visualizações para investigar a relação entre as características dos clientes e a ocorrência de inadimplência.

### 2. Preparação e tratamento dos dados

Foram realizadas as seguintes etapas:
- Identificação e tratamento de idades negativas.
- Separação das variáveis preditoras e da variável-alvo.
- Divisão dos dados em conjuntos de treinamento (80%) e teste (20%).
- Preenchimento de valores ausentes utilizando a mediana.
- Padronização das variáveis numéricas.

O pré-processamento foi implementado utilizando pipelines, garantindo que os parâmetros de transformação fossem ajustados somente com os dados de treinamento.

### 3. Desenvolvimento dos modelos

Foram desenvolvidos e comparados três algoritmos de classificação:

- **Regressão Logística:** modelo utilizado como abordagem estatística de classificação.
- **Árvore de Decisão:** algoritmo capaz de identificar padrões por meio de regras e divisões dos dados.
- **Random Forest:** algoritmo que combina múltiplas árvores de decisão para realizar previsões.

A comparação foi realizada por meio de validação cruzada estratificada com cinco divisões (*Stratified K-Fold Cross Validation*).

### 4. Avaliação dos modelos

Para comparar os algoritmos, foram utilizadas as seguintes métricas:

- **Acurácia:** proporção de previsões corretas.
- **Precision:** proporção de clientes classificados como inadimplentes que realmente eram inadimplentes.
- **Recall:** proporção de clientes inadimplentes corretamente identificados.
- **F1-score:** média harmônica entre Precision e Recall.
- **ROC-AUC:** capacidade de discriminação entre as classes considerando diferentes limiares de classificação.

## Resultados

### Comparação durante a validação cruzada

A Árvore de Decisão apresentou o melhor F1-score entre os três modelos avaliados.

| Modelo | Acurácia | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Árvore de Decisão | 98,81% | 98,13% | 93,35% | 95,65% | 96,53% |
| Random Forest | 98,13% | 96,26% | 90,25% | 93,06% | 99,80% |
| Regressão Logística | 95,00% | 85,28% | 78,71% | 81,34% | 98,39% |

### Avaliação final — Árvore de Decisão

Após a seleção, o modelo foi treinado utilizando o conjunto de treinamento e avaliado com os dados de teste, que não participaram do treinamento.

Resultados obtidos:

| Métrica | Resultado |
|---|---:|
| Acurácia | 98,00% |
| Precision | 91,53% |
| Recall | 94,74% |
| F1-score | 93,10% |

O modelo identificou corretamente 54 dos 57 clientes inadimplentes presentes no conjunto de teste, deixando de identificar apenas três casos.

Esse resultado demonstra uma boa capacidade de identificação de clientes inadimplentes dentro da base analisada.

## Conclusão

Os resultados indicam que informações como idade e valor do empréstimo podem contribuir para a identificação de clientes com maior risco de inadimplência.

Entre os algoritmos avaliados, a Árvore de Decisão apresentou o melhor desempenho geral durante a validação cruzada, alcançando um F1-score de 95,65%.

Na avaliação final, utilizando os dados de teste, o modelo obteve 98% de acurácia e 94,74% de Recall.

Portanto, o projeto demonstra o potencial da aplicação de técnicas de Machine Learning como ferramentas de apoio à análise de risco de crédito.

## Limitações e oportunidades de melhoria

Apesar dos resultados positivos, algumas limitações devem ser consideradas:

- A base possui uma quantidade limitada de registros e variáveis.
- Os resultados obtidos não garantem o mesmo desempenho em bases de dados reais ou em outros contextos.
- Variáveis adicionais, como histórico de pagamentos, comprometimento de renda e histórico financeiro, poderiam enriquecer a análise.
- A avaliação com novas bases de dados seria importante para verificar a capacidade de generalização do modelo.

Como oportunidades de evolução, podem ser explorados ajustes de hiperparâmetros, comparação com outros algoritmos e técnicas adicionais de interpretação dos modelos.

## Tecnologias e bibliotecas

- **Python**
- **Pandas:** manipulação e análise de dados.
- **NumPy:** operações numéricas.
- **Matplotlib:** visualização de dados.
- **Seaborn:** construção de gráficos estatísticos.
- **Scikit-learn:** pré-processamento, desenvolvimento e avaliação dos modelos.
- **Jupyter Notebook:** desenvolvimento e documentação do projeto.

## Como executar o projeto

1. Clone este repositório:

   ```bash
   git clone https://github.com/SEU-USUARIO/analise-risco-credito.git
   ```

2. Acesse a pasta do projeto:

   ```bash
   cd analise-risco-credito
   ```

3. Instale as dependências:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

4. Inicie o Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Abra o arquivo `analise_risco_credito.ipynb` e execute as células.

**Importante:** mantenha o arquivo `credit_data.csv` na mesma pasta do notebook para que o carregamento dos dados funcione corretamente.

---

**Projeto desenvolvido para fins de estudo e portfólio, com foco em análise de dados e Machine Learning aplicado à previsão de risco de crédito.**
