# style guide
Este guia é uma lista de convenções adotadas para como se escrever código/documentação/perguntas durante o projeto.  
  
## language
- Inglês é a principal lingua do projeto. Se espera encontrar ela para:  
  - Titulos em documentações  
  - Códigos em geral  
  - Git commits  
- Português é usado para explicar detalhes em documentações  
- Ninguém é perfeito então não espere encontrar gramática perfeita de ninguém, não importa o idioma.  
  - Não tenha medo de corrigir outros e de escrever algo errado, estamos todos aqui para aprender e melhorar  
  - O foco é caminhar para algo que muitos possam ler e entender  

## documentation
- A idéia é deixar a documentação o mais próxima possível de onde ela é usada e evitar repetição de documentação  
  - Explicação para uma linha do código deve ficar comentado a cima da linha  
  - Explicação para uma função do código deve ficar escrita no [docstring](https://en.wikipedia.org/wiki/Docstring)/[docblock](https://en.wikipedia.org/wiki/Docblock) da função  
  - Explicação para um repositório deve ficar no [README.md](https://en.wikipedia.org/wiki/README)  
- Todo repositório tem que ter o arquivo README.md  
  - Esse arquivo deve explicar **apenas** aquele repositório  
  - Esse arquivo não deve entrar em detalhes de repositórios filhos  
- Utilize [Mermaid Markdown](https://mermaid-js.github.io/mermaid/#/) para [diagramas](https://en.wikipedia.org/wiki/Diagram)  
  - Motivo: imagens não são fáceis de alterar (normalmente envolve em compartilhar algum arquivo antes de exportar para imagem)  

## questions
- Utilizamos as [issues](https://docs.github.com/en/issues) dos repositórios para perguntas e respostas  
  - A issue deve ser criada no repositório aonde a dúvida se originou  
  - Antes de criar, procure saber se a mesma pergunta já ocorreu em outra issue e foi respondida  
    - Se a pergunta ocorreu mas não foi respondida, reviva a pergunta dentro daquela issue  
- O repositório para perguntas gerais é o mesmo onde esta documentação se encontra  

## python code
- [PEP 8](https://peps.python.org/pep-0008/) & [PEP 257](https://peps.python.org/pep-0257/)  
  - As convenções para escrever cóigo python são basicamente aquelas ditadas nos PEP  
  - Usar o formatador de texto **black** e **isort**  
