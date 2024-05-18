# Pandas
O Pandas é uma biblioteca em Python projetada para análise e manipulação de dados tabulares, oferecendo estruturas de dados, sendo as principais o DataFrame e Series.
Importando o Pandas em seu ambiente de desenvolvimento favorito, não importa qual seja.

```sh
import pandas as pd
`````
Utilização da biblioteca:
- Series: é uma estrutura unidimensional, tendo apenas um tipo de dado e armazenando dados mais simples e homogêneos. 
```sh
valores = [10, 25, 40, 75, 50]
serie = pd.Series(valores)
`````
- DataFrame: é a principal estrutura de dados do Pandas e organiza os dados em uma tabela com linhas e colunas, parecido com uma tabela de banco de dados. 
```sh
# Este DataFrame será usado para os próximos tópicos
vendas = {
    'Data': ['2024-05-14', '2024-05-15', '2024-05-16', '2024-05-17', '2024-05-18', '2024-05-19', '2024-05-20'],
    'Vendas': [150, 220, None, 175, 160, 180, 250],
    'Produto': ['A', 'B', 'C', 'D', None, 'F', 'G'],
    'Quantidade': [10, 150, 30, None, 50, 60, 70]
}
df = pd.DataFrame(vendas)
`````
## Operações estatísticas
Algumas funções básicas da biblioteca permitem operações estatísticas nas estruturas de dados, entre elas:
```sh
# Operações baseadas na coluna Vendas
media = df['Vendas'].mean()
mediana = df['Vendas'].median()
moda = df['Vendas'].mode()
desvioPadrao = df['Vendas'].std()
variancia = df['Vendas'].var()
contagem = df['Vendas'].count()
`````
## Limpeza e Preparação de Dados
Preencher valores ausentes, remover linhas e valores duplicados no DataFrame.
```sh
df['Vendas'].fillna(160, inplace=True) # Preenche com o valor 160
df.dropna(subset=['Produto', 'Quantidade'], inplace=True) # Remove linha com valor ausente nas colunas específicas
df.drop_duplicates(inplace=True) # Remove valores duplicados
`````
Converter a coluna 'Data' para um datetime.
```sh
df['Data'] = pd.to_datetime(df['Data'])
`````
Também podemos detectar, tratar e/ou excluir outliers. 
Neste exemplo, foi usada a técnica do IQR (Intervalo Interquartil) para a coluna 'Quantidade'.
```sh
# Calcular os quartis Q1 e Q3 para achar o IQR
Q1 = df['Quantidade'].quantile(0.25)
Q3 = df['Quantidade'].quantile(0.75)
IQR = Q3 - Q1

limiteInferior = Q1 - 1.5 * IQR
limiteSuperior = Q3 + 1.5 * IQR

# Remover outliers
df = df[(df['Quantidade'] >= limiteInferior) & (df['Quantidade'] <= limiteSuperior)]
`````
Com a limpeza e preparação realizada, o DataFrame ficou assim:
```sh
print(df)
# Output
        Data  Vendas Produto  Quantidade
0 2024-05-14   150.0       A        10.0
2 2024-05-16   160.0       C        30.0
5 2024-05-19   180.0       F        60.0
6 2024-05-20   250.0       G        70.0
`````
## Leitura e Escrita de Dados
A biblioteca tem recursos para ler e escrever em dezenas de formatos diferentes, entre eles: CSV, Excel, JSON, SQL, HTML, HDF5, Parquet e muitos outros formatos.
```sh
# Escrita do DataFrame do exemplo anterior para o arquivo 'vendas.xlsx', suportado pelo Excel
df.to_excel('vendas.xlsx', index=False)
# Leitura dos dados do arquivo 'vendas.xlsx'
dfExcel = pd.read_excel('vendas.xlsx')
`````
## Análise exploratória e visualização de dados
Mostrar as primeiras, últimas e determinadas linhas do DataFrame.
```sh
print(df.head(2)) # Primeiras duas linhas
print(df.tail(2)) # Últimas duas linhas
print(df.loc[[0, 5], ['Produto', 'Vendas']]) # Linha 0 e Linha 5 das colunas específicas
`````
Mostrar estatísticas descritivas das colunas numéricas.
```sh
print(df.describe().round(2)) # Valores com apenas duas casas após a vírgula

#Output
                      Data  Vendas  Quantidade
count                    4    4.00        4.00
mean   2024-05-17 06:00:00  185.00       42.50
min    2024-05-14 00:00:00  150.00       10.00
25%    2024-05-15 12:00:00  157.50       25.00
50%    2024-05-17 12:00:00  170.00       45.00
75%    2024-05-19 06:00:00  197.50       62.50
max    2024-05-20 00:00:00  250.00       70.00
std                    NaN   45.09       27.54
`````
Visão geral do DataFrame.
```sh
print(df.info()) 

#Output 
<class 'pandas.core.frame.DataFrame'>
Index: 4 entries, 0 to 6
Data columns (total 4 columns):
 #   Column      Non-Null Count  Dtype
---  ------      --------------  -----
 0   Data        4 non-null      datetime64[ns]
 1   Vendas      4 non-null      float64
 2   Produto     4 non-null      object
 3   Quantidade  4 non-null      float64
dtypes: datetime64[ns](1), float64(2), object(1)
memory usage: 160.0+ bytes
None
`````
Agregar dados de uma ou mais colunas.
```sh
print(df.agg({'Vendas': 'sum', 'Quantidade': 'sum'}))

#Output
Vendas        740.0
Quantidade    170.0
dtype: float64
`````
# Conclusão
Ao importar o Pandas em qualquer ambiente de desenvolvimento Python, você ganha acesso a uma ampla gama de funcionalidades para trabalhar com dados de forma rápida e eficaz.
Além das operações básicas de criação e manipulação de dados, como a criação de Series e DataFrames, o Pandas oferece uma variedade de funções para análise estatística, limpeza e preparação de dados, leitura e escrita de dados em diferentes formatos, e análise exploratória e visualização de dados.

Outras funções úteis do Pandas incluem:
- Filtragem de dados: para selecionar dados com base em condições específicas.
- Ordenação de dados: para ordenar os dados com base em uma ou mais colunas.
- Operações de combinação de dados: para combinar dados de diferentes fontes usando operações como merge e join.
- Transformação de dados: para aplicar funções de transformação aos dados, como mapeamento, aplicação de funções element-wise e aplicação de funções de agregação.