---
source_pdf: referencias/tcc do primeira versao do emuseu, forma antiga.pdf
extracted_with: pdftotext (UTF-8)
---

UNIVERSIDADE TECNOLÓGICA FEDERAL DO PARANÁ
CURSO DE TECNOLOGIA EM SISTEMAS PARA INTERNET

ALEXANDRE TAKESHI OGASSAHARA GONZAGA

E-MUSEU: UM SISTEMA DE UM MUSEU VIRTUAL DE
INFORMÁTICA

PROJETO DE TRABALHO DE CONCLUSÃO DE CURSO DE GRADUAÇÃO

GUARAPUAVA
2022

ALEXANDRE TAKESHI OGASSAHARA GONZAGA

E-MUSEU: UM SISTEMA DE UM MUSEU VIRTUAL DE
INFORMÁTICA

Monografia de Trabalho de Conclusão de Curso de graduação,
apresentado à disciplina de Trabalho de Conclusão de Curso
2, do Curso Superior de Tecnologia em Sistemas para Internet
– TSI – da Universidade Tecnológica Federal do Paraná –
UTFPR – Câmpus Guarapuava, como requisito parcial para
obtenção do tı́tulo de Tecnólogo em Sistemas para Internet.
Orientador:

Sediane Carmem Lunardi Hernandes
Universidade Tecnológica Federal do Paraná

Coorientador: Angelita Maria De Ré
Universidade Estadual do Centro Oeste

GUARAPUAVA
2022

4.0 Internacional

Esta licença permite remixe, adaptação e criação a partir do trabalho, mesmo
para fins comerciais, desde que sejam atribuı́dos créditos ao(s) autor(es) e
que licenciem as novas criações sob termos idênticos. Conteúdos elaborados
por terceiros, citados e referenciados nesta obra não são cobertos pela licença.

RESUMO

GONZAGA, Alexandre. E-MUSEU: UM SISTEMA DE UM MUSEU VIRTUAL DE INFORMÁTICA. 2022. 19 f. Projeto de Trabalho de Conclusão de Curso de graduação – Curso de
Tecnologia em Sistemas para Internet, Universidade Tecnológica Federal do Paraná. Guarapuava,
2022.
O cenário de museus virtuais brasileiros ainda é bastante tı́mido, especialmente na área de
informática. A Universidade Tecnológica Federal do Paraná (UTFPR) e a Universidade Estadual
do Centro-Oeste (UNICENTRO) possuem projetos de extensão ligados ao lixo eletrônico com
muitas peças de informática que podem ser catalogadas para a criação de um museu virtual.
Assim, a proposta desse trabalho é enriquecer o cenário nacional de museus virtuais com um
site de um museu virtual de informática, tornando prático e acessı́vel informações a todas as
pessoas que quiserem conhecer um pouco mais sobre a história de computadores, peças e itens
de informática. O museu virtual de informática, o E-museu, a ser desenvolvido apresentará uma
interface simples, amigável e intuitiva com explicações e curiosidades relevantes para instigar e
alimentar a curiosidade daqueles que visitarem o E-museu. Para isso, será utilizada uma metodologia própria de desenvolvimento. Com o desenvolvimento de um museu virtual voltado para
a área de informática os interesses histórico, cultural e tecnológico da sociedade são preservados.
Palavras-chave: Museu Virtual. Museu Virtual de Informática. História de computadores.
Tecnologia da Informação

LISTA DE FIGURAS

Figura 1 – Museu virtual da Coopermiti. . . . . . . . . . . . . . . . . . . . . . . . . 6
Figura 2 – Museu virtual da Universidade Estadual de Maringá. . . . . . . . . . . . . 6
Figura 3 – Museu virtual do Museu Nacional da Computação do Reino Unido. . . . . 7
Figura 4 – Metodologia adotada para o trabalho. . . . . . . . . . . . . . . . . . . . . 9
Figura 5 – Modelagem do banco de dados do sistema E-museu com base no trabalho
de Galvão e Bernardes (2011). . . . . . . . . . . . . . . . . . . . . . . . . 13
Figura 6 – Tela inicial do sistema. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
Figura 7 – Tela que apresenta um pouco sobre as entidades envolvidas na criação do
sistema. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
Figura 8 – Tela que explica como o usuário pode contribuir com o museu virtual. . . . 15
Figura 9 – Tela onde se disponibiliza o formulário de cadastro de novos itens ao sistema. 15
Figura 10 – Tela onde se apresenta a linha do tempo de determinada categoria. . . . . 16
Figura 11 – Tela em que se visualiza os detalhes de um aparelho especifico. . . . . . . 16

LISTA DE TABELAS

Tabela 1 – Requisitos Funcionais. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
Tabela 2 – Requisitos Não Funcionais. . . . . . . . . . . . . . . . . . . . . . . . . . 12

LISTA DE ABREVIATURAS E SIGLAS

NASA

National Aeronautics and Space Administration

UTFPR

Universidade Tecnológica Federal do Paraná

UNICENTRO

Universidade Estadual do Centro-Oeste

DIN

Departamento de Informática

UEM

Universidade Estadual de Maringá

HTML

HyperText Markup Language

PHP

Hypertext Preprocessor

CSS

Cascading Style Sheets

SQL

Structured Query Language

SUMÁRIO

1 – INTRODUÇÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
1.1 Objetivos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
1.1.1 Objetivo geral . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
1.1.2 Objetivos especı́ficos . . . . . . . . . . . . . . . . . . . . . . . . . .
1.2 Justificativa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
1.3 Organização do trabalho . . . . . . . . . . . . . . . . . . . . . . . . . . . .

1
2
2
2
2
3

2 – REVISÃO DE LITERATURA . . . . . . . . . . . . . . . . . . . . . . . . .
2.1 Museu Virtual . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.2 Trabalhos Relacionados a Museus virtuais . . . . . . . . . . . . . . . . . . .

4
4
5

3 – METODOLOGIA . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

9

4 – PROJETO DO SISTEMA . . . . . . . . . . . . . . . . . . . . . . . . . .
4.1 Arquitetura do sistema . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
4.2 Requisitos do sistema . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
4.3 Modelagem do banco de dados . . . . . . . . . . . . . . . . . . . . . . . .
4.4 Apresentação do sistema . . . . . . . . . . . . . . . . . . . . . . . . . . . .

10
10
10
12
13

5 – CONSIDERAÇÕES FINAIS . . . . . . . . . . . . . . . . . . . . . . . . .

17

Referências . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

18

1

1 INTRODUÇÃO

Desde muito tempo atrás, o homem, por ser curioso e ter interesse no passado,
coleciona objetos que fazem parte da cultura e do passado de um povo. Muitas vezes, esses
objetos não possuem valor monetário, mas um valor histórico imensurável (BAUER, 2022).
Por conta disso, foram criados os museus, locais sem fins lucrativos que tem como objetivo
apresentar, toda ou em partes, a história e a cultura de um povo. Por exemplo, o Museu
Britânico1 , um dos maiores museus do mundo, tem como um dos seus artigos a Pedra de
Roseta, um item muito importante para a história da civilização egı́pcia, que já foi uma das
maiores do mundo.
Um museu não precisa ser um local fı́sico, pode ser criado no mundo digital. Isso é
conveniente, pois a Internet está acessı́vel a uma grande parte da população (SILVA, 2022).
Com isso, facilita a visitação de pessoas que, talvez, não teriam acesso se o museu fosse fı́sico.
O museu do Louvre2 , o maior museu de arte do mundo, disponibiliza a visitação de quatro
galerias de arte, através da Internet, com muitas informações adicionais nas obras. A NASA3
também possui algo similar em que o usuário pode se locomover virtualmente pelos seus centros
de pesquisa, analisar objetos e ferramentas, além de contar com textos informativos sobre cada
detalhe.
O objetivo principal de aprender sobre o passado é compreender o presente, tanto em
questões culturais como também em questões tecnológicas, de forma a evitar erros cometidos.
Os museus de informática existem para servir a esse mesmo propósito, mostrar para as pessoas
o passado dos computadores, ensinar e registrar tudo o que foi criado de mais marcante até o
momento atual (VOLTOLINI, 2015).
A Universidade Tecnológica Federal do Paraná (UTFPR) e a Universidade Estadual
do Centro-Oeste (UNICENTRO) possuem projetos ligados ao lixo eletrônico. A UTFPR possui
o projeto Tecno-Lixo: Oficina do Aprender (HAYNE et al., 2022) e a UNICENTRO o projeto
E-Lixo (Ré; THOMEN, 2021). Os projetos recebem peças de computadores que as pessoas
não utilizam mais. Muitas peças são reaproveitadas ou reutilizadas no projeto e várias outras
são recolhidas pela empresa SUC-Ambiental4 por não possuı́rem mais nenhum uso prático nos
projetos. A empresa, recebendo as peças não utilizadas faz o descarte correto das mesmas. A
SUC-Ambiental possui licença municipal para isso. Contudo, por um lado, tem-se o descarte
correto das peças, mas por outro, a história da peça é perdida; pois, as informações sobre essa
peça ajudariam a contar um pouco da história da informática.
Como base no que foi descrito, seria importante que algo fosse proposto para que a
história de algumas peças de informática não fosse perdida. Nesse sentido, o desenvolvimento
1

https://www.britishmuseum.org/
https://www.louvre.fr/en
3
https://oh.larc.nasa.gov/oh/
4
Comércio de varejo com foco em peças e acessórios de aparelhos eletrônicos.
2

Capı́tulo 1. INTRODUÇÃO

2

de um museu virtual voltado para a área de informática atenderia ao interesse histórico, cultural
e tecnológico da sociedade. Este museu armazenaria os detalhes da aparência, especificações,
usos e outros aspectos das peças, para que sejam preservandas as suas histórias.
1.1 Objetivos
1.1.1 Objetivo geral
Desenvolver um museu virtual de informática que tem como propósito registrar e
apresentar para as pessoas, a história e aparência de computadores, peças de computadores ou
itens de informática que já caı́ram em desuso.
1.1.2 Objetivos especı́ficos
Como objetivos especı́ficos deste trabalho tem-se:
• Implementar um site com uma interface amigável e intuitiva;
• Fazer com que seja possı́vel cadastrar novas peças de computador pelo usuário administrador do sistema;
• Permitir que usuários do site sugiram e ajudem a cadastrar novas peças no sistema;
• Possibilitar que o administrador do sistema analise e aceite, ou não, as sugestões de
novas peças feitas pelos usuários ou adição de curiosidades aos itens já cadastrados;
• Organizar os itens do museu por categoria e também por data;
• Adicionar imagens e detalhes em texto para cada item do museu;
• Criar um mascote que servirá como um assistente virtual;
• Desenvolver um sistema de navegação com um visual que simule uma linha do tempo
para os itens do museu.
1.2 Justificativa
A criação de um museu virtual abre espaço para apresentar a história de itens variados
de informática que foram recebidos pelos projetos E-Lixo (Ré; THOMEN, 2021) e Tecno-Lixo:
Oficina do Aprender (HAYNE et al., 2022). Estes itens, que foram doados por seus antigos
donos, por não terem mais utilidade, poderão ganhar um novo propósito.
Desta forma, é de interesse histórico, social e cultural, a implementação de um museu
virtual voltado para a área de informática, que registre e apresente para as pessoas, a história
e aparência de computadores, peças de computadores ou itens de informática que um dia já
foram utilizados. Também, o impacto que a tecnologia teve em nossa sociedade, facilitando a
execução de tarefas rotineiras no cotidiano das pessoas.

Capı́tulo 1. INTRODUÇÃO

3

1.3 Organização do trabalho
O trabalho é dividido como segue. No Capı́tulo 2 são descritos os conceitos principais
sobre Museus virtuais e os trabalhos relacionados. O Capı́tulo 3 trata dos materiais e métodos
que serão utilizados para o desenvolvimento do E-museu. No Capı́tulo 4 são apresentados
os requisitos do sistema, sua modelagem e o visual do site. Por fim, no Capı́tulo 5 algumas
considerações finais são explanadas.

4

2 REVISÃO DE LITERATURA

Neste capı́tulo serão apresentados alguns conceitos de Museu Virtual e alguns trabalhos
relacionados.
2.1 Museu Virtual
Chegar em um consenso sobre a definição de museu virtual é um assunto ainda
bastante controverso. Diversos amantes e estudiosos de museologia discutem sobre e dão suas
próprias conclusões a respeito. Rosali Henriques fez um estudo e pesquisou sobre a opinião de
dezenas de pessoas envolvidas no âmbito museológico. A autora não concordou com a maioria
das definições dadas pelos pesquisados, pois se apoiavam muito na ideia de que um museu
virtual era apenas um ambiente virtual para se expor o objeto material digitalizado. Após
ponderar sobre, chegou a seguinte conclusão: ”(..) museu virtual é aquele que faz da internet
espaço de interação através de ações museológicas com o seu público” (HENRIQUES, 2018).
Com isso, diz-se que não basta catalogar e listar os itens de um museu com uma
descrição extensa de seu funcionamento. A chave para que um museu possa ser considerado
como tal é de como é apresentada a informação ao público e como é disposta essa informação.
Baseando-se nessas questões, o museu virtual de informática deste projeto, o E-museu, apresentará computadores, peças de computadores ou itens de informática de forma simples ao
usuário, com explicações e curiosidades que realmente sejam relevantes para instigar e alimentar
a curiosidade daqueles que visitarem o Museu.
Em Dutra (2018), Eichler e Pino (2007), Schweibenz (1998) quatro tipos de museus virtuais são apresentados, sendo que ambos possuem caracterı́sticas similares, porém se
diferenciam por quais informações e pelo modo que são apresentadas ao público. São eles:
• Museu Panfleto/Folheto: Tem como princı́pio divulgar o museu, apresentando suas
exposições e artigos que poderão ser visualizados somente no museu fı́sico no qual o
panfleto faz referência.
• Museu de Conteúdo: O conteúdo do museu é apresentado de maneira mais direta e
convida o visitante a explorá-lo de maneira online. Por não ter didática na apresentação
das coleções do museu, esse estilo de museu é mais recomendados aos visitantes que já
possuem um conhecimento prévio sobre o que vão ver.
• Museu Interativo: Apresenta o museu e suas coleções de maneira mais didática, muitas
vezes utilizando uma linguagem que seja eficaz para a idade e para o conhecimento prévio
dos visitantes. Outro ponto interessante é a presença de informações adicionais para os
itens do museu que ajudam a instigar a curiosidade de seus visitantes.
• Museu Virtual: São os museus que possuem informações detalhadas de suas coleções.
Suas informações sao escritas e apresentadas com bastante qualidade, sendo muitas vezes

Capı́tulo 2. REVISÃO DE LITERATURA

5

escritas por profissionais da área. Alguns museus virtuais se baseiam em museus fı́sicos,
e apresentam exposições que possam ter sido descontinuadas no museu fı́sico.
Analisando os tipos de museus é possı́vel chegar a conclusão de que o museu virtual de
informática a ser desenvolvido nesse projeto terá muitas similaridades com o Museu Interativo
e o Museu Virtual. Isso porque o E-museu contemplará a presença de descrições em uma
linguagem mais simples e pensada para ser lida por pessoas de todas as idades e grupos sociais,
informações adicionais para alimentar e instigar a curiosidade dos visitantes, informações
detalhadas e aprofundadas àquelas pessoas mais interessados, além da presença de profissionais
da área da tecnologia administrando as informações que serão inseridas ou retiradas do sistema
do E-museu.
2.2 Trabalhos Relacionados a Museus virtuais
Não existem muitos exemplares brasileiros de museu virtual. Os poucos que existem
estão desatualizados ou de difı́cil acesso, principalmente pela falta de manutenção e de
acompanhamento dos avanços das tecnologias utilizadas para o desenvolvimento de sistemas
para a Internet. Desta forma, para ilustrar este cenário foram selecionados alguns museus
virtuais, como o Museu Virtual da Coopermiti, o Museu Virtual da Universidade Estadual de
Maringá (UEM) e o Museu Nacional da Computação do Reino Unido.
A Coopermiti é uma cooperativa brasileira de triagem de lixo eletrônico sem fins
lucrativos, e através disso também visa realizar outros trabalhos, como: inclusão social e digital,
educação e capacitação. No site da Coopermiti1 é disponibilizada uma variedade de páginas
e uma delas é a página do museu2 . Nessa página, apresentada na Figura 1, é possı́vel ter
acesso a história, caracterı́sticas e, em certas ocasiões, imagens de uma variedade de aparelhos
eletroeletrônicos de diferentes fabricantes. Isso, por meio de uma interface simples, porém
intuitiva e fácil de navegar. A interface é baseada em uma grade de várias imagens, em que
cada imagem representa um item do museu e, com um clique se obtém mais informações sobre
o item em questão. Entretanto, há um problema na apresentação de informações, o que pode
afastar o leitor devido a grande quantidade de informações organizadas de maneira confusa no
detalhamento dos aparelhos.

1
2

https://coopermiti.com.br
https://coopermiti.com.br/museu-menu/

Capı́tulo 2. REVISÃO DE LITERATURA

6

Figura 1 – Museu virtual da Coopermiti.
Outro exemplo de museu virtual é o museu da UEM, o qual é apresentado na Figura
2. No site do Departamento de Informática (DIN)3 da UEM tem-se o acesso ao museu4
em que várias informações sobre o projeto e a área de Tecnologia da Informação (TI) são
disponibilizadas, com destaque ao museu representado por uma linha do tempo. Sua interface é
bem simples e defasada por não ter sido atualizada há bastante tempo, porém é muito rica em
informações, não só de aparelhos eletroeletrônicos, mas também da história da computação.

Figura 2 – Museu virtual da Universidade Estadual de Maringá.
O último exemplo a ser apresentado é o tour virtual 3D oferecido pelo Museu Nacional
3
4

http://ws2.din.uem.br/ museu/
http://ws2.din.uem.br/ museu/virtualhtml/index.htm

Capı́tulo 2. REVISÃO DE LITERATURA

7

da Computação do Reino Unido5 . A Figura 3 apresenta uma das páginas do site desse museu.
O site apresenta, no idioma inglês, informações sobre o museu, como horário de funcionamento
e notı́cias, além da possibilidade de agendamento para visitas presenciais e compras de ingressos
para acesso ao museu fı́sico. O site também oferece um tour virtual6 . Nele é possı́vel se
locomover para pontos especı́ficos do museu e olhar para todas as direções; e, assim analisar
os itens para obter mais informações. O seu funcionamento é bastante similar ao Google
Maps7 (ferramenta da Google de visualização de mapas do planeta Terra) no modo Street
View (recurso do Google Maps em que é possı́vel visualizar a localidade do mapa em vistas
panorâmicas que simulam três dimensões, facilitando o entendimento daquele local).

Figura 3 – Museu virtual do Museu Nacional da Computação do Reino Unido.
Cada um dos três museus apresentados possuem suas particularidades, pontos positivos
e também negativos. Como pontos positivos podemos destacar a interface simples e intuitiva
de se navegar do museu virtual da Coopermite; a abundância de informações sobre a história
da computação e sobre os aparelhos eletroeletrônicos da UEM e a possibilidade de se ter
uma experiência remota bem próxima da que seria presencialmente no Museu Nacional da
Computação. Como pontos negativos podem ser destacados a falta de investimento ou de
atualizações na maneira de apresentar as informações no museu virtual da Coopermite e da
UEM, apesar desses museus estarem bem completos no quesito informação. No site do Museu
Nacional da Informática do Reino Unido, a interface de navegação pelo museu virtual é bastante
poluı́do de informações, e além disso, há também a barreira de linguagem, que por ser um site
para falantes da lı́ngua inglesa, acaba-se afastando alguns visitantes.

5

https://www.tnmoc.org
https://www.tnmoc.org/3d-virtual-tour
7
https://www.google.com.br/maps/
6

Capı́tulo 2. REVISÃO DE LITERATURA

8

Com base nos pontos positivos e negativos destacados anteriormente, pretende-se
criar um sistema de museu virtual onde a apresentação e a navegação seja simples, mais
amigável com o visitante, além da disponibilização de um assistente virtual. Com o assistente
virtual, perguntas básicas serão respondidas e ele servirá como um guia na navegação. Além
disso, o sistema facilitará a criação e adição de novos artigos no museu (aparelhos ou itens de
informática) para o administrador e também para os usuários do site. Isso para que sempre
seja incluı́do conteúdo novo e atualizado.

9

3 METODOLOGIA

A metodologia a ser utilizada para o desenvolvimento do museu virtual foi criada
especificamente para este projeto (Figura 4).

Figura 4 – Metodologia adotada para o trabalho.
De inı́cio serão elaborados os requisitos do sistema, os quais estão relacionados aos
objetivos especı́ficos do projeto. Esses requisitos serão levantados se baseando em outros
museus virtuais já consolidados e nos trabalhos de Eichler e Pino (2007), Galvão e Bernardes
(2011). Após isso, uma reunião de planejamento acontecerá para que os requisitos da fase de
desenvolvimento sejam levantados. Os requisitos desta fase são os objetivos a serem alcançados
no ciclo de desenvolvimento (no caso deste projeto em especı́fico, o perı́odo de desenvolvimento
tem de duas a quatro semanas). Em seguida, tem-se a etapa de desenvolvimento propriamente
dito, onde a programação do sistema acontece, a qual se baseia nos objetivos estabelecidos na
fase anterior. A duração de cada fase de desenvolvimento pode ser de duas a quatro semanas,
isso dependerá da quantidade de melhorias necessárias e também da complexidade das tarefas.
Ao final de cada fase, uma versão do sistema executável estará disponı́vel para que seja testada.
Os testes serão realizados por outras pessoas. Isso para que sejam analisadas possı́veis
melhorias na interface, que serão implementadas de acordo com o retorno dos usuários que
testarão o sistema, os usuários sendo: a orientadora, a coorientadora e outras pessoas que forem
selecionadas e que estejam disponı́veis para essa tarefa. Ao término de ciclo de desenvolvimento,
uma reunião com a orientadora e coorientadora será realizada; e, após cada reunião, um novo
ciclo de desenvolvimento iniciará a partir da etapa de requisitos de desenvolvimento, com os
requisitos para a próxima fase de desenvolvimento atualizados.

10

4 PROJETO DO SISTEMA

Este capı́tulo apresenta, a arquitetura do sistema, os requisitos funcionais e nãofuncionais do sistema do museu virtual de informática, a modelagem do banco de dados do
sistema e o protótipo das telas do site.
4.1 Arquitetura do sistema
O sistema terá uma arquitetura baseada em front-end (o visual e toda a parte em que
o usuário pode interagir com o site) e back-end (onde está o servidor e a maior parte lógica do
site). As linguagens de programação utilizadas serão: Html, CSS e JavaScript no front-end do
site, e PHP e SQL no back-end do site. Será utilizado o framework Laravel para facilitar a
conexão do site com o banco de dados.
4.2 Requisitos do sistema
Os requisitos funcionais de um sistema determinam as funcionalidades e comportamentos que deverão estar presentes na versão final desse mesmo sistema, já os requisitos
não funcionais determinam aspectos como: restrições, segurança, performance e limitações do
sistema a ser desenvolvido. Assim, a seguir são apresentadas duas tabelas com os requisitos do
sistema do museu virtual de informática (E-museu). A Tabela 1 possui os requisitos funcionais
e a Tabela 2 apresenta os requisitos não funcionais do sistema (ROCHA; MAGALHãES, 2019).
Um aspecto muito importante de todo museu é ser autêntico, ter a confiança dos
visitantes de que aquilo que está sendo apresentado é verdadeiro. Com essa questão em
mente, as funcionalidades do sistema foram projetadas com base na pesquisa de Dutra (2018),
nele se estuda e discute como transmitir a sensação de autenticidade do museu virtual ao
visitante através da interface do site. Os elementos destacados como indicadores favoráveis a
autenticidade do sistema por (DUTRA, 2018) são:
• desenhos de vias que conectam as obras numa galeria de arte;
• áudio guia;
• qualidade de imagens;
• visualização de detalhes com nitidez;
• visualização de obras em ângulos e posições diferentes;
• visualização de outras imagens de contextualização da obra;
• contextualização histórica da obra;
• dados do artista junto com a obra.
Com exceção de áudios guia e imagens de contexto de itens do museu, o restante
dos elementos favoráveis estarão presentes no sistema de museu virtual deste projeto. Como
elementos que desfavorecem a autenticidade do sistema, citados também por Dutra (2018)

Capı́tulo 4. PROJETO DO SISTEMA

11

Tabela 1 – Requisitos Funcionais.
Identificador

Detalhes

RF001

O sistema deve listar os aparelhos (equipamentos e itens de informática)
do banco de dados em ordem de criação dos mesmos.
O sistema deve possibilitar a busca e a filtragem de aparelhos.
O sistema deve listar os dados de um aparelho em especı́fico.
O sistema deve apresentar os componentes de um aparelho com um link
de acesso a página própria deles.
O sistema deve apresentar um assistente virtual em todas as suas telas.
O sistema deve disponibilizar opções para interagir com o assistente
virtual.
O sistema deve apresentar tutoriais e explicações referentes a navegação
e funcionalidades do site, se assim for requisitado ao assistente virtual.
O sistema deve apresentar informações extras sobre um aparelho se assim
for requisitado para o assistente virtual.
O sistema deve disponibilizar um formulário para o usuário cadastrar um
aparelho por conta própria.
O sistema, no formulário de cadastro de algum item, irá conferir de
antemão se determinado item já está disponı́vel no banco de dados ou
não, antes que seja enviado para aprovação do administrador.
O administrador deve ter acesso a uma página exclusiva a ele, com o
fornecimento de um usuário e senha corretos. Nela será disponibilizada
uma tabela com os envios de formulários de usuários comuns.
O administrador deve ter a opção de editar e validar envios de formulários
de usuários comuns, para decidir se serão listados no museu virtual ou
não.
O usuário comum deve ter acesso a todas as páginas do museu virtual,
sem necessidade de cadastro, com exceção da página exclusiva ao administrador.
O usuário pode editar aparelhos, e adicionar marcas ao sistema.
O usuário pode visualizar imagens de vários ângulo de um item, além de
aproximar a imagem para mais detalhes.

RF002
RF003
RF004
RF005
RF006
RF007
RF008
RF009
RF010

RF011

RF012

RF013

RF014
RF015

tem-se: anúncios publicitários e salas que existem no museu fı́sico, porém não disponı́veis no
museu virtual. No sistema do E-museu não haverá a presença de anúncios e de salas de um
museu fı́sico porque esse não está presente em ambas as Instituições envolvidas no projeto.
Um dos aspectos principais do sistema é a facilidade de se adicionar itens novos ao
museu, tanto pelo administrador, como também pelos usuários do sistema. Sem a necessidade
de possuirem uma conta no sistema, os usuários do poderão sugerir novos itens para o museu,
fornecendo informações sobre o mesmo, assim como imagens e vı́deos se possı́vel. Cada sugestão
de usuário será analisada pelo administrador do sistema, e ele decidirá se aceita, ou não, a
sugestão de adição do novo item.
O assistente virtual servirá mais como um recurso visual pelo qual os usuários do site
poderão escolher opções variadas como: filtragem de itens, busca de aparelhos especı́ficos no

Capı́tulo 4. PROJETO DO SISTEMA

12

Tabela 2 – Requisitos Não Funcionais.
Identificador

Detalhes

RN001
RN002

O sistema será desenvolvido usando o framework Laravel.
O sistema será desenvolvido utilizando as linguagens PHP, Html, CSS e
JavaScript.
O banco de dados do sistema será desenvolvido utilizando a linguagem
SQL.
O sistema não deve apresentar lentidão em suas listagens e envios de
formulários.
Só deve ser possı́vel acessar a página do administrador com o fornecimento
do nome de usuário e senha corretos.
A interface do sistema deve ser responsiva e dinâmica.
A interface do sistema deve ser simples e fácil de se navegar.
A interface do sistema deve funcionar corretamente em várias dimensões
de telas.

RN003
RN004
RN005
RN006
RN007
RN008

banco de dados, além da descoberta de mais detalhes sobre um determinado item do museu.
O assistente virtual saberá reagir a essas opções com base nas informações do banco de dados.
A base do desenvolvimento dessa interação será o Ajax. Nele é possı́vel fazer requisições ao
servidor, sem que seja recarregada a página da web, tornando essa interação mais dinâmica.
4.3 Modelagem do banco de dados
A organização das tabelas do banco de dados foi projetada com base em um artigo
escrito por Galvão e Bernardes (2011), que apesar de se tratar de um museu virtual da Coleção
Etnográfica Carlos Estevão de Oliveira e não possuir relação direta com o tema do E-museu, os
mesmos princı́pios podem ser aplicados para facilitar a navegação, a disposição das informações,
a interação do usuário com os itens do museu e a facilidade de busca por aparelhos especı́ficos
no sistema.
Dentro deste contexto, a Figura 5 apresenta as tabelas projetadas para o banco de
dados do sistema E-museu. A modelagem do banco de dados foi projetada para ser eficiente e
fácil de ser alterada após a criação das tabelas. Armazenará todas as informações intrı́nsecas
de aparelhos eletrônicos, por isso não terá colunas vazias na inserção de dados. O ponto mais
interessante a ser destacado é a tabela ”extras”. Nela serão armazenadas todas as informações
extras que os aparelhos podem vir a ter ou não. A organização dos aparelhos eletrônicos do
museu por categorias, peso, altura, largura, comprimento, marca, série, modelo, código e data
foi planejado desta forma para facilitar a filtragem das informações a serem apresentadas ao
usuário do museu, visto que a exagerada exposição de informações mais atrapalha do que ajuda
o usuário.
O banco de dados apresentará também uma tabela para contas de administrador e
uma para as mı́dias do site (imagens e vı́deos). Essas tabelas serão geradas através do Laravel,

Capı́tulo 4. PROJETO DO SISTEMA

13

que possui ferramentas próprias para isso.

Figura 5 – Modelagem do banco de dados do sistema E-museu com base no trabalho de Galvão
e Bernardes (2011).

4.4 Apresentação do sistema
O visual do museu virtual foi projetado para que a interface se torne simples, sem
excesso de informações, intuitiva e de fácil interação. Desta forma, permitirá que todo e
qualquer usuário consiga navegar pelas páginas do site com facilidade e ao mesmo tempo
encontrar o que procura.
Praticamente, todas as telas poderão ser acessadas por qualquer usuário sem a
necessidade de um cadastro, com exceção da tela de validação de envios dos usuários. Essa
decisão foi tomada porque a exigência da criação de uma conta de usuário para acesso ao site
poderia afastar potenciais visitantes.
Em todas as telas, a assistente virtual estará presente para fornecer várias informações,
dependendo do contexto e da tela em que o usuário se encontrar. Além disso, perguntas
genéricas poderão ser realizadas pelo usuário e respondidas pela assistente.
A tela inicial do sistema, figura 6, apresenta brevemente o museu virtual, além de dar
direções de como se navegar pelo mesmo. Todas as telas apresentadas apresentam a esquerda
a interface para celular a a direita a interface para páginas web em desktop.

Capı́tulo 4. PROJETO DO SISTEMA

14

Figura 6 – Tela inicial do sistema.

Figura 7 – Tela que apresenta um pouco sobre as entidades envolvidas na criação do sistema.
Na tela representada pela Figura 7, informações sobre as entidades envolvidas na
criação do sistema são apresentadas.
A tela da Figura 8 apresenta como o usuário pode contribuir com o site e a Figura
9 apresenta o formulário para sugestão de aparelhos para o museu. A tela de visualização de
envios de usuários, só pode ser acessada pelo administrador do site, com o usuário e senha
corretos. Nela o administrador poderá modificar e aprovar os envios dos usuários. Esses envios
podem ser de novos itens para o catálogo do museu ou complementos a itens que já estavam
no catálogo. O visual desta tela não foi disponibilizado por não ter necessariamente nenhum
elemento especial, sendo composto apenas por uma tabela, onde será possı́vel aplicar alguns

Capı́tulo 4. PROJETO DO SISTEMA

15

Figura 8 – Tela que explica como o usuário pode contribuir com o museu virtual.

Figura 9 – Tela onde se disponibiliza o formulário de cadastro de novos itens ao sistema.
filtros para facilitar a visualização de elementos especı́ficos, além de botões de validação e
edição dos envios.
A tela mais importante do museu é a tela de exploração, a qual é apresentada na
Figura 10. Nela o usuário poderá navegar por uma linha do tempo (simulando a linhas do
tempo que são vistas em museus fı́sicos, por exemplo) e visualizar imagens, vı́deos, textos
e informações extras pela assistente virtual. Se o visitante desejar, ele pode visualizar mais
detalhes de um item especı́fico do museu (Figura 11).

Capı́tulo 4. PROJETO DO SISTEMA

16

Figura 10 – Tela onde se apresenta a linha do tempo de determinada categoria.

Figura 11 – Tela em que se visualiza os detalhes de um aparelho especifico.
Os visuais das telas para aparelhos móveis também são apresentados em que os
elementos foram reorganizados para facilitar o uso em telas menores e mais estreitas.
Espera-se que o site do sistema do E-museu seja, além de simples, intuitivo e de fácil
navegação, atrativo e que desperte o interesse dos acadêmicos e alunos da região para que
conheçam os cursos das Universidades envolvidas.

17

5 CONSIDERAÇÕES FINAIS

Neste trabalho, propõe-se implementar um museu virtual de informática para apresentar
e resgatar um pouco da história de peças ou itens de informática que já foram utilizados, e
que hoje em dia podem estar caindo no esquecimento. Desta forma, espera-se alcançar os
objetivos propostos seguindo a metodologia de desenvolvimento proposta, bem como as etapas
de planejamento do trabalho. As principais dificuldades previstas na parte de implementação
são a modelagem do banco de dados, devido a quantidade e tipos diferentes de informações
que se tem em cada peça; e, a apresentação dessas informações no site para que apresente um
visual amigável, responsivo e intuitivo.
A execução deste projeto exigirá o conhecimento e a aplicação de vários conceitos e
tecnologias que foram trabalhados durante o curso de Tecnologia em Sistemas para Internet da
Universidade Tecnológica Federal do Paraná (UTFPR) - Campus Guarapuava. Serão colocados
em prática os princı́pios e fundamentos de programação de computadores, design gráfico,
interaçao homem-computador, banco de dados, além de princı́pios de análise e projeto de
software, entre outros. Isso para planejar o visual e o fluxo de funcionamento do sistema, bem
como para que o banco de dados seja o mais eficiente e otimizado possı́vel. As linguagens de
programação, utilizadas durante o curso, como Html, Javascript, PHP, CSS e SQL serão utilizadas no desenvolvimento do sistema do museu virtual chamado de E-museu. A documentação
e o planejamento de como resolver problemas e definir os estágios da execução desse projeto
foram baseados no aprendizado obtido durante o curso.
O site do museu virtual de informática divulgará de forma indireta o curso de Tecnologia
em Sistemas para Internet do Campus Guarapuava e o curso de Ciência da Computação da
UNICENTRO para a comunidade em geral, bem como estimulará outros acadêmicos a se
envolverem nos projetos de extensão relacionados ao trabalho em questão.

18

Referências

BAUER, J. MUSEU, MUSEOLOGIA E MUSEOGRAFIA. 2022. Disponı́vel em: <https:
//www.triscele.com.br/triscele/museu-museologia-e-museografia#:˜:text=Surge%20o%
20Primeiro%20Museu%3A%20a,em%20templos%2C%20santuÃarios%20e%20tumbas.>
,
Acesso em: 3 de outubro de 2022. Citado na página 1.
DUTRA, L. F. GESTÃO DA INFORMAÇÃO E TECNOLOGIAS: DIRETRIZES
PARA PROJETOS DA INTERFACE DE MUSEUS VIRTUAIS NO ÂMBITO DA
AUTENTICIDADE. 2018. Disponı́vel em: <https://repositorio.ufmg.br/bitstream/1843/
ECIP-B88MAM/1/dissertacao de mestrado ppg goc larissa fernandes dutra.pdf>. Acesso em:
26 de Novembro de 2022. Citado 2 vezes nas páginas 4 e 10.
EICHLER, M. L.; PINO, J. C. D. Museus virtuais de ciências: uma revisão e indicações
técnicas para o projeto de exposições virtuais. 2007. Disponı́vel em: <https://seer.ufrgs.
br/index.php/renote/article/view/14377/8274>. Citado 2 vezes nas páginas 4 e 9.
GALVãO, G. K. A.; BERNARDES, D. A. de M. A organização da informação como
instrumento de preservação e acesso ao Museu Virtual da Coleção Etnográfica Carlos
Estevão de Oliveira. 2011. Disponı́vel em: <http://200.156.20.26/index.php/ppgpmus/
article/view/119/170>. Citado 4 vezes nas páginas , 9, 12 e 13.
HAYNE, D. R. et al. Tecno-lixo: Oficina do aprender. XII Seminário de Extensão e Inovação
XXVII Seminário de Iniciação Cientı́fica e Tecnológica da UTFPR, Santa Helena,
2022. Disponı́vel em: <https://www.even3.com.br/anai/seisicite2022/>. Citado 2 vezes nas
páginas 1 e 2.
HENRIQUES, R. Os museus virtuais: conceito e configurações. 2018. Disponı́vel
em: <https://recil.ensinolusofona.pt/bitstream/10437/9299/1/6337-49-19613-1-10-20181218.
pdf>. Acesso em: 26 de Novembro de 2022. Citado na página 4.
ROCHA, R. da S.; MAGALHãES, T. M. de. ENGENHARIA DE REQUISITOS. 2019. Disponı́vel em: <https://www.fsd.edu.br/wp-content/uploads/2019/12/
artigo27-RAFAEL-e-TERESINHA.pdf>. Acesso em: 20 de Novembro de 2022. Citado na
página 10.
Ré, A. M. D.; THOMEN, M. A. F. Cartilha de sugestões para atividades
em oficinas pedagógicas utilizando de informática LIXOELETRÔ. 2021. Disponı́vel em: <https://www3.unicentro.br/decomp/wp-content/uploads/sites/77/2021/09/
CartilhaLixoEletronico.pdf>. Acesso em: 25 de setembro de 2022. Citado 2 vezes nas páginas
1 e 2.
SCHWEIBENZ, W. The “Virtual Museum”1 : New Perspectives For Museums to
Present Objects and Information Using the Internet as a Knowledge Base and
Communication System. 1998. Disponı́vel em: <http://www.informationswissenschaft.org/
wp-content/uploads/isi/isi1998/14 isi-98-dv-schweibenz-saarbruecken.pdf>. Acesso em: 26 de
Novembro de 2022. Citado na página 4.
SILVA,
2021,

H. 81% da
diz
pesquisa;

população brasileira acessou a
TV
supera
computador
como

internet em
meio. 2022.

Referências

19

Disponı́vel
em:
<https://g1.globo.com/tecnologia/noticia/2022/06/21/
81percent-da-populacao-brasileira-acessou-a-internet-em-2021-diz-pesquisa.ghtml>. Acesso
em: 25 de setembro de 2022. Citado na página 1.
VOLTOLINI, R. Museu da Informática é inaugurado em SP; faça agora
um tour online! 2015. Disponı́vel em: <https://www.tecmundo.com.br/brasil/
85078-museu-informatica-inaugurado-sp-faca-tour-online.htm>. Acesso em: 3 de outubro de 2022. Citado na página 1.

