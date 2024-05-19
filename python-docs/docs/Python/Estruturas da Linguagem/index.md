# Estruturas da Linguagem

## Variáveis

Variáveis em Python são usadas para armazenar valores que podem ser manipulados e referenciados ao longo do código.

As variáveis em Python são dinamicamente tipadas, o que significa que você não precisa declarar o tipo da variável explicitamente. 
O tipo é determinado automaticamente com base no valor atribuído.
Você declara uma variável simplesmente atribuindo um valor a um nome de variável usando o operador '='.

Exemplo:

	x = 10          # Inteiro
	nome = "Alice"  # String
	pi = 3.14159    # Float (ponto flutuante)
	flag = True     # Booleano

Você pode usar a função type() para verificar o tipo de uma variável:

	print(type(x))    # <class 'int'>
	print(type(nome)) # <class 'str'>
	print(type(flag)) # <class 'bool'>

Os nomes das variáveis devem seguir certas regras:

--Devem começar com uma letra (a-z, A-Z) ou um sublinhado (_).
--Podem conter letras, dígitos (0-9) e sublinhados.
--Não podem começar com um dígito.
--São sensíveis a maiúsculas e minúsculas ('nome' e 'Nome' são variáveis diferentes).


## Vetores e Listas

Em Python, vetores são geralmente implementados usando listas.
Uma lista é uma coleção ordenada e mutável que pode conter elementos de diferentes tipos, incluindo outros objetos e estruturas de dados.

Você pode criar uma lista simplesmente colocando uma série de elementos entre colchetes [], separados por vírgulas:

	--Lista de inteiros
	numeros = [1, 2, 3, 4, 5]

	--Lista de strings
	nomes = ["Joao", "Pedro", "Maria"]

	--Lista mista
	mista = [2, "TESTE", 123.32, True]

Os elementos de uma lista podem ser acessados usando índices. Os índices começam em 0 para o primeiro elemento:

	numeros = [10, 20, 30, 40, 50]

	print(numeros[0])  # Saída: 10
	print(numeros[2])  # Saída: 30

Você pode adicionar e remover elementos de uma lista usando métodos como append(), insert(), remove(), e pop().

	numeros = [10, 20, 30]

	numeros.append(40)
	print(numeros)  # Saída: [10, 20, 30, 40]

	numeros.remove(30)
	print(numeros)  # Saída: [10, 20, 40]

	ultimo = numeros.pop()
	print(ultimo)   # Saída: 40
	print(numeros)  # Saída: [10, 20]

	primeiro = numeros.pop(0)
	print(primeiro)  # Saída: 10
	print(numeros)  # Saída: [20]

Use a função len() para obter o número de elementos em uma lista:

	numeros = [10, 20, 30, 40, 50]
	print(len(numeros))  # Saída: 5
	
Você pode iterar sobre os elementos de uma lista usando um loop for:

	numeros = [10, 20, 30, 40, 50]

	for num in numeros:
		print(num)
		
## Dicionário

Dicionários em Python são coleções de pares chave-valor, onde cada chave é única dentro do dicionário.
Eles são mutáveis, o que significa que podem ser modificados após a criação, e são frequentemente usados para armazenar dados associados ou para representar objetos complexos.

Você pode criar um dicionário usando chaves {} e incluindo pares chave-valor separados por dois pontos ':' :

	dicionario_vazio = {}
	
	aluno = {
		"nome": "Joao",
		"nota": 8.7,
		"curso": "Ciencia da Computacao"
	}
	
Os valores em um dicionário podem ser acessados usando suas chaves:

	print(aluno["nome"])  # Saída: Joao
	print(aluno["curso"]) # Saída: Ciencia da Computacao
	
Você pode modificar os valores associados às chaves existentes ou adicionar novos pares chave-valor:

	aluno["nome"] = "Pedro"
	print(aluno)  # Saída: {'nome': 'Pedro', 'nota': 8.7, 'curso': 'Ciencia da Computacao'}
	
Você pode remover pares chave-valor de um dicionário usando os métodos del, pop() e popitem().

	del aluno["curso"]
	print(aluno) # Saída: {'nome': 'Joao', 'nota': 8.7}
	
	nota = aluno.pop("nome")
	print(nota)   # Saída: "Joao"
	print(aluno)  # Saída: {'nota': 8.7}
	
	ultimo_item = aluno.popitem()
	print(ultimo_item)  # Saída: ('nota', 8.7)
	print(aluno)        # Saída: {}
	
Você pode iterar sobre os elementos de um dicionário usando um loop for. Existem três métodos principais para acessar os elementos durante a iteração:

--keys(): Retorna todas as chaves do dicionário.
--values(): Retorna todos os valores do dicionário.
--items(): Retorna pares chave-valor do dicionário.

	for chave in aluno.keys():
		print(chave)
	
	for valor in aluno.values():
		print(valor)
		
	for chave, valor in aluno.items():
		print(chave, valor)
		
Outros métodos para trabalhar com dicionários:
		
--get(): Retorna o valor para uma chave, ou um valor padrão se a chave não existir.
--clear(): Remove todos os elementos do dicionário.
--copy(): Retorna uma cópia rasa do dicionário.

	nota = aluno.get("nota")
	print(idade)  # Saída: 8.7
	
	aluno.clear()
	print(aluno)  # Saída: {}

	aluno = {"nome": "Joao", "idade": 22}
	copia_aluno = aluno.copy()
	print(copia_aluno)  # Saída: {'nome': 'Joao', 'idade': 22}

## Estruturas Condicionais

Usamos estruturas condicionais para executar código específico com base em determinadas condições. A estrutura condicional mais comum é o `if`:

```python
x = 10
if x > 0:
    print("x é positivo")
```

Também podemos adicionar um `else` para executar código quando a condição não é verdadeira:

```python
x = -10
if x > 0:
    print("x é positivo")
else:
    print("x não é positivo")
```

E podemos usar `elif` para verificar várias condições:

```python
x = 0
if x > 0:
    print("x é positivo")
elif x < 0:
    print("x é negativo")
else:
    print("x é zero")
```

## Estruturas de Repetição

Usamos loops para repetir um bloco de código várias vezes. O loop `for` é usado para iterar sobre uma sequência (como uma lista, tupla, dicionário, conjunto ou string):

```python
for i in range(5):
    print(i)
```

O loop `while` é usado para repetir um bloco de código enquanto uma condição é verdadeira:

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

## Funções

Em Python, uma função é um bloco de código reutilizável que realiza uma ação específica. Definimos funções usando a palavra-chave `def`:

```python
def hello(name):
    return "Olá, " + name
```

Podemos então chamar a função usando seu nome e passando os parâmetros necessários:

```python
print(hello("Mundo"))
```

## Importação e Uso de Bibliotecas

Em Python, podemos usar bibliotecas para adicionar funcionalidades ao nosso código. Para usar uma biblioteca, primeiro precisamos importá-la usando a palavra-chave `import`:

```python
import math
```

Podemos então usar as funções e classes da biblioteca:

```python
print(math.sqrt(16))
```

Também podemos importar apenas partes específicas de uma biblioteca:

```python
from math import sqrt
```

E podemos dar um apelido a uma biblioteca para tornar nosso código mais fácil de escrever:

```python
import math as m
```