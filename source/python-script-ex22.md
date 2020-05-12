---
title: python script ex22 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex22'


## python ex22

Python mysql example: ex22

```python
nome = """<p>&nbsp;</p>
<p><strong>JUVENILE MALE WHITE BELT</strong></p>
<p>&nbsp;</p>
<p>White Belt / Juvenile Male / Light</p>
<p>Malik Bourja (BJJ Akademie)</p>
<p>Franz Kluge (BJJ Dresden)</p>
<p>Adrian Pietrowiak (Gfteam Paraiba Akademie)</p>
<p>James Choi (BJJ Akademie)</p>
<p>&nbsp;</p>"""
#print('Carlos' in nome)
#print(len(nome), nome.count('a'), nome.find('Ricardo'), nome.replace('Carlos', 'Ziegler')) #conta caracter e troca caracter

#print(nome.title(), nome.capitalize()) # deixa o primeiro caractere maiusculo, / deixa o primeiro caractere da Frase
#print(nome.strip()) # remove espacos desnecessarios
#print((nome.split())) # separa a String em uma lista --- posso usar com caractere /
#print('-'.join(nome.split())) # junta as strings
#print(nome.split('/')) # assim que usa para dividir string pela /

#nome1= nome.remo('<p>')
#nome2= nome1.split('</p>')
nome1= nome.replace('<p>', '')
nome2= nome1.replace('</p>', '')
nome22= nome2.replace('p>\n', '')
nome11= nome22.replace('&nbsp;', '')
nome12= nome11.replace('<', '')
nome33= nome12.replace('strong>', '')
nome44= nome33.replace('\n', '')
nome55= nome44.strip()

nome77= (nome55.splitlines()) #poe tudo como 1 elemento na lista
nome00=nome77[0] #uma string recebe o elemento da lista
nom1=nome00.strip()
nom2= nom1.replace('JUVENILE MALE WHITE BELT/White Belt / Juvenile Male / Light', '')

nom5= nom2[0]
nom6= nom2.replace(')', '/:')
nom7= nom6.replace('(', '-:')
nom8= nom7.strip()
nom9= nom8.split('/')
print(type(nom9))
print(nom9)
nom10=str(nom9)
print('aqui é nom10: {}'.format(nom10))
print(len(nom10))
print(type(nom10))

nom11= nom10.split('-')
print(nom11)








```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
