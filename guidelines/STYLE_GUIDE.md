# style guide
Este guia é uma lista de convenções adotadas para como se escrever código/documentação/perguntas/sugestões durante o projeto.  

## software design
- Em questões de [input/output](https://en.wikipedia.org/wiki/Input/output)  
  - Software responsável por receber os dados dita o formato em que quer receber os dados  
  - Software responsável por enviar os dados deve formatar de acordo com o ditado pelo receptor  
    - Cada transmissor vai provávelmente escrever seu próprio código para transmitir os dados, se o receptor tiver que adaptar para cada um destes formatos de dados nós podemos acabar com 2N códigos escritos. Para diminuir isto é recomendável que apenas os transmissores escrevam da maneira esperada pelo receptor, o que irá diminuir para N códigos escritos  

## python code
- [PEP 8](https://peps.python.org/pep-0008/) & [PEP 257](https://peps.python.org/pep-0257/)  
  - As convenções para escrever cóigo python são basicamente aquelas ditadas nos PEP  
  - Usar o formatador de texto **black** e **isort**  
