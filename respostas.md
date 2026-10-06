# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Ricardo Ongari
Matrícula: 26128487
Usuário do GitHub: RicardoOngari
Usuário do Docker Hub: ricardoongari

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
   R: Usei a imagem base nginx:1.27-alpine. O tamanho final da imagem ficou em 73.6MB.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.
   R: Usei o comando: docker run --rm ricardoongari/agrovale-portal:1.0-26128487 ls /usr/share/nginx/html
   O comando mostrou o index.html, estilo.css e 50x.html.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.
   R: O nome completo da imagem publicada foi ricardoongari/agrovale-portal:1.0-26128487
   Link: https://hub.docker.com/r/ricardoongari/agrovale-portal

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?
   R: Foi usado um token para fazer o login pelo terminal, assim não precisa usar a senha da conta direto e tambem da pra controlar as permissões.

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | `COPY site/ /usr/share/nginx/html/` | A página de manutenção não estava sendo copiada para a pasta que o Nginx usa. | O container ficou rodando, mas quando acessei a porta 7087 apareceu a página padrão "Welcome to nginx!". | Adicionei `COPY site/ /usr/share/nginx/html/` no Dockerfile. |
| 2 | | | | |
| 3 | | | | |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?
   R: A ordem é `-p porta do computador:porta do container`. Então no `-p 7042:80`, a porta 7042 é do computador e a 80 é do container. Já no `-p 80:7042`, a porta 80 é do computador e a 7042 é do container. A porta do container é sempre o segundo número.

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`?
   R: Porque `db` é o nome do serviço do MariaDB dentro da rede do Docker Compose. O WordPress consegue acessar o banco usando esse nome. Se usasse `localhost`, ele tentaria acessar o banco dentro do próprio container do WordPress.

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando.
   R: A porta 3306 não precisa ser publicada porque o WordPress acessa o banco pela rede interna do Docker. Se precisar consultar o banco, posso usar o comando:
   `docker compose exec db mariadb -u agrovale -p agrovale_blog`

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?
   R: Usei `docker compose down` para derrubar a stack e depois `docker compose up -d` para subir de novo. O comando `docker compose down -v` poderia apagar o post porque ele remove os volumes, onde ficam os dados do WordPress.

10. Código de conclusão impresso pelo verificador: AGROVALE-26128487-CE1632BE
