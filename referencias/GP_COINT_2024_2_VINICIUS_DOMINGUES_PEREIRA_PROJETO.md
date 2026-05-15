---
source_pdf: referencias/original-pdfs/GP_COINT_2024_2_VINICIUS_DOMINGUES_PEREIRA_PROJETO.pdf
extracted_with: pdftotext (UTF-8)
---

UNIVERSIDADE TECNOLÓGICA FEDERAL DO PARANÁ

VINICIUS DOMINGUES PEREIRA

BAIRROFORTE: UM APLICATIVO COLABORATIVO PARA MONITORAMENTO
DE SEGURANÇA EM TEMPO REAL ENTRE MORADORES E
COMERCIANTES

GUARAPUAVA
2025

VINICIUS DOMINGUES PEREIRA

BAIRROFORTE: UM APLICATIVO COLABORATIVO PARA MONITORAMENTO
DE SEGURANÇA EM TEMPO REAL ENTRE MORADORES E
COMERCIANTES

BairroForte: A collaborative app for real-time security monitoring between
residents and merchants

Projeto de Trabalho de Conclusão de Curso
de Graduação apresentado como requisito para
obtenção do título de Tecnólogo em Tecnologia
em Sistemas para Internet do Curso Superior
de Tecnologia em Sistemas para Internet da
Universidade Tecnológica Federal do Paraná.
Orientador: Prof. Dr. Roni Fabio Banaszewski

GUARAPUAVA
2025

4.0 Internacional

Esta licença permite compartilhamento, remixe, adaptação e criação a partir do trabalho, mesmo para fins comerciais, desde que sejam atribuídos créditos ao(s) autor(es).
Conteúdos elaborados por terceiros, citados e referenciados nesta obra não são cobertos pela licença.

RESUMO

O presente trabalho aborda o desenvolvimento do BairroForte, um aplicativo de segurança
colaborativa projetado para empoderar comunidades urbanas e suburbanas na prevenção
de crimes e fortalecimento da sensação de segurança. A justificativa para o projeto está
na crescente preocupação com a segurança pública e a falta de ferramentas eficazes para
comunicação e ação comunitária em áreas vulneráveis. O objetivo principal do aplicativo é
conectar moradores, comerciantes e profissionais de segurança, permitindo o monitoramento
de ocorrências em tempo real, o envio e recebimento de alertas personalizados e a formação
de grupos comunitários para ações preventivas. O projeto também contempla a personalização
das notificações, permitindo que os usuários definam preferências como categorias, raio de
alcance e horários. Embora ainda em fase de concepção, os resultados esperados incluem
maior engajamento comunitário, redução de incidentes em áreas monitoradas e aumento da
confiança entre moradores e comerciantes. O BairroForte destaca-se por oferecer controle
total sobre privacidade, ferramentas de comunicação direta e relatórios estratégicos, como
mapas de calor de criminalidade. Conclui-se que o BairroForte tem potencial para transformar a
forma como comunidades lidam com a segurança, promovendo um ambiente mais conectado,
colaborativo e seguro.
Palavras-chave: segurança colaborativa; aplicativo móvel; prevençäo de crimes; geolocalizaçäo; .

ABSTRACT

This study addresses the development of BairroForte, a collaborative security application
designed to empower urban and suburban communities in crime prevention and enhancing the
sense of safety. The justification for the project lies in the growing concern over public safety
and the lack of effective tools for communication and community action in vulnerable areas.
The primary objective of the application is to connect residents, business owners, and security
professionals, enabling real-time monitoring of incidents, sending and receiving personalized
alerts, and forming community groups for preventive actions. The project also includes notification customization, allowing users to set preferences such as categories, coverage radius, and
schedules. Although still in the conception phase, the expected outcomes include increased
community engagement, a reduction in incidents in monitored areas, and greater trust between
residents and business owners. BairroForte stands out by offering complete control over privacy,
direct communication tools, and strategic reports, such as crime heat maps. It is concluded that
BairroForte has the potential to transform how communities address security, fostering a more
connected, collaborative, and safe environment.
Keywords: collaborative security; mobile app; crime prevention; geolocation; .

LISTA DE FIGURAS

Figura 1 – Funcionamento do docker . . . . . . . . . . . . . . . . . . . . . . . . . .

12

Figura 2 – Dinâmica do método Scrum. . . . . . . . . . . . . . . . . . . . . . . . .

13

Figura 3 – Quadro kanban simples. . . . . . . . . . . . . . . . . . . . . . . . . . . .

14

Figura 4 – GitHub projects. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

Figura 5 – Family360 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

17

Figura 6 – Find My Kids . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

18

Figura 7 – Family360 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

19

Figura 8 – Iniciais

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

Figura 9 – Configurações . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

26

Figura 10 – Estatísticas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

27

Figura 11 – Canal de dúvidas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

27

Figura 12 – Arquitetura do Banco de Dados . . . . . . . . . . . . . . . . . . . . . . .

29

LISTA DE ABREVIATURAS E SIGLAS

Siglas
FCM

Firebase Cloud Messaging

IBGE

Instituto Brasileiro de Geografia e Estatística

MVP

Minimum Viable Product(Produto Mínimo Viável)

PNAD

Pesquisa Nacional por Amostra de Domicílios Contínua

SGBD

Sistema de Gerenciamento de Banco de Dados(Data Base Management System)

SQL

Structured Query Language(Linguagem de consulta estruturada)

SUMÁRIO
1

INTRODUÇÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

7

1.1

Justificativa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

8

1.2

Objetivos

8

1.2.1

Objetivo geral

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

9

1.2.2

Objetivos específicos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

9

1.3

Organização do trabalho . . . . . . . . . . . . . . . . . . . . . . . . . . .

9

2

REFERENCIAL TEÓRICO . . . . . . . . . . . . . . . . . . . . . . . . . . .

10

2.1

Tecnologias do lado cliente . . . . . . . . . . . . . . . . . . . . . . . . .

10

2.1.1

Flutter

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

10

2.1.2

FlutterFlow . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

10

2.2

Tecnologias do lado servidor . . . . . . . . . . . . . . . . . . . . . . . .

10

2.2.1

NodeJS e NestJS

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

11

2.2.2

Firebase Cloud Messaging (FCM) . . . . . . . . . . . . . . . . . . . . . . .

11

2.2.3

Docker . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

11

2.2.4

MySQL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

12

2.3

Processo de desenvolvimento . . . . . . . . . . . . . . . . . . . . . . . .

12

2.3.1

Metodologia ágil Scrum . . . . . . . . . . . . . . . . . . . . . . . . . . . .

12

2.3.2

Kanban . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

13

2.4

Ferramentas de desenvolvimento . . . . . . . . . . . . . . . . . . . . . .

14

2.4.1

Git e GitHub . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

14

2.4.2

GitHub Projects

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

3

TRABALHOS RELACIONADOS . . . . . . . . . . . . . . . . . . . . . . .

16

3.1

Family360 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

16

3.2

Find My Kids

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

18

3.3

Life360 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

19

3.4

Considerações . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

19

4

MATERIAIS E MÉTODOS . . . . . . . . . . . . . . . . . . . . . . . . . . .

21

5

ANÁLISE E PROJETO DO SISTEMA . . . . . . . . . . . . . . . . . . . . .

22

5.1

Escopo do sistema . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

22

5.2

Planejamento da primeira sprint . . . . . . . . . . . . . . . . . . . . . . .

24

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

5.3

Prototipação das telas . . . . . . . . . . . . . . . . . . . . . . . . . . . .

24

5.4

Modelagem do Banco de Dados . . . . . . . . . . . . . . . . . . . . . . .

28

5.5

Considerações Finais

. . . . . . . . . . . . . . . . . . . . . . . . . . . .

29

6

CONCLUSÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

31

REFERÊNCIAS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

32

APÊNDICE A

FUNCIONALIDADES PLANEJADAS PARA EVOLUÇÃO
DO SISTEMA . . . . . . . . . . . . . . . . . . . . . . . .

35

A.1 Funcionalidades Should Have (Deveria Ter) . . . . . . . . . . . . . .

35

A.2 Funcionalidades Could Have (Poderia Ter)

. . . . . . . . . . . . . .

35

A.3 Funcionalidades Won’t Have This Time (Não Terá Desta Vez) . . . .

36

7

1 INTRODUÇÃO
A segurança pública é uma preocupação crescente em muitas regiões urbanas e suburbanas, especialmente em áreas onde a criminalidade tem aumentado significativamente nos
últimos anos. A sensação de insegurança afeta não apenas os moradores, mas também os
pequenos comerciantes, que, muitas vezes, se tornam alvos de crimes como roubos e furtos.
De acordo com a Pesquisa Nacional por Amostra de Domicílios Contínua (PNAD) do
Instituto Brasileiro de Geografia e Estatística (IBGE), em 2021, 60,4% dos moradores do Norte
do Brasil se sentem inseguros ao andar sozinhos à noite nos arredores de seus domicílios,
enquanto no Sul essa porcentagem é de 38,1%, e no Brasil apenas 48,3% se sentem seguras
(IBGE, 2021). Esses dados evidenciam a necessidade de soluções que aumentem a sensação
de segurança entre os moradores e até mesmo comerciantes locais, demonstrando a base para
o desenvolvimento de soluções que promovam segurança colaborativa.
O aspecto da segurança pública tem um profundo impacto na qualidade de vida e na
vitalidade econômica das comunidades. Quando ocorrem aumentos nos índices de criminalidade, as pessoas tendem a modificar suas rotinas e, então, evitam determinada região e/ou
horários, limitando o fluxo de indivíduos e afetando o comércio local. Esse quadro não apenas
limita a chegada de novos negócios, como também compromete a confiança das pessoas com
seu espaço de vida, o que limita o crescimento econômico e o desenvolvimento sustentável da
região.
Nas situações cotidianas, como os trajetos para o trabalho, a maioria dos moradores desconhece, mediante informações em tempo real, os pontos mais críticos da segurança. Sem que
exista uma forma clara e atualizada sobre quais ruas e/ou bairros apresentam riscos maiores,
acabam, involuntariamente, se colocando em situações de risco. Essa ausência de informação
favorece uma maior vulnerabilidade e uma maior sensação de insegurança, gerando um círculo
no qual a própria comunidade vai se sentindo acuada e receosa em relação ao seu território.
Esse cenário é agravado pela ausência de um sistema abrangente de vigilância, especialmente nas áreas periféricas, o que intensifica a sensação de insegurança, dado que a
cobertura de câmeras de monitoramento é escassa. Um exemplo é o caso de roubos em ruas
desprovidas de monitoramento, sem registros visuais que facilitem a identificação dos responsáveis. Frequentemente, esses incidentes acabam no campo da impunidade, perpetuando o
sentimento de insegurança entre os moradores. Essa realidade reforça a urgência na implementação de soluções eficazes que respondam a essas necessidades (MIYAZAKI, 2024).
O desenvolvimento de tecnologias para a circulação de informações de segurança em
tempo real, pode transformar a experiência da vida e locomoção nas cidades. A criação de
ferramentas intuitivas de geolocalização e de comunicação instantânea, por exemplo, poderia funcionar como uma rede protetora, por onde as pessoas normatizariam e compartilhariam
informações sobre as áreas com risco. Com uma plataforma tecnológica acessível, as comuni-

8

dades ganhariam uma maneira mais imediata de observar seu meio e agir colaborativamente
pela segurança, isto é, proporcionaria uma organização espontânea.
A implementação de tal solução funcionaria como uma aliada preventiva, onde a intensificação da vigilância e da organização do bairro não apenas aumentaria a sensação de
segurança, mas, sobretudo, ajudaria desestimular atividades delituosas, promovendo, assim,
o sentimento de união dos moradores. Dessa forma, a tecnologia se apresentaria como uma
conexão essencial entre a necessidade de segurança e a vontade de uma convivência mais
tranquila e confiante.

1.1

Justificativa
Em um momento em que os perigos estão sempre presentes e a vulnerabilidade é sen-

tida em toda parte, a necessidade de refletir sobre maneiras de tornar as regiões mais seguras
transforma-se em um desafio de emergência. Diariamente, os cidadãos modificam seus comportamentos e evitam alguns lugares, mas a falta de informação precisa sobre os riscos reais
diminui a atos de intuição. Em vez de gerar uma segurança edificadora, eles concedem acesso
a um sentimento de incerteza, mantendo o público em uma posição defensiva, criando barreiras
para o comércio local, que desempenha um papel crítico em um clima de confiança.
É nesse contexto que aparece a necessidade de uma solução prática e simples, assegurando que as populações possam obter dados confiáveis sobre a segurança no seu entorno
e, com isto, tornar o cotidiano mais seguro e menos sujeito a imprevistos.
A possibilidade de colaborar organizada por intermédio de uma plataforma disponível
não só permitiria dar maior segurança para quem mora e trabalha nessas regiões como também
atuaria como uma barreira natural contra crimes. Bairros que realizam vigilância e comunicação
estruturada geralmente inibem os ilícitos, uma vez que o criminoso é dissuadido pela ideia de
que suas ações podem ser observadas e denunciadas facilmente. Assim, a tecnologia não é
apenas um instrumento para fomentar a segurança, mas sim uma base para construir os ambientes urbanos onde proteção e qualidade de vida são concomitantes, prestando atendimento
para o desenvolvimento de comunidades mais coesas e resilientes.

1.2

Objetivos
Nesta seção serão apresentados o objetivo geral e objetivos específicos do presente

trabalho.

9

1.2.1

Objetivo geral
Desenvolver um aplicativo nomeado como BairroForte para permitir a troca de informa-

ções ajudando na segurança local e comercial a partir da colaboração entre comerciantes e
moradores, permitindo a troca de informações em tempo real sobre incidentes locais e promovendo ações de prevenção contra a criminalidade.

1.2.2

Objetivos específicos
• Desenvolver uma plataforma que utilize geolocalização para monitoramento de ocorrências de segurança.
• Implementar funcionalidades de envio e recebimento de alertas em tempo real para
incidentes promovendo a integração entre moradores e comerciantes.
• Desenvolver funcionalidades que permita aos usuários, com o devido consentimento,
registrar e compartilhar informações como câmeras de segurança, compartilhando a
localização de câmeras.
• Desenvolver um sistema de notificações personalizáveis, mantendo a segurança dos
dados dos usuários e a comunicação de informações pertinentes e customizadas a
cada um deles.
• Implementar a configuração de informações no aplicativo mantendo a segurança e
integridade dos usuários.

1.3

Organização do trabalho
O restante do trabalho está dividido em cinco capítulos. O Capítulo 2 apresenta e des-

taca toda a base tecnológica utilizada para o desenvolvimento do sistema. Em seguida, o Capítulo 3 apresenta uma análise de aplicativos semelhantes existentes no mercado, destacando
suas funcionalidades e limitações. No Capítulo 4 são detalhados os materiais e métodos adotados para o desenvolvimento do projeto, com base no referencial teórico previamente abordado.
O Capítulo 5 define o escopo do sistema, passando por artefatos e modelagens essenciais ao
seu desenvolvimento. Por fim, o Capítulo 6 sintetiza os principais aspectos propostos ao longo
do trabalho e apresenta sugestões para aprimoramentos futuros.

10

2 REFERENCIAL TEÓRICO
Este capítulo apresenta os conceitos e as tecnologias utilizadas no desenvolvimento
de aplicações modernas, destacando suas funcionalidades e contribuições para garantir segurança, eficiência e comunicação em tempo real. A estrutura de um sistema desse tipo geralmente se organiza em três camadas principais: front-end (interface do usuário), back-end (processamento e lógica do sistema) e banco de dados (armazenamento das informações). Essa
arquitetura permite a escalabilidade, a segurança e a facilidade de manutenção da aplicação.

2.1

Tecnologias do lado cliente
A camada de front-end é a interface do sistema com o usuário, sendo responsável pela

apresentação das informações, pela coleta de dados e pela experiência visual. Essa camada
transforma os dados processados em elementos gráficos interativos, como botões, formulários
e menus, permitindo a navegação intuitiva e eficiente dentro da aplicação.

2.1.1

Flutter
O Flutter é um framework de código aberto desenvolvido pelo Google para a criação de

interfaces visuais interativas e responsivas. Utilizando a linguagem Dart, permite o desenvolvimento de aplicativos nativos para dispositivos móveis, web e desktop a partir de uma única
base de código. Seu conjunto abrangente de widgets e componentes facilita a construção de
interfaces modernas e de alto desempenho, garantindo consistência e fluidez na experiência do
usuário (FLUTTER, 2024).

2.1.2

FlutterFlow
O FlutterFlow é uma plataforma de desenvolvimento visual baseada no Flutter, permi-

tindo a criação de aplicativos móveis sem a necessidade de codificação manual. Sua interface
de arrastar e soltar possibilita a rápida prototipagem e implementação de soluções, além de
oferecer integração com bancos de dados em tempo real e autenticação de usuários. O código gerado pelo FlutterFlow pode ser exportado para personalizações avançadas no Flutter,
tornando-se uma opção flexível para desenvolvedores (FLUTTERFLOW, 2025).

2.2

Tecnologias do lado servidor
O back-end é responsável pelo processamento das informações e pela implementação

das regras de negócio da aplicação. Ele recebe as requisições do front-end, interage com o

11

banco de dados e retorna as respostas adequadas ao usuário, garantindo que as operações
sejam realizadas de forma segura, eficiente e organizada.

2.2.1

NodeJS e NestJS
Node.js é um ambiente de execução que permite a execução de código JavaScript no

servidor. Com seu modelo de entrada/saída assíncrono e orientado a eventos, é altamente
eficiente para lidar com múltiplas requisições simultâneas. É amplamente utilizado no desenvolvimento de servidores, APIs e aplicações web escaláveis (NODEJS, 2024) NestJS é um
framework baseado em Node.js que utiliza TypeScript para estruturar aplicações de back-end
de maneira modular e escalável. Ele incorpora princípios da programação orientada a objetos,
funcional e reativa, tornando o desenvolvimento de APIs e microsserviços mais organizado e
manutenível (NESTJS, 2024).

2.2.2

Firebase Cloud Messaging (FCM)
O Firebase Cloud Messaging (FCM) é um serviço do Firebase que permite o envio de

mensagens e notificações push para aplicativos Android, iOS e web de maneira eficiente e
escalável. Ele possibilita a comunicação entre servidores e dispositivos, garantindo a entrega
de mensagens em tempo real ou com agendamento.
O FCM suporta notificações tanto direcionadas a usuários específicos quanto em larga
escala, utilizando tópicos, grupos de dispositivos ou segmentação avançada com base em dados analíticos. Além disso, integra-se facilmente com outros serviços do Firebase, como o Firebase Analytics, permitindo personalizar e otimizar o engajamento dos usuários. Com suporte a
mensagens prioritárias e envio baseado em condições de rede, o FCM é uma solução robusta
para manter os usuários informados e engajados em tempo real(GOOGLE, 2025).

2.2.3

Docker
O Docker é uma tecnologia de containerização que possibilita embalar uma aplicação e

as suas dependências, em um ambiente isolado conforme apresentado na Figura(1), assegurando que o software opere da mesma forma em qualquer infraestrutura. A tecnologia se utiliza
da criação de contêineres que são unidades leves e portáveis, propiciando uma carga maior
de eficiência no desenvolvimento, teste e entrega do aplicativo. Com Docker é possível executar múltiplas instâncias de um sistema, sem conflitos, entre as dependências. Dessa forma, a
gestão das aplicações torna-se mais ágil e segura.(DOCKER, 2025)

12

Figura 1 – Funcionamento do docker
Fonte: (GULIYEVA, 2023).

2.2.4

MySQL
MySQL caracteriza-se como um Sistema de Gerenciamento de Banco de Dados(Data

Base Management System) (SGBD) relacional de código aberto que é utilizado extensivamente para o armazenamento, organização e gerenciamento de grandes volumes de dados.
Esse SGBD utiliza a linguagem de manipulação e consulta de dados Structured Query Language(Linguagem de consulta estruturada) (SQL) sendo muito conhecido por sua confiabilidade, seu alto desempenho e sua escalabilidade. Ele é utilizado extensivamente no ambiente
das aplicações Web, nos sistemas empresariais e nos serviços de nuvem devidos à sua compatibilidade com diversas linguagens de programação e a facilidade de integração que estas
diferentes linguagens proporcionam (ORACLE, 2025).

2.3

Processo de desenvolvimento
O desenvolvimento de software envolve diversas etapas, desde a concepção da ideia até

a entrega do produto final. Para garantir um fluxo de trabalho eficiente, são adotadas metodologias e práticas que promovem a organização, o acompanhamento do progresso e a colaboração
entre os membros da equipe.

2.3.1

Metodologia ágil Scrum
O Scrum é um framework ágil de gerenciamento de projetos destinado a atingir a entrega

incremental e iterativa de produtos conforme ilustrado na Figura(3), dividindo o desenvolvimento
em ciclos curtos denominados Sprints, de 2 a 4 semanas. Assim, permite que a equipe possa

13

se adaptar rapidamente a mudanças e melhorar continuamente o produto. O Scrum descreve
os papéis essenciais, consistindo no Product Owner, que é o responsável por definir as prioridades, no Scrum Master, que atua como facilitador, garantindo a aplicação eficaz da metodologia,
e por fim, o Time de Desenvolvimento, que é o encarregado por implementar as funcionalidades previstas. Esse framework fomenta colaboração, transparência e flexibilidade para garantir
entregas frequentes e de alta qualidade (SCRUMGUIDES, 2025).

Figura 2 – Dinâmica do método Scrum.
Fonte: (EDUCAçãO, 2024).

2.3.2

Kanban
Kanban é uma abordagem visual para gerenciamento de fluxo de trabalho, originada no

Sistema Toyota de Produção. Ele utiliza um quadro dividido em colunas, representando diferentes fases do processo, como Fazer, Fazendo e Feito.
Os cartões visuais movidos entre as colunas permitem um acompanhamento claro das
tarefas em andamento, facilitando a identificação de gargalos e a otimização da produtividade.
Devido à sua flexibilidade, o Kanban pode ser aplicado em diferentes contextos, incluindo desenvolvimento de software, gestão de projetos e organização pessoal.

14

Figura 3 – Quadro kanban simples.
Fonte: (DONTUS, 2025).

2.4

Ferramentas de desenvolvimento
A escolha de ferramentas adequadas é fundamental para aumentar a produtividade e

garantir a qualidade no desenvolvimento de software. Essas ferramentas automatizam processos, organizam o código e facilitam a colaboração entre os membros da equipe.

2.4.1

Git e GitHub
O Git é um sistema de versionamento de código amplamente utilizado por desenvolve-

dores para gerenciar projetos de software de forma eficiente. Sua principal característica é o
modelo distribuído, permitindo que cada colaborador tenha uma cópia completa do repositório,
garantindo autonomia no desenvolvimento e maior segurança dos dados. Além disso, o Git possibilita a criação de ramificações (branches), permitindo que diferentes funcionalidades sejam
desenvolvidas separadamente e, posteriormente, integradas ao código principal (GIT, 2025).
Dentre os principais benefícios do Git, destacam-se:
• Histórico completo: Todas as alterações feitas no código são armazenadas, possibilitando que os desenvolvedores acompanhem e revertam mudanças quando necessário.
• Flexibilidade no desenvolvimento: O sistema de ramificações permite testar e desenvolver novas funcionalidades sem comprometer a estabilidade do projeto.
• Trabalho colaborativo: Com suporte a múltiplos contribuidores, permite que equipes
trabalhem simultaneamente sem conflitos.
Complementando o uso do Git, o GitHub é uma plataforma online que facilita o armazenamento e a colaboração em projetos versionados. Ele fornece recursos para compartilhamento
de código, revisão de alterações, rastreamento de problemas e automação de processos de
desenvolvimento. Uma das ferramentas mais relevantes do GitHub é o GitHub Actions, que per-

15

mite a automação de testes e implantações, otimizando o fluxo de trabalho de desenvolvimento
contínuo (GITHUB, 2024).
O uso combinado do Git e do GitHub possibilita um desenvolvimento mais organizado,
seguro e eficiente, sendo uma escolha essencial para equipes que buscam qualidade e controle
no gerenciamento de software.

2.4.2

GitHub Projects
O GitHub Projects é uma ferramenta integrada ao GitHub, que realiza o gerenciamento

de projetos de forma flexível e colaborativa. A Figura(4) apresenta o visual desta ferramenta.
Basicamente, a ferramenta combina funcionalidades de quadros kanban, listas de tarefas e
automações para acompanhar o progresso do desenvolvimento de software. Ao contrário das
outras ferramentas de gerenciamento, o GitHub Projects é fortemente integrado aos repositórios, o que possibilita vincular issues, pull requests e commits ao planejamento das tarefas e à
execução do trabalho(GITHUB, 2025).

Figura 4 – GitHub projects.
Fonte: Autoria própria.

16

3 TRABALHOS RELACIONADOS
Atualmente, existem diversos sistemas e aplicativos que têm como objetivo integrar a
vizinhança, promovendo a troca de informações e a colaboração entre moradores. Esses serviços, que emergem da necessidade de segurança e interação social, aproveitam a tecnologia
para fortalecer os laços comunitários e criar ambientes mais seguros

3.1

Family360
O Family360 se apresenta como uma excelente escolha para aqueles que desejam mo-

nitorar a sua família e garantir maior segurança. Ele inclui muitas funcionalidades voltadas para
monitorar em tempo real onde estão todos os integrantes da família (Figura 5a). Um dos recursos mais interessantes do Family360 é o "Watch Over Me". Ele oferece a possibilidade de se
pedir para alguém ficar vigiando você, enquanto você realiza um trajeto considerado arriscado,
por exemplo, voltando para casa à noite. Isso gera uma sensação a mais de estar protegido
para os dois lados, tanto para quem está sendo monitorado, quanto para o "vigia" (FAMILY360,
2024).
Outra funcionalidade nos casos de emergência é o envio de alertas por e-mail, acionando o botão Send Emergency Alert (enviar alerta de emergência), em vez de somente notificar os familiares do circulo, um e-mail com a localização exata da pessoa em emergência
será enviado. Isso que garante que o alerta será recebido, mesmo se alguém estiver com as
notificações desligados ou sem acesso ao celular no momento como na Figura 5b.

17

(a) Visualização do Círculo Familiar na Interface do Family360

(b) Notificação de Emergência
no Family360

Figura 5 – Family360

18

3.2

Find My Kids
Outro aplicativo bastante utilizado para o monitoramento familiar é o Find My Kids, de-

senvolvido especificamente para pais que desejam saber em tempo real a localização de seus
filhos (Figura 6a). O app possui ainda várias funcionalidades interessantes para resguardar os
pequenos (Figura 6b). Como o alerta de localização e o registro de movimentação. O "Escute o
que está acontecendo" é um recurso bem interessante do Find My Kids, com o qual é possível escutar o som do ambiente, nas proximidades do celular do filho. Esse recurso pode auxiliar
muito os pais a detectar rapidamente se houver algum problema, se o filho estiver correndo risco
por exemplo. Outra característica legal é a possibilidade de criar zonas seguras, como a escola
e/ou a casa e receber notificações quando a criança entra ou sai dessas zonas (FINDMYKIDS,
2024).

(a) Tela de Localização em
Tempo Real no Aplicativo
Find My Kids

(b) Tela de Informações e Atividades do Filho no Aplicativo
Find My Kids

Figura 6 – Find My Kids

19

3.3

Life360
O Life360 é um aplicativo de rastreamento de celulares com mais de 70 milhões de

usuários (LIFE360, 2024), amplamente utilizado para monitorar a localização de filhos e parentes. Embora o rastreamento em tempo real seja seu principal objetivo, o aplicativo oferece
diversas funcionalidades adicionais, como a visualização do nível de bateria e a possibilidade
de enviar alertas para informar quando um membro da família chega a um local específico, tal
como ilustrado na Figura 7a (UOL, 2023). Outro recurso interessante é o sistema de detecção
de colisão, que emite alertas em caso de paradas bruscas, proporcionando maior segurança
durante o acompanhamento de trajetos, conforme a Figura 7b.

(a) Tela Inicial de Monitoramento Familiar no Aplicativo
Life360

(b) Notificação de Colisão no
Aplicativo Life360

Figura 7 – Family360

3.4

Considerações
Os aplicativos analisados, como Family360, Find My Kids e Life360, oferecem diversas

funcionalidades focadas na segurança e no bem-estar familiar, como rastreamento em tempo

20

real, alertas de emergência e até detecção de colisões. Esses recursos são eficazes para o monitoramento familiar, mas apresentam limitações quando pensamos em uma abordagem mais
ampla e comunitária, que envolva não só as famílias, mas também comerciantes e moradores
em geral.
O BairroForte surge justamente para preencher essa lacuna, com uma proposta que vai
além do monitoramento individual. O objetivo é criar uma solução colaborativa de segurança
comunitária, permitindo que moradores e comerciantes compartilhem informações em tempo
real sobre incidentes, ajudando a promover um ambiente mais seguro para todos.
O estudo dos aplicativos existentes foi fundamental para identificar funcionalidades essenciais, como geolocalização e alertas, que serão adaptadas e ampliadas para uma abordagem mais abrangente de segurança comunitária no BairroForte. Assim, essa análise não só
serviu como ponto de partida para o desenvolvimento do projeto, mas também ajudou a identificar onde o BairroForte pode inovar e trazer benefícios reais para a comunidade.

21

4 MATERIAIS E MÉTODOS
No desenvolvimento deste projeto, a metodologia Scrum será adaptada para atender às
necessidades específicas do trabalho, garantindo um fluxo de trabalho organizado e eficiente.
Os papéis dentro da metodologia serão desempenhados de maneira estratégica, visando otimizar a comunicação e a entrega contínua de funcionalidades. O professor orientador assumirá
as funções de Product Owner e Scrum Master. Como Product Owner, ele será responsável por
definir e priorizar os requisitos do projeto, além de fornecer feedbacks constantes para garantir
que o produto final esteja alinhado com os objetivos estabelecidos. Como Scrum Master, ele auxiliará na remoção de impedimentos, oferecendo suporte ao desenvolvimento e garantindo que
a metodologia Scrum seja corretamente aplicada. O desenvolvedor, por sua vez, será responsável por implementar todas as funcionalidades do sistema conforme as orientações e prioridades
definidas. Ele organizará suas atividades em sprints quinzenais, assegurando que ao final de
cada ciclo seja entregue um incremento funcional do sistema.
Cada Sprint terá duração de duas semanas, priorizando a entrega de valor incremental
com funcionalidades implementadas conforme o feedback contínuo do orientador. No início de
cada Sprint, será realizado um planejamento detalhado para definir as funcionalidades a serem
desenvolvidas, revisar pendências anteriores e estabelecer objetivos estratégicos para o ciclo.
Durante a Sprint, o orientador fornecerá feedback contínuo sobre as implementações, sugerindo
ajustes e refinamentos conforme necessário, garantindo que os resultados estejam alinhados às
expectativas do projeto. Ao final de cada Sprint, será conduzida uma retrospectiva para avaliar
dificuldades, identificar melhorias e analisar os sucessos alcançados. Esse processo permitirá
ajustes contínuos para otimizar o fluxo de trabalho e aprimorar a qualidade do produto final.
Serão utilizados diferentes ambientes para gerenciamento do projeto. O ambiente de desenvolvimento será destinado à implementação, permitindo que o desenvolvedor faça ajustes,
adicione funcionalidades e corrija erros. Já o ambiente de testes servirá para validar as funcionalidades antes das entregas quinzenais. Após cada Sprint, o código será migrado para este
ambiente, onde passará por verificações finais para garantir que o sistema esteja livre de erros
críticos e pronto para ser integrado. Esse fluxo estruturado permitirá uma abordagem organizada, garantindo um desenvolvimento iterativo e alinhado com as necessidades do projeto.
Para uma entrega eficiente de notificações o Firebase será integrado ao ambiente de
desenvolvimento desde o início do projeto. O desenvolvedor implementará as funcionalidades
necessárias para configurar o FCM, permitindo o envio de notificações personalizadas aos dispositivos dos usuários. Essas notificações podem incluir alertas de segurança,incidentes e mensagens importantes do sistema, promovendo um canal de comunicação direta entre os usuários
e o aplicativo.

22

5 ANÁLISE E PROJETO DO SISTEMA
Neste capitulo será apresentando a maneira adotada para desenvolver a aplicação móvel, com foco em auxiliar moradores e comerciantes de uma determinada área a monitorar a
segurança local de forma colaborativa. O sistema será projetado para permitir a troca de informações em tempo real sobre incidentes de segurança, incluindo a visualização de ocorrências,
alertas de risco e a criação de corredores seguros com o auxílio de câmeras de vigilância. A
aplicação BairroForte visa promover uma organização comunitária que aumente a sensação de
segurança e ajude a inibir atividades criminosas na vizinhança.

5.1

Escopo do sistema
Para estruturar o desenvolvimento do BairroForte, está sendo adotado o método MoS-

CoW de priorização de funcionalidades, que categoriza os requisitos em quatro grupos: Must
Have (Deve Ter), Should Have (Deveria Ter), Could Have (Poderia Ter) e Won’t Have This Time
(Não Terá Desta Vez) (SEBRAE, 2024). O escopo deste projeto concentra-se na implementação de um Minimum Viable Product(Produto Mínimo Viável) (MVP) além de que para fins de
validação e testes a primeira versão será apenas para Android, contemplando exclusivamente
as funcionalidades Must Have, com o objetivo de atender às necessidades fundamentais de segurança da comunidade. Funcionalidades adicionais das demais categorias serão consideradas
em futuras versões do aplicativo, conforme sua evolução e feedback dos usuários.
O BairroForte contará com quatro perfis principais de usuários, cada um com permissões e funcionalidades específicas para proporcionar uma experiência otimizada e eficaz de
monitoramento e comunicação de segurança, à saber: morador e comerciante, administrador,
segurança privada e segurança pública.
Mais precisamente, os moradores e comerciantes são os usuários principais do sistema,
que interagem diretamente com as funcionalidades de monitoramento e comunicação de segurança. Esses usuários poderão compartilhar e receber informações sobre ocorrências locais,
ajudando a proteger seus imóveis e estabelecimentos.
O administrador do sistema será responsável pela segurança e organização das informações dentro da plataforma, garantindo que os dados dos usuários e das ocorrências sejam
protegidos e que as funcionalidades estejam disponíveis para os usuários de forma eficiente.
Os profissionais de segurança privada, como vigilantes contratados ou empresas de
segurança, poderão receber alertas específicos e responder a incidentes rapidamente. Esse
perfil visa proporcionar suporte adicional aos moradores e comerciantes, atuando em conjunto
com a comunidade para reduzir riscos. Por fim, mas somente em versões futuras, os agentes
de segurança pública, como policiais e guardas municipais. Estes terão acesso ao aplicativo em
versões futuras. Esse perfil permitirá que as autoridades recebam notificações de incidentes em

23

tempo real e tenham uma visão mais detalhada sobre as áreas de risco, facilitando a tomada de
decisões de segurança pública.
Para complementar a definição do escopo do BairroForte, a Tabela 1 apresenta as histórias do usuário que fazem parte das funcionalidades classificadas como Must Have no método
MoSCoW. Essas histórias representam os principais requisitos do MVP, garantindo que a primeira versão do aplicativo atenda às necessidades essenciais de segurança da comunidade.
ID

Prioridade

Descrição (História do Usuário)

1

Alta

Geolocalização para Monitoramento de Ocorrências – Como morador ou comerciante, quero visualizar o mapa da região com marcações
de incidentes, para evitar áreas de risco e planejar rotas mais seguras.

2

Alta

Envio e Recebimento de Alertas em Tempo Real – Como morador ou
comerciante, quero receber notificações e enviar alertas sobre ocorrências de segurança, para contribuir com a comunidade e estar ciente de
possíveis perigos.

3

Alta

Comunicação Direta com Órgãos de Segurança Pública – Como morador ou comerciante, quero me comunicar diretamente com a polícia
local ou guarda municipal em casos de emergência via meio de comunicação oficial disponibilizado pelas autoridades.

4

Alta

Registro e Compartilhamento de Localização de Câmeras de Segurança – Como morador ou comerciante, quero cadastrar e compartilhar
a localização de câmeras de segurança residenciais ou comerciais na
área, para criar “corredores seguros” e aumentar a vigilância na comunidade.

5

Alta

Alertas para Empresas de Segurança Privada e Vigilantes de Bairro
– Como morador ou comerciante, quero que o aplicativo envie notificações para a empresa de segurança privada ou vigilante do bairro, para
que estes possam monitorar e responder a incidentes em tempo real.

6

Média

Canal para tirar dúvidas e reportar falhas – Como morador ou comerciante, quero um canal para tirar dúvidas relacionadas às funcionalidades e poder reportar possíveis falhas encontradas no aplicativo.

7

Alta

Recebimento de Alertas Prioritários – Como segurança privada,
quero receber notificações de incidentes em minha área de patrulha,
para responder rapidamente a ameaças e proteger os moradores.

8

Alta

Configuração e Monitoramento de API Segura – Como administrador, quero implementar e monitorar uma API segura para gerenciar a
comunicação de dados, protegendo a privacidade e a integridade das
informações dos usuários.

9

Média

Gerenciamento de Notificações Personalizadas – Como administrador, quero configurar as notificações do sistema de forma personalizada, para garantir que os usuários recebam informações relevantes
para suas áreas de atuação e interesse.
Tabela 1 – Historias do usuário

24

5.2

Planejamento da primeira sprint
Por adotar uma metodologia ágil, o desenvolvimento do BairroForte será realizado de

forma incremental, priorizando a entrega contínua de valor. Dessa forma, a primeira sprint foi
definida para iniciar a construção do sistema com um conjunto essencial de funcionalidades.
Nesta sprint, foram selecionadas as histórias do usuário identificadas pelos IDs 1, 2 e 4,
conforme priorização estabelecida pelo método MoSCoW. Essas funcionalidades garantem uma
base sólida para a interação entre os usuários, possibilitando o monitoramento de ocorrências, a
comunicação em tempo real e o compartilhamento de informações relevantes para a segurança
comunitária.

5.3

Prototipação das telas
O planejamento da primeira Sprint do projeto BairroForte tem como foco o desenvolvi-

mento das telas ilustradas na Figura 8c, Figura 8a e Figura 8b, que são essenciais para garantir um fluxo básico de funcionamento do aplicativo. Primeiramente, a Tela do Mapa Interativo
ilustrada na Figura (8c) pode ser considerada a principal do aplicativo. Nela, o usuário pode
visualizar um mapa detalhado da região, com indicadores que representam diferentes eventos
e alertas:
• Os ícones de exclamação indicam alertas de segurança cadastrados pelos usuários.
• Os ícones de câmera simboliza cãmeras de segurança cadastradas pelos usuários.
• A localização do usuário é destacada com um marcador "EU".
• Há botões para acessar câmeras de vigilância, incidentes registrados, perfil do usuário
e o botão de SOS para acesso ao numero da policia local, além de acesso a dúvidas
e relatórios.
Para registrar incidentes, foi prototipada a tela apresentada na Figura 8a, a qual é essencial para o funcionamento do aplicativo no envio e recebimento de alertas em tempo real.
Esta tela possui:
• Um campo para o usuário inserir a categoria que pode ser Roubo, Furto , Vandalismo
ou Outro.
• Um campo para selecionar a localização do incidente.
• Uma opção selecionar a data da ocorrência.
• E a opção do usuário colocar alguma descrição.

25

Para o registro de câmeras, foi prototipada a tela ilustrada na Figura 8b. Essa tela é fundamental para o acompanhamento de áreas com maior cobertura de câmeras. Seus elementos
incluem:
• Um campo para compartilhar a localização da câmera.
• E a opção de adicionar alguma descrição

(a) Tela de registro de incidentes

(b) Tela de registro de câ-(c) Tela do Mapa Interativo
meras
Figura 8 – Iniciais

Essas telas estabelecem a base para o funcionamento inicial do aplicativo, permitindo
que os usuários registrem e consultem informações relevantes para a segurança da vizinhança.
Além das telas contempladas na primeira Sprint, algumas outras foram criadas para
auxiliar na construção do backlog e na visualização mais ampla do produto final. Essas telas
têm como objetivo complementar a experiência do usuário e fornecer funcionalidades adicionais
que aprimoram a usabilidade do BairroForte. Entre as telas adicionais, destacam-se:
• Tela de Notificações Personalizadas (Figura 9a) : Permite que o usuário configure suas
preferências de alertas, ajustando categorias de incidentes, raio de cobertura e horários de recebimento.
• Configuração de privacidade (Figura 9b) : Permite que o usuário ajuste suas preferências de privacidade de acordo com suas necessidades.

26

(a) Notificações personalizadas

(b) Configurações de privacidade

Figura 9 – Configurações

• Tela de Estatísticas e Relatórios (Figura 10a e 10b): Exibe dados analíticos sobre os
incidentes, câmeras, grupos e notificações registradas.

27

(a) Opções de relatórios

(b) Relatório de incidentes

Figura 10 – Estatísticas

• Tela de Suporte e FAQ (Figura 11): Centraliza informações úteis, perguntas frequentes
e um canal para tirar dúvidas sobre o funcionamento do aplicativo.

Figura 11 – Canal de dúvidas

28

5.4

Modelagem do Banco de Dados
A modelagem do banco de dados para o sistema pode ser visualizada na Figura 12,

onde consiste nas seguintes tabelas principais:
• users: tabela que contém todos os usuários do sistema, com suas informações de contato, como nome e e-mail, além de configurações de autenticação, como senha e tipo
de usuário (morador, segurança privada, etc.). Também armazena a localização geográfica do usuário e suas configurações de privacidade, como visibilidade em grupos e
compartilhamento de informações reportadas no mapa.
• notification_settings: tabela que armazena as configurações de notificações de cada
usuário, permitindo personalizar o raio em quilômetros para receber notificações, as
categorias de alertas (roubo, furto, vandalismo, etc.), o período do dia em que notificações podem ser enviadas e se as notificações devem ser limitadas aos grupos aos
quais o usuário pertence.
• incidents: tabela que registra todos os incidentes reportados, incluindo tipo (roubo,
furto, vandalismo, etc.), descrição, localização e status (aberto, em análise ou resolvido). Cada incidente é associado ao usuário que o reportou.
• cameras: tabela que gerencia o cadastro de câmeras de segurança, contendo a localização, área de cobertura e informações sobre o compartilhamento (se a câmera é
pública ou privada).
• security_groups: tabela que armazena os grupos de segurança formados por moradores e comerciantes. Cada grupo tem um nome, um criador e pode ser associado a
diversos usuários.
• user_security_groups: tabela de conexão N para N entre usuários e grupos de segurança. Registra quais usuários fazem parte de quais grupos, além de armazenar a
data de entrada no grupo.
• notifications: tabela que registra todas as notificações enviadas pelo sistema. Contém
o tipo de notificação (geral, geolocalizada ou personalizada), o conteúdo da mensagem
e um indicador de se a notificação é direcionada à segurança privada.
• notification_recipients: tabela de conexão entre notificações e usuários, garantindo
que cada notificação possa ser enviada para múltiplos destinatários. Registra quais
usuários receberam cada notificação e a data em que foi recebida.
• messages: tabela que armazena mensagens trocadas entre usuários, contendo o remetente, destinatário e o conteúdo da mensagem.

29

• permissions: tabela que gerencia as permissões de acesso no sistema. Define os
tipos de permissão (leitura, escrita, gerenciamento) e os usuários associados a cada
uma delas.
• faqs: tabela que armazena as perguntas frequentes e suas respostas. Inclui categorias
(como notificações, segurança e grupos) e um contador de visualizações, permitindo
identificar as perguntas mais acessadas.
• security_assignments: tabela que associa vigilantes ou empresas de segurança a
áreas ou grupos específicos. Permite gerenciar áreas de atuação e enviar notificações
baseadas na localização dos incidentes.

Figura 12 – Arquitetura do Banco de Dados

5.5

Considerações Finais
O corrente capítulo detalhou a estrutura e as diretrizes adotadas para o desenvolvimento

do aplicativo BairroForte, destacando as principais funcionalidades, perfis de usuários e a mo-

30

delagem do sistema. A partir do método MoSCoW, foi possível definir as prioridades para o
MVP, garantindo que os aspectos essenciais da segurança comunitária sejam abordados já na
primeira versão do sistema.
A segmentação dos usuários em diferentes perfis permite um controle mais eficiente das
funcionalidades e promove uma interação direcionada entre moradores, comerciantes, seguranças privados e, futuramente, agentes de segurança pública. A inclusão de um mapa interativo
como elemento central da aplicação reforça o objetivo de facilitar a comunicação e a visualização de ocorrências em tempo real, promovendo maior engajamento da comunidade.
Além disso, o planejamento da primeira Sprint priorizou funcionalidades críticas para o
funcionamento do sistema, como geolocalização, envio e recebimento de alertas e o registro
de câmeras de segurança. Essas funcionalidades são fundamentais para consolidar a base da
plataforma e permitir futuras melhorias e expansões.
Por fim, a modelagem das telas e do banco de dados proporciona uma visão estruturada do funcionamento do aplicativo, garantindo que o desenvolvimento siga uma abordagem
coerente e alinhada com os requisitos estabelecidos. Com essa base sólida, o BairroForte está
preparado para entrar na fase de implementação, onde os conceitos apresentados neste capítulo serão traduzidos em um sistema funcional e acessível para a comunidade.

31

6 CONCLUSÃO
O projeto BairroForte foi idealizado para oferecer uma solução prática, colaborativa e
tecnológica, que promova a união comunitária em prol de um objetivo comum: um ambiente
mais seguro e conectado.
Com funcionalidades como monitoramento de ocorrências em tempo real, notificações
personalizadas e grupos de segurança comunitária, o BairroForte posiciona-se como uma ferramenta inovadora para transformar bairros em redes colaborativas de proteção. A integração
com câmeras de segurança e, futuramente, com órgãos públicos, amplia ainda mais o alcance
e o impacto do sistema.
Por fim, este trabalho destaca a importância da união entre tecnologia e comunidade
para resolver problemas sociais complexos. O BairroForte tem o potencial de se tornar um modelo para outras regiões, contribuindo para cidades mais seguras, conectadas e sustentáveis.

32

REFERÊNCIAS

DOCKER. Develop faster. Run anywhere. 2025. Disponível em: https://www.docker.com/.
Acesso em: 07 fev. 2025.
DONTUS. O que é Kanban e como aplicar em sua clínica! 2025. Disponível em:
https://dontus.com.br/o-que-e-kanban-e-como-aplicar-em-sua-clinica-2/. Acesso em: 07 fev.
2025.
EDUCAçãO, G. Metodologia Scrum: o que é, para que serve e exemplos para aplicar no
seu negócio. 2024. Disponível em: https://g4educacao.com/blog/metodologia-scrum. Acesso
em: 07 fev. 2025.
FAMILY360. FREQUENTLY ASKED QUESTIONS. 2024. Disponível em: https://www.
family360locator.com/faqs. Acesso em: 14 nov. 2024.
FINDMYKIDS. 1 Kids GPS Tracker App. 2024. Disponível em: https://findmykids.org/pt-br/.
Acesso em: 14 nov. 2024.
FLUTTER. Build for any screen. 2024. Disponível em: https://flutter.dev/. Acesso em: 08 nov.
2024.
FLUTTERFLOW, I. A. r. r. Rethink how you build. 2025. Disponível em: https://www.flutterflow.
io/product. Acesso em: 06 jan. 2024.
GIT. About - Branching and Merging. 2025. Disponível em: https://git-scm.com/about/
branching-and-merging. Acesso em: 08 nov. 2024.
GITHUB. Documentação GitHub. 2024. Disponível em: https://docs.github.com/pt. Acesso
em: 08 nov. 2024.
GITHUB. Planning and tracking with Projects. 2025. Disponível em: https://docs.github.com/
en/issues/planning-and-tracking-with-projects. Acesso em: 07 fev. 2025.
GOOGLE. Faça seu app o melhor possível com o Firebase e a IA generativa. 2025.
Disponível em: https://firebase.google.com/?hl=pt-br. Acesso em: 07 fev. 2025.
GULIYEVA, V. Docker. 2023. Disponível em: https://medium.com/@vezife07102002/
docker-ec68f72bccfb. Acesso em: 07 fev. 2025.
IBGE. Pesquisa Nacional por Amostra de Domicílios Contínua. 2021. Instituto Brasileiro
de Geografia e Estatística. Disponível em: https://biblioteca.ibge.gov.br/visualizacao/livros/
liv101984_informativo.pdf. Acesso em: 10 out. 2024.
LIFE360. More wandering, less wondering. 2024. LIFE360. Disponível em: https:
//www.life360.com/intl/location-safety/. Acesso em: 30 out. 2024.
MIYAZAKI, S. Y. M. FATORES FISCAIS E SOCIOECONÔMICOS QUE AFETAM A
CRIMINALIDADE NO BRASIL. 2024. Disponível em: https://www.scielo.br/j/cgpc/a/
rhTv7DbF6qw8ndHZYYYFJ3K/. Acesso em: 12 nov. 2024.
NESTJS. Hello, nest! 2024. Disponível em: https://docs.nestjs.com/. Acesso em: 11 nov. 2024.
NODEJS. Executar a JavaScript em Toda Parte. 2024. Disponível em: https://nodejs.org/pt.
Acesso em: 08 nov. 2024.

33

ORACLE. MySQL and HeatWave Summit. 2025. Disponível em: https://www.mysql.com/.
Acesso em: 07 fev. 2025.
SCRUMGUIDES. What is Scrum? 2025. Disponível em: https://scrumguides.org. Acesso em:
07 fev. 2025.
SEBRAE. O método MoSCoW para definição de prioridades. 2024. Disponível em: https:
//sebrae.com.br/Sebrae/Portal%20Sebrae/Arquivos/ebook_sebrae_metodologia_moscow.pdfl.
Acesso em: 12 nov. 2024.
UOL. App espião ou ajuda com filhos? Como funciona app que rastreia parentes.
2023. Universo Online. Disponível em: https://www.uol.com.br/tilt/noticias/redacao/2023/12/10/
app-life-360-como-funciona-rastrear-familia.htm. Acesso em: 30 out. 2024.

34

APÊNDICE A – Funcionalidades Planejadas para Evolução do Sistema

35

A.1

Funcionalidades Should Have (Deveria Ter)
Essas funcionalidades são importantes para enriquecer a experiência dos usuários, mas

o BairroForte poderá cumprir seu propósito principal sem elas.

Morador / Comerciante
• Mapa de Calor de Criminalidade
Como usuário, quero visualizar um mapa de calor com base em dados de ocorrências
passadas, para identificar áreas com maior incidência de crimes e tomar precauções
ao transitar por essas regiões.
• Feedback da Comunidade para Atualização de Dados
Como usuário, quero poder reportar incidentes ou mudanças nas condições de segurança, para que a plataforma atualize os dados e melhore a precisão dos alertas.

Segurança Privada
• Canal de Comunicação Exclusivo com Moradores
Como segurança privada, quero ter um canal exclusivo para comunicação com moradores e comerciantes, para coordenar ações preventivas de segurança.

Administrador
• Ferramenta de Controle de Acessos
Como administrador, quero gerenciar o acesso dos usuários e monitorar a interação
com as funcionalidades, para garantir que apenas usuários autorizados contribuam
com informações de segurança.

A.2

Funcionalidades Could Have (Poderia Ter)
Essas funcionalidades são desejáveis e podem agregar valor adicional ao aplicativo,

mas não são essenciais para o funcionamento inicial.

Morador / Comerciante
• Histórico de Incidentes Personalizado

36

Como usuário, quero acessar um histórico de incidentes em minha área, para analisar
padrões de segurança e melhorar minha rotina de prevenção
• Criação de Grupos de Comunidade
Como usuário, quero formar grupos de segurança com vizinhos ou colegas comerciantes, para compartilhar informações e alertas de forma privada e colaborativa.

Segurança Privada
• Visualização Avançada de Corredores Seguros
Como segurança privada, quero visualizar áreas com maior cobertura de câmeras de
segurança, para patrulhar mais eficientemente.

Administrador
• Integração com Redes Sociais e Plataformas de Comunicação
Como administrador, quero permitir que alertas e dados de segurança sejam compartilhados em redes sociais, para ampliar a visibilidade e o engajamento da comunidade.

A.3

Funcionalidades Won’t Have This Time (Não Terá Desta Vez)
Essas funcionalidades são relevantes para futuras versões do aplicativo, mas não serão

incluídas na fase inicial de desenvolvimento por questões de tempo e recursos.
• Integração com Sistemas de Segurança Pública com Resposta Automática
A possibilidade de integração com sistemas de segurança pública que permitam uma
resposta automática por parte das autoridades será considerada para versões futuras.

