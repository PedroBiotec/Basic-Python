# Aula 8 - Condições Aninhadas

Tags: Estudo, Ok
Text: else if, elif, datatime, bin(), oct(), hex()

- Condições Aninhadas: Aninhar é colocar uma coisa dentro da outra:
- Estruturas condicionais dentro de estruturas condicionais.
- Para mais caminhos, acrescentar  “elif”:
    
    1° Caminho = Se = if
    
    2° Caminho = Senão Se = ~~else if~~ = elif
    
    3° Caminho = Senão = else
    
    ```python
    nome = str(input('Qual é o seu nome? '))
    if nome == 'Jp':
        print('Que nome bonito!')
    elif nome == 'Gustavo' or nome == 'Maria' or nome == 'Paulo':
        print('Seu nome é bem popular no Brasil.')
    else:
        print(f'Tenha um bom dia, {nome}!')
    ```
    

### Desafio 36: Escreva um programa para aprovar o empréstimo bancário para a compra de uma casa.

- Pergunte o valor da casa, o salário do comprador e em quantos anos ele vai pagar.
- A prestação mensal não pode exceder 30% do salário ou então o empréstimo será negado.

```python
valor_casa = float(input('Valor da casa: R$ '))
salario_comprador = float(input('Salário do comprador: R$ '))
anos_pagar = float(input('Quantos anos de financiamento? '))

trinta_salario = salario_comprador / 0.3
prestacao_mensal = valor_casa / (anos_pagar * 12)

print(f'Para pagar uma casa de R$ {valor_casa:.2f} em {anos_pagar}, a prestação será de R$ {prestacao_mensal:.2f}.')
if prestacao_mensal >= trinta_salario:
    print('Empréstimo negado.')
else:
    print('Empréstimo aceito!')
----------------------------------------------------------------------------------
Valor da casa: R$ 10000
Salário do comprador: R$ 2000
Quantos anos de financiamento? 5
Para pagar uma casa de R$ 10000.00 em 5.0 anos, a prestação será de R$ 166.67.
Empréstimo aceito!
```

### Desafio 37: Escreva um programa em Python que leia um número inteiro qualquer e peça para o usuário escolher qual será a base de conversão: 1 para binário, 2 para octal e 3 para hexadecimal.

```python
num =int(input('Digite um número inteiro: '))
print('''Escolha uma das bases de conversão:
[ 1 ] converter para BINÁRIO
[ 2 ] converter para OCTAL
[ 3 ] converter para HEXADECIMAL''')

opcao = int(input('Sua opção: '))

if opcao == 1:
      print(f'{num} para BINÁRIO é igual a {bin(num)[2:]}.')
elif opcao == 2:
      print(f'{num} para OCTAL é igual a {oct(num)[2:]}.')
elif opcao == 3:
      print(f'{num} para HEXADECIMAL é igual a {hex(num)[2:]}.')
else:
      print('Opção inválida, tente novamente.')
-----------------------------------------------------------------------
Digite um número inteiro: 569
Escolha uma das bases de conversão:
[ 1 ] converter para BINÁRIO
[ 2 ] converter para OCTAL
[ 3 ] converter para HEXADECIMAL
Sua opção: 1
569 para BINÁRIO é igual a 1000111001.
```

### Desafio 38: Escreva um programa que leia dois números inteiros e compare-os. mostrando na tela uma mensagem:

- O primeiro valor é maior
- O segundo valor é maior
- Não existe valor maior, os dois são iguais

```python
primeiro = input('Primeiro número: ')
segundo = input('Segundo número: ')

if primeiro > segundo:
    print('O primeiro número é maior.')
elif segundo > primeiro:
    print('O segundo número é maior.')
elif primeiro == segundo:
    print('Não existe valor maior, os dois são iguais.')
-----------------------------------------------------------------------
Primeiro número: 8
Segundo número: 5
O primeiro número é maior.
```

### Desafio 39: Faça um programa que leia o ano de nascimento de um jovem e informe, de acordo com a sua idade, se ele ainda vai se alistar ao serviço militar, se é a hora exata de se alistar ou se já passou do tempo do alistamento. Seu programa também deverá mostrar o tempo que falta ou que passou do prazo.

```python
from datetime import date

nascimento = int(input('Ano de nascimento: '))

atual = date.today().year
idade = atual - nascimento
passou = idade - 18
faltam = 18 - idade
sera = atual + faltam
foi = atual - passou

sexo = str(input('Você é homem ou mulher? ')).strip().upper()
if sexo == 'HOMEM':
    print(f'O homem que nasceu em {nascimento} tem {idade} anos em {atual}.')
    if idade > 18:
        print(f'Você já deveria ter se alistado há {passou} anos.')
        print(f'Seu alistamento foi em {foi}.')
    elif idade < 18:
        print(f'Ainda faltam {faltam} anos para o alistamento')
        print(f'Seu alistamento será em {sera}.')
    elif idade == 18:
        print('Você deve se alistar esse ano.')
else:
    print('Você não precisa se alistar.')
-----------------------------------------------------------------------
Ano de nascimento: 2005
Você é homem ou mulher? Homem
O homem que nasceu em 2005 tem 18 anos em 2023.
Você deve se alistar esse ano.
```

### Desafio 40: Crie um programa que leia duas notas de um aluno e calcule sua média, mostrando uma mensagem no final, de acordo com a média atingida:

– Média abaixo de 5.0: REPROVADO

– Média entre 5.0 e 6.9: RECUPERAÇÃO

– Média 7.0 ou superior: APROVADO

```python
primeira = float(input('Digite a nota da primeira avaliação: '))
segunda = float(input('Digite a nota da segunda avaliação: '))
media = float((primeira + segunda) / 2)
print(f'Tirando {primeira} e {segunda}, o aluno tem a média de {media}.')
if media < 5.0:
    print('O aluno está REPROVADO')
elif media >= 5.0 and media <= 6.9:
    print('O aluno está em RECUPERAÇÃO')
elif media >= 7.0:
    print('O aluno está APROVADO')
-----------------------------------------------------------------------
Digite a nota da primeira avaliação: 8.5
Digite a nota da segunda avaliação: 7.5
Tirando 8.5 e 7.5, o aluno tem a média de 8.0.
O aluno está APROVADO
```

### Desafio 41: A Confederação Nacional de Natação precisa de um programa que leia o ano de nascimento de um atleta e mostre sua categoria, de acordo com a idade:

- Até 9 anos: MIRIM
- Até 14 anos: INFANTIL
- Até 19 anos: JÚNIOR
- Até 25 anos: SÊNIOR
- Acima de 25 anos: MASTER

```python
from datetime import date
atual = date.today().year
nascimento = int(input('Ano de Nascimento: '))
idade = atual - nascimento
print(f'O atleta tem {idade} anos')
if idade <= 9:
    print('Você está na categoria MIRIM.')
elif idade >=9 and idade <= 14:
    print('Você está na categoria INFANTIL.')
elif idade >=14 and idade <= 19:
    print('Você está na categoria JÚNIOR.')
elif idade >=19 and idade <= 25:
    print('Você está na categoria SÊNIOR.')
elif idade >= 25:
    print('Você está na categoria MASTER.')
-----------------------------------------------------------------------
Ano de Nascimento: 2005
O atleta tem 18 anos
Você está na categoria JÚNIOR.
```

### Desafio 42: Refaça o DESAFIO 35 dos triângulos, acrescentando o recurso de mostrar que tipo de triângulo será formado:

- EQUILÁTERO: todos os lados iguais
- ISÓSCELES: dois lados iguais, um diferente
- ESCALENO: todos os lados diferentes

```python
r1 = float(input('Digite o primeiro número: '))
r2 = float(input('Digite o segundo número: '))
r3 = float(input('Digite o terceiro número: '))

if r1 < r2 + r3 and r2 < r1 + r3 and r3 < r1 + r2:
    if r1 == r2 == r3:
        print('Os segmentos acima formam um triângulo equilátero.')
    elif r1 == r2 != r3 or r1 == r3 != r2 or r2 == r3 != r1:
        print('Os segmentos acima formam um triângulo isósceles.')
    elif r1 != r2 != r3:
        print('Os segmentos acima formam um triângulo escaleno.')
else:
    print('Os segmentos acima não podem formar um triângulo.')
-----------------------------------------------------------------------
Digite o primeiro número: 7
Digite o segundo número: 8
Digite o terceiro número: 5
Os segmentos acima formam um triângulo escaleno.
```

### Desafio 43: Desenvolva uma lógica que leia o peso e a altura de uma pessoa, calcule seu Índice de Massa Corporal (IMC) e mostre seu status, de acordo com a tabela abaixo:

- IMC abaixo de 18,5: Abaixo do Peso
- Entre 18,5 e 25: Peso Ideal
- 25 até 30: Sobrepeso
- 30 até 40: Obesidade
- Acima de 40: Obesidade Mórbida

```python
peso = float(input('Qual seu peso? (kg) '))
altura = float(input('Qual sua altura? (m)'))
imc = peso / (altura ** 2)

print(f'Seu imc é {imc:.2f}.')
if imc < 18.5:
    print('Você está abaixo do peso.')
elif imc > 18.5 and imc < 25:
    print('Você está com o peso ideal.')
elif imc > 25 and imc < 30:
    print('Você está em sobrepeso.')
elif imc > 30 and imc < 40:
    print('Você está em obesidade.')
elif imc > 40:
    print('Você está em Obesidade Mórbida.')
-----------------------------------------------------------------------
Qual seu peso? (kg) 80
Qual sua altura? (m)1.92
Seu imc é 21.70.
Você está com o peso ideal.
```

### Desafio 44: Elabore um programa que calcule o valor a ser pago por um produto, considerando o seu preço normal e condição de pagamento:

- à vista dinheiro/cheque: 10% de desconto
- à vista no cartão: 5% de desconto
- em até 2x no cartão: preço formal
- 3x ou mais no cartão: 20% de juros

```python
preço = float(input('Preço das compras: R$ '))
forma = int(input('''Digite a forma de pagamento:
[ 1 ] - À vista dinheiro/cheque
[ 2 ] - À vista no cartão
[ 3 ] - Em até 2x no cartão
[ 4 ] - 3x ou mais no cartão:
Qual é a opção? '''))

if forma == 1:
    dinheiro = preço - (preço * 10 / 100)
    print(f'Sua compra de R$ {preço} tem 10% de desconto e vai custar R$ {dinheiro}.')
elif forma == 2:
    vista_cartao = preço - (preço * 5 / 100)
    print(f'Sua compra de R$ {preço} tem 5% de desconto e vai custar R$ {vista_cartao}.')
elif forma == 3:
    duas_cartao = preço
    print(f'Sua compra de R$ {preço} custará 2 parcelas de {duas_cartao / 2}.')
elif forma == 4:
    vezes = int(input('De quantas vezes? '))
    tres_cartao = (preço * 20 / 100) + preço
    print(f'Sua compra de R$ {preço} custará R$ {tres_cartao} com {vezes} parcelas de R$ {tres_cartao / vezes}.')
else:
    print('Opção inválida, tente novamente')
-----------------------------------------------------------------------
Preço das compras: R$ 1000
Digite a forma de pagamento:
[ 1 ] - À vista dinheiro/cheque
[ 2 ] - À vista no cartão
[ 3 ] - Em até 2x no cartão
[ 4 ] - 3x ou mais no cartão:
Qual é a opção? 4
De quantas vezes? 8
Sua compra de R$ 1000.0 custará R$ 1200.0 com 8 parcelas de R$ 150.0.
```

### Desafio 45: Crie um programa que faça o computador jogar Jokenpô com você.

```python
from random import randint
from time import sleep

print('=================Jokenpô=================')
print('''Vamos jogar Jokenpô?
Opções:
[ 1 ] Pedra
[ 2 ] Papel
[ 3 ] Tesoura''')
sleep(1)

print('Já decidi minha jogada! Vamos lá.')
pc = randint(1,3)
opção = int(input('Qual sua jogada? '))

print('JO...')
sleep(1)
print('KEN...')
sleep(1)
print('PÔ!')
sleep(1)

if pc == 1:    #Pc jogou Pedra
    if opção == 1:
        print('Nós escolhemos Pedra, empatamos!')
    if opção == 2:
        print('Você escolheu Pedra e eu Papel, o Papel embrulha a Pedra. Eu venci!')
    if opção == 3:
        print('Você escolheu Pedra e eu Tesoura, a Pedra esmaga a Tesoura. Você venceu, parabéns!')
if pc == 2:    #Pc jogou Papel
    if opção == 1:
        print('Você escolheu Papel e eu Pedra, o Papel embrulha a Pedra. Você venceu, parabéns!')
    if opção == 2:
        print('Nós escolhemos Papel, empatamos!')
    if opção == 3:
        print('Você escolheu Papel e eu Tesoura, a Tesoura corta o Papel. Eu venci!')
if pc == 3:  # Pc jogou Tesoura
    if opção == 1:
        print('Você escolheu Tesoura e eu Pedra, a Pedra esmaga a Tesoura. Eu venci!')
    if opção == 2:
        print('Você escolheu Tesoura e eu Papel, a Tesoura corta o Papel. Você venceu, parabéns!')
    if opção == 3:
        print('Nós escolhemos Tesoura, empatamos!')
else:
        print('Jogada Inválida.')
print('Obrigado por jogar! Independente do resultado: Bom jogo!')
-----------------------------------------------------------------------
=================Jokenpô=================
Vamos jogar Jokenpô?
Opções:
[ 1 ] Pedra
[ 2 ] Papel
[ 3 ] Tesoura
Já decidi minha jogada! Vamos lá.
Qual sua jogada? 1
JO...
KEN...
PÔ!
Você escolheu Tesoura e eu Pedra, a Pedra esmaga a Tesoura. Eu venci!
Obrigado por jogar! Independente do resultado: Bom jogo!

Process finished with exit code 0
```
