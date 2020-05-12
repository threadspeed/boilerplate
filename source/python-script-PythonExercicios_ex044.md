---
title: python script PythonExercicios ex044 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex044'


## python PythonExercicios ex044

Python mysql example: PythonExercicios ex044

```python
print('{:=^40}'.format(' LOJAS HENRIQUE DEIVISSON '))
preço = float(input('Digite o valor do produto: R$'))
print('''FORMAS DE PAGAMENTO:
[ 1 ] - À VISTA Dinheiro/Cheque
[ 2 ] - À VISTA Cartão
[ 3 ] - Cartão 2X
[ 4 ] - Cartão 3X ou mais''')
opção = int(input('Digite o número relacionado a forma de pagamento: '))
if opção == 1:
    print('Você recebeu 10% de desconto. Sendo assim vai pagar R${:.2f}'.format(preço - (preço * 10 / 100)))
elif opção == 2:
    print('Voce recebeu 5% de desconto. Sendo assim vai pagar R${:.2f}'.format(preço - (preço * 5 / 100)))
elif opção == 3:
    print('O valor a ser pago é de 2 parcelas de R${:.2f}'.format(preço / 2))
elif opção == 4:
    cartao = int(input('Em quantas vezes deseja dividir a sua parcela? OBS.: Apenas Números de 3 a 12: '))
    parcela = (preço + (preço * 20 / 100)) / cartao
    print('O valor a ser pago é de {}x de R${:.2f} COM JUROS'.format(cartao, parcela))
    print('O valor final será de R${:.2f} NO FINAL.'.format(parcela * cartao))
else:
    preço = 0
    print('Opção inválida de pagamento. Tente novamente!')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
