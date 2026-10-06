# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Ricardo Ongari
Matrícula: 26128487
Usuário do GitHub: Ricardo Ongari
Usuário do Docker Hub: ricardoongari

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
   R: Usei a imagem base nginx:1.27-alpine. O tamanho final da imagem do portal foi 73.6MB.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.
   R: Usei o comando: docker run --rm ricardoongari/agrovale-portal:1.0-26128487 ls /usr/share/nginx/html
   O comando mostrou index.html, estilo.css e 50x.html.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.
   R: Nome completo da imagem publicada: ricardoongari/agrovale-portal:1.0-26128487

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?
   R: Docker Hub usa um token para autenticação no terminal, evitando o uso direto da senha da conta e permitindo controlar as  permissões de acesso

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`?

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando.

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?

10. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
