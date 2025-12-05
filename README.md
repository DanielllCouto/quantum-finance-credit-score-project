# Quantum Finance – Plataforma de Machine Learning para Score de Crédito

## Sobre o Projeto

O **Quantum Finance** é uma plataforma completa de Machine Learning que demonstra o ciclo de vida de uma solução de inteligência artificial em produção, desde a concepção e tratamento dos dados até a entrega de uma aplicação funcional para o usuário final. O projeto abrange **Engenharia de Dados, Ciência de Dados, Engenharia de Machine Learning e MLOps**, integrando todas as camadas necessárias para que um modelo de ML gere valor de forma contínua, confiável e escalável.

A solução foi estruturada em três repositórios especializados, cada um representando uma responsabilidade bem definida no pipeline de Machine Learning:

- **Modelagem e Experimentação:** Análise exploratória de dados, pré-processamento avançado, engenharia de features, treinamento e otimização de modelos.
- **API de Inferência:** Serviço de predição em tempo real, construído com arquitetura serverless na AWS, garantindo escalabilidade e observabilidade em produção.
- **Frontend:** Aplicação web interativa que permite aos usuários consumir a API e obter previsões de score de crédito de forma intuitiva.

## Stack Tecnológico

### Engenharia e Ciência de Dados

O pipeline de dados utiliza ferramentas consolidadas para garantir qualidade, reprodutibilidade e rastreabilidade:

- **Python 3.10+** como linguagem principal
- **Pandas e NumPy** para manipulação e análise de dados
- **Scikit-learn** para pré-processamento e modelos base
- **Matplotlib e Seaborn** para visualização exploratória

### Modelagem de Machine Learning

A experimentação e otimização de modelos foi realizada com algoritmos de alta performance:

- **LightGBM, CatBoost e XGBoost** para modelos de Gradient Boosting
- **GridSearchCV e RandomizedSearchCV** para otimização de hiperparâmetros
- **StackingClassifier** para construção de ensembles
- **Validação cruzada externa** para garantir generalização

### MLOps e Automação

A governança e rastreabilidade do projeto foram implementadas através de um ecossistema integrado de ferramentas:

- **MLflow + DagsHub** para rastreamento de experimentos e versionamento de modelos
- **DVC** para versionamento de dados em S3
- **GitHub Actions** para automação de CI/CD, testes e orquestração de deploys
- **Pytest** para testes unitários e de integração

### Infraestrutura e Backend

A API foi implementada em uma arquitetura serverless na AWS:

- **AWS Lambda** para computação serverless
- **Amazon API Gateway** para gerenciamento de requisições e autenticação
- **Amazon ECR** para containerização com Docker
- **Amazon S3** para persistência de dados e auditoria
- **Amazon CloudWatch** para monitoramento e observabilidade

### Frontend

O frontend foi desenvolvido com foco em experiência do usuário e integração com a API:

- **Streamlit** para construção rápida de interfaces interativas
- **Streamlit Cloud** para deploy contínuo
- **Requests** para comunicação com a API

## Repositórios do Projeto

A solução está organizada em três repositórios, cada um com responsabilidades bem definidas:

| Repositório | Descrição | Link |
| :--- | :--- | :--- |
| **Modelagem e Experimentação** | Contém o pipeline completo de dados, notebooks de experimentação, treinamento de modelos e testes. Implementa pré-processamento avançado, engenharia de features, otimização de hiperparâmetros e construção de ensembles. | [quantum-finance-credit-score](https://github.com/DanielllCouto/quantum-finance-credit-score) |
| **API de Inferência** | Código da API RESTful, infraestrutura como código, pipeline de CI/CD e testes de integração. Responsável por servir o modelo em produção com alta disponibilidade e observabilidade. | [quantum-finance-api-credit-score](https://github.com/DanielllCouto/quantum-finance-api-credit-score) |
| **Frontend com Streamlit** | Aplicação web interativa que consome a API de inferência. Implementa normalização de dados, montagem de payloads e exibição de resultados de forma visual. | [quantum-finance-app-credit-score](https://github.com/DanielllCouto/quantum-finance-app-credit-score) |

## Principais Características Técnicas

### Pré-processamento e Engenharia de Dados

O pipeline de dados implementa estratégias avançadas de tratamento e transformação:

- **Imputação inteligente** de valores ausentes utilizando clustering KMeans, baseada em variáveis correlacionadas e conhecimento de negócio
- **Tratamento de inconsistências** e mitigação de outliers com base em análises estatísticas
- **Preservação de informação** através de flags de missing quando o padrão de ausência é informativo
- **Mitigação de data leakage** com identificação preventiva de variáveis com risco de vazamento
- **Engenharia de features** com normalização e padronização para otimizar representação nos modelos

### Experimentação e Otimização de Modelos

A abordagem de modelagem combina exploração sistemática com otimização rigorosa:

- **Avaliação de múltiplos algoritmos** (Random Forest, XGBoost, LightGBM, CatBoost) para identificar o melhor desempenho
- **Otimização de hiperparâmetros** com GridSearchCV e RandomizedSearchCV para maximizar performance
- **Construção de ensembles** utilizando Stacking para combinar a força de múltiplos preditores
- **Validação cruzada externa** para garantir que as métricas reflitam a capacidade de generalização real

### Métricas Alinhadas ao Negócio

A avaliação do modelo foi estruturada com foco no impacto de negócio:

- **Recall da classe 'Poor'** como métrica principal, priorizando a detecção de clientes de alto risco
- **Recall Macro, F1-Score e Matriz de Confusão** para garantir desempenho equilibrado
- **Modelo campeão:** Ensemble Stacking (LightGBM + CatBoost) com **Recall superior a 0.83** na classe 'Poor'

### CI/CD e Monitoramento

A automação e rastreabilidade foram implementadas através de pipelines de CI/CD:

- **Testes automatizados** com Pytest para validar integridade do código e do modelo
- **Relatórios de métricas** gerados automaticamente comparando versões do modelo
- **Orquestração de deploys** que sincroniza o repositório de modelo com o repositório da API
- **Monitoramento contínuo** em produção com CloudWatch, rastreando performance e distribuição de previsões

## Fluxo End-to-End

O projeto demonstra um fluxo completo de Machine Learning em produção:

1. **Dados brutos** são versionados com DVC e armazenados em S3
2. **Pré-processamento e engenharia de features** são realizados em notebooks reprodutíveis
3. **Experimentos** são rastreados no MLflow com parâmetros, métricas e artefatos
4. **Modelo campeão** é registrado no MLflow Model Registry
5. **Testes automatizados** validam a integridade do modelo
6. **Deploy da API** é acionado automaticamente quando um novo modelo é registrado
7. **Frontend** consome a API e disponibiliza previsões para usuários finais

## Arquitetura da Solução

### Visão Geral da API

A arquitetura da API foi projetada para ser altamente escalável e resiliente, utilizando uma abordagem serverless na AWS. O fluxo de uma requisição passa por todos os componentes da infraestrutura, desde o cliente até a resposta da predição.

<img width="1412" height="1240" alt="Arquitetura" src="https://github.com/user-attachments/assets/fa87eb5e-812d-4b6b-b106-1dc9fe78698c" />

**Figura 1: Arquitetura da API**

### Fluxo de CI/CD e Orquestração

O fluxo de CI/CD foi desenhado para ser totalmente automatizado, garantindo a integração e entrega contínua de novas versões do modelo, da API e do frontend. O diagrama abaixo detalha as etapas de cada pipeline, desde o commit do código até o deploy em produção.

<img width="1655" height="1087" alt="CI CD Blue print" src="https://github.com/user-attachments/assets/31ed9d1e-b6fc-46a6-966b-d2b5a76f7960" />


**Figura 2: Fluxo de CI/CD**


## Resultados Alcançados

- ✅ **Dataset otimizado:** Processamento resultou em dataset balanceado, livre de data leakage e pronto para modelagem
- ✅ **Modelo de alta performance:** Ensemble Stacking alcançou Recall superior a 0.83 na classe 'Poor'
- ✅ **Pipeline reprodutível:** Solução totalmente documentada desde ingestão de dados até registro do modelo
- ✅ **Automação completa:** CI/CD integrado sincronizando modelo, API e frontend
- ✅ **Observabilidade em produção:** Monitoramento contínuo com CloudWatch e auditoria de predições em S3

## Conecte-se

👨‍💻 **Daniel Estrella Couto**

- [LinkedIn](https://www.linkedin.com/in/daniel-estrella-couto)
- [GitHub](https://github.com/estrellacouto05)
