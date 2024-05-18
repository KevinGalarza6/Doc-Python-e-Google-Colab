# Sklearn

O Scikit-learn é uma biblioteca projetada para aprendizado de máquina e mineração de dados, oferecendo ferramentas para modelagem preditiva e análise estatística.

```sh
import sklearn
`````
Utilização da biblioteca:
A Aprendizagem de máquina é dividida em duas categorias principais(Aprendizado Supervisionado e Não-Supervisionado) com cinco subcategorias totais:
- Classificação.
- Regressão
- Clusterização
- Associação (sklearn não tem algoritmos de associação, apenas a biblioteca mlxtend)
- Sumarização

## Aprendizado Supervisionado
 Classificação: ferramentas para classificação de dados, como SVM, KNN, árvores de decisão, etc...
```sh
# Exemplo com KNN
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier

# Carregar o conjunto de dados Iris
iris = load_iris()
X = iris.data
y = iris.target

# Dividir o conjunto de dados em conjuntos de treino e teste
X_treino, X_teste, y_treino, y_teste = train_test_split(X, y, test_size=0.3, random_state=42)

# Treinar o modelo
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_treino, y_treino)

# Previsões
previsoes = knn.predict(X_teste)
````
Regressão: ferramentas para regressão, como regressão linear, regressão de Ridge, regressão de Lasso, etc...
```sh
# Exemplo com Regressão Linear
from sklearn.linear_model import LinearRegression

# Dados de exemplo
X = [[1], [2], [3], [4], [5]]
y = [1.2, 2.3, 3.1, 3.9, 5.1]

# Treinar o modelo
modelo = LinearRegression()
modelo.fit(X, y)

# Previsões
previsoes = modelo.predict([[6]])
`````

## Aprendizado Não-Supervisionado
Clusterização: ferramentas para clusterização de dados, como K-means, DBSCAN, e clustering hierárquico.
```sh
# Exemplo com K-Means
from sklearn.cluster import KMeans
import numpy as np

# Dados de exemplo
X = np.array([[1, 2], [1, 4], [1, 0],
              [10, 2], [10, 4], [10, 0]])

# Treinar o modelo
kmeans = KMeans(n_clusters=2, random_state=0)
kmeans.fit(X)

# Previsões
rotulos = kmeans.predict([[0, 0], [12, 3]])
centroides = kmeans.cluster_centers_
`````
Sumarização: Ferramentas para reduzir a dimensionalidade dos dados e extrair características importantes, como PCA e SVD.
```sh
# Exemplo com PCA
from sklearn.decomposition import PCA
import numpy as np

# Dados de exemplo
X = np.array([[2.5, 2.4], [0.5, 0.7], [2.2, 2.9],
              [1.9, 2.2], [3.1, 3.0], [2.3, 2.7],
              [2, 1.6], [1, 1.1], [1.5, 1.6], [1.1, 0.9]])

# Treinar o modelo
pca = PCA(n_components=1)
componentes_principais = pca.fit_transform(X)

# Resultados
variancia_explicada = pca.explained_variance_ratio_
`````

## Pré-processamento de Dados
#### Normalização e Padronização
A normalização e padronização ajustam os valores dos dados para ficarem em uma escala comum, o que é importante para muitos algoritmos de machine learning.
```sh
from sklearn.preprocessing import StandardScaler, MinMaxScaler
import numpy as np

dados = np.array([[1, 2], [2, 3], [3, 4], [4, 5]])

# Padronização (z-score)
padronizador = StandardScaler()
dadosPadronizados = padronizador.fit_transform(dados)
print(dadosPadronizados)

# Normalização (min-max)
normalizador = MinMaxScaler()
dadosNormalizados = normalizador.fit_transform(dados)
print(dadosNormalizados)
`````
#### Transformação de Recursos
A transformação de recursos modifica os dados para melhor adaptá-los aos algoritmos de machine learning, como a criação de novas features polinomiais ou codificação one-hot.
```sh
from sklearn.preprocessing import PolynomialFeatures, OneHotEncoder
import numpy as np

# Dados para transformação polinomial
dados = np.array([[2, 3], [3, 4], [4, 5]])

# Transformação polinomial de grau 2
transformadorPolinomial = PolynomialFeatures(degree=2)
dadosPolinomiais = transformadorPolinomial.fit_transform(dados)
print(dadosPolinomiais)

# Dados para one-hot encoding
categorias = np.array([['A'], ['B'], ['C'], ['A']])

# One-hot encoding
codificador = OneHotEncoder(sparse=False)
categoriasCodificadas = codificador.fit_transform(categorias)
print(categoriasCodificadas)
`````
## Seleção de Modelo
#### Validação Cruzada
A validação cruzada é uma técnica para avaliar a performance de um modelo, dividindo os dados em múltiplas partes e treinando o modelo em diferentes subconjuntos dos dados.
```sh
from sklearn.model_selection import KFold, cross_val_score
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import load_iris

# Carregar dados
iris = load_iris()
dados, rotulos = iris.data, iris.target

# Validação cruzada com KFold
kf = KFold(n_splits=5)
modelo = LogisticRegression(max_iter=200)
pontuacoes = cross_val_score(modelo, dados, rotulos, cv=kf)
print(pontuacoes)
`````
#### Busca de Hiperparâmetros
A busca de hiperparâmetros ajusta os parâmetros de um modelo para encontrar a melhor combinação usando técnicas como a busca em grade.
```sh
from sklearn.model_selection import GridSearchCV
from sklearn.svm import SVC
from sklearn.datasets import load_iris

# Carregar dados
iris = load_iris()
dados, rotulos = iris.data, iris.target

# Definir parâmetros para a busca
parametros = {'C': [0.1, 1, 10], 'kernel': ['linear', 'rbf']}

# Realizar a busca
modelo = SVC()
buscaEmGrade = GridSearchCV(modelo, parametros, cv=5)
buscaEmGrade.fit(dados, rotulos)
print(buscaEmGrade.best_params_)
`````
## Conjunto de Dados
#### Datasets Incorporados
A biblioteca inclui vários conjuntos de dados reais e sintéticos para testar e experimentar diferentes algoritmos de aprendizagem de máquina.
```sh
from sklearn.datasets import load_iris, load_digits

# Carregar conjunto de dados Iris
iris = load_iris()
print(iris.data.shape)

# Carregar conjunto de dados Digits
digitos = load_digits()
print(digitos.data.shape)
`````

#### Geradores de Dados Sintéticos
Os geradores de dados sintéticos criam conjuntos de dados artificiais que podem ser usados para testar algoritmos de machine learning.
```sh
from sklearn.datasets import make_classification, make_regression

# Gerar dados de classificação
dadosClassificacao, rotulosClassificacao = make_classification(n_samples=100, n_features=5)
print(dadosClassificacao.shape, rotulosClassificacao.shape)

# Gerar dados de regressão
dadosRegressao, rotulosRegressao = make_regression(n_samples=100, n_features=5)
print(dadosRegressao.shape, rotulosRegressao.shape)
`````
## Pipelines
Os pipelines permitem a combinação de vários passos de pré-processamento e modelagem em uma única sequência, facilitando a manutenção e a replicabilidade dos experimentos.
```sh
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Carregar dados
iris = load_iris()
dados, rotulos = iris.data, iris.target

# Dividir os dados em treino e teste
dadosTreino, dadosTeste, rotulosTreino, rotulosTeste = train_test_split(dados, rotulos, test_size=0.2, random_state=42)

# Criar um pipeline
pipeline = Pipeline([
    ('padronizador', StandardScaler()),
    ('svm', SVC())
])

# Treinar o pipeline
pipeline.fit(dadosTreino, rotulosTreino)

# Fazer previsões
previsoes = pipeline.predict(dadosTeste)
print(previsoes)
`````
## Métricas de Avaliação
- Classificação: Acurácia, Precisão, Recall e F1-Score.
- Regressão: Erro Quadrático Médio e Coeficiente de Determinação.
- Clusterização: Coeficiente de Silhueta e Índice de Davies-Bouldin
- Sumarização: Inércia e Variação Explicada

## Análise de Modelos 
#### Validação e Ajuste de Modelos
A validação e ajuste de modelos permitem verificar a performance de um modelo para diferentes valores de hiperparâmetros, ajudando a evitar overfitting.
```sh
from sklearn.model_selection import validation_curve
from sklearn.datasets import load_iris
from sklearn.svm import SVC
import numpy as np

# Carregar dados
iris = load_iris()
dados, rotulos = iris.data, iris.target

# Validar curva de complexidade do modelo
parametrosIntervalo = np.logspace(-6, -1, 5)
pontuacoesTreino, pontuacoesTeste = validation_curve(SVC(), dados, rotulos, param_name="gamma", param_range=parametrosIntervalo, cv=5)

print(pontuacoesTreino)
print(pontuacoesTeste)
`````
## Curvas de Aprendizado e Validação
As curvas de aprendizado ajudam a entender a performance de um modelo com diferentes tamanhos de conjunto de treinamento, indicando se o modelo sofre de high bias ou high variance.
```sh
from sklearn.model_selection import learning_curve
from sklearn.datasets import load_iris
from sklearn.ensemble import RandomForestClassifier
import matplotlib.pyplot as plt
import numpy as np
`````