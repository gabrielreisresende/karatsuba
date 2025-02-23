# Algoritmo de Karatsuba

## Descrição
Este projeto consiste na implementação do algoritmo de Karatsuba em Python para a multiplicação eficiente de dois números inteiros grandes.
O algoritmo de Karatsuba é uma técnica que reduz a complexidade da multiplicação de grandes inteiros comparada à multiplicação direta.
A técnica padrão da multiplicação tem a complexidade de O(n²), já o Algoritmo de Karatsuba consegue reduzir essa complexidade para 
O(n<sup>1.585</sup>), no qual n é o número de dígitos dos números a serem multiplicados.
O princípio básico por trás do algoritmo de Karatsuba é que duas grandes multiplicação de números podem ser feitas através de manipulações
mais simples e menores multiplicação de números, além de adições e subtrações, que são operações muito menos custosas do ponto de vista computacional.

## Versão do Python
Este projeto foi desenvolvido na versão Python 3.11.9 do Python.

## Come executar
1 - Clone o repositório do GitHub para sua máquina local.
```
git clone https://github.com/gabrielreisresende/karatsuba.git
```
2 - Certifique-se de que Python 3.x está instalado em seu sistema.  <br>
3 - Navegue até o diretório do projeto através do terminal ou prompt de comando.  <br>
4 - Execute o arquivo main.py com o comando:
```
python main.py
```

## Implementação 
- Inicialmente é feita uma verificação para executar o algoritmo somente se os números de entrada tiverem mais de um dígito. Caso ao contrário, é realizada a operação de multiplicação padrão
  para servir de caso base para a recursão, o qual permite terminar a recursão quando os números são suficientemente pequenos: <br>
 ```if x < 10 or y < 10: return x * y```
- Caso os números sigam o fluxo, será obtido o maior número de dígitos entre so dois números e, após isso, divide esse resultado ao meio;
    ```maxLenght = max(len(str(x)), len(str(y)))``` <br>
    ```half = maxLenght // 2```
- Depois, é feita a divisão dos dois números a serem multiplicados em duas metades: <br>
  ```high_x, low_x = divmod(x, 10**half)``` <br>
  ```high_y, low_y = divmod(y, 10**half)```
- Após isso, são feitas três chamadas recursivas para obter os seguintes produtos:
  1)  Calcula a multiplicação das partes menos significativas: <br>
  ```z0 = karatsuba(low_x, low_y)``` 
  2)  Calcula a multiplicação da soma das partes alta e baixa dos dois números: <br>
  ```z1 = karatsuba((low_x + high_x), (low_y + high_y)))```
  3)  Calcula a multiplicação das partes mais significativas: <br>
  ```z2 = karatsuba(high_x, high_y)```
- Por fim, o resultado é calculado com base na fórmula do Karatsuba e retornado para o usuário:
  1)  É multiplicado por 10<sup>2*half</sup>  para posicionar corretamente o resultado das partes mais significativas: <br>
  ```z2 * 10**(2*half)```  
  2)  É calculada a diferença entre z1, z2 e z0 e posiciona o resultado no meio:  <br>
  ``` ((z1 - z2 - z0) * 10**half)```
  3)  É adicionado o resultado das partes menos significativas diretamente:  <br> ```z0```
- A soma desses três termos dá o resultado final da multiplicação de x e y.

## Saída da Execução
![image](https://github.com/user-attachments/assets/47822143-fff3-405b-ba0b-bc5c448f0992)
