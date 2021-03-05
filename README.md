# Desafio QA Banking - API

Primeiramente, ficamos muito felizes pelo seu interesse em fazer parte do nosso time de QA de Banking. :DD

Como um time super dinâmico, que somos, segue o seu primeiro desafio conosco.

# O desafio 

O desafio é composto de duas etapas.

A primeira dela tem como objetivo avaliar o planejamento do candidatos em casos de testes. O fluxo a ser considerado nesta etapa é o fluxo de abertura de contas de um app da empresa Star.

A segunda etapa tem como objetivo avaliar o candidato na automatização dos testes de API.

## 1. Planejamento
A Start é uma fintech que quer oferecer um novo produto para os seus clientes: uma conta corrente. A conta corrente é direcionada para empresas e com ela a cliente consegue fazer transferências internas e externas, pagamentos de boleto, compras com o cartão de débito e emitir boletos de cobrança. As telas na imagem anexa mostram o fluxo de abertura de conta no app que a Start espera lançar para os seus clientes.

[IMAGEM](https://github.com/laspbr/Banking/blob/master/88742049-8429b400-d117-11ea-80a0-b86f26ed20ab.png)

Seu desafio nessa etapa é criar um planejamento dos casos de teste que você julgar necessário para ter o fluxo de abertura de conta bem testado. A ideia é apenas descrever os casos de teste. 

### Critérios de Avaliação

   - Qualidade dos cenários de testes;
   - Organização.
   
### Pontos adicionais 
   - Utilizar o formato Gherkin para a descrever os casos.

## 2. Automação

Sua missão é desenvolver alguns testes automatizados para a nossa API pública:

### Instruções iniciais

Para você desenvolver o desafio, utilize a seguinte conta que foi criada no nosso ambiente de Sandbox com dados fictícios.

- username - desafioqastone@gmail.com
- password - desafioqa

Você consegue acessar sua conta por esse link: https://sandbox.conta.stone.com.br/login.

Pronto! Você já está pronto para começar seu desafio.

Para se logar pela linha de comando, basta usar o seguinte comando:

```
curl https://login.sandbox.stone.com.br/auth/realms/stone_account/protocol/openid-connect/token \
	  -d 'client_id=admin-cli' \
	  -d 'username=YYYYYYYYY' \
	  -d 'password=ZZZZZZZZZ' \
          -d 'grant_type=password'
```

Isso te devolverá um `access_token`. Use-o para se autenticar nas chamadas para a API.

Você pode fazer transferências internas para essa conta:  
- Stone: 197  
- Agência: 0001  
- Conta: 475384

### Cenário

A Stone possui uma API de [OpenBanking](https://en.wikipedia.org/wiki/Open_banking) que estamos testando e evoluindo continuamente. O link para a documentação de referência é https://docs.openbank.stone.com.br/. 

Queremos que você use esta API para nos mostrar como iria automatizar as várias formas de se inferir qualidade das entregas.

Por exemplo: temos um endpoint para simular uma transação interna em `api/v1/dry_run/internal_transfers`. Queremos que você proponha uma solução de automação neste ambiente de "sandbox" da API. 

Espera-se que você faça a automação de 3 endpoints:

- Saldo: `GET api/v1/accounts/:id/balance`
- Extrato: `GET api/v1/accounts/:id/statement`
- Simulação de transferência interna: `POST api/v1/dry_run/internal_transfers`

Os dados para acesso serão detalhados mais abaixo.

### Critérios de Avaliação

Levaremos em conta os seguintes fatores:

- Organização
- Conhecimento de APIs;
- Ferramentas de automação de análise de qualidade;
- Escrita de cenários sobre os endpoints;
- Geração de relatórios/métricas de qualidade;
- Conhecimento de GIT.

### Como operar na API de sandbox da Stone OpenBanking?

Todos os endpoints possuem autenticação. Utilizamos OAuth2 e OpenID Connect como especificações de autenticação e autorização. Para o desafio de QA, criamos uma "client application" e um usuário para os testes:

- client_id: XXXXXXXXXX
- username: YYYYYYYY
- password: ZZZZZZZZ

Para conseguir o token de acesso, basta fazer um POST para o nosso IAM:

```
curl https://login.sandbox.stone.com.br/auth/realms/stone_account/protocol/openid-connect/token \
	  -d 'client_id=XXXXXXXXXX' \
	  -d 'username=YYYYYYYYY' \
	  -d 'password=ZZZZZZZZZ' \
          -d 'grant_type=password'
```

## Envio do desafio

- O desafio deve conter, no mínimo, um projeto de código que instrumente o uso da API seguindo um conjunto de cenários que você mesmo irá criar para os 3 enpoints citados acima;
- A execução deve retornar um status;
- A escolha da plataforma de automação é livre;
- Ao término da execução deve ser gerado um relatório sobre as APIs testadas (cenários com sucesso/falha, timing, security e etc);
- As instruções para executar o projeto devem estar no README na pasta raíz do repositório.

Você deve disponibilizar seu código no Github e manter o repositório como privado. Quando terminar, nos informe para enviarmos o usuário que deve ter acesso para avaliação.

O repositório deve ser facilmente executável!

Bom desafio! 
