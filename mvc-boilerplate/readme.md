# Funcionamento - Atividade de sala
No projeto, o **model** é responsável por acessar e manipular o banco de dados, como criar e deletar alunos ou cursos. O **controller** recebe as requisições dos usuários, comunica com o model para tratar os dados e define qual resposta será enviada ao usuário. Já os **endpoints** são as rotas que permitem que o usuário interaja com o sistema, conectando as requisições HTTP ao controller.

# 1. Arquitetura MVC
**Model:**
A camada de manipulação de dados e regras de negócio do sistema. Tudo que envolve lógica de dados e interação com o banco de dados é configurado no Model.<br><br>
**View:**
A apresentação, ou seja, como os dados são mostrados ao usuário. Ela recebe dados do Controller, geralmente por meio de API, e os exibe usando HTML, CSS e JavaScript.<br><br>
**Controller:**
A ponte entre o o Model e View dentro do sistema. Ele recebe as requisições do usuário, processa essas requisições, chama o Model para manipular os dados, e envia esses dados para a View.<br><br>
**Fluxo do sistema:**<br>
Usuário faz uma requisição, por exemplo, acessa uma URL.<br>
Controller recebe essa requisição, interpreta o que precisa ser feito e solicita dados ao Model.<br>
Model acessa o banco de dados, processa as informações e retorna os dados ao Controller.<br>
Controller pega esses dados e renderiza uma View ou envia uma resposta em JSON.<br>
A View recebe os dados do Controller e exibe para o usuário de forma visual.<br>

# 2. Troca de dados usando JSON
O envio e recebimento de dados em JSON normalmente acontece em rotas de API, onde o backend responde com dados ao frontend.
Quando uma rota responde em JSON, o Controller utiliza o método res.json() do Express para enviar um objeto JavaScript em JSON.

```javascript
exports.byCurso = async (req, res) => {
  const { curso_id } = req.params;
  const alunos = await Aluno.findByCurso(curso_id);
  res.json(alunos);
};
```

# 3. Uso de HTML
Usar HTML básico com formulários e tabelas é importante porque melhora a visualização para o usuário: ele pode enviar informações para o site (com formulários) e ver os dados organizados (em tabelas). Mesmo com tecnologias novas, essas estruturas são simples e funcionam em qualquer navegador.<br>
No back-end com Node.js, usar HTML básico ajuda a montar páginas rápidas para cadastro, consulta e edição de dados, sem complicação. É uma solução prática para protótipos ou quando não é preciso algo muito avançado.

# Boilerplate MVC em Node.js com PostgreSQL

Este projeto é um boilerplate básico para uma aplicação Node.js seguindo o padrão MVC (Model-View-Controller), utilizando PostgreSQL como banco de dados.

## Requisitos

- Node.js (versão X.X.X)
- PostgreSQL (versão X.X.X)

## Instalação

1. **Clonar o repositório:**

```bash
   git clone https://github.com/seu-usuario/seu-projeto.git
   cd seu-projeto
```

2. **Instalar as dependências:**
    
```bash
npm install
```
    
3. **Configurar o arquivo `.env`:**
    
Renomeie o arquivo `.env.example` para `.env` e configure as variáveis de ambiente necessárias, como as configurações do banco de dados PostgreSQL.
    

Configuração do Banco de Dados
------------------------------

1. **Criar banco de dados:**
    
    Crie um banco de dados PostgreSQL com o nome especificado no seu arquivo `.env`.
    
2. **Executar o script SQL de inicialização:**
    
```bash
npm run init-db
```
    
Isso criará a tabela `users` no seu banco de dados PostgreSQL com UUID como chave primária e inserirá alguns registros de exemplo.
    

Funcionalidades
---------------

* **Padrão MVC:** Estrutura organizada em Model, View e Controller.
* **PostgreSQL:** Banco de dados relacional utilizado para persistência dos dados.
* **UUID:** Utilização de UUID como chave primária na tabela `users`.
* **Scripts com `nodemon`:** Utilização do `nodemon` para reiniciar automaticamente o servidor após alterações no código.
* **Testes:** Inclui estrutura básica para testes automatizados.

Scripts Disponíveis
-------------------

* `npm start`: Inicia o servidor Node.js.
* `npm run dev`: Inicia o servidor com `nodemon`, reiniciando automaticamente após alterações no código.
* `npm run test`: Executa os testes automatizados.
* `npm run test:coverage`: Executa os testes e gera um relatório de cobertura de código.

Estrutura de Diretórios
-----------------------

* **`config/`**: Configurações do banco de dados e outras configurações do projeto.
* **`controllers/`**: Controladores da aplicação (lógica de negócio).
* **`models/`**: Modelos da aplicação (definições de dados e interações com o banco de dados).
* **`routes/`**: Rotas da aplicação.
* **`tests/`**: Testes automatizados.
* **`views/`**: Views da aplicação (se aplicável).

Contribuição
------------

Contribuições são bem-vindas! Sinta-se à vontade para abrir um issue ou enviar um pull request.

Licença
-------

Este projeto está licenciado sob a Licença MIT.

Este README.md fornece uma visão geral clara do boilerplate, incluindo instruções de instalação, configuração do banco de dados, funcionalidades principais, scripts disponíveis, estrutura de diretórios, como contribuir e informações de licença. Certifique-se de personalizar as seções com detalhes específicos do seu projeto conforme necessário.