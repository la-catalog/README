# style guide
Este guia é uma lista de convenções adotadas para como se escrever código/documentação durante o projeto.  
  
## language
- Inglês é a principal lingua do projeto. Se espera encontrar ela para:  
  - Titulos de documentação  
  - Códigos em geral  
  - Git commits  
- Português é usado para explicar detalhes em documentações  

## documentation
- Todo repositório tem que ter o arquivo [README.md](https://en.wikipedia.org/wiki/README)  
  - Esse arquivo deve explicar **apenas** aquele repositório  
  - Esse arquivo não deve entrar em detalhes de repositórios filhos  
  - A idéia é deixar a documentação o mais próxima possível de onde ela é usada e evitar repetição de documentação  
- Utilize [Mermaid Markdown](https://mermaid-js.github.io/mermaid/#/) para [diagramas](https://en.wikipedia.org/wiki/Diagram)  
  - Motivo: imagens não são fáceis de alterar (normalmente envolve em compartilhar algum arquivo antes de exportar para imagem)  

## python code
- [PEP 8](https://peps.python.org/pep-0008/) & [PEP 257](https://peps.python.org/pep-0257/)  
  - As convenções para escrever cóigo python são basicamente aquelas ditadas nos PEP  
  - Usar o formatador de texto **black** e **isort**  
