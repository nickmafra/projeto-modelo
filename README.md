[![Build Status](https://travis-ci.com/nickmafra/spring-boot-template.svg?branch=master)](https://travis-ci.com/nickmafra/spring-boot-template)
# spring-boot-template

Projeto modelo usando Spring Boot

O objetivo deste projeto é aplicar o máximo de conhecimento em uma aplicação spring boot, com boas práticas e funcionalidades.
Assim, caso seja preciso relembrar de alguma funcionalidade, basta verificar neste projeto.
Este repositório também pode ser utilizado com template para outros repositórios.


## Executando o sistema

Após compilar com o maven, execute o jar com o perfil spring `local` (a partir da pasta raiz do projeto):
```
java -jar -Dspring.profiles.active=local ./target/spring-boot-template-0.0.1-SNAPSHOT.jar
```

## Usando o sistema

O sistema estará disponível localmente na porta 8080, com HTTPS, através do Swagger-UI:
  https://localhost:8080/swagger-ui.html

>Nota: como é usado certificado HTTPS auto gerado, o navegador diz que não é seguro no primeiro acesso. Basta avançar a tela.

>Nota: a maioria das rotas são privadas, exigindo autenticação. As rotas da saudacao-controller são públicas.

## Autenticando

A autenticação utilizada é via Bearer token JWT, onde após realizado o login é recebido um token representando a sessão, que deve ser enviado em toda requisição.

- Use a rota POST `/api/usuarios` (dentro do usuario-controller) para cadastrar um usuário. Confira na resposta se houve sucesso.
- Em seguida use seu usuário para realizar login na rota `/login`. Na resposta haverá um bearer token, copie-o (com a palavra Bearer também!).
- Para que seu navegador use o token em toda requisição, clique em Authorize (lá em cima à direita, tem um botão com cadeado verde) e cole o token.
- Teste a autenticação executando uma requisição GET na rota `/api/usuarios`. Se tudo der certo, serão listados os usuários cadastrados.

## Banco de dados

Por ser um projeto template, o projeto usa o banco H2. Este banco funciona tanto no teste de compilação, com dados em memória,
quanto ao executar localmente, com dados na pasta `db/data`. Para limpar o banco de dados, basta excluir esta pasta.

Caso deseje ver os dados do banco de dados, deixe o sistema no ar e acesse a URL `https://localhost:8080/h2-console`.
Os dados de acesso de encontram no arquivo `config/application-local.properties`, são as propriedade iniciadas com `spring.datasource`.

