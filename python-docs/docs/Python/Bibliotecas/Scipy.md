# SciPy

SciPy é uma biblioteca fundamental para a computação científica, construída sobre a base sólida do NumPy, oferecendo uma amplas funcionalidades para resolver problemas matemáticos, científicos e de engenharia. Enquanto NumPy é excelente para manipulação e operações em arrays multidimensionais, SciPy expande essas capacidades com funções adicionais para álgebra linear, otimização, integração, interpolação, análise de Fourier, processamento de sinais, estatísticas e muito mais.

```sh
import numpy as np
# Recomenda-se importar apenas os submódulos necessários para economizar memória e acelerar o script.
from scipy import stats, linalg, optimize
`````
Utilização da biblioteca:
- É fundamental ter conhecimento da biblioteca numpy, suas funções e resoluções.

Por que usar a biblioteca SciPy ao invés da NumPy?
- Funcionalidades avançadas de álgebra linear, enquanto a NumPy fornece funções mais básicas.
- Mais robusta e abrangente se comparada com a NumPy, que é mais rápida para operações simples.
- Contém otimizações para certos cálculos que podem serem lentos ou inexistentes na NumPy.

## Distribuição Estatísticas
Assim como o NumPy, o SciPy oferece suporte para várias distribuições estatísticas, mas com funcionalidades extras.
```sh
# Distribuição Normal
# Criação de uma variável aleatória normalmente distribuída
rvNormal = stats.norm(loc=0, scale=1)  # Média = 0, Desvio padrão = 1
aleatoriosNormal = rvNormal.rvs(size=100)  # Gera 100 números aleatórios
mediaNormal = rvNormal.mean()  # Média da distribuição
varianciaNormal = rvNormal.var()  # Variância da distribuição
`````

## Testes Estatísticos
A biblioteca ornece uma amplos testes estatísticos para diferentes propósitos.
```sh
# Teste t de Student
# Verifica se há diferença significativa entre as médias de duas amostras independentes
amostra1 = np.random.normal(loc=0, scale=1, size=100)
amostra2 = np.random.normal(loc=0.5, scale=1, size=100)
tStatistic, pValue = stats.ttest_ind(amostra1, amostra2)

# Teste qui-quadrado
# Testa a independência entre variáveis categóricas em uma tabela de contingência
tabelaContingencia = np.array([[10, 20, 30], [6,  9,  17]])
chi2Statistic, pValue, degreesOfFreedom, expected = stats.chi2_contingency(tabelaContingencia)
`````

## Álgebra Linear Avançada
```sh
# Decomposição de Valores Singulares (SVD)
matriz = np.random.random((3, 3))
U, S, V = linalg.svd(matriz)

# Autovalores e Autovetores
autovalores, autovetores = linalg.eig(matriz)

# Resolução de Equações Lineares Esparsas
matrizEsparsa = np.array([[1, 0, 0], [0, 0, 2], [0, 0, 0]])
b = np.array([1, 0, -1])
x = linalg.spsolve(matrizEsparsa, b)
`````
## Otimização e Ajuste de Curvas
Opções para otimização numérica e ajuste de curvas.
```sh
# Otimização de Funções
def func(x):
    return x**2 + 10*np.sin(x)

otimizacao = optimize.minimize(func, x0=0)

# Ajuste de Curvas
x = np.linspace(0, 10, 100)
y = func(x) + np.random.normal(size=x.size)
parametros, covariancia = optimize.curve_fit(func, x, y)
`````