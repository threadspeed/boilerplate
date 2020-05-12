---
title: python script PythonExercicios Jogo%2520da%2520Forca (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios Jogo%2520da%2520Forca'


## python PythonExercicios Jogo%2520da%2520Forca

Python example: PythonExercicios Jogo%2520da%2520Forca

```python
#Para dividir a palavra use list(variavel da palavra)

palavra = input("Digite a palavra para a forca: ")
palavra = list(palavra)
palavra_original = palavra
palavra_nova = []
print("A palavra tem {} letras, boa sorte".format(len(palavra)))
letra = ""
forca = 0
for c in range(len(palavra) -1): palavra_nova.append("x")
while True:

    letra = input("Digite uma letra: ")
    if letra in palavra_original:
        if palavra.count(letra) > 0 and palavra.count(letra) == 1:
            palavra_nova.insert(palavra_original.index(letra), letra)
            if "x" in palavra_nova:
                palavra_nova.remove("x")
        while palavra.count(letra) > 1:
            palavra_nova.insert(palavra_original.index(letra),letra)
            if "x" in palavra_nova:
                palavra_nova.remove("x")
    else:
        print("ERRROOOOOOOUUUUUUUU")
        forca += 1

    print(palavra_nova)
    if forca >= 5:
        break
    if len(palavra_nova) == len(palavra_original):
        "".join(palavra_nova)
        "".join(palavra_original)

    if palavra_nova == palavra_original:
        print("Parabens voce conseguio")
        print(palavra_original)
        break



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
