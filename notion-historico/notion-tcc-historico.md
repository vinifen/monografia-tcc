---
title: TCC — histórico (Notion)
source_html: notion-historico/notion-tcc-historico.html
---

# TCC

## Diário

### TOTAL: 240h

### Mês 05/26

#### 12/05/26

- Total: 5h

- Atividades: Terminei o Emuseu, arrumei na casa os ultimos passos, revisei tudo e fui para utfpr implementar e colocar no https://coolify.e-museu.gp.utfpr.edu.br/ usando deploy automatico pelo github webhook por sugestao do professor Diego

#### 10/05/26

- Total: 1h

- Atividades:

#### 09/05/26

- Total: 2h

- Atividades: Removi tudo que eu tinha feito de novo melhorei o qrcode do emauseu e coloquei creditos no about e falei pro deigo configurar o subdomain para ter coolify, ativei tambem a autenticacao de 2 etapas no coolify para melhorar a segunranca ja que vai ficar exposto. antes eu achava que realmente nao era para expor o coolify por um questao de seguranca mas pelo jeito era pra expor por praticidade, tirando assim a necessidade de metodos mais complexos

#### 08/05/26

- Total: 1h

- Atividades: Professor coorientador Diego Marczal veio falar comigo que era melhor expor o coolify em um subdominio

#### 07/05/26

- Total: 1h

- Atividades: Fiz melhorias no sistema de auto deploy buscando o problema no github actions e pareceu ser o token de autoticacao que criei sendo em um formato ruim, vale contar que no curl ele funcionava mas no github action nao. com isso pedi para a sediane ir na utfpr trocar o token. ela nao fez

#### 06/05/26

- Total: 9h

- Atividades: Fiquei o dia inteiro implementando um sistema de auto deploy baseado em cron no coolify com script no projeto que verifica mudancas no repositorio e envia o gatilho para o coolify atualizar e fui para utfpr implementar porém conversando com os professores roni depois hermano emerson e marcelo vichar foi orientado eu mudar de abordagem com eu tendo a ideia de criar um endpoint no projeto para receber triggers do github a cada mudancas, utilizando github action, entao apesar de estr tudo funcionando já na utfpr, resolvi implementar isso pois seria menos custoso em relacao de processamento, mais alinhado, dai fiquei até das 18:00 até 23:00 na utfpr criando esse novo deploy com eu nao conseguindo completar totalmente porem já conseguindo fazer o deplyo por meio do novo endpoint, ainda ficou dando problema no github action com eu buscando melhorar isso outro dia.

#### 05/05/26

- Total: 5h

- Atividades: Fui na UTFPR, fiquei la 5 horas, implementei o production e staging, deu tudo certo menos o deploy automatico, por algum motivo o coolify nao esta vendo a mudanca no git e atualizando automaticamente, amanha vou ir na utf de novo e espero pela ultima vez

### Mês 04/26

#### 29/04/26

- Total: 2h

- mexi no emuseu na presencialmente utfpr

#### 25/04/26

- Total: 6h

- Terminei primeira parte do emuseu

#### 24/04/26

- Total: 8hr

- informei que comprei um pendrive para guardar coisas do emuseu, guardei senhas do emuseu, criei github. groq e openroute para o emuseu, refatorei o sistema de traducao com ia

#### 22/04/26

- Total:

#### 21/04/26

- Total: 10h

- terminei refatoracao e coloquei traducao com ia no admin usando varios servicos para aumentar o numero de usos

#### 19/04/25

- Total: 8h

- Todos os testes e refatoracao

#### 12/04/25

- Total: 3h

- fiz antibot com cloudflare

#### 08/04/26

- Total: 10h

- Ir pra utf arrumar infra e envs

#### 07/04/26

- Total: 10h

- Fui na utfpr terminei primeira parte do emuseu

#### 06/04/26

- Total: 4h

#### 05/04/26

- Total: 10h

- Fluxo público: código de 6 dígitos por e-mail + confirmação na sessão antes de contribuir com itens/extras.

- E-mails transacionais: confirmação de receção de contribuição (item/extra) quando o mailer está configurado.

- Segurança UX: rate limits nos endpoints; mensagens genéricas em produção se o mail falhar ou não estiver configurado.

- Dados: last_email_verification_at no colaborador; admin pode marcar confirmação manualmente.

- Infra: Redis para sessão e cache (throttles + estado de verificação); Docker local com serviço Redis; Coolify com Redis externo.

- Testes: feature + unitários para verificação, erros de mail e regras de contribuição; PHPUnit com array para mail/sessão.

- Repositório: .env ignorado; cuidado com APP_KEY no .env.example e não commitar emuseu_dump.sql (tem hashes de utilizadores).

#### 04/04/26

- Total: 10h

Fiz envio de email com resend  e fiz funcionar autenticacao pelo email ao enviar um item ou extra

#### 03/04/26

- Total: 7h

- Terminei parte de suporte a varias linguas, fiz todo o layuout, melhorei otimizacao das querys sql, fiz mais algumas refatoracoes pelo o codigo, principalmente depois da implementacao de varias linguas foi necessario refatorar coisas

### Mês 03/26

#### 29/03/26 - Domingo

- Total: 9h

- Já terminei pr do js e fazer, fiz coisa pra cassete, um monte de tabela nova para aceitar multiplos idiomas, fiz pr

#### 28/03/26 - Sabado

- Total: 4h

- Arrumar js do emuseu

#### 26/03/26

- Total: 2h

- Terminei componentizacao de views, enviei pr, meet com Sediane as 21hrs

#### 25/03/26

- Total: 1h

- mais componentizacao em views

#### 24/03/26

- Total: 1h

- inputs e melhorar componentizacao

#### 23/03/26

- Total: 2h

- Comecei a componentizar elementos mais individuais das views

#### 22/03/26

- Total: 3h

- Reestruturacao enorme das vies e tambem mexi nos controlers e componentizei coisas gerais das views

#### 21/03/26

- Total: 1h

- Reestruturar views, fazer issue 40 e PR 41

#### 20/03/26

- Total: 2h

- Mais alguma correcoes e envio de hotfix

#### 19/03/26

- Total: 3h

- Com o dump do banco e storage de imagens do emuseu, eu pedi pra ia organizar as coisas relacionadas com migrate atual, organizando o tambem e a organizacao do arquivo de storage

#### 16/03/26

- Total: 3h

- terminei refatoracao de controllers fiz merges prs e falei com o prof diego

#### 15/03/26

- Total: 2h

- Fiz mais refatoracao em controllers seguindo o padrao

#### 14/03/26 - Sabado

- Total: 3h

- Fiz mais refatoracao, parte 2 de controllers, mexi baswtante no query de items e admin, centralizei tudo em support. Removi o query controller porque nao era semantico

#### 13/03/26

- Total: 4h

- Terminei a primeira parte da refatoracao dos controlers onde refatorei boa parte da parte de item e admin de item tambem mexi no blade e js

#### 12/03/26

- Total: 4h

- refactor em item controller, js, nomenclatura de section para item categories

#### 08/03/26

- Total: 3h

- Refatorei controller de Admin items

#### 07/03/26

- Total: 2h

- Comecei refatoracao de controllers, o core do projeto

#### 05/03/26

- Início: 08:40

- Pausa: 9:29 - 10:00

- Pausa 2: 2 horas de pausa

- Fim: 14:50

- Total: 3h39

- Comecar refatoracao dos controllers e cleaning de coisa noa usadas como parte de atuh

#### 01/03/26

- Total: 8h

- Nome de tabelas arrumados, sections → item_categories, categories → tag_categories, users → admin, proprietaries →collaborators, tag_items → item_tag, arrumei session para aceitar admin_id, arrumei collaborators para usar enum external e internal, removi is_admin de admins. Coloquei session do admin pra salvar no banco

### Mês 02/26

#### 24/02/26

- Total: 5h

- Fiz toda a parte de traducao alem de adicionar o domain admin e refactorar parte de resources. conversei com a professora

#### 23/02/26

- Total: 2h

- Comecei mexer na parte de i18n

#### 20/02/26

- Total: 3h

- Terminei a pr base refactor

#### 18/02/26

- Total: 3h

- Arrumei pint, estudei projeto e como refatorar, removi coisas nao usadas

#### 17/02/26

- Total: 4h

- Consegui fazer funcionar s3 no coolify e linkar com laravel

#### 16/02/26

- Total: 8h

- Arrumei o storage do emuseu

#### 15/02/26

- Total: 3h

- Atualizei o projeto para usar padrão de dominios

- Estudei como fazer persistencia de files. basicamente mudar o storage do laravel para um servico coolify. Achei esse servico que parece ser bom: MinIO

#### 11/02/26

- Total: 3h

- Fiz funcionar o banco pelo coolify, era problema ao ativar configuracao `Connect To Predefined Network` em advanced. tentei configurar healthcheck para parar de aparecer aviso de check no coolify, porem quando adicionei, comecou dar erro 404, to estuando ainda, por enquanto vou deixar sem

#### 10/02/26

- Total: 3h

- Criei banco com coolify e mudei no projeto para acessar pela url

#### 07/02/26

- Total: 2h

- configurei coolify com organizacao, removi networks e adicionei configuracao para buscar evitar problema depois do deploy que estava acontecendo

#### 04/02/26

- Total: 1h

- conversei com prof Sediane, mostrei tudo que fiz e criamos github organization

### Mês 01/26

#### 27/01/26

- Total: 3h

- ci github

#### 26/01/26

- Ferramentas de qualidade de código

- Total: 4h

#### 25/01/26

- Total: 4h

- Ferramentas de qualidade de código

#### 24/01/26

- Total: 2h

#### 23/01/26

- Total: 3h

- Atualizar laravel e php para novas versoes (php 8.5, laravel 12)

#### 20/01/25

- Total: 5h

- Mudar para poder incluir dados do banco como volumes do docker compose

#### 19/01/26

- Total: 2h

#### 15/01/26

- Total: 2h

- Arrumei problema de nginx adicionado mais 2 arquivos para configuracao de staging e production por causa dos nomes de service do docker-compose diferentes, rodei tudo funcionou, porém agora crashou, testar no proximo dia.

#### 14/01/26

- Total: 4h

- fiz ambiente de staging, documentacao no github, refiz o coofily e tentei fazer funcionar, sem sucesso

#### 11/01/26

- Total: 1h

- tentei rodar de novo e deu erro

#### 08/01/25

- Total: 2h

- Fiz parte da documentacao coolify, fiz merge para a main e comecei a fazer a parte da main no coolify, pena que crashou quando fui subir, talvez problema de ter duas ao mesmo tempo? pf nÃO

#### 07/01/25

- Total: 3 horas

- Fiz funcionar deploy automatico e subi coolify na minha VPS da digital ocean

#### 06/01/25

- Total: 30min

- Testei deploy automatico com commit que não funcionou, amanhã vou tentar adicionar um webhook no github para o colify

#### 05/01/26

- Início: 18:30

- Fim: 21:00

- Total: 2h30

- Hoje consegui fazer o E-Museu rodar no navegador.

#### 04/01/26

- Total: 5 horas

- Fiz primeira configuracão do colify e código do e-museu.

#### 01/01/26

- Total: 30min

### Mês 12/25

#### 31/12/25

- Total: 2h00

### Configurão inicial

- 25 h

- Tempo para fazer a configuração inicial e atualizacões de tecnologias. foi feito toda a parte de docker e separacão de ambientes

## Algumas das coisas feitas

- nao ta mostrando senha no input de senha quando clica no

- rate limit em enviar email, rate limit bem baixo

- A feature de `users` não é coerente com o nome pois todos os users são sempre admins (mudar nome para admin remover coluna is_admin)

- Conversar sobre colaboradores (tira is_admin, pesquisar sobre validacao do email)

- Parece que nao é usado o recuperar a senha, e onde isso seria usado sendo que o unico tipo de usuario é o admin? (nao sera utilizado)

- Sections aparecem como Categorias no frontend, incoerência de nomes. (sections → categories)

- COnversar sobre como funciona colaboradores, sobre eles serem por emails com qualquer outra pessoa podendo se passar pois nao tem nenhuma verificacao, talvez adicionar um login por exmail ou as vezes nem é necessario essa verificaao de email, só salvar na coluna ebeleza

- Arrumar bloqueio de dois admin editando o mesmo item

### O que foi feito

comentario de block admin traduzido (Não é possível fazer alterações enquanto outro administrador estiver editando o mesmo.)

- Category no banco e backend está relacionada com Categoria de etiquetas. É necessário analisar a necessidade dessa tabela `categories` pois poderia ser somente uma nova coluna do tipo enum em `tags` (categories→ tag_categories)

- Conversar sobre como `item_component` funciona (nao mudar)

- Refatorar o web routes, foi melhorado names, routas, e removido middlewares usados direto no controller e padronizado uso no routes

- mudado pro padrão de arquivos do Laravel 12, comor remover arquivos kernel porque Laravel 12 indexas automaticamente

- Removido mais middlewares

- Removido providers

- separacao de responsabilidades em concerns

- Adicionar request id em cada rota/cotnrollers

- ta torto aqui embaixo no staging prod em public e admin:

- Tcc Nicolas

- arrumar js refatorar JS

- conversar sediane necssidade de lock em admin

- Perguntar para sediane sobre como vai ser o codigo de identificacao

- Develop nao funciona no firefox

- Icones de botoes nao apraecem em develop mas aparecem em prod

- parece que só funciona o coisa de editar com 2 admin no prod, testar isso

- arrumar imagens

- Tem tabelas que nao precisao de traducao tipo marcas, acho que só essa

- item controller show parte ir para service

- adicionar coisa que ve em que idioma o navegador esta e muda a linguagem

- dar uma olhada nas querys, se nao esta ruim

- varios erros em buscas nas tabelas, tipo por name, tem que testar mais, em admin que vi.

- Arrumar frontend que esta com scroll e tamanho proporcoes estranhas

- Adicionar .ico no emuseu

- arrumar para os selects nao exibirem tudo e terem pesquisa neles

- salvar dados de enviar colaboracao no localstorage e fazer logica e salvar e excluir quando enviar

- Ter botao de reset em pesquisas, tanto em tables de admin, quanto em filtros do frontend em items index

- arrumar requests e entradas e update e create e views relacionado a traducoes, fazer de forma didatica e facil para o usuario

- Arrumar filtragem no frontend em items publicos

- parece que quando roda teste, ele exclui o banco do local, testar isso no local e prod-local e arrumar

- colocar ratelimit

- em staging, debug mode do laravel nao funciona direito

- colocar todos os imports no padrao de por domains, assim reduzindo linhas

- adicionar na tabela de collaborators, uma coluna de verificado.

- mudar de neutral para universal

- adicionar tabela de localicao de itens, para ter tipo utfpr, unicentro, dai é novo crud

- arrumar criacao automatica de identication code e sua busca em /codes que faz redirect para o item

- recaptcha em catalog/items extra e create e adming login

- fazer todos os testes

- categoria select public create nao exibe item salvo no localstorage
