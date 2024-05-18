# Numpy

O NumPy é uma biblioteca utilizada na computação numérica que oferece suporte para realizar operações com arrays multidimensionais (ndarray) e usar funções matemáticas com operações rápidas para tratamento e limpeza de dados, geração de subconjuntos e filtragens, estatísticas descritivas, manipulação de dados relacionais, manipulações de dados em grupos, entre outros tipos de processamento. Além de ocupar menos memória, as operações são mais velozes e tem a facilidade de execução de cálculos numéricos.

```sh
import numpy as np
```

## Utilização da biblioteca

- Ndarray: é uma estrutura básica da biblioteca NumPy e pode ter qualquer número de dimensões.
- É fundamental conhecer os arrays em python, bem como sua criação e funcionamento.

```sh
# Criação do array e conversão para um ndarray bidimensional de floats
array = [[6, 7.5], [8, 15], [27, 1.5]]
meuArray = np.array(array)
```

Criar um ndarray com determinados valores.

```sh
arrayZeros = np.zeros((3,3), dtype=int) # Preenchido com zeros
arrayUns = np.ones((3,3), dtype=int) # Preenchido com uns
arrayUnsComo = np.ones_like(arrayUns) # # Preenchido com uns, com base nas dimensões do arrayUns
arrayVazio = np.empty((3,3), dtype=int) # Sem estar preenchido, mas terá lixo de memória
arrayCheioValorEspecifico = np.full((3, 3), 5) # Preenchido com valor específico, no caso 5
matriz_identidade = np.eye(3) # Elementos da diagonal principal são iguais a 1 e todos os outros são iguais a 0.
```

Inicialização dos ndarrays para os próximos tópicos

```sh
ndarray1 = np.array([[1, 2], [3, 4]])
ndarray2 = np.array([[5, 6], [7, 8]])
```

## Operações Básicas, Estatísticas e Comparativas

Criando operações básicas em ndarrays de forma simples.

```sh
ndarray3 = ndarray1 + ndarray2
subtracao = ndarray1 - ndarray2
multiplicacao = ndarray1 * ndarray2
divisao = ndarray1 / ndarray2
```

 Similar com a biblioteca pandas, podemos criar operações estatísticas, porém com ndarrays.

```sh
media = np.mean(ndarray3)
mediana = np.median(ndarray3)
desvioPadrao = np.std(ndarray3)
variancia = np.var(ndarray3)
minimo = np.min(ndarray3)
maximo = np.max(ndarray3)
```

Por fim, temos as operações comparativas.

```sh
# Retornam sempre valores booleanos
ndarray3Bool = ndarray3 <= 5 # Percorre o array testando cada número
comparacaoMaior = ndarray1 > ndarray2
```

## Geração de Números Aleatórios

Podemos criar arrays de números aleatórios com diferentes distribuições e características, como números uniformemente distribuídos entre dois valores específicos, números aleatórios de uma distribuição normal (gaussiana), entre outros.

```sh
aleatorio = np.random.rand(*ndarray3.shape) #  Aleatório entre 0 e 1 com a mesma forma do 'ndarray1'
numerosDeterminadosAleatorios = np.random.uniform(0, 10, size=(3, 3)) # Números entre 0 e 10
numerosAleatorios = np.random.randn(3, 3) # Números aleatórios
inteiroAleatorio = np.random.randint(5, 100, size=(3, 3)) # Números inteiros entre 5 e 100
amostraAleatoria = np.random.choice(ndarray3.flatten(), size=5)  # Amostra aleatória com 5 elementos do 'ndarray3'
```

## Manipulação Avançada e Álgebra Linear

### Indexação e Slicing

Indexação: acesso direto a elementos específicos de um array usando seus índices (posições). Existem vários tipos de indexação: básica, por lista de índices, com array de índices, com passo, e a avançada.
Slicing: extração de subarrays a partir de um array principal utilizando intervalos de índices.

```sh
# Indexação Básica
elemento = ndarray1[1, 1]  # Acessando o elemento na segunda linha, segunda coluna
elemento = ndarray3[2, 3]  # Acessando o elemento da terceira linha, terceira coluna

# Indexação Avançada
ultimaLinha = array_3x3[-1, :] # Acessando a última linha usando índices negativos
excetoPrimeiraColuna = array_3x3[:, 1:] # Acessando todos os elementos exceto a primeira coluna

# Slicing
linha = ndarray3[0]  # Acessando a primeira linha inteira
coluna = ndarray3[:, 2]  # Acessando a terceira coluna inteira
submatriz = ndarray1[0:2, 0:2] # Acessando uma submatriz
```

### Reshape e Transposição

Reshape: alteração da forma (dimensões) de um array sem modificar seus dados.
Transposição: troca de linhas por colunas em um array, invertendo suas dimensões.

```sh
# Reshape
reshaped = ndarray3.reshape(1, 8) # Mudando a forma do array combinado para 1x8

# Transposição
ndarray1Transposto = ndarray1.T
```

### Concatenação e Divisão

Concatenação: combinação de dois ou mais arrays ao longo de um eixo especificado (linha ou coluna).
Divisão: separação de um array em vários subarrays ao longo de um eixo especificado.

```sh
# Concatenação
concatenadoLinhas = np.concatenate((ndarray1, ndarray2), axis=0)
concatenadoColunas = np.concatenate((ndarray1, ndarray2), axis=1)

# Divisão
divididoLinhas = np.split(ndarray3, 2, axis=0)
divididoColunas = np.split(ndarray3, 2, axis=1)
```

### Álgebra Linear

Existem diversas funções para operações de álgebra linear, incluindo produto de matrizes, cálculo de determinantes, inversão de matrizes, decomposições, resolução de sistemas de equações lineares e muito outros.

```sh
produtoMatricial = np.dot(ndarray1, ndarray2) # Produto matricial
determinante = np.linalg.det(ndarray3) # Determinante
inversa = np.linalg.inv(ndarray3) # Inversa da matriz
U, R = np.linalg.qr(ndarray3, mode='r') # Decomposição UR
print(np.allclose(np.dot(U, R), ndarray3)) # Verificando se está correta (U * R deve ser igual a ndarray3)

# Sistemas de equações lineares
# Coeficientes das equações
A = ndarray1 
b = ndarray2
# Resolução do sistema de equações lineares Ax = b
x = np.linalg.solve(A, b)
# Exibindo a solução
print("Solução do sistema de equações lineares:")
print(x)
# Verificando se a solução está correta (Ax deve ser igual a b)
print("\nVerificação: Ax = b")
print(np.allclose(np.dot(A, x), b))

#Output
Solução do sistema de equações lineares:
[[-3. -4.]
 [ 4.  5.]]
Verificação: Ax = b
True
```