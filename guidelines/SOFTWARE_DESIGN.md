# software design
- Em questões de [input/output](https://en.wikipedia.org/wiki/Input/output)  
  - Software responsável por receber os dados dita o formato em que quer receber os dados  
  - Software responsável por enviar os dados deve formatar de acordo com o ditado pelo receptor  
    - Cada transmissor vai provávelmente escrever seu próprio código para transmitir os dados, se o receptor tiver que adaptar para cada um destes formatos de dados nós podemos acabar com 2N códigos escritos. Para diminuir isto é recomendável que apenas os transmissores escrevam da maneira esperada pelo receptor, o que irá diminuir para N códigos escritos  
