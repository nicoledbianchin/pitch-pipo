# Pipo pitch

## Introdução
A solução é uma API Rest construída com Typescript e Express.

## Idealização
A partir do pitch apresentado, pensei em um fluxo inicial para o cadastro sendo:
1 - informar para a plataforma a empresa na qual se deseja incluir um funcionário, e a plataforma retornará os dados que são necessários para a inclusão desse funcionário nos benefícios da empresa
2 - informar para a plataforma os dados necessários para a inclusão do funcionário

Dessa forma, a pessoa responsável por cadastrar novos funcionários precisará inicialmente apenas saber a empresa na qual se deseja incluir funcionários, e depois preenche apenas o necessário para essa inclusão. Como a minha solução se limita ao backend, isso se traduz em duas requisições HTTP distintas. 

Caso um frontend fosse adicionado, a solução ainda se aplica pois poderíamos por exemplo ter uma aplicação web com um dropdown, onde seria selecionada a empresa na qual se deseja adicionar um funcionário, e depois de selecionado, um formulário é apresentado pedindo apenas as informações necessárias (formulário seria feito com os campos retornados da primeira requisição).

Tomada essa decisão de como funciona o fluxo, pensei na arquitetura da solução:
- Application - camada mais superficial, recebe as requisições e roteia para as services
- Service - camada responsável pela lógica de negócios (no caso da etapa 1, retornar os dados necessários, no caso da etapa 2, direcionar os cadastros para os repositórios necessários)
- Repository - camada que se comunica com serviços externos - banco de dados (inicialmente um arquivo JSON), plataformas de cadastro dos parceiros

Iniciarei pelo desenvolvimento da etapa 1. É preciso armazenar quais dados são necessários para o cadastro em cada benefício, inicialmente para abstrair a complexidade de um banco de dados, os colocarei em um JSON.

## To do
O que ainda precisa ser feito
- Middleware para tratar erros
- Adicionar requisições exemplo
- Adicionar testes de mutação

## Parking lot
Parking lot de ideias que surgem durante o desenvolvimento
- Na parte de cadastro de novos funcionários, criar camada que serve como "outbound" dos parceiros, deixando as regras que dependem do parceiro isoladas, o que ajuda quando novos parceiros forem adicionados