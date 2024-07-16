# Desvendando os Segredos do Petróleo: Uma Aventura com Python e Dados

## Introdução

Já pensou em como os dados podem transformar a maneira como empresas petrolíferas operam? Em um projeto recente, mergulhei fundo no fascinante mundo da análise de dados na indústria petrolífera. Vou compartilhar como utilizei Python, SQL e técnicas de modelagem para desvendar os segredos da produção de petróleo em plataformas offshore.

## O Desafio

Nosso objetivo era claro: transformar dados brutos em insights valiosos que pudessem otimizar as operações de produção de petróleo. Precisávamos extrair, integrar e analisar dados de diversas fontes para melhorar a eficiência e prever a produção futura.

## Extraindo e Integrando Dados

O primeiro passo foi mergulhar no mar de dados brutos. Utilizando Python, extraí informações de diferentes fontes, incluindo bancos de dados internos da Petrobras e APIs externas de parceiros. Com o SQL, integrei e limpei esses dados, garantindo que estivessem prontos para análise. 


import pandas as pd
import requests
import sqlalchemy

# Conexão com banco de dados
engine = sqlalchemy.create_engine('mysql+pymysql://user:password@host/db')

# Extração de dados do banco de dados interno
query = "SELECT * FROM producao_petroleo"
dados_internos = pd.read_sql(query, engine)

# Extração de dados de APIs externas
response = requests.get('https://api.externapetro.com/dados')
dados_externos = pd.DataFrame(response.json())

# Integração dos dados
dados = pd.concat([dados_internos, dados_externos], ignore_index=True)

# Limpeza dos dados
dados.drop_duplicates(inplace=True)
dados.fillna(method='ffill', inplace=True)


## Modelagem e Insights

Com o poder do Pandas e do Scikit-learn, aprofundei-me na modelagem de dados. Criei modelos de regressão para prever a produção futura com base nos dados históricos e identifiquei correlações entre variáveis para entender os fatores que impulsionam o desempenho das operações.


import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Preparação dos dados
X = dados[['temperatura', 'pressao', 'manutencao']]
y = dados['producao']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Criação do modelo de regressão linear
modelo = LinearRegression()
modelo.fit(X_train, y_train)

# Previsões
y_pred = modelo.predict(X_test)

# Avaliação do modelo
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')


## Resultados e Impacto

Os resultados foram impressionantes. Entreguei análises e insights valiosos para a equipe de engenharia e operações da empresa petrolífera. Essas informações foram usadas para otimizar a produção e melhorar a eficiência das operações nas plataformas offshore.

## Conclusão

Este projeto foi uma jornada emocionante através do mundo dos dados e da indústria petrolífera. Demonstrou como o uso eficaz de Python, SQL e técnicas de modelagem de dados pode agregar valor significativo às operações de uma empresa como a Petrobras. E, acima de tudo, mostrou o poder que os dados têm para transformar o mundo ao nosso redor.

### Pontos Importantes

1. **Introdução**: Fornece uma visão geral do projeto e sua importância.
2. **O Desafio**: Define claramente o problema que o projeto aborda.
3. **Extraindo e Integrando Dados**: Descreve como os dados foram coletados e preparados para análise.
4. **Modelagem e Insights**: Explica as técnicas de modelagem utilizadas e os insights obtidos.
5. **Resultados e Impacto**: Resume os benefícios e melhorias alcançadas com o projeto.
6. **Conclusão**: Reflete sobre a experiência e o valor do projeto.
