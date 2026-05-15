---
source_pdf: referencias/GP_COINT_2025_1_ADNIR_LUIZ_DE_ANDRADE_JUNIOR_MONOGRAFIA.pdf
extracted_with: pdftotext (UTF-8)
---

UNIVERSIDADE TECNOLÓGICA FEDERAL DO PARANÁ

ADNIR ANDRADE

THEMYS - ASSISTENTE DE RPG DE MESA PARA CAMPANHAS QUE
UTILIZAM O SRD 5.2.1 DO D&D

GUARAPUAVA
2025

ADNIR ANDRADE

THEMYS - ASSISTENTE DE RPG DE MESA PARA CAMPANHAS QUE
UTILIZAM O SRD 5.2.1 DO D&D

Themys - TTRPG Assistant for campaigns using D&D’s SRD 5.2.1

Trabalho de Conclusão de Curso de Graduação
apresentado como requisito para obtenção do
título de Tecnólogo em Tecnologia em Sistemas
para Internet do Curso Superior de Tecnologia
em Sistemas para Internet da Universidade
Tecnológica Federal do Paraná.
Orientador: Prof. Dr. Diego Marczal
Coorientador: Prof. Me. Denis Lucas Silva

GUARAPUAVA
2025

4.0 Internacional

Esta licença permite remixe, adaptação e criação a partir do trabalho, para fins não comerciais, desde que sejam atribuídos créditos ao(s) autor(es). Conteúdos elaborados
por terceiros, citados e referenciados nesta obra não são cobertos pela licença.

ADNIR ANDRADE

THEMYS - ASSISTENTE DE RPG DE MESA PARA CAMPANHAS QUE
UTILIZAM O SRD 5.2.1 DO D&D

Trabalho de Conclusão de Curso de Graduação
apresentado como requisito para obtenção do
título de Tecnólogo em Tecnologia em Sistemas
para Internet do Curso Superior de Tecnologia
em Sistemas para Internet da Universidade
Tecnológica Federal do Paraná.

Data de aprovação: 30/junho/2025

Diego Marczal
Doutor
Universidade Tecnológica Federal do Paraná - Campus Guarapuava

Alessandro Dias Batista
Especialista

Eleandro Maschio
Doutor
Universidade Tecnológica Federal do Paraná - Campus Guarapuava

Renata Luiza Stange
Doutora
Universidade Tecnológica Federal do Paraná - Campus Guarapuava
GUARAPUAVA
2025

Dedico este trabalho a todos que duvidam da
própria capacidade, que acreditam não
aguentar ou que sentem que não são o
suficiente: vocês podem muito mais do que
imaginam.

AGRADECIMENTOS
Muito pensei no que escrever aqui, mas acredito que, se eu colocasse em palavras toda
a imensa gratidão que sinto por todos que me incentivaram e me ajudaram nos últimos anos,
facilmente ultrapassaria o tamanho completo deste trabalho de conclusão. Portanto, tentarei ser
breve.
Agradeço imensamente ao meu orientador, Professor Dr. Diego Marczal. Não apenas
pela sua dedicação, conhecimento e atenção aos detalhes, mas por ter acreditado na minha
ideia e ter me ajudado a transformá-la em realidade — tudo isso enquanto me fazia alcançar
novos níveis de profissionalismo, ainda com espaço para se preocupar com minha saúde e
sanidade. Eu não poderia ter desejado orientador melhor.
Preciso também agradecer à responsável pelo início de toda esta jornada: minha mãe,
Eva Partocki, que me colocou a ideia na cabeça de fazer este curso. Como agradecimento,
aterrorizei ela por três anos seguidos dizendo que trancaria minha matrícula. Obrigado por todas
as conversas, risadas e por escutar meus desabafos. Você foi, de longe, a pessoa que mais
torceu por mim e me apoiou durante esses últimos anos. Quando me faltavam forças, você
estava lá para me emprestá-las. Obrigado por tudo, mãe.
E, por fim, agradeço a todos que fizeram parte desta trajetória, de alguma forma. Ao
André Lauer, Fernando Rocha e todo o pessoal da COGETI e ASCOM, pelo carinho e amizade
durante e após meu estágio; ao Eloi Mamcasz e Josnei Bueno, da Ponto Gestor, por terem
acreditado no meu potencial como desenvolvedor e por terem sido os melhores empregadores
que eu poderia desejar; a todas as meninas do Restaurante Universitário, que sempre fizeram
o melhor para nos ver alimentados e felizes (são muitas para citar, mas adoro cada uma de
vocês) — obrigado pela amizade, pelo cuidado e pelas conversas; ao grupo Paladino Degolado,
ao grupo experimental do Themys, e a todos que me ajudaram a divulgar o sistema e viabilizar
os testes necessários para este trabalho (incluindo, nomeadamente, minha irmã Bruna Andrade
- ela me mata se eu não fizer isto. Obrigado Bruna!).
E, claro, agradeço a todos os professores da UTFPR. Sei que teria desistido do curso se
não fosse pela qualidade do ensino que encontrei aqui. Vocês sempre entregaram muito mais
do que eu poderia imaginar, e cobraram de forma a me forçar a crescer. Obrigado por sempre
aguentarem meus trabalhos absurdamente gigantes — vocês são incríveis!
Mesmo que seu nome não esteja citado diretamente aqui, se você participou da minha
vida acadêmica, saiba que foi importante para mim. Foram anos aprendendo, ensinando ou sonhando juntos. Você fez parte desta conquista — mesmo que tenha entrado tarde em minha
vida, mesmo que tenha saído cedo demais, mesmo que tenha me motivado ou até antagonizado. Somos o conjunto de todas as nossas experiências, e sou grato por ter tido a oportunidade
de experienciar cada uma delas com você. Mesmo que, ao final, “você” se torne apenas uma
palavra anônima em um parágrafo, isso não muda o fato de quem “você” foi na minha vida.

RESUMO

Este trabalho apresenta o desenvolvimento do Themys, um sistema web voltado ao suporte
de campanhas de RPG de mesa baseadas no System Reference Document (SRD) 5.2.1
de Dungeons & Dragons (D&D). O objetivo principal foi oferecer uma ferramenta prática,
pedagógica e fiel às regras oficiais, com foco na criação e gestão de personagens. O processo
de desenvolvimento envolveu desde o levantamento de requisitos, com a participação de
usuários reais, até a implementação de um fluxo completo de criação de personagens. A
avaliação do sistema ocorreu por meio de testes em sessões reais de jogo e coleta de dados
via formulários, gerando métricas qualitativas e quantitativas. Os resultados indicaram que,
mesmo em sua versão inicial, o Themys demonstrou potencial significativo e foi bem recebido
tanto por usuários iniciantes quanto experientes. O sistema foi validado como um Minimum
Viable Product (MVP) funcional e servirá de base para futuras evoluções técnicas e conceituais
no ecossistema digital de apoio ao TTRPG.
Palavras-chave: role-playing game (rpg); jogos; dungeons & dragons; aplicativo web.

ABSTRACT

This work presents the development of Themys, a web-based system designed to support
tabletop RPG campaigns based on the SRD 5.2.1 of D&D. The main objective was to provide
a practical, educational tool that is aligned with the official rules, focusing on character creation
and management. The development process covered the entire cycle, from requirements
gathering, with real user participation, to the implementation of a complete character creation
flow. The system was evaluated through testing in real gameplay sessions and data collection
via forms, resulting in both qualitative and quantitative metrics. The results indicated that, even
in its initial version, Themys demonstrated significant potential and was well received by both
beginner and experienced users. The system was validated as a functional MVP and will serve
as a foundation for future technical and conceptual evolutions in the digital ecosystem of TTRPG
support tools.
Keywords: role-playing game (rpg); games; management; web application.

LISTA DE FIGURAS

Figura 1 – Fluxo de desenvolvimento utilizado durante a produção do sistema . .

26

Figura 2 – Resultado da pergunta “Há quanto tempo você joga RPG de Mesa?” . .

30

Figura 3 – Resultado da pergunta “Qual é o máximo que você estaria disposto a
pagar por mês por determinado aplicativo?” . . . . . . . . . . . . . . .

31

Figura 4 – Resultado da pergunta “Qual é o máximo que você estaria disposto a
pagar por ano por determinado aplicativo? (este valor seria um pacote
anual)”

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

31

Figura 5 – Exemplo de Resposta - Buy a Feature . . . . . . . . . . . . . . . . . . .

35

Figura 6 – Exemplo de Resposta - Buy a Feature . . . . . . . . . . . . . . . . . . .

35

Figura 7 – Features mais votados . . . . . . . . . . . . . . . . . . . . . . . . . . . .

36

Figura 8 – Features escolhidos . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

36

Figura 9 – Tela Inicial

39

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

Figura 10 – Fluxo de Autenticação. Da esquerda para a direita: (A) Tela inicial, (B)
Registro de Conta, (C) Seleção de Função, (D) Edição de Perfil. . . . . .

40

Figura 11 – Fluxo Geral. Da esquerda para a direita: (A) Seleção de Função, (B) Seleção de Campanha, (C) Seleção de Personagem.

. . . . . . . . . . . .

40

Figura 12 – Dashboard, parte 1 e parte 2 . . . . . . . . . . . . . . . . . . . . . . . .

41

Figura 13 – Fluxo do Personagem - Inventário. Da esquerda para a direita: (A) Menu
Lateral, (B) Listagem de Items. . . . . . . . . . . . . . . . . . . . . . . .

42

Figura 14 – Fluxo do Personagem - Diário. Da esquerda para a direita: (A) Menu
Lateral, (B) Listagem de Entradas, (C) Criação de entradas. . . . . . . .

42

Figura 15 – Criação de Personagem - Parte 1. Da esquerda para a direita: (A) Seleção de raça, (B) Seleção de classe, (C) Seleção de Cantrips, (D) Seleção
de Spells. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

43

Figura 16 – Criação de Personagem - Parte 2. Da esquerda para a direita: (A) Seleção de background, (B) Distribuição de Atributos, (C) Seleção de Habilidades. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

43

Figura 17 – Modal Explicativo da feature Nightvision. Da esquerda para a direita: (A)
Seleção de classe, (B) Modal explicativo de ícone. . . . . . . . . . . . .

44

Figura 18 – Modal Explicativo do Cantrip Fire Bolt. Da esquerda para a direita: (A)
Seleção de Cantrip, (B) Modal explicativo de magia. . . . . . . . . . . .
Figura 19 – Modal Explicativo da Skill Deception.

. . . . . . . . . . . . . . . . . . .

Figura 20 – Distribuição das linguagens no repositório segundo o GitHub

45
45

. . . . .

49

Figura 21 – Tela de login, antes e após atualização . . . . . . . . . . . . . . . . . . .

51

Figura 22 – Listagem de campanhas na visão de mestre e modal de criação de nova
campanha . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

52

Figura 23 – Modal para geração de código de convite (Mestre) e Modal para inserção de código de convite (Jogador) . . . . . . . . . . . . . . . . . . . .

53

Figura 24 – Código responsável por gerar identificadores únicos para o sistema de
convite de campanhas . . . . . . . . . . . . . . . . . . . . . . . . . . . .

53

Figura 25 – Componente OptionsGrid exibindo as possíveis opções de Alignments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

56

Figura 26 – Componente adicional exibido apenas para personagens da raça elfo,
referente ao traço Keen Senses . . . . . . . . . . . . . . . . . . . . . . .

57

Figura 27 – Mini-calculadora para distribuição dos bônus de atributos concedidos
pelo Background . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

59

Figura 28 – Tela de distribuição de atributos com os métodos Standard Array (esq.)
e Random Generation (dir.) . . . . . . . . . . . . . . . . . . . . . . . . .
Figura 29 – Trecho da função de cálculo de custo no método Point Cost

61

. . . . . .

62

. . . . . . . .

63

Figura 31 – Função responsável pelo cálculo dos modificadores de atributo . . . .

63

Figura 32 – Função responsável pelo cálculo do bônus de proficiência . . . . . . .

64

Figura 33 – Tela de seleção de Skills seguida da listagem completa de Skills . . . .

65

Figura 30 – Tela de distribuição de atributos com método Point Cost

Figura 34 – Modal de exibição dos detalhes de uma magia, acessível diretamente
na etapa de seleção . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
Figura 35 – Tela de seleção de Cantrips (esq.) e Spells (dir.)

. . . . . . . . . . . . .

66
66

Figura 36 – Encadeamento informativo entre palavras-chave: exibição na ficha, modal explicativo e referências cruzadas . . . . . . . . . . . . . . . . . . .

67

Figura 37 – Exemplo de botão de ajuda no card de Skills e modal explicativo com
links para keywords . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

68

Figura 38 – Cabeçalho de edição exibido na ficha de personagem para o mestre . .

69

Figura 39 – Página de edição de personagem na visão do mestre, com edição livre
de classe e habilidades . . . . . . . . . . . . . . . . . . . . . . . . . . .

69

Figura 40 – Página de edição de magias na visão do mestre, com as magias agrupadas por nível e opção de filtro por classe . . . . . . . . . . . . . . . .

70

Figura 41 – Versão anterior da página inicial do Themys, utilizando imagem gerada
por inteligência artificial . . . . . . . . . . . . . . . . . . . . . . . . . . .

71

Figura 42 – Página inicial atualizada do Themys, sem utilizar nenhum conteúdo gerado por IA . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

71

Figura 43 – Logo do Themys, gerada com auxílio de IA e posteriormente modificada
manualmente . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

72

Figura 44 – Diagrama final do banco de dados do sistema Themys . . . . . . . . . .

73

Figura 45 – Distribuição do nível de familiaridade dos participantes com D&D 5e . .

77

Figura 46 – Intenção dos usuários em incorporar o Themys em campanhas futuras

78

LISTA DE ABREVIATURAS E SIGLAS

Abreviaturas
D&D

Dungeons & Dragons

DM

Dungeon Master

Siglas
MVP

Minimum Viable Product

NPC

Non-playable Character

OGL

Open Game License

PWA

Progressive Web App

RPG

Role-Playing Game

SRD

System Reference Document

TTRPG

Tabletop Role-Playing Game

SUMÁRIO
1

INTRODUÇÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

13

1.1

Objetivos

14

1.1.1

Objetivo geral

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

14

1.1.2

Objetivos específicos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

1.2

Justificativa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

1.3

Estrutura do trabalho . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

16

2

FUNDAMENTOS DE TTRPG . . . . . . . . . . . . . . . . . . . . . . . . .

17

2.1

RPG de Mesa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

17

2.2

Sessões e Campanhas . . . . . . . . . . . . . . . . . . . . . . . . . . . .

17

2.3

System Reference Document . . . . . . . . . . . . . . . . . . . . . . . .

17

2.4

O papel do Jogador . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

18

2.5

O papel do Mestre

18

2.6

Materiais necessários e opcionais

. . . . . . . . . . . . . . . . . . . . .

19

3

THEMYS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

20

3.1

Escopo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

20

3.2

Perspectiva . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

21

3.3

Descrição dos usuários . . . . . . . . . . . . . . . . . . . . . . . . . . .

21

3.3.1

Usuários . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

21

3.3.2

Mestres . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

22

3.3.3

Jogadores . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

22

4

MATERIAIS E MÉTODOS . . . . . . . . . . . . . . . . . . . . . . . . . . .

24

4.1

Materiais . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

24

4.2

Métodos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

4.2.1

Pré-Produção

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

4.2.2

Produção . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

4.2.3

Pós-Produção . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

27

5

PLANEJAMENTO DO PROJETO . . . . . . . . . . . . . . . . . . . . . . .

28

5.1

Grupo Experimental

. . . . . . . . . . . . . . . . . . . . . . . . . . . . .

28

5.2

Levantamento de Requisitos . . . . . . . . . . . . . . . . . . . . . . . . .

28

5.2.1

Elaboração do Formulário . . . . . . . . . . . . . . . . . . . . . . . . . . .

28

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

5.2.2

Resultados Obtidos

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

29

5.3

Priorização de Requisitos . . . . . . . . . . . . . . . . . . . . . . . . . .

32

5.3.1

MoSCoW e Buy a Feature . . . . . . . . . . . . . . . . . . . . . . . . . . .

32

5.3.2

Tempo de Desenvolvimento e Precificação dos Requisitos . . . . . . . . . .

33

5.3.3

Preparo do Material Utilizado . . . . . . . . . . . . . . . . . . . . . . . . .

34

5.3.4

Execução do Buy a Feature . . . . . . . . . . . . . . . . . . . . . . . . . .

34

5.3.5

Resultados Obtidos

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

35

5.4

Histórias de Usuário . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

37

5.5

Protótipo de Telas

38

5.5.1

Área Pública e Conceito Visual

. . . . . . . . . . . . . . . . . . . . . . . .

39

5.5.2

Autenticação . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

39

5.5.3

Visão do Jogador . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

40

5.5.4

Visão do Personagem . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

41

5.5.5

Criação de Personagem . . . . . . . . . . . . . . . . . . . . . . . . . . . .

43

5.5.6

Demais telas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

46

6

DESENVOLVIMENTO . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

47

6.1

Visão Geral do Processo de Desenvolvimento . . . . . . . . . . . . . . .

47

6.2

Organização das Tarefas . . . . . . . . . . . . . . . . . . . . . . . . . . .

47

6.2.1

Fluxo de Tarefas no ClickUp . . . . . . . . . . . . . . . . . . . . . . . . . .

47

6.2.2

Divisão entre Épicos e Tarefas Isoladas . . . . . . . . . . . . . . . . . . . .

48

6.3

Execução Técnica

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

48

6.4

Métricas Gerais do Desenvolvimento . . . . . . . . . . . . . . . . . . . .

49

6.5

Épicos Desenvolvidos . . . . . . . . . . . . . . . . . . . . . . . . . . . .

50

6.5.1

Atualização do Layout . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

50

6.5.2

Criação Básica de Campanhas e Personagens . . . . . . . . . . . . . . . .

51

6.5.3

Criação Completa de Personagem

54

6.6

Últimos Ajustes e Encerramento do Desenvolvimento

. . . . . . . . . .

68

6.6.1

Edição de Personagem pelo Mestre . . . . . . . . . . . . . . . . . . . . . .

68

6.6.2

Remoção de imagem gerada por AI . . . . . . . . . . . . . . . . . . . . . .

70

6.7

Banco de Dados Final . . . . . . . . . . . . . . . . . . . . . . . . . . . .

72

7

RESULTADOS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

74

7.1

Sessão Real de Teste . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

74

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . . . . . . . . . . . . . . . . .

7.2

Respostas do Formulário de Feedback . . . . . . . . . . . . . . . . . . .

76

7.2.1

Perfil dos participantes . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

77

7.2.2

Dados quantitativos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

77

7.2.3

Percepção sobre uso de Inteligência Artificial . . . . . . . . . . . . . . . . .

79

7.3

Métricas do Sistema . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

80

8

CONSIDERAÇÕES FINAIS . . . . . . . . . . . . . . . . . . . . . . . . . .

81

REFERÊNCIAS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

82

GLOSSÁRIO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

83

APÊNDICE A

FORMULÁRIO COMPLETO UTILIZADO NA PESQUISA
COM USUÁRIOS . . . . . . . . . . . . . . . . . . . . . .

APÊNDICE B

85

REQUISITOS IDENTIFICADOS POR MEIO DE PESQUISA
DE FORMULÁRIO

. . . . . . . . . . . . . . . . . . . . . 114

B.1 Features para o TCC . . . . . . . . . . . . . . . . . . . . . . . . . . . 114
B.2 Features para futuras versões (pós-TCC) . . . . . . . . . . . . . . . 117

ANEXOS

120

ANEXO A – FICHA OFICIAL DE PERSONAGEM DA 5A EDIÇÃO DE DUNGEONS & DRAGONS, PUBLICADA PELA WIZARDS OF THE
COAST

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . 122

13

1 INTRODUÇÃO
Em 1974, foi lançado o primeiro Tabletop Role-Playing Game (TTRPG), o D&D, um jogo
de fantasia medieval criado pelos americanos Ernest Gary Gygax e David Arneson. Ao longo
das décadas que seguiram sua criação, D&D se tornou uma parte inseparável da cultura pop,
influenciando jogos eletrônicos, literatura, filmes e, é claro, o surgimento de centenas de outros
sistemas de TTRPGs (PYE, 2023).
O RPG de mesa, como é conhecido no Brasil, é um jogo interativo e colaborativo onde
os Jogadores assumem os papéis de personagens em uma história narrada e controlada por
um Mestre. As ações dos Jogadores são guiadas por um conjunto de regras definidas pelo
sistema utilizado, geralmente envolvendo o uso de dados multifacetados (como, por exemplo,
os dados de 20 lados, 10 lados, 6 lados, etc.) para determinar os resultados das ações, que são
moldadas pelo livre arbítrio e criatividade dos participantes. Para garantir a ordem e fluidez do
jogo, o Mestre atua como árbitro e guia para os Jogadores envolvidos.
Com sua capacidade de promover a inventividade e a interação social entre os Jogadores, os TTRPGs não apenas mantiveram sua relevância por cinquenta anos no mercado de
entretenimento, como também trouxeram benefícios para áreas como a educação e a psicologia, sendo hoje em dia utilizados para o letramento digital (BOTELHO; PETRONILHO; DIAS,
2023). Durante e após a pandemia de COVID-19, TTRPGs se beneficiaram com um crescimento em popularidade devido à sua essência colaborativa e imersiva em um momento em que
as pessoas buscavam formas de lidar com os efeitos psicológicos negativos do isolamento social. Estudos demonstraram que jogadores de Role-Playing Game (RPG) conseguem expressar
mais empatia e criatividade do que não jogadores de RPG (SHI, 2024).
Contudo, mesmo com tantos benefícios e crescimento, pouco foi feito para a modernização e automatização dos jogos de TTRPGs. A maioria dos aplicativos disponíveis, que servem
esta funcionalidade, são tão complexos de serem usados quanto as próprias regras do jogo,
funcionando mais como substitutos do que ferramentas facilitadoras (MARKS, 2024).
Sistemas de RPG de mesa frequentemente enfrentam problemas com a perda de anotações em papel e a dificuldade de consultar regras espalhadas por diversos materiais, como
livros e compêndios. Isso prejudica a fluidez das sessões, exigindo constantes interrupções para
esclarecer dúvidas ocultas em manuais extensos. Em uma era marcada pela busca por informações rápidas, essa complexidade afasta novos jogadores, que muitas vezes desistem antes de
compreender as regras. Mesmo o D&D, sistema mais popular no mercado de TTRPG, enfrenta
esse desafio, afetando tanto iniciantes quanto veteranos em busca de experiências mais ágeis.
Para mitigar esses problemas, o presente trabalho detalha o desenvolvimento e implementação do Themys Project, um assistente para Campanhas que utilizam o SRD 5.2.1 do
D&D. O software aborda as principais dificuldades enfrentadas por jogadores de RPG de mesa,
como a gestão de fichas de personagens e o acompanhamento das regras durante as sessões,
proporcionando a Mestres e Jogadores uma experiência mais fluida e organizada em compa-

14

ração aos métodos tradicionais em papel, centralizando as informações essenciais e facilitando
a visualização de regras e referências. Além disso, o Themys Project permite que um Dungeon
Master (DM) gerencie e personalize suas Campanhas por meio de um painel de controle, onde
pode visualizar e alterar as informações básicas dos personagens dos jogadores, como suas
classes, magias e habilidades.
O software, porém, não teve como objetivo virtualizar o jogo, portanto, não incluiu funcionalidades como editores de mapas ou comunicação por voz. Em vez disso, concentrou-se
em fornecer um suporte eficiente e complementar ao jogo tradicional, com o intuito de facilitar o
foco na narrativa e promover a integração descomplicada de jogadores iniciantes.
Para o desenvolvimento do projeto, foi analisado o preeminente Roll20 1 , uma aplicação
web para a execução de TTRPGs, oferecendo ferramentas para mapas virtuais, rolagem de
dados e gestão de personagens e Campanhas, bem como a ferramenta oficial de criação de
Ficha de Personagem do D&D, a fim de entender melhor as necessidades dos Jogadores e
Mestres e como suprir essas demandas de maneira mais eficiente.
O Themys Project, ou simplesmente “Themys”, visou preencher uma lacuna significativa
no mercado de RPGs de mesa ao oferecer uma solução que combina eficiência e praticidade,
proporcionando ferramentas para a gestão centralizada de personagens, Campanhas e regras.
O sistema facilita a organização de informações essenciais, permitindo que Mestres e Jogadores acessem rapidamente dados importantes, com cálculos de jogo automatizados e acesso
simplificado às regras por meio de palavras-chave, otimizando o tempo e reduzindo erros durante as sessões. Com o avanço da tecnologia e a crescente demanda por soluções digitais, o
Themys se mostrou uma ferramenta útil e pedagógica para a comunidade de RPG, recebendo
feedback positivo dos usuários por contribuir na organização das sessões e por ajudar a mitigar
um dos desafios mais recorrentes apontados por Jogadores e Mestres: a desorganização nas
mesas de TTRPG.
Embora inicialmente focado no SRD 5.2.1 do D&D, o software foi desenvolvido com uma
estrutura interna flexível, com banco de dados e componentes isolados, visando facilitar futuras
adaptações para mudanças de regras, ou adaptações de outros sistemas de regras.

1.1

1.1.1

Objetivos

Objetivo geral
Desenvolver um sistema para auxiliar Mestres e Jogadores de TTRPG a organizar e

gerenciar Campanhas que utilizam do SRD 5.2.1 do D&D.
1

https://roll20.net/

15

1.1.2

Objetivos específicos
Apesar do sistema ter o potencial de abranger diversas funcionalidades e melhorias

futuras, o que será abordado no Capítulo 3, os objetivos específicos deste projeto são:
• Implementar um sistema de busca para regras, magias e habilidades, permitindo buscas por frases ou termos, com as informações já inseridas no banco de dados;
• Desenvolver um sistema de keywords que destaque termos específicos dentro das
descrições de regras, magias e habilidades, fornecendo mais informações aos jogadores. As keywords serão definidas diretamente no banco de dados;
• Criar um gerenciador de magias que exiba as magias disponíveis para determinado
personagem conforme o seu nível e classe, com valores dinâmicos de dano e efeito
baseados no personagem ativo;
• Produzir um gerenciador de inventário que permita adicionar e remover itens, bem
como aumentar ou diminuir suas quantidades;
• Elaborar um sistema de criação de personagens de nível 1, permitindo seleção de
classe, raça, habilidades e distribuição de atributos;
• Projetar um dashboard para exibição de informações gerais de personagens, como
atributos2 , Skills3 , Spells4 e Cantrips5 ;
• Organizar um diário de Campanha e personagens para permitir a criação e edição de
textos e anotações importantes por Jogadores e Mestres.

1.2

Justificativa
O desenvolvimento do Themys foi motivado pela ausência de ferramentas simplificadas

e acessíveis no mercado de RPGs de mesa. Apesar da existência de plataformas robustas
como o Roll20, muitas delas são complexas e voltadas para funcionalidades avançadas, o que
nem sempre atende às necessidades de Jogadores e Mestres que procuram soluções práticas
e organizadas para suas sessões. Mesmo a ferramenta oficial do D&D6 enfrenta críticas por
sua falta de intuitividade e por representar uma barreira de entrada para novos jogadores, o que
pode afastar aqueles que buscam uma experiência mais direta e acessível.
2

3

4
5
6

Valores que representam as capacidades físicas e mentais do personagem, como Força, Destreza,
etc.
Perícias que indicam o conhecimento ou treino do personagem em áreas específicas, como Furtividade ou História.
Magias conjuradas por personagens com habilidades arcanas ou divinas.
Magias de nível 0, simples e de uso ilimitado.
https://www.dndbeyond.com/characters/

16

O problema da complexidade é ainda mais acentuado para DMs, que precisam ter um
conhecimento substancial do jogo e de suas regras para organizar uma Campanha de D&D.
Além dos conhecimentos específicos do sistema de regras, o Mestre também tem a responsabilidade de as ensinar aos Jogadores que não as conhecem. A combinação dessa curva de
aprendizado com a falta de ferramentas simplificadas faz com que iniciantes sejam sufocados
pela vasta quantidade de documentações, regras e referências interligadas. Isso tudo contribui
para uma cultura exclusiva, onde o acesso ao mundo dos TTRPGs frequentemente depende da
ajuda de jogadores mais experientes, o que pode complicar ou até mesmo impossibilitar jogos
criados por um grupo de iniciantes. A argumentação apresentada neste parágrafo é respaldada
pela entrevista com jogadores, conforme descrito no Capítulo 5.
Diante desse cenário, o Themys busca contribuir para uma experiência mais acessível e
organizada para os jogadores. Atualmente, muitos jogadores enfrentam dificuldades ao consultar regras dispersas em livros e materiais digitais, o que pode tornar o aprendizado do sistema
lento e desmotivador. O Themys busca centralizar esse acesso às regras de forma mais pedagógica e acessível, especialmente durante o processo de criação de personagens, contribuindo
para uma experiência mais fluida, organizada e acolhedora, principalmente para iniciantes.

1.3

Estrutura do trabalho
A estrutura deste trabalho visa a seguinte organização: o Capítulo 2 apresenta os fun-

damentos de TTRPG, destacando e explicando os termos comuns utilizados pela comunidade
para melhor entendimento deste trabalho; em seguida, o Capítulo 3 detalha como o sistema
Themys foi inicialmente conceptualizado para aprimorar a experiência dos jogadores de RPG
de mesa; o Capítulo 4 cita os recursos, ferramentas, frameworks e tecnologias utilizadas na execução do projeto, assim como a estratégia de desenvolvimento adotada; o Capítulo 5 aborda
como foi realizado o levantamento de requisitos e planejamento do projeto, incluindo as técnicas
utilizadas para definir prioridades e funcionalidades, além da definição das histórias de usuário
e a apresentação dos protótipos desenvolvidos; o Capítulo 6 descreve o processo de desenvolvimento técnico do sistema, desde a organização das tarefas até os desafios enfrentados; o
Capítulo 7 apresenta os resultados obtidos, com destaque para os dados coletados por meio de
formulários, o teste realizado com o sistema, e a análise final da solução; e, enfim, o Capítulo 8
apresenta as considerações finais sobre o Themys Project e explora seu potencial como uma
ferramenta de administração de jogos de TTRPG.

17

2 FUNDAMENTOS DE TTRPG
Com o intuito de esclarecer o cenário de aplicação e proporcionar uma melhor compreensão do problema a ser tratado por este trabalho, este capítulo se destina a explicar os termos
comumente utilizados quando nos referimos a TTRPG.

2.1

RPG de Mesa
O RPG de Mesa, TTRPG, é um gênero cujo elemento central é a interpretação de papéis

em um ambiente de mesa. Para a correta execução do jogo, são necessárias duas funções
distintas: a de Jogador e a de Mestre. Ao longo da sessão ou campanha, cada Jogador assume
o papel de um determinado personagem em um cenário fictício, interagindo com o mundo do
jogo conforme as regras do sistema possibilitam. Nesse processo, os Jogadores devem se
colocar na perspectiva de seus personagens, compreendendo e agindo de acordo com seus
pensamentos, emoções e motivações (HAMMER et al., 2018). Os TTRPGs permitem que os
Jogadores tenham um grau significativo de liberdade para manipular seus personagens e tomar
ações que terão impactos variados no mundo do jogo. Contudo, tais ações são arbitradas pela
intervenção do Mestre e muitas vezes determinadas pelo uso de dados multifacetados para
definir o sucesso ou fracasso de suas ações.

2.2

Sessões e Campanhas
Os TTRPGs são jogados em Sessões, que são encontros presenciais ou virtuais onde

os Jogadores se reúnem para participar de uma narrativa conduzida por um Mestre, o qual pode
ter criado a história ou adaptado uma já existente. A duração e a continuidade de uma sessão
dependem exclusivamente do planejamento do Mestre e do engajamento dos Jogadores. Se
a história planejada pelo Mestre tiver a duração de apenas um encontro, ela é chamada de
One Shot. Caso a história seja planejada para ser desenvolvida ao longo de várias sessões,
ela é chamada de “Campanha”. Uma sessão pode durar desde alguns minutos até, como é
mais comum, se estender por horas. As sessões podem ocorrer com a ausência de alguns
Jogadores, mas nunca sem a presença de um Mestre. O importante é que todos os participantes
de uma sessão possam se comunicar de forma síncrona, seja oralmente ou por escrito, visto
que TTRPG é fortemente dependente de interpretação, comunicação e participação ativa.

2.3

System Reference Document
O SRD é uma compilação de regras e conteúdos disponibilizados por um editor de jogos

de TTRPG para uso público. Ele serve como uma referência oficial e detalhada das mecânicas

18

e diretrizes do sistema de jogo, facilitando a criação de materiais que utilizem essas regras,
desde que sigam os termos da licença correspondente. No caso do SRD 5.2.1, referente à 5ª
edição de D&D, o conteúdo foi disponibilizado sob a licença Creative Commons Attribution 4.0
International (CC-BY 4.0)1 . Isso significa que qualquer pessoa pode copiar, distribuir, adaptar
e até comercializar obras derivadas do SRD, desde que forneça o devido crédito à Wizards
of the Coast, respeitando os termos da licença. Esse novo modelo substitui o uso da antiga
Open Game License (OGL) (Open Game License), ampliando a liberdade de uso e reforçando
a natureza aberta e compartilhável do conteúdo.

2.4

O papel do Jogador
No TTRPG, o Jogador interpreta um personagem, o qual pode ser criado por ele de

acordo com as regras do sistema ou ser um personagem já existente naquele universo. O papel
do Jogador é tomar decisões e realizar ações em determinado contexto baseado na perspectiva, motivações e características desse personagem. Durante as sessões, os Jogadores podem
colaborar entre si para desenvolver a história do jogo, enfrentando desafios e resolvendo conflitos propostos pela narrativa apresentada pelo Mestre. Embora a colaboração seja comum, nada
impede que os Jogadores antagonizem uns aos outros, desde que isso esteja alinhado com os
objetivos e princípios de seus próprios personagens.

2.5

O papel do Mestre
O Mestre, também conhecido como DM no contexto de Dungeons & Dragons e utilizado

neste trabalho para fins de abreviação, é o responsável por conduzir e narrar o jogo. Utilizando
um cenário preexistente ou sua própria criatividade, ele cria e descreve todos os elementos relacionados à história da Sessão. O DM desempenha um papel complexo, controlando os diversos
Non-playable Character s (NPCs) aliados e inimigos, arbitrando as regras, determinando os resultados das ações dos Jogadores, definindo consequências e ajustando a história conforme
as ações tomadas. No final, o Mestre é fundamental para manter o ritmo do jogo e garantir que
todos os Jogadores estejam envolvidos na narrativa. É importante destacar que o DM não deve
ser visto como um adversário dos Jogadores, mas como um facilitador que traz o RPG à vida,
garantindo uma experiência envolvente, dinâmica e justa.
Devido à necessidade de gerenciar simultaneamente todos os Jogadores e controlar os
diversos elementos da sessão, não é incomum que Mestres busquem várias ferramentas para
auxiliá-los na organização e administração do jogo. Essas ferramentas podem incluir aplicativos
de gestão de campanhas, softwares para rolagem de dados, geradores de mapas, planilhas de
controle de personagens, geradores de NPCs e itens.
1

Licença disponível em: https://creativecommons.org/licenses/by/4.0/

19

2.6

Materiais necessários e opcionais
Para uma experiência completa em um TTRPG, diversos materiais podem ser utiliza-

dos para facilitar o entendimento e a fluidez do jogo, aumentando a imersão dos participantes.
Embora alguns desses itens sejam essenciais, outros são opcionais e podem ser adaptados
conforme as preferências e necessidades do grupo.
Os materiais básicos incluem os livros de regras, que são essenciais para definir o sistema de jogo. Estes livros podem ser publicados por grandes editoras, por equipes independentes ou criados pelo próprio Mestre, conhecidos como “Homebrew”.
Outros materiais essenciais são os dados. Dependendo do sistema de jogo, diferentes
tipos de dados podem ser necessários, como dados de seis faces (d6), dados de vinte faces
(d20), entre outros. Esses dados são utilizados para determinar o sucesso ou fracasso das
ações dos personagens durante o jogo, adicionando um elemento de aleatoriedade e imprevisibilidade às sessões.
Outro material muito utilizado é o escudo do Mestre, que é projetado para ocultar informações dos Jogadores, como estatísticas dos inimigos e anotações do Mestre. Este item também oferece uma área prática para consultas de regras, já que essas informações são frequentemente impressas ou coladas na parte interna do escudo. A utilização do escudo do Mestre
não só ajuda a manter a organização e a privacidade das informações, mas também contribui
para aumentar a tensão e o suspense durante as rolagens de dados realizadas pelo Mestre.
Essa estratégia é eficaz para criar um ambiente mais envolvente e manter o engajamento dos
Jogadores ao longo do jogo.
Lápis, papéis e canetas são indispensáveis para anotações, como a manutenção de
fichas de personagens e a escrita de anotações durante as sessões. Mapas e miniaturas são
frequentemente utilizados para representar a posição dos personagens e dos elementos do
cenário, ajudando a visualizar a ação e a movimentação no jogo.
A utilização desses materiais visa enriquecer a experiência de jogo e aumentar a imersão dos Jogadores no mundo fictício escolhido pelo Mestre. Embora a presença de todos esses
itens não seja obrigatória, estes podem contribuir significativamente para a dinâmica e o engajamento durante as sessões de RPG. Por esse motivo, são amplamente procurados e valorizados
por entusiastas do hobby.
No próximo capítulo, será possível perceber que o Themys Project buscou incorporar
várias das utilidades mencionadas acima, proporcionando ao Mestre e aos Jogadores uma
experiência mais descomplicada.

20

3 THEMYS
Neste capítulo, é apresentada a concepção inicial do Themys Project, um sistema desenvolvido para auxiliar Jogadores e DMs em suas sessões de TTRPG para o SRD 5.2.1 do
D&D. A seção 3.1 discute o escopo do sistema, detalhando suas funcionalidades e áreas de
aplicação.

3.1

Escopo
O software foi idealizado com o objetivo de auxiliar Jogadores e DMs em suas sessões

de TTRPG que utilizam o SRD 5.2.1 do D&D, por meio de um sistema acessível para a gestão e
organização do jogo e de seus personagens. Procurou-se, desde o início, evitar que a aplicação
interferisse de maneira intrusiva na imersão das sessões, propondo, em vez disso, uma solução
equilibrada que respeitasse as decisões do Mestre e a fluidez narrativa da mesa.
Nesse contexto, o nome Themys foi escolhido em alusão à deusa titã Têmis, figura da
mitologia grega associada à justiça e à ordem. Tradicionalmente representada com uma balança nas mãos, Têmis simboliza o equilíbrio e a imparcialidade almejados pelo aplicativo. Além
disso, a escolha da referência mitológica reforça o caráter imersivo do projeto, aproximando-o
do universo fantástico que compõe o imaginário dos jogos de RPG de mesa.
A seguir, apresentam-se as principais funcionalidades concebidas para o sistema durante sua fase de planejamento. Cabe destacar que as funcionalidades aqui descritas representam a visão idealizada do sistema no início do projeto, como parte de um MVP conceitualmente
completo. As implementações efetivamente realizadas durante o trabalho são abordadas posteriormente no Capítulo 6.
• Criação e Gestão de Personagens: Permite aos usuários criar, editar e gerenciar
seus personagens, com ferramentas para registrar e alterar atributos, habilidades, equipamentos e outras propriedades inerentes ao personagem conforme as regras estabelecidas no SRD 5.2.1 e permissões configuradas pelo Mestre. Permite também ao DM
visualização e manipulação total dos personagens dos Jogadores para melhor preparo
das sessões, podendo utilizar esta ferramenta para aumentar a imersão do jogo.
• Rastreamento de Alterações: Mantém um registro das alterações realizadas nos personagens e nos inventários, facilitando a continuidade entre as sessões e garantindo
que não ocorram possíveis trapaças por parte dos Jogadores.
• Biblioteca de Regras: Oferece um repositório de regras e referências para consulta
rápida, que pode ser personalizado pelo Mestre com alterações no conteúdo original.
As regras são as mesmas disponibilizadas no SRD 5.2.1 do D&D, que inclui diretrizes
para publicar conteúdo sob a Creative Commons.

21

• Gerenciamento de Itens e Inventários: Facilita o controle de itens e equipamentos,
permitindo que Mestres e Jogadores atualizem e acompanhem os inventários de forma
eficiente e síncrona.

3.2

Perspectiva
Durante sua concepção, esperava-se que o Themys Project pudesse contribuir para uma

experiência mais organizada e envolvente tanto para Mestres quanto para Jogadores de TTRPG
que utilizam o sistema SRD 5.2.1 do D&D. Com a implementação de funcionalidades como
criação e gestão de personagens, biblioteca de regras e gerenciamento de itens e inventários,
o sistema foi pensado para simplificar a administração das sessões de RPG.
A intenção era que o sistema não apenas facilitasse o trabalho do Mestre, permitindo
que este se concentrasse mais na narrativa e menos na logística, mas também aumentasse o
engajamento dos Jogadores, ao proporcionar ferramentas que enriquecessem a imersão e a
interatividade no jogo. Ao integrar diversas utilidades auxiliares em um único sistema, o Themys
foi concebido como uma solução com potencial para transformar a forma como as sessões de
TTRPG são conduzidas, atraindo mais jogadores ao reduzir o aspecto intimidador das regras.

3.3

Descrição dos usuários
O Themys Project foi projetado para atender a dois perfis principais de usuários: DMs

e Jogadores. Cada perfil possui permissões e níveis de acesso distintos, adaptados às suas
funções no jogo. No entanto, é importante frisar que um usuário pode atuar tanto como DM
quanto como Jogador, dependendo se deseja criar ou participar de campanhas. Por este motivo, um usuário do sistema Themys terá acesso a duas visões distintas, a de Mestre e a de
Jogador, podendo alternar entre elas a partir de uma tela de seleção de função conforme suas
necessidades.
Na sequência, serão descritos os perfis e listadas as permissões de cada tipo de usuário.

3.3.1

Usuários
No Themys Project, um usuário é uma pessoa cadastrada no sistema e identificada por

um endereço de e-mail. Cada usuário pode criar várias campanhas com seu perfil de Mestre e,
como Jogador, pode ter vários personagens, cada um participando de uma campanha diferente.
É importante frisar que um usuário não pode atuar como DM e Jogador na mesma campanha.
Além das permissões específicas de cada perfil, todos os usuários têm a capacidade
de:

22

• Gerenciar Informações Pessoais: Os usuários podem alterar suas informações pessoais, como foto de perfil e nickname, para personalizar sua experiência no sistema;
• Acessar Visões de Mestre e Jogador: Os usuários podem acessar a visão correspondente de DM ou Jogador a partir da tela de seleção de função. Eles poderão alternar
entre essas visões conforme suas necessidades e funções em diferentes campanhas;
• Aceitar Convites para Campanhas: Jogadores podem aceitar convites enviados por
e-mail para ingressar em campanhas criadas por outros Mestres, facilitando sua participação em novas aventuras e histórias.

3.3.2

Mestres
Os Mestres são os usuários responsáveis por criar e conduzir as sessões de TTRPG.

Eles possuem as seguintes permissões e responsabilidades:
• Criação e Edição de Campanhas: Permite criar, editar e deletar campanhas, além de
adicionar e remover Jogadores das campanhas criadas;
• Gestão de Personagens: Proporciona acesso completo para visualizar e modificar os
personagens dos Jogadores, facilitando o controle e o preparo das sessões;
• Configuração de Regras: Permite a edição das descrições das regras na biblioteca de
regras, ajustando seu conteúdo para atender de forma mais precisa às necessidades
específicas de sua campanha;
• Configuração de Permissões: Permite a personalização das permissões dos Jogadores, definindo o acesso à edição de aspectos dos personagens, como atributos e
inventário;
• Gerenciamento de Inventários: Facilita a adição, remoção e modificação de itens
nos inventários dos personagens, mantendo o controle dos recursos disponíveis e utilizando este recurso para elementos de surpresa durante a história;
• Envio de Notificações: Habilita o envio de notificações para o e-mail cadastrado dos
Jogadores sobre eventos, atualizações e lembretes importantes;

3.3.3

Jogadores
Os Jogadores são os usuários que participam das sessões de TTRPG interpretando

seus personagens. Eles possuem as seguintes permissões e responsabilidades:

23

• Criação e Edição de Personagens: Uma vez dentro de uma campanha, permite criar
e modificar personagens, ajustando atributos, habilidades, equipamentos e outras propriedades, conforme permitido pelas regras do jogo e habilitado pelo DM;
• Consulta de Regras: Provê acesso à biblioteca de regras para referência rápida durante as sessões;
• Gestão de Inventários: Facilita o gerenciamento de inventário, sendo possível adicionar ou remover itens conforme as permissões configuradas pelo DM;
• Edição de Diário: Permite utilizar o sistema de diário para realizar anotações relevantes para a sessão, como a história do seu personagem, NPCs importantes, localizações relevantes, entre outros.
Essa estrutura de permissões visa garantir que cada usuário tenha as ferramentas necessárias para desempenhar seu papel de maneira eficaz, contribuindo para uma experiência
de jogo mais fluida e envolvente.

24

4 MATERIAIS E MÉTODOS
Este capítulo discute as tecnologias, ferramentas e metodologias empregadas no desenvolvimento do sistema Themys, organizando-se em duas seções: materiais utilizados e métodos
adotados.

4.1

Materiais
Para a prototipação das telas, foi utilizado o Figma1 , enquanto a modelagem do banco

de dados e a definição das cardinalidades das tabelas foram criadas com o dbdiagram.io2 .
A organização dos requisitos e a criação das User Stories foram elaboradas na plataforma
ClickUp3 .
Uma vez concluída essa base inicial, o monolito do projeto foi desenvolvido utilizando
o framework Ruby on Rails4 . A escolha por essa tecnologia se deu devido à sua facilidade e
praticidade para a criação de uma aplicação voltada à entrega de um MVP. Em conjunto com
o Rails, foi utilizado o banco de dados SQLite5 , o que facilitou a integração entre as camadas e
centralizou o desenvolvimento do projeto.
O front-end da aplicação foi desenvolvido principalmente com ferramentas nativas do
Rails, minimizando o uso de bibliotecas externas. Essa abordagem buscou maximizar o aproveitamento dos recursos internos do framework, garantindo uma integração eficiente e preparando
o sistema para uma futura implementação como um Progressive Web App (PWA). Ainda dentro
do ecossistema nativo do Rails, foram utilizados Turbo6 e Stimulus7 para otimizar a interação e
a experiência do usuário, enquanto o Kamal8 foi empregado para realizar o deploy da aplicação.
Para a estilização do front-end, foi adotado o Tailwind9 .
Por fim, o projeto foi conteinerizado utilizando Docker Compose10 , com o objetivo de
garantir uma melhor organização e segurança dos ambientes de desenvolvimento. O versionamento do código foi realizado com Git11 , sendo o GitKraken12 utilizado para o gerenciamento
dos commits, enquanto o repositório foi hospedado no GitHub13 , que também serviu como plataforma de integração contínua.
1

https://www.figma.com/
https://dbdiagram.io/
3
https://clickup.com/
4
https://rubyonrails.org/
5
https://www.sqlite.org/
6
https://turbo.hotwired.dev/
7
https://stimulus.hotwired.dev/
8
https://kamal.hotwired.dev/
9
https://tailwindcss.com/
10
https://docs.docker.com/compose/
11
https://git-scm.com/
12
https://www.gitkraken.com/
13
https://github.com/
2

25

4.2

Métodos
O processo de construção do sistema foi dividido em três grandes etapas, as quais serão

descritas na sequência: pré-produção, produção e preparação para a pós-produção.

4.2.1

Pré-Produção
Para garantir que o software atendesse às necessidades do público-alvo, foi realizada

uma etapa de pré-produção com apoio de um grupo experimental no levantamento dos requisitos ideais, sem considerar limitações de prazo ou recursos.
Para isso, foi aplicado um formulário estruturado para levantar as necessidades dos
usuários, cujas respostas foram analisadas e priorizadas com base nas técnicas MoSCoW
(CONSORTIUM, 2024) e Buy-A-Feature (TURNER, 2011). O processo completo está detalhado
no Capítulo 5.
Após a definição dos requisitos, estimou-se o esforço necessário para cada item, organizando as entregas de forma lógica e prática. As user stories priorizadas foram registradas no
ClickUp, sendo agrupadas em épicos quando apropriado, e serviram de base para o planejamento do ciclo de desenvolvimento.

4.2.2

Produção
A etapa de produção abrangeu o desenvolvimento completo do sistema, desde a pro-

gramação até os testes finais do MVP. Sua metodologia foi sintetizada a seguir, enquanto os
aspectos técnicos são detalhados no Capítulo 6.
O projeto seguiu um ciclo estruturado: cada épico definido na pré-produção era dividido
em tarefas menores, organizadas no ClickUp segundo critérios de lógica, usabilidade e dependências técnicas.
O processo de desenvolvimento de cada tarefa envolvia:
1. Escolha da tarefa ativa com base na ordem planejada;
2. Desenvolvimento da funcionalidade com a inclusão de testes automatizados, quando
aplicável;
3. Criação de uma pull request no GitHub;
4. Execução dos testes automatizados via GitHub Actions14 para validar a estabilidade do
código;
5. Revisão da pull request pelo professor orientador;
14

https://docs.github.com/actions

26

6. Aplicação de correções sugeridas e, após aprovação, conclusão da tarefa;
Após a conclusão de todas as tarefas vinculadas a um épico, era realizada a verificação
final e, estando tudo aprovado, executava-se o merge da branch correspondente na main.
A funcionalidade era então considerada estável e passava para a etapa de validação com os
usuários.
Em casos em que não era possível realizar testes de usabilidade completos, fosse pela
dependência entre funcionalidades ou pela complexidade das regras do RPG, foram utilizados
recursos como vídeos demonstrativos, capturas de tela e explicações detalhadas. Ainda assim,
buscou-se a validação do grupo por meio de conversas e feedback qualitativo.
Esse ciclo iterativo foi aplicado a cada novo épico selecionado, seguindo os princípios das abordagens incremental e evolucionária de engenharia de software (SOMMERVILLE,
2018). Essa abordagem permitiu manter um ritmo constante de entregas e ajustes, tornando o
processo de desenvolvimento mais adaptável às necessidades do projeto.
O ciclo descrito anteriormente está representado na Figura 1, que ilustra as etapas envolvidas no desenvolvimento incremental do sistema.

Figura 1 – Fluxo de desenvolvimento utilizado durante a produção do sistema

27

4.2.3

Pós-Produção
A etapa de pós-produção marcou a finalização do projeto como Trabalho de Conclusão

de Curso e serviu como transição entre a idealização acadêmica e a possibilidade futura de
um produto voltado ao mercado. Após a realização de testes práticos, conduzidos durante uma
campanha jogada presencialmente, e a coleta de dados por meio de formulários, conversas e
experimentação, foi documentado um conjunto de aprendizados com vista a um possível lançamento comercial. Esse processo funcionou como um post-mortem do projeto, e seus principais
resultados são detalhados no Capítulo 7.

28

5 PLANEJAMENTO DO PROJETO
Neste capítulo, são apresentados os aspectos teóricos e práticos utilizados no levantamento de requisitos, etapa correspondente à pré-produção.

5.1

Grupo Experimental
Para iniciar o planejamento do projeto, foi decidido formar um grupo experimental, com

o objetivo de representar os Project Owners1 ao longo do desenvolvimento. Esse grupo atuaria
em três fases principais: o levantamento de requisitos, sua priorização e, finalmente, a validação
das versões entregues durante o desenvolvimento.
A busca por participantes foi direcionada a pessoas que tivessem jogado recentemente
ou que estivessem ativamente jogando campanhas de D&D, utilizando a última versão do sistema disponível no mercado, que atualmente é a 5ª edição. A busca por voluntários foi inicialmente realizada por meio do Paladino Degolado, o clube de RPG de mesa do campus de
Guarapuava da UTFPR. Além disso, também foram procurados grupos de RPG locais por meio
de redes sociais, bem como por meio de contatos de segundo e terceiro grau (ou seja, contatos
de amigos de amigos).
Uma das principais dificuldades foi garantir a participação feminina, já que o grupo era
majoritariamente masculino. Com o apoio de voluntários e esforço para equilibrar a proporção
de gênero, chegou-se a um total de 25 participantes: 16 homens e 9 mulheres.
Foi decidido, então, que o grupo experimental se comunicaria oficialmente através de
um grupo no Whatsapp2 , o qual serviria como principal canal de interação e feedback direto
durante o desenvolvimento.

5.2

Levantamento de Requisitos
Para garantir que o projeto fosse capaz de resolver um problema real e agregar valor às

campanhas dos jogadores de D&D, foi planejada a coleta de requisitos ideais, ou seja, a identificação de todos os requisitos possíveis em um cenário onde não há limitações de recursos,
tempo ou orçamento.

5.2.1

Elaboração do Formulário
Para contornar a dificuldade de entrevistar os 25 participantes, optou-se por aplicar um

formulário estruturado com 61 questões divididas em 8 seções. Com exceção da primeira, de ca1

2

Termo comumente utilizado em metodologias ágeis para designar a figura responsável por representar
os interesses do cliente ou usuário final durante o desenvolvimento de um projeto.
https://web.whatsapp.com/

29

ráter introdutório, as demais abordaram aspectos relevantes para o desenvolvimento do sistema,
permitindo validar ideias iniciais e levantar novos requisitos. Abaixo apresenta-se um resumo do
conteúdo de cada seção. A versão completa do formulário está disponível no Apêndice A.
• Introdução: Apresentação do assistente Themys e o objetivo do formulário;
• Perfil do Usuário: Perguntas básicas sobre nome, idade, gênero e entendimento de
inglês (apenas leitura), sendo esta última importante para avaliar se o grupo teria dificuldades com uma versão inicial do aplicativo apenas em inglês;
• Experiência: Investigou tempo e frequência de jogo, formato das sessões, papéis preferidos (Jogador ou Mestre), além de classes e raças favoritas (dados úteis para orientar decisões de escopo);
• Uso de Aplicativos Estabelecidos: Investigou o uso prévio de aplicativos de apoio a
TTRPG, frequência, funcionalidades mais valorizadas ou ausentes, motivos de abandono e sugestões de funcionalidades ideais;
• Problemas do Dungeons and Dragons e TTRPG: Abordou dificuldades enfrentadas
por Jogadores e Mestres, como criação e gestão de personagens, organização das
sessões e consulta de regras, encerrando com a indicação da regra que mais gostariam de ver automatizada;
• Validações: Nesta seção, foram feitas várias perguntas para determinar a importância
de possíveis recursos na visão dos participantes. As respostas foram dadas em uma
escala de 0 a 10, onde 0 significava “nunca usaria este recurso” e 10 significava “usaria
sempre este recurso”. Os requisitos abordados foram baseados nas ideias apresentadas na proposta inicial deste trabalho de conclusão de curso, no Capítulo 3;
• Monetização: Esta seção foi inteiramente especulativa. Explorou-se a aceitação dos
participantes quanto a diferentes formas de monetização, como anúncios e assinaturas, bem como a disposição em pagar por planos específicos.
• Considerações Finais: Além de abrir espaço para sugestões e preferências de comunicação durante o desenvolvimento, esta seção buscou validar a escolha das fontes do
sistema: todo o formulário foi construído com as mesmas, e a última pergunta avaliou
sua legibilidade e estética.

5.2.2

Resultados Obtidos
Entre os vinte e cinco participantes do grupo experimental, 24 responderam todas as

perguntas do formulário. A idade dos participantes variou entre 18 a 33 anos, com uma média
de 24 anos. A maioria (87,5%) dos entrevistados afirmou ter compreensão suficiente de inglês

30

para leitura e entendimento, sendo que apenas uma pessoa declarou não compreender nada
do idioma.
Quanto à experiência com RPG, 33,3% dos entrevistados são novos jogadores, enquanto 58,3% jogam há mais de 3 anos, conforme ilustra a Figura 2.

Figura 2 – Resultado da pergunta “Há quanto tempo você joga RPG de Mesa?”

A frequência com que os participantes jogam RPG ficou com uma divisão equilibrada
entre jogadores que jogam várias vezes por mês e aqueles que raramente conseguem jogar.
Verificou-se também uma preferência predominante pelo papel de Jogador, pois a cada
3 membros do grupo experimental, 2 são Jogadores preferenciais. Embora fatores como dificuldade e exigência do papel de Mestre tenham sido mencionados, a escolha entre Jogador e
Mestre pareceu depender principalmente do gosto pessoal.
Quanto ao uso de aplicativos, foi verificado que 70,8% dos entrevistados os utilizavam
de maneira frequente, e vários foram os aplicativos elencados, tendo funcionalidades desde
a criação de mapas até a virtualização do ambiente de TTRPG. Os principais motivos para
deixar de usar os aplicativos foram custos elevados, falta de funcionalidades essenciais ou a
necessidade de usar múltiplos aplicativos simultaneamente, o que gerava desorganização e
perda de imersão. Alguns usuários também mencionaram a interface não intuitiva e problemas
técnicos, como travamentos. Contraintuitivamente, a maneira mais utilizada para se acessar
estes aplicativos não são dispositivos móveis, e sim computadores.
Se tratando de problemas com o sistema do D&D, os participantes relataram dificuldades na criação de personagens devido a complexidade e à falta de intuição do processo, como a
distribuição de atributos e a escolha de habilidades, talentos e equipamentos. Além disso, muitos jogadores enfrentam dificuldades em encontrar informações específicas nos livros, o que
torna o processo demorado e confuso, especialmente para iniciantes. Este problema não é exclusivo de novos Jogadores, já que os principais problemas enfrentados pelos DMs incluem o
gerenciamento de fichas, itens, regras e condições dos Jogadores e NPCs durante a sessão,
o que leva à necessidade de buscar informações nos livros e apêndices a todo momento. A
quantidade excessiva de regras dificulta a compreensão e acaba atrasando as sessões, e, levando em conta que os participantes também enfrentam dificuldades com a falta de clareza em
algumas regras, as quais referenciam outras regras, denota ainda mais a necessidade de uma
centralização e organização das informações.

31

Quanto à questão de monetização, os participantes demonstraram diferentes níveis de
disposição para pagar pelo aplicativo. Em relação à assinatura mensal, conforme ilustra a Figura 3, 16,7% estariam dispostos a pagar até 5 reais, 29,2% até 10 reais, 25% até 20 reais e
29,2% até 30 reais.

Figura 3 – Resultado da pergunta “Qual é o máximo que você estaria disposto a pagar por mês
por determinado aplicativo?”

Já no modelo anual, conforme ilustra a Figura 4, 41,7% aceitariam pagar entre R$ 50
e R$ 100 (valor equivalente a R$ 4,16 a R$ 8,33 mensais), 20,8% estariam dispostos a pagar
entre R$ 200 e R$ 300 (equivalente a R$ 16,66 a R$ 25 mensais), e 12,5% concordariam em
pagar R$ 50,00, enquanto 16,7% pagariam entre R$ 100 e R$ 200 e 8,3% aceitariam pagar
entre R$ 300 e R$ 400.

Figura 4 – Resultado da pergunta “Qual é o máximo que você estaria disposto a pagar por ano
por determinado aplicativo? (este valor seria um pacote anual)”

Além disso, 95% dos participantes mostraram interesse em assinar um plano “party”,
no qual um usuário pagaria um valor mais alto para adicionar até 5 pessoas ao mesmo plano,
mesmo sabendo que esse plano poderia ser de 50% a 70% mais caro do que o plano anual.
Ademais, os comentários e feedback obtidos por meio do formulário foram amplamente
positivos. Quando questionados sobre a possibilidade de o aplicativo melhorar a experiência
de jogo, alguns participantes destacaram pontos como: “Imensamente. A ideia de facilitar de
maneira específica o que mais segura o RPG pelo caráter automático é muito valiosa. Afinal de
contas, o sistema tem que ser um acessório para o que mais importa: a narrativa e a interpretação”, e ainda, “O aplicativo pode ajudar os iniciantes a aprenderem mais rápido como jogar
e também ajuda aqueles que jogam de vez em quando a lembrar das informações, tanto do
personagem quanto das regras”.

32

Por fim, ao longo de todo o formulário, foi possível levantar 41 requisitos para a construção de um “aplicativo ideal”3 . As sugestões variaram desde funcionalidades já previstas, como
a criação de personagens, até propostas mais avançadas, como a geração de imagens por
inteligência artificial. A lista completa desses requisitos encontra-se no Apêndice B.

5.3

Priorização de Requisitos
Uma vez analisado o formulário de levantamento de requisitos e documentados os re-

sultados, percebeu-se que era necessário filtrar o que foi obtido antes mesmo de escrever as
histórias de usuário.
Esta etapa, embora tenha ocorrido em um espaço de tempo menor do que o levantamento de requisitos, exigiu um preparo maior para sua devida execução. Ao longo das próximas
subseções, é discutido o processo de idealização desta etapa até o resultado alcançado.

5.3.1

MoSCoW e Buy a Feature
De modo geral, todos os requisitos levantados agregariam valor significativo ao assis-

tente de TTRPG Themys. No entanto, considerando as limitações de tempo neste estágio inicial
de desenvolvimento, tornou-se essencial aplicar um processo criterioso de priorização. Isso garantiu que os recursos mais relevantes fossem implementados primeiro, possibilitando a entrega
de uma versão funcional e eficiente do sistema. Para isso, utilizou-se uma combinação das técnicas MoSCoW e Buy a Feature.
A técnica MoSCoW é um método de priorização que classifica os requisitos por ordem
de importância: Must, Should, Could e Won’t. No entanto, quando aplicada isoladamente, pode
gerar escolhas tendenciosas ou pouco representativas das necessidades reais dos stakeholders. Para mitigar esse risco, utilizou-se a técnica Buy a Feature como complemento, permitindo
que os participantes priorizassem funcionalidades por meio de uma simulação de investimento
com orçamento fictício.
O Buy a Feature é uma técnica de priorização onde os participantes “compram” funcionalidades com um orçamento fictício, ajudando a identificar quais recursos são mais valorizados.
Para este projeto, foi criada uma versão modificada desta técnica para que ela fosse utilizada
em conjunto com MoSCoW. Nesta versão, há três momentos distintos:
• Pré-seleção das Funcionalidades: Inicialmente, foram pré-selecionadas as funcionalidades a serem consideradas na dinâmica, baseando-se na viabilidade de implementação. Funcionalidades inviáveis, seja por questões financeiras ou restrições de tempo,
foram categorizadas como “Won’t” no MoSCoW. Isso permitiu que os participantes focassem apenas nos requisitos possíveis de serem implementados;
3

Considerando as funcionalidades mais valorizadas e desejadas pelos participantes do levantamento.

33

• Primeira Etapa de Compra (Must): Após calcular e precificar os requisitos remanescentes, os participantes receberam 60% do valor total do orçamento para gastar.
As funcionalidades compradas nesta etapa foram consideradas como “Must” no MoSCoW ;
• Segunda Etapa de Compra (Should): Na última etapa, os participantes escolheram
entre as funcionalidades restantes, usando apenas os 40% restantes do orçamento. As
funcionalidades compradas nesta fase foram categorizadas como “Should” no MoSCoW, enquanto as que não foram compradas em nenhuma das etapas foram automaticamente classificadas como “Could”.
Para entendimento de escopo considerado neste projeto, o Must compreende as funcionalidades principais e essenciais para este trabalho. O Should consiste nas funcionalidades
desejáveis para a finalização do trabalho, mas que não são necessárias para sua conclusão. O
Could inclui tudo o que foi planejado para ser implementado após a conclusão deste trabalho
para uma primeira versão comercial. Finalmente, as funcionalidades inicialmente categorizadas como Won’t serão reavaliadas após a conclusão deste trabalho para terem sua prioridade
reclassificada.
Vale ressaltar que a combinação dessas técnicas trata-se de uma proposta original desenvolvida especificamente neste trabalho. Apesar das buscas realizadas, não foram encontradas referências que associassem diretamente as metodologias MoSCoW e Buy a Feature da
forma aqui apresentada.

5.3.2

Tempo de Desenvolvimento e Precificação dos Requisitos
Antes de iniciar o processo de Buy a Feature, foi necessário precificar os requisitos. As

seguintes etapas foram realizadas para chegar aos valores finais:
• Primeiramente, foi determinado o tempo disponível para a execução do projeto, assumindo um cenário mais restritivo para simular o pior caso possível. Concluiu-se que,
com uma média de 10 a 12 horas semanais, seria possível dedicar um total de 180
horas ao projeto antes do término do prazo;
• Em seguida, com base em experiências anteriores com requisitos semelhantes, foi
estimado o tempo médio necessário para a conclusão de cada item. Para acomodar
imprevistos e variações de dificuldade, adicionaram-se de 1 a 5 horas extras conforme
o nível de exigência de cada tarefa.
• Posteriormente, definiu-se um valor arbitrário para a hora de trabalho, a fim de padronizar a precificação. O valor estipulado foi de R$ 50,00 por hora;

34

• Com isso, obteve-se um orçamento fictício total de R$ 9.000,00 para a execução do
projeto, com os requisitos variando entre R$ 300,00 e R$ 1.600,00. Conforme definido na subseção anterior, 60% do orçamento foi destinado para a primeira etapa, e
40% para a segunda, totalizando, respectivamente, R$ 5.400,00 para a etapa “Must” e
R$ 3.600,00 para a etapa “Should”.

5.3.3

Preparo do Material Utilizado
Com os orçamentos e requisitos devidamente precificados, foi necessário buscar uma

plataforma para a execução da dinâmica do Buy a Feature, visto que organizar todos os vinte e
cinco membros do grupo experimental para realizar a dinâmica de forma síncrona seria inviável.
Após uma pesquisa, constatou-se que não existiam plataformas online gratuitas para essa finalidade, muito menos opções adaptáveis, considerando que a versão do Buy a Feature utilizada
no projeto é uma adaptação do modelo original.
Desta forma, foi criada uma planilha no Google Sheets4 para automatizar o processo.
Devido às limitações da ferramenta e à natureza “gamificada” da dinâmica, suas particularidades foram explicadas por meio de um vídeo e instruções compartilhadas no grupo de Whatsapp.
Para que cada participante tivesse conhecimento sobre o funcionamento de cada funcionalidade, foi criado um glossário explicativo, detalhando o que representava cada feature
disponível para compra, suas funcionalidades e limitações. O glossário ficou disponível em uma
aba da própria planilha e também em um documento compartilhado na plataforma Notion5 , para
facilitar a leitura e o acesso às informações.
Após os membros consultarem o material de apoio e esclarecerem suas dúvidas, a
planilha foi finalmente compartilhada com o grupo experimental.

5.3.4

Execução do Buy a Feature
A execução da dinâmica ocorreu ao longo de uma semana. Dos 25 participantes, 16

participaram da atividade. Nenhum dos envolvidos violou as regras estabelecidas, e 6 deles
utilizaram o espaço extra para comentário a fim de explicar a lógica por trás de suas decisões, o
que ajudou a compreender melhor a intenção desses participantes como stakeholders. Nenhum
dos participantes apresentou dificuldade durante a execução do Buy a Feature.
Abaixo, é possível observar nas figuras uma amostra das respostas obtidas pelos participantes. Na Figura 5, a pessoa conseguiu utilizar todos os recursos sem exceder o limite em
nenhuma das etapas. No segundo caso, ilustrado pela Figura 6, o participante ultrapassou em
R$ 150,00 o orçamento da primeira etapa, valor que foi subtraído da etapa seguinte. Ainda as4

5

Disponível
em
https://docs.google.com/spreadsheets/d/13LlU_t6MGxiJj9b_
sYQ8kn17ig45pLZbXzIVczDtjBs/edit?usp=sharing
https://www.notion.so/

35

sim, o participante conseguiu finalizar a atividade de modo que, ao fim da segunda etapa, não
houvesse déficit, restando exatamente R$ 150,00. É importante frisar que o critério fundamental
para validação da atividade era não ultrapassar o orçamento total ao término da segunda etapa.

Figura 5 – Exemplo de Resposta - Buy a Feature

Figura 6 – Exemplo de Resposta - Buy a Feature

5.3.5

Resultados Obtidos
Após o término do tempo estabelecido para as respostas, foram verificadas as opções

mais votadas em cada etapa, conforme mostra a Figura 7. Com base nas decisões, foram
elaborados cenários possíveis para implementar os requisitos mais votados, respeitando as
regras previamente estabelecidas. Ao final, restaram duas opções viáveis. Após uma breve
análise de viabilidade, a opção ilustrada na Figura 8 foi escolhida.
Por fim, a priorização por meio do MoSCoW ficou da seguinte forma:

36

Figura 7 – Features mais votados

Figura 8 – Features escolhidos

• Must:
– Pesquisa de regras/magias/habilidades;
– Sistema de Keywords para pesquisa;
– Gerenciamento de magias I;
– Gerenciador de inventário I;
– Criação de personagens I;
– Dashboard de PCs e NPCs;
– Diário de campanha e personagens I;
– Personalização de personagem I.

37

• Should:
– Sistema de Level Up I;
– Gerenciamento de combate I;
– Gerenciador de equipamentos.
• Could:
– Agendador de sessões I;
– Soundboard (efeitos sonoros);
– Presets de personagens;
– Rolagem de dados I;
– Cronômetro I;
– Tutorial de uso do aplicativo;
– Tradução e internacionalização do conteúdo.

5.4

Histórias de Usuário
Apresentam-se aqui os requisitos priorizados como Must na técnica MoSCoW, organi-

zados como histórias de usuário. Embora todos tenham sido planejados nesta fase, nem todos
foram concluídos dentro do prazo. O desenvolvimento de cada um será detalhado no Capítulo 6.
• Pesquisa de regras/magias/habilidades
1. Como usuário, quero pesquisar por frases ou termos para encontrar rapidamente informações sobre regras, magias ou habilidades.
• Sistema de Keywords para pesquisa
1. Como usuário, quero que termos que referenciem outras regras, magias ou
habilidades estejam destacados para identificar conexões com facilidade.
2. Como usuário, desejo ver a definição de um termo ao clicar nele, facilitando a
compreensão do seu significado.
• Gerenciamento de magias I
1. Como Jogador, quero escolher magias conforme meu nível e classe, seguindo
as regras do jogo.
2. Como Jogador, quero que o dano das magias já considerem meus atributos.
• Gerenciador de inventário I

38

1. Como Jogador, quero poder adicionar e remover itens do meu inventário facilmente, para que eu possa gerenciar meus recursos de forma eficiente.
2. Como Mestre, quero poder manipular o inventário dos Jogadores para os surpreender conforme o desenvolvimento da história.
• Criação de Personagens I
1. Como Jogador, quero criar um personagem de nível 1, selecionando sua
classe, raça, habilidades e distribuindo seus atributos, para começar minha
aventura com um personagem personalizado.
2. Como Mestre, quero criar um NPC para utilizar durante o jogo.
3. Como usuário, quero que as opções disponíveis durante a criação de personagem sejam exibidas dinamicamente, para garantir que as combinações
listadas sejam possíveis conforme as regras.
4. Como Jogador, preciso ver apenas as magias compatíveis com minha classe.
• Dashboard de PCs e NPCs
1. Como Jogador, preciso de um dashboard que reúna os dados dos meus personagens, facilitando o acompanhamento durante a campanha.
2. Como Mestre, quero que o dashboard de NPCs seja ativado após a criação
de um NPC, para gerenciar facilmente gerenciá-los.
3. Como usuário, quero que o dashboard reflita as informações definidas pelo
Mestre, para acompanhar o status de cada personagem.
• Diário de campanha e personagens I
1. Como usuário, quero ter uma área dedicada para criar e editar textos e anotações importantes, para que eu possa manter um registro das decisões, eventos e desenvolvimentos da campanha.
• Personalização de personagem I
1. Como usuário, quero poder carregar uma imagem personalizada para a ficha do meu personagem, para que ela reflita minha visão do personagem de
forma visual e para que os outros possam o ver da mesma forma.

5.5

Protótipo de Telas
Ao longo desta seção, são apresentados os protótipos de interface concebidos durante o

planejamento do sistema, seguindo a abordagem mobile first. Como será possível observar no

39

Capítulo 6, embora muitas das telas tenham sido ajustadas ou substituídas durante o desenvolvimento, os protótipos aqui apresentados desempenharam um papel fundamental na definição
da arquitetura de navegação e na validação preliminar da experiência do usuário.

5.5.1

Área Pública e Conceito Visual
Na Figura 9, é possível observar o conceito inicial da área pública do aplicativo.

Figura 9 – Tela Inicial

O estilo visual do protótipo foi construído com base em elementos da fantasia medieval,
aplicando de forma consistente uma textura de pergaminho envelhecido com bordas queimadas, tons escuros e sombras para evocar a atmosfera de sessões de RPG. As fontes sépia e
douradas garantem legibilidade e reforçam a estética de antiguidade. Complementando o aspecto místico, a imagem de fundo retrata a deusa Têmis, símbolo de justiça, equilíbrio e ordem,
conectando visualmente a proposta do aplicativo ao universo fantástico de D&D.

5.5.2

Autenticação
O fluxo de autenticação foi projetado para ser simples, guiando o usuário desde a criação

de conta até a personalização de seu perfil. A Figura 10 ilustra esse percurso, que inclui a tela
inicial, o registro de conta, a escolha da função (Jogador ou Mestre) e o menu de edição de
dados pessoais, como nome, senha e imagem.

40

Figura 10 – Fluxo de Autenticação. Da esquerda para a direita: (A) Tela inicial, (B) Registro de
Conta, (C) Seleção de Função, (D) Edição de Perfil.

5.5.3

Visão do Jogador
O fluxo idealizado para a área do Jogador é apresentado na Figura 11.

Figura 11 – Fluxo Geral. Da esquerda para a direita: (A) Seleção de Função, (B) Seleção de Campanha, (C) Seleção de Personagem.

Esse fluxo tem início na tela de “Seleção de Função” (A), onde o usuário escolhe entre
DM ou Player, sendo então direcionado à respectiva área do sistema. Em seguida, o Jogador
acessa a tela de seleção de campanhas (B), visualizando apenas aquelas para as quais foi

41

convidado por um DM, e, por fim, a tela de seleção de personagens (C), onde pode criar novos
personagens ou selecionar um já existente para acessar sua dashboard.

5.5.4

Visão do Personagem
A seleção de um personagem leva o Jogador à Ficha de Personagem, estruturada

com base nos elementos essenciais da ficha oficial do D&D (disponível para visualização no
Anexo A). Por exigir a organização de um grande volume de dados, este foi o layout mais desafiador do sistema, resultando no protótipo mostrado na Figura 12.

Figura 12 – Dashboard, parte 1 e parte 2

A dashboard foi projetada com ícones para atributos principais, seções agrupadas logicamente (como atributos, condições e habilidades) e menus accordion, elementos interativos
que permitem expandir ou recolher blocos de conteúdo, para organizar melhor as informações
menos acessadas. Os dados exibidos seriam apenas consultáveis, cabendo ao DM realizar
quaisquer alterações.
Embora a dashboard centralizasse as informações principais, funcionalidades mais detalhadas seriam acessadas por um menu lateral, aberto pelo ícone no canto superior esquerdo,
com opções como inventário, diário e etapas anteriores do fluxo.
A primeira versão do inventário foi concebida de forma simples, exibindo apenas nome,
quantidade e peso dos itens. Nesta iteração inicial, apenas o DM poderia adicionar ou remover
itens, evitando trapaças. Para acessá-la, seguir-se-ia o fluxo ilustrado na Figura 13.

42

Figura 13 – Fluxo do Personagem - Inventário. Da esquerda para a direita: (A) Menu Lateral, (B)
Listagem de Items.

Já a tela de “Diário do Personagem” foi projetada como um espaço para anotações
importantes sobre o personagem ou a campanha, como ilustrado na Figura 14.

Figura 14 – Fluxo do Personagem - Diário. Da esquerda para a direita: (A) Menu Lateral, (B) Listagem de Entradas, (C) Criação de entradas.

Estas anotações substituiriam os esboços de texto que geralmente são feitos em arquivos de texto ou rabiscados na ficha. Seguindo o padrão visual da dashboard, como mostrado na
Figura 14 (B), cada entrada seria composta por um título e expandida por meio de um menu accordion, favorecendo uma visualização limpa e eficiente, especialmente em dispositivos móveis.
Novas anotações poderiam ser adicionadas por meio da tela exibida na Figura 14 (C).

43

5.5.5

Criação de Personagem
Para acessar qualquer funcionalidade mencionada, o Jogador precisaria antes passar

pelo processo de criação de personagens. Como o próprio SRD exige múltiplas etapas, o fluxo
foi dividido em diversas telas, organizadas conforme a ordem lógica da criação de personagem,
como ilustram a Figura 15 e a Figura 16.

Figura 15 – Criação de Personagem - Parte 1. Da esquerda para a direita: (A) Seleção de raça, (B)
Seleção de classe, (C) Seleção de Cantrips, (D) Seleção de Spells.

Figura 16 – Criação de Personagem - Parte 2. Da esquerda para a direita: (A) Seleção de background, (B) Distribuição de Atributos, (C) Seleção de Habilidades.

Criar um novo personagem de Jogador, ou mesmo um NPC, é um dos processos mais
demorados e complexos do D&D, independentemente do nível de experiência do Jogador. Isso
se deve não apenas à quantidade de etapas envolvidas, mas também à necessidade de consultar informações correlacionadas para completar cada uma delas. Por esse motivo, as telas de

44

Criação de Personagem foram concebidas com foco na intuitividade visual e na apresentação
clara de informações e referências cruzadas.
A Figura 15 (A) ilustra a primeira tela do processo de criação de personagem, dedicada
à seleção de gênero e raça. Ao selecionar uma raça, suas informações específicas seriam exibidas automaticamente para auxiliar na escolha. Supondo, por exemplo, que o Jogador optasse
pela raça “Tiefling”, ele poderia visualizar, conforme ilustrado na Figura 17 (A), que essa raça
concederia três Race Features especiais.

Figura 17 – Modal Explicativo da feature Nightvision. Da esquerda para a direita: (A) Seleção de
classe, (B) Modal explicativo de ícone.

Caso não reconhecesse algum ícone, o Jogador poderia clicar sobre ele para exibir
um modal com a descrição correspondente, como mostra a Figura 17 (B). No exemplo citado,
isso revelaria que o ícone central representa a habilidade passiva Nightvision. As descrições
destacariam as informações principais em negrito, com observações adicionais apresentadas
como notas de rodapé.
Nas telas ilustradas pelas figuras Figura 15 (B) e (C), os Cantrips e Spells são representados por ícones, facilitando a associação visual e a memorização. Cada magia possui um ícone
próprio, e as oito escolas de magia do D&D são distinguidas por cores. Essa solução também
evita o excesso de texto, especialmente útil em dispositivos móveis.
Conforme já descrito, o Jogador poderia clicar em qualquer magia para visualizar seus
detalhes, como ilustra a Figura 18. Isso eliminaria a necessidade de consultar o livro de regras,
bastando um clique no ícone para acessar efeitos, danos e restrições. Termos relevantes seriam
destacados, e referências cruzadas apareceriam no rodapé.
A exibição de informações em modais não se limitaria a ícones e botões, mas também
abrangeria keywords. Na Figura 16 (A), termos como Deception e Sleight of Hand, na seção

45

Figura 18 – Modal Explicativo do Cantrip Fire Bolt. Da esquerda para a direita: (A) Seleção de
Cantrip, (B) Modal explicativo de magia.

Skills, seriam exemplos de keywords: palavras clicáveis que revelariam mais informações, conforme ilustrado na Figura 19.

Figura 19 – Modal Explicativo da Skill Deception.

É importante frisar que essa forma de exibição de informações por meio de modais não
se restringiria à criação de personagens, sendo aplicada em todo o aplicativo. O objetivo seria
garantir que o significado dos termos do sistema estivesse sempre acessível aos Jogadores,
facilitando sua memorização por meio da repetição e da associação visual.

46

O sistema também buscaria simplificar a distribuição de pontos de habilidade, conforme
ilustrado na Figura 16 (B). Como o custo para aumentar um valor varia conforme a pontuação
atual, o sistema realizaria os cálculos automaticamente, atualizando em tempo real os pontos
disponíveis, os valores base e seus modificadores. Caso o Jogador desejasse, ele também
poderia resetar a distribuição a qualquer momento, recuperando todos os pontos, ou optar por
distribuir a pontuação de forma aleatória.
Outra automação que visava facilitar o processo de criação de personagem era a seleção de skills. De acordo com as regras do D&D, um personagem pode aprimorar um número
específico de skills, sendo que as opções disponíveis dependem diretamente da classe e do
background escolhidos. Assim, o Jogador poderia selecionar apenas entre as opções exibidas,
determinadas condicionalmente com base nas escolhas feitas nas etapas anteriores, como ilustrado na tela da Figura 16 (C).
Seguindo esse princípio de automação, bônus adicionais concedidos a certas skills seriam somados e indicados por ícones de estrela. Um botão explicativo permitiria ao Jogador
entender o motivo de algumas opções estarem indisponíveis, e cada skill apareceria como uma
keyword, podendo ser clicada para exibir uma descrição resumida.
Após concluir esse último passo, o Jogador seria direcionado a uma tela semelhante à
dashboard, onde poderia visualizar todas as informações do seu personagem, como uma “ficha
de personagem”. Nessa tela, o Jogador teria a opção de aceitar ou excluir o personagem criado.
Em seguida, ele seria redirecionado para a tela de Seleção de Personagens, conforme ilustrado
na subseção 5.5.3 (C), finalizando, assim, o fluxo de criação de personagem.

5.5.6

Demais telas
Nem todas as telas foram prototipadas neste estágio. Funcionalidades como a busca

por magias ou a edição da imagem de perfil do personagem, por exemplo, não chegaram a
ser representadas em protótipo. Devido a limitações de tempo, imprevistos e à densidade das
tarefas, fatores que serão detalhados no próximo capítulo, optou-se por concentrar o desenvolvimento nas telas já concebidas, por estas representarem o núcleo funcional do sistema. Vale
destacar que muitas das telas apresentadas nesta seção foram, com as devidas adaptações,
reaproveitadas na visualização do Mestre.
O fluxo completo das telas prototipadas está disponível por meio da apresentação do
protótipo na plataforma Figma6 .

6

Disponível em https://tinyurl.com/azszc6ap

47

6 DESENVOLVIMENTO

6.1

Visão Geral do Processo de Desenvolvimento
O desenvolvimento do sistema seguiu o fluxo metodológico definido na etapa de pré-

produção, conforme descrito no Capítulo 5. O ciclo representado no fluxograma da Capítulo 4 foi
adotado como base para a execução, com adaptações conforme a dificuldade de cada tarefa ou
desafio enfrentado. Esse planejamento prévio foi fundamental para garantir um ritmo constante
de entregas e validações, mesmo diante das limitações de tempo e escopo.
No entanto, mesmo com tal preparo, o escopo originalmente planejado precisou ser
ajustado ao longo do desenvolvimento a fim de assegurar a entrega de um sistema funcional
e estável. Com isso, o foco principal foi direcionado à implementação do fluxo completo de
criação de personagens — considerado o núcleo da proposta do sistema, dada a dependência
das demais funcionalidades em relação a esse componente central. Os desafios enfrentados
e a justificativa para essa mudança de escopo serão discutidos em maior detalhe ao longo da
seção 6.5.
Para melhorar a organização e previsibilidade ao longo do processo, a estrutura do
banco de dados do sistema foi documentada e mantida em constante evolução por meio da
ferramenta online dbdiagram.io. Sempre que novas entidades ou relacionamentos eram implementados, o modelo era atualizado, proporcionando uma visão clara e consolidada da arquitetura do sistema. A versão final do diagrama será apresentada na seção 6.7, acompanhada de
comentários sobre as principais decisões de modelagem adotadas.

6.2

6.2.1

Organização das Tarefas

Fluxo de Tarefas no ClickUp
O gerenciamento das tarefas foi realizado por meio de um quadro visual adaptado, ins-

pirado em modelos de fluxo contínuo como o Kanban, mas estruturado com colunas definidas:
Icebox, Planning, In Progress, In Review, Completed e Closed.
As tarefas priorizadas com base nas histórias de usuário eram inicialmente inseridas
na coluna Icebox, onde permaneciam até serem refinadas e planejadas. Durante esse planejamento, cada tarefa recebia estimativas de tempo, pontos de esforço, prioridade, tags e eventuais
relações de dependência. Em seguida, passavam para a coluna In Progress, marcando o início
do desenvolvimento. O tempo de execução foi inicialmente registrado com o cronômetro nativo
do ClickUp, mas passou a ser controlado manualmente após o término do período gratuito da
ferramenta.

48

Tarefas concluídas seguiam para a coluna In Review, aguardando validação do professor
orientador. Quando aprovadas, eram movidas para Completed, onde aguardavam o merge com
a branch principal do projeto. Após esse processo, passavam para a coluna Closed, sendo
oficialmente consideradas finalizadas.
Vale destacar que, ao longo do projeto, foram incluídas tarefas adicionais não previstas
inicialmente, mas relevantes para a maturidade do sistema, como melhorias visuais, ajustes de
licenciamento e tratamento de erros.

6.2.2

Divisão entre Épicos e Tarefas Isoladas
Durante o planejamento, por exigirem múltiplas etapas interdependentes, algumas fun-

cionalidades foram agrupadas em conjuntos maiores chamados de épicos. Essa organização
permitiu que o desenvolvimento seguisse um fluxo coeso e resultasse em entregas completas
e testáveis ao final de cada conjunto.
Os três principais épicos desenvolvidos ao longo deste trabalho foram:
• Atualização do Layout: responsável pela definição da aparência das áreas públicas
e privadas do sistema, com foco na padronização visual e identidade estética;
• Criação Básica de Campanhas e Personagem: responsável por estruturar o fluxo de
criação de campanhas e associação de personagens, ainda utilizando placeholders1 ;
• Criação de Personagens: responsável pela implementação completa do fluxo de criação de um personagem de nível 1.
Esses épicos serão retomados ao longo deste capítulo, com base nos registros feitos
durante o desenvolvimento.

6.3

Execução Técnica
Conforme apresentado no Capítulo 4, o sistema foi desenvolvido com Ruby on Rails,

conteinerizado com Docker e versionado no GitHub, onde também foram realizadas revisões
por meio de pull requests. O banco de dados local utilizou SQLite e os testes automatizados
foram priorizados nas partes críticas da aplicação.
Vale destacar que, embora tenham sido realizados diversos testes, seu escopo foi limitado devido à grande quantidade de tabelas e relações envolvidas. Optou-se, portanto, por
concentrar os esforços em cobrir os fluxos principais da aplicação. Implementar uma cobertura
abrangente exigiria um tempo significativamente maior, o que não era viável dentro dos prazos
estabelecidos.
1

Elementos temporários inseridos no sistema apenas para fins de visualização ou estruturação, sem
funcionalidade real.

49

O fluxo de integração contínua foi mantido com GitHub Actions, garantindo a execução
automática dos testes antes de qualquer merge. No front-end, utilizou-se Turbo, Stimulus e
Tailwind, assegurando uma interface responsiva, coesa e de fácil manutenção.

6.4

Métricas Gerais do Desenvolvimento
Ao longo do ciclo de desenvolvimento, o sistema Themys passou por um processo in-

tenso de construção, validação e refinamento contínuo. Para compreender a dimensão técnica
do trabalho realizado, esta seção apresenta um panorama quantitativo das atividades, funcionalidades, estruturas e artefatos produzidos durante a execução do projeto.
No total, foram concluídas 19 tarefas, das quais três configuraram épicos de maior profundidade técnica e organizacional. No repositório, foram abertas e finalizadas 14 merge requests, totalizando exatamente 600 commits, 548 arquivos alterados e um saldo de 12.141
linhas de código adicionadas ao projeto (13.527 adicionadas e 1.386 removidas). Para que isto
fosse possível, contabilizou-se aproximadamente 190 horas e 4 minutos de programação ativa
dedicados diretamente à implementação destas funcionalidades.
A estrutura do sistema também atingiu um grau de robustez considerável. Foram implementados 34 models distintos, com uso de relacionamentos tradicionais e associações polimórficas. O banco de dados obtido ao final do desenvolvimento ficou composto por 35 tabelas, 258
colunas e 42 chaves estrangeiras, representando a densidade estrutural do modelo.
Em termos de garantia de qualidade, o projeto contou com 211 testes automatizados,
que, ao todo, realizaram 321 assertions2 . O diretório principal do sistema, app/, que concentra a lógica de domínio da aplicação, totalizou 422 arquivos. Já o diretório test/, destinado
exclusivamente aos testes, acumulou 162 arquivos ao final do desenvolvimento.
Por fim, em termos de composição técnica, o código-fonte foi predominantemente escrito
em Ruby (65,3%), seguido por HTML (25,8%), JavaScript (7%), CSS (1,3%)3 e outros recursos
(0,6%). Esses dados foram extraídos diretamente da seção de estatísticas de linguagem do
repositório hospedado no GitHub, conforme ilustra a Figura 20.

Figura 20 – Distribuição das linguagens no repositório segundo o GitHub

2

3

Uma assertion (ou asserção) é uma verificação feita durante um teste automatizado para garantir que
determinado valor ou comportamento esteja conforme o esperado.
Este valor pode ser subestimado devido ao uso do Tailwind, baseado em classes utilitárias.

50

6.5

Épicos Desenvolvidos
Esta seção focará exclusivamente nos épicos desenvolvidos, uma vez que neles se con-

centraram os principais desafios técnicos e decisões de projeto enfrentadas ao longo do trabalho. Para cada épico, serão apresentados seu propósito, o planejamento inicial, a execução
com os desafios encontrados e, por fim, os resultados obtidos ao seu término. Tarefas menores
e isoladas, voltadas à manutenção ou correções pontuais, não serão abordadas em detalhes,
pois atuaram como suporte aos épicos principais ou ajustes complementares.

6.5.1

Atualização do Layout
Este épico teve como objetivo implementar uma padronização visual abrangente no sis-

tema, com base nas diretrizes definidas nos protótipos desenvolvidos no Figma. Isso incluiu
a estilização de páginas como login, cadastro, perfil e dashboard, além de elementos globais
como plano de fundo, ícones, modais e a criação de uma nova logomarca. O intuito era preparar
visualmente o sistema para que o foco, a partir de então, se voltasse ao desenvolvimento das
funcionalidades do MVP.
Para acelerar essa etapa, partiu-se de uma estrutura previamente construída com o auxílio do professor orientador, voltada à autenticação e ao gerenciamento de sessões — referida
aqui como projeto bootstrap4 . Essa decisão permitiu concentrar os esforços nas partes centrais
da proposta, uma vez que fluxos como login e cadastro não representavam desafios técnicos
relevantes para este trabalho. Ainda assim, foi necessário adquirir familiaridade com a estrutura de front-end do Rails, a organização inicial do projeto e as mudanças introduzidas pelo
TailwindCSS 4, que alteraram significativamente a configuração de temas, variáveis e extensões.
Paralelamente ao refinamento visual, também foram padronizados aspectos essenciais
do fluxo de trabalho, como a nomenclatura de branches, critérios para criação de tarefas e estrutura dos pull requests. Essas definições visaram manter consistência tanto na organização
do repositório quanto na escrita do código. Para isso, o ambiente de desenvolvimento (RubyMine5 ) foi configurado com regras de identação e estilo, e integraram-se ferramentas como o
RuboCop6 e o Tailwind Class Sorter7 para reforçar boas práticas e uniformidade.
Apesar de não envolver diretamente programação, essa etapa foi intensiva em discussões e refinamentos, exigindo diversas iterações e validações com o professor orientador até
que se chegasse a um modelo satisfatório. A estrutura final adotada foi mantida ao longo de todo
4

5
6
7

Neste contexto, o termo refere-se a uma base previamente estruturada, reaproveitada com o objetivo
de acelerar o início do desenvolvimento.
https://www.jetbrains.com/ruby/
https://rubocop.org/
https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss

51

o desenvolvimento e contribuiu significativamente para a manutenção da qualidade do código e
do processo colaborativo.
Por fim, foi definida a logomarca oficial do sistema enquanto trabalho de conclusão.
Esse processo contou com uma votação entre os membros do grupo experimental, a partir
de um conjunto de alternativas geradas com auxílio de ferramentas de inteligência artificial. A
logo escolhida passou por refinamentos manuais até se adequar à identidade desejada para o
produto.
Ao final deste épico, o sistema passou a contar com uma identidade visual mais coesa
e moderna. A Figura 21 ilustra a transformação visual consolidada nesta etapa, comparando a
aparência original com a versão atualizada. Cabe ressaltar, contudo, que ajustes visuais pontuais continuaram sendo realizados até a finalização do TCC, visando aprimoramentos de usabilidade e contraste.

Figura 21 – Tela de login, antes e após atualização

6.5.2

Criação Básica de Campanhas e Personagens
Este épico teve como objetivo viabilizar o fluxo central do sistema: a criação de cam-

panhas por mestres e a associação de personagens por jogadores. Para isso, implementou-se
uma estrutura simples e funcional, na qual o mestre pode criar campanhas e compartilhar um
código de convite com os jogadores, que, por sua vez, podem ingressar nas campanhas e vincular personagens. Essa abordagem evitou autenticações complexas e representou a base para
o desenvolvimento dos módulos seguintes.

52

O desenvolvimento começou pela visão do mestre, com a criação de uma tela dedicada à listagem de campanhas e um modal para cadastro de novas, conforme ilustrado na
Figura 22. Como o fluxo completo de criação de personagens ainda não havia sido implementado, utilizou-se dados placeholder apenas para validar a interação entre campanhas, usuários
e personagens. O foco dessa etapa foi garantir a comunicação mínima necessária entre os dois
papéis centrais do sistema: o DM e os jogadores.

Figura 22 – Listagem de campanhas na visão de mestre e modal de criação de nova campanha

Essa etapa marcou o primeiro contato aprofundado do autor com o Turbo do Rails. A
combinação de uma abordagem monolítica com uso intensivo de partials, modais e automatização da camada de apresentação gerou uma curva de aprendizado significativa. Foi necessário
pausar temporariamente o desenvolvimento para revisar conceitos, consultar materiais especializados e discutir pontos críticos com o professor orientador. Esse aprofundamento técnico foi
essencial para superar os desafios e dar continuidade às implementações.
Após a conclusão da visão de mestre, o foco voltou-se à visão de jogador. Para reaproveitar a estrutura já implementada, utilizou-se o ViewComponent 8 , garantindo a reutilização
de elementos visuais de forma organizada e encapsulada. Com a base da visão do jogador
concluída, foi implementado um fluxo compartilhado entre ambas as áreas: cada mestre podia
gerar um código de convite único para sua campanha, e os jogadores, por sua vez, utilizavam
esse código em um modal específico para ingressar diretamente na campanha correspondente,
conforme ilustra a Figura 23.
Vale constar que uma tarefa para automatizar o envio do código por e-mail chegou a
ser registrada, mas como foi considerada secundária para os objetivos deste trabalho, ela foi
inserida na Icebox. O fluxo de convite, portanto, foi desenvolvido de forma simples, porém eficaz:
8

https://viewcomponent.org/ — Biblioteca mantida pelo time do GitHub que permite a criação de componentes reutilizáveis em aplicações Rails, promovendo uma abordagem mais modular e semelhante
à de frameworks como React.

53

Figura 23 – Modal para geração de código de convite (Mestre) e Modal para inserção de código de
convite (Jogador)

um identificador único e de fácil leitura, suficiente para garantir a entrada segura e direta de
jogadores nas campanhas, conforme ilustrado na Figura 24.

Figura 24 – Código responsável por gerar identificadores únicos para o sistema de convite de
campanhas

Para finalizar este épico, foi implementada uma criação de personagem simplificada,
com o objetivo de simular o funcionamento completo do fluxo. Os campos do formulário foram
estruturados a partir de uma hash9 , utilizada para preencher opções de dropdown, como raça,
classe e alinhamento. Não houve preocupação com a fidelidade às regras do SRD nem com
a estética da interface: o foco foi viabilizar a criação funcional de um personagem, ainda que
tecnicamente incorreto, para validar o ciclo de uso do épico de ponta a ponta.
Ao término deste épico, o sistema passou a oferecer uma estrutura funcional mínima
para a interação entre usuários em seus diferentes papéis. Mestres podiam criar campanhas,
gerar códigos de convite e visualizar os jogadores participantes; jogadores, por sua vez, podiam
ingressar nessas campanhas utilizando os códigos recebidos e criar personagens com dados
fictícios, ainda sem funcionalidades vinculadas às regras do SRD. Embora a criação de personagens estivesse em um estado prototípico, essa etapa foi essencial para consolidar a base de
relacionamento entre campanhas, usuários e personagens — uma fundação indispensável para
9

Estrutura de dados nativa da linguagem Ruby, similar a um objeto, que permite armazenar pares de
chave e valor.

54

a mecânica central da plataforma, que seria aprofundada no épico seguinte. Para validar as interações até esse ponto, o sistema foi compartilhado com o grupo experimental, acompanhado
de vídeos demonstrativos, o que possibilitou o recebimento de feedback preliminar e assegurou
que o fluxo proposto por este épico atendesse às expectativas básicas de uso.

6.5.3

Criação Completa de Personagem
O desenvolvimento deste épico seguiu, em diversos momentos, a clássica lei de Murphy:

a cada nova etapa, o que podia dar errado, deu errado. Desde o início, compreendia-se que este
seria o módulo mais desafiador de todo o projeto. Até então, o sistema era agnóstico às regras
do jogo — sua estrutura limitava-se à gestão de usuários e campanhas. Para viabilizar a criação
de personagens dentro dos parâmetros do SRD, foi necessário iniciar um estudo aprofundado
do documento, identificando todas as etapas envolvidas na construção de um personagem,
bem como as variações e particularidades introduzidas pelas diferentes opções disponíveis ao
jogador.
Quase 25% do conteúdo do próprio SRD — um documento de 364 páginas — é dedicado exclusivamente à criação e evolução de personagens, com esse processo iniciando-se na
página 19 e estendendo-se até a página 88. Diante desse cenário, optou-se por uma abordagem baseada em formulário multi-etapas (multi-step form), com navegação dinâmica e validações específicas por etapa. Cada passo seria representado por um FormObject independente,
centralizado em um componente gerenciador responsável por coordenar a transição entre as
etapas, armazenar os dados temporariamente e aplicar validações específicas em cada ponto
do fluxo. Essa estrutura também deveria permitir navegação bidirecional, adaptação dinâmica
conforme decisões anteriores e controle refinado das regras aplicáveis em cada fase.
A ordem das etapas foi planejada com base na lógica de dependência entre escolhas,
inspirando-se na proposta original do SRD, mas adaptada para garantir melhor fluidez e usabilidade. Para facilitar o entendimento e manter consistência com os termos utilizados no sistema,
os nomes dos passos serão apresentados em português seguidos de sua nomenclatura em
inglês (utilizada na interface). Essa abordagem visa evitar confusões entre termos comuns e
termos técnicos, garantindo maior clareza ao longo deste capítulo.
1. Biografia (Biography): nome, gênero, descrição e alinhamento (alignment);
2. Linhagem (Lineage): raça (race), subespécie (subspecies) — se houver — e tamanho
(size);
3. Classe (Class): escolha da classe (class) do personagem;
4. Origem (Origin): definição da origem ou histórico do personagem (background);
5. Atributos (Abilities): distribuição dos pontos de atributos;

55

6. Perícias (Skills): seleção das perícias (skills) disponíveis conforme classe e origem;
7. Truques (Cantrips): escolha dos truques (cantrips), se aplicável à classe;
8. Magias (Spells): escolha das magias (spells), se aplicável à classe;
9. Confirmação (Confirmation): exibição da ficha do personagem (character sheet) para
revisão e confirmação final.
Após pesquisa e diversas conversas com o professor orientador, definiu-se uma arquitetura baseada em três elementos principais:
• Um componente central de navegação, chamado StepManager, responsável por
controlar o fluxo entre as etapas e o estado geral do processo;
• Um formulário base que atuaria como classe abstrata para os FormObjects especializados;
• Um FormObject específico para cada etapa, dedicado à validação e lógica daquela
parte do formulário.
Para garantir persistência e continuidade na criação de personagem — especialmente
considerando a possibilidade do usuário interromper o processo ou trocar de dispositivo — foi
criada uma tabela dedicada no banco de dados. Essa tabela armazenaria o progresso da criação como um único campo JSON, juntamente com a etapa atual do usuário no fluxo. Chegou-se
a considerar o uso de sessions10 , mas optou-se pelo armazenamento em banco de dados por
três motivos principais: maior segurança na persistência dos dados, simplificação do gerenciamento de sessão em múltiplos dispositivos e melhor escalabilidade futura.
Apesar da base arquitetural bem definida, ao longo das mais de 150 horas dedicadas
a este épico, diversos ajustes foram exigidos na estrutura do formulário. A generalização das
funcionalidades na classe pai revelou-se especialmente complexa devido à variedade de dados
manipulados em cada etapa. A dificuldade em configurar os strong parameters11 foi recorrente,
principalmente nas etapas em que os dados possuíam estruturas aninhadas.
Apesar dos inúmeros ajustes, o fluxo de navegação aqui descrito foi estabelecido e
estabilizado com sucesso ao longo do desenvolvimento. Como prova da maturidade do sistema,
uma das últimas alterações — a separação da etapa de magias em duas (uma para Cantrips
e outra para Spells) — foi realizada com esforço mínimo, graças à flexibilidade da estrutura
construída.
10

Sessions são estruturas utilizadas pelo Rails para armazenar temporariamente dados do usuário
entre requisições, geralmente por meio de cookies.
11
Os strong parameters são uma funcionalidade do Rails que define explicitamente quais atributos
podem ser recebidos de forma segura por meio de requisições web.

56

Com a base do multi-step form já funcional, iniciou-se a substituição gradual dos placeholders utilizados no épico anterior. As informações antes concentradas em uma única tela
foram redistribuídas entre etapas específicas, conforme o planejamento original. A partir disso,
deu-se início à implementação efetiva de cada uma dessas etapas, respeitando a ordem definida.
Devido às particularidades técnicas de cada fase, o desenvolvimento será descrito em
etapas, garantindo clareza quanto aos desafios enfrentados e às soluções adotadas.
A etapa Biography foi a mais simples do processo, por não depender de decisões anteriores nem impactar etapas futuras. O foco principal esteve na criação de um componente
reutilizável chamado OptionsGrid, que serviria de base visual e funcional para outras fases
do formulário. Esse componente exibia uma grade de botões clicáveis, cada um representando
uma opção válida, como ilustrado na Figura 25, com o valor selecionado armazenado em um
campo oculto (hidden input)12 para facilitar a submissão.

Figura 25 – Componente OptionsGrid exibindo as possíveis opções de Alignments

O maior desafio técnico dessa etapa foi a introdução ao Stimulus, biblioteca JavaScript
integrada ao Hotwire, utilizada para adicionar interatividade de forma reativa. A curva de aprendizado envolveu leitura da documentação oficial e experimentações práticas, essenciais para
consolidar o entendimento de sua aplicação no projeto.
A implementação da etapa Lineage marcou o início dos desafios sistêmicos do formulário. Em teoria, bastaria permitir ao usuário escolher raça, subespécie (quando aplicável) e
tamanho, armazenando apenas os respectivos IDs. Na prática, no entanto, o avanço das etapas seguintes exigiu retornos frequentes a essa fase, devido a particularidades de determinadas
raças e subespécies que impactavam diretamente regras ou valores aplicados nas fases posteriores.
12

Hidden input é um tipo de campo invisível em formulários HTML, utilizado para armazenar valores
sem exibi-los diretamente ao usuário.

57

A seleção de uma raça desencadeava, sozinha, uma série de comportamentos que precisavam ser tratados de forma reativa:
• Traits: cada raça possui habilidades especiais chamadas traits, que precisavam ser
carregadas e exibidas dinamicamente ao usuário, com explicações claras sobre seus
efeitos.
• Subespécies: algumas raças exigem a escolha de uma subespécie, cujas opções variam conforme a raça. Isso exigiu fluxos distintos de validação e renderização, dependendo da presença ou não dessa escolha.
• Habilidades da subespécie: muitas subespécies adicionam efeitos que impactam etapas futuras, como ganho de cantrips ou alterações de velocidade. Essas informações
precisavam ser armazenadas e propagadas corretamente pelo formulário.
• Tamanho: enquanto a maioria das raças possui um tamanho fixo, algumas oferecem
variação. Nesses casos, foi necessário utilizar o componente OptionsGrid para
permitir a escolha do tamanho desejado.
Desta maneira, algumas raças exigiram adaptações específicas no fluxo de criação. No
caso dos humanos, foi necessário permitir a escolha de uma perícia adicional na etapa correspondente (Skills), armazenando essa informação separadamente. Já os elfos apresentaram um
desafio maior: o traço especial Keen Senses concede ao jogador a possibilidade de escolher entre três perícias — Insight, Perception ou Survival — mesmo que elas não estejam normalmente
disponíveis para sua classe. Para evitar conflitos nas validações da etapa de seleção de perícias, essa escolha foi realocada para a etapa de Lineage, sendo exibida apenas quando a raça
elfo é selecionada. O componente exibido nessa tela só foi implementado posteriormente, durante o desenvolvimento da etapa de perícias, já que sua lógica pertencia originalmente àquela
fase, como pode ser visto na Figura 26.

Figura 26 – Componente adicional exibido apenas para personagens da raça elfo, referente ao
traço Keen Senses

58

A implementação também teve que considerar as dependências cruzadas entre etapas.
Caso o jogador voltasse para alterar suas decisões nesta fase, o sistema precisava redefinir
apenas os campos impactados pela nova escolha (como spells, cantrips ou skills), preservando
as informações das etapas independentes (como atributos) e evitando frustrações com perda
de progresso. Para garantir esse comportamento dinâmico de redefinição parcial, o componente GridOptions foi adaptado para realizar requisições Turbo, permitindo a atualização
imediata das seções afetadas sempre que uma nova opção fosse selecionada. Embora essa
abordagem adicionasse alguns milissegundos de latência — em comparação à instantaneidade
proporcionada pelo Stimulus — ela se mostrou mais eficaz para manter a integridade do fluxo,
especialmente ao lidar com dados sensíveis e interdependentes. Essa solução exigiu estudo
adicional, já que o Turbo possui limitações conhecidas ao lidar com atualizações em blocos
internos de formulários criados com form_with no Rails13 .
Durante essa fase, foi possível perceber que o SRD 5.2.1 havia sido significativamente
expandido em relação à versão anterior, incorporando regras de suplementos oficiais. Essa
mudança inesperada tornou a implementação mais extensa, exigindo decisões técnicas que
não estavam previstas no planejamento inicial, e consolidando a etapa de Lineage como uma
das mais críticas de todo o projeto — embora, como se veria adiante, não fosse a última a
apresentar grandes desafios.
Em contraste com a etapa anterior, a seleção de Class mostrou-se significativamente
mais simples — em parte porque um de seus elementos mais complexos, os chamados features, ainda não havia sido totalmente automatizado até a conclusão deste trabalho. No contexto
do D&D, features são habilidades especiais concedidas pela classe escolhida, capazes de modificar atributos, conceder proficiências ou alterar mecânicas do jogo.
É o caso da Primal Order, da classe druida, que exige inicialmente a escolha entre
duas ordens: Magician ou Warden. Cada escolha ativa efeitos distintos e, no caso de Magician,
ainda há uma segunda decisão encadeada — o jogador precisa definir qual perícia (Arcane ou
Nature) será beneficiada com um bônus, calculado com base no modificador de Wisdow do
personagem, sendo o valor mínimo a ser adicionado +1.
Como essas decisões exigem lógica condicional complexa e afetam várias etapas do
formulário, optou-se por marcar essas features com instruções para que o DM faça os ajustes
manualmente. Embora provisória, essa solução manteve a funcionalidade sem comprometer o
cronograma do projeto.
Além de exibir as informações essenciais da classe escolhida, como atributos principais
e dados de vida, essa etapa também definia regras que influenciariam etapas seguintes —
como o número e o conjunto de perícias disponíveis. Essas regras eram registradas no JSON
da criação para garantir validações consistentes. Caso o usuário alterasse a classe, apenas
13

Formulários construídos com form_with encapsulam blocos de dados de forma dinâmica, e o
Turbo não atualiza corretamente partials localizados dentro desses contextos, exigindo abordagens
específicas para substituição parcial de conteúdo.

59

os campos dependentes, como perícias e magias, eram atualizados, preservando os demais
dados preenchidos.
A etapa Origin, responsável pela escolha do background, termo mantido em inglês neste
trabalho por não haver uma tradução amplamente aceita, apresentou desafios específicos devido à mudança de abordagem entre versões do D&D. Na versão 5.2.1, a seleção de um background passou a ser obrigatória e impacta diretamente atributos, perícias e outras características. Com isso, foi necessário criar campos específicos no JSON de criação para distinguir as
informações escolhidas manualmente pelo usuário daquelas concedidas automaticamente pelo
background.
A principal peculiaridade desta etapa, no entanto, foi a definição dos bônus de atributos. Enquanto versões anteriores do sistema associavam esses bônus às raças, no SRD 5.2.1
essa responsabilidade foi transferida para o background. Com isso, o jogador passa a escolher
três atributos, definidos pelo background selecionado, e deve distribuir entre eles três pontos,
com a limitação de que no máximo dois pontos podem ser alocados em um mesmo atributo.
A implementação dessa lógica foi postergada para um momento posterior, pois dependia do
desenvolvimento prévio da calculadora de atributos, construída na etapa seguinte (de Skills).
A Figura 27 ilustra o resultado final da funcionalidade após a conclusão do componente.

Figura 27 – Mini-calculadora para distribuição dos bônus de atributos concedidos pelo Background

60

Para evitar interferências nas validações e cálculos da etapa seguinte, optou-se por armazenar os bônus de atributos de forma separada e aplicá-los apenas na fase final de confirmação do personagem, assegurando maior previsibilidade no fluxo.
A etapa de distribuição dos atributos (Abiltiies) foi uma das mais complexas de todo o
processo de criação de personagem, tanto em termos de lógica quanto de usabilidade. Conforme definido no SRD 5.2.1, existem três métodos distintos para a definição dos valores de
Ability Scores:
• Standard Array: oferece um conjunto fixo de valores (8, 10, 12, 13, 14, 15), que devem
ser distribuídos entre os seis atributos do personagem, sem repetições. Esse método
garante equilíbrio entre personagens ao limitar o potencial máximo e mínimo de cada
valor.
• Random Generation: rolagem clássica de dados do D&D, onde são rolados 4 dados
de 6 faces, descarta-se o menor valor, e soma-se o resultado. Repete-se isto até que
se tenha seis resultados diferentes. A partir daí, o jogador pode distribuir os valores livremente entre os seis atributos. Este método introduz variações significativas na força
do personagem, podendo gerar combinações mais fracas ou poderosas.
• Point Cost: utiliza o sistema conhecido como Point Buy, no qual o jogador começa com
um total de 27 pontos e pode gastá-los para aumentar os atributos conforme uma tabela de custos progressivos. Este método oferece controle preciso sobre a construção
do personagem, com restrições que evitam desequilíbrios extremos.
Como a configuração de campanha estava fora do escopo deste MVP, os três métodos
foram disponibilizados ao jogador, cabendo ao mestre decidir qual utilizar. A decisão reforça a
proposta do sistema de servir como apoio — e não substituto — ao papel do mestre, mesmo
com possíveis automatizações futuras.
A partir dessa decisão, surgiram dois desafios técnicos. O primeiro foi estrutural: permitir
que o jogador alternasse entre os três métodos sem que dados de um influenciassem os outros.
O sistema também precisava restaurar corretamente os valores preenchidos, sem permitir que
escolhas vantajosas — como as do modo aleatório — comprometessem o equilíbrio do jogo.
O segundo desafio dizia respeito à lógica interna de cada método. Embora compartilhassem semelhanças na interface, cada abordagem possuía particularidades que exigiram tratamentos distintos no código. Dentre elas, o modo de compra de pontos (Point Cost) foi o mais
exigente, pois envolve validações contínuas, controle de orçamento e atualizações dinâmicas
de modificadores, sendo consideravelmente mais complexo do que os demais.
Com estes desafios em mente, foi optado por iniciar o trabalho focando apenas na troca
entre os métodos de distribuição. Para isto, foram implementadas requisições Turbo nos botões, garantindo que os componentes fossem resetados a cada alteração de método e, com

61

isso, preservando a integridade dos dados inseridos. Já a lógica de manipulação dos pontos foi
inteiramente implementada via Stimulus.
Para implementar o método Standard Array, adotou-se uma lógica de alocação dinâmica, em que os valores disponíveis eram exibidos no topo da interface. O jogador podia selecionar um valor e atribuí-lo a qualquer atributo, trocando as posições livremente até que todos
estivessem preenchidos. Essa foi a primeira aplicação prática do Stimulus no projeto, exigindo
várias refatorações até que a lógica de seleção e troca fosse plenamente compreendida e implementada de forma eficiente — experiência que contribuiu significativamente para a fluidez
das etapas seguintes.
Embora semelhante ao método anterior, o Random Generation exigia uma lógica adicional: permitir que o jogador escolhesse entre gerar os valores automaticamente (conforme as
regras) ou inseri-los manualmente (a partir de uma rolagem física). Para evitar a adição de novos elementos à interface, a escolha do modo de rolagem foi implementada com Stimulus, por
meio de um botão do tipo switch. Embora mais estável do que abordagens anteriores baseadas
em Turbo, essa solução gerou certa poluição visual, motivo pelo qual uma tarefa foi registrada
no backlog para refinamentos futuros, após a entrega do TCC.
A Figura 28 apresenta ambas as interfaces Standard Array e Random Generation lado
a lado.

Figura 28 – Tela de distribuição de atributos com os métodos Standard Array (esq.) e Random
Generation (dir.)

62

Por fim, o modo Point Cost foi, de longe, o mais desafiador — tanto do ponto de vista técnico quanto de usabilidade. Sua complexidade conceitual começa pelas próprias regras: todos
os atributos iniciam com valor 8 e, para aumentá-los, o jogador deve gastar pontos (limitados
a 27) conforme uma tabela de custos progressivos. A Tabela 1 apresenta os valores definidos
pelo SRD 5.2.1.
Tabela 1 – Tabela de custos do sistema Point Buy
Valor do Atributo Custo em Pontos
8
0
9
1
10
2
11
3
4
12
13
5
14
7
15
9

Como exemplo, considere um jogador que deseja elevar um atributo de 12 para 14. O
custo total seria de 7 pontos: 4 para chegar a 12, mais 1 para alcançar 13, e 2 adicionais para
atingir 14. Caso deseje recuar de 15 para 14 em outro atributo, ele recuperaria 2 pontos (de
9 para 7), que podem ser realocados. Apesar de simples em teoria, esse sistema costuma
confundir jogadores menos experientes na prática.
Para implementar essa lógica de forma eficiente, o cálculo do custo de pontos foi encapsulado em uma função simples, baseada no padrão identificado entre os valores. A Figura 29
ilustra essa abordagem.

Figura 29 – Trecho da função de cálculo de custo no método Point Cost

O resultado final da tela de distribuição por Point Cost contou com uma interface simplificada, na qual o jogador selecionava um dos atributos (clicando em seu nome ou valor) e
utilizava botões de incremento e decremento para ajustar os valores desejados. A Figura 30
ilustra o resultado final dessa etapa.
O componente aplicava validações para garantir que os atributos permanecessem entre
8 e 15, com um placar no topo indicando, em tempo real, os pontos restantes. Para facilitar
ajustes, também foi adicionado um botão de reset, permitindo reiniciar a distribuição a qualquer
momento.

63

Figura 30 – Tela de distribuição de atributos com método Point Cost

Com os três métodos de distribuição implementados, restava automatizar o cálculo dos
modificadores. Para isso, foi criada uma biblioteca dedicada14 , centralizando essa lógica em
um único local. Como os modificadores influenciam diversas áreas do sistema, como jogadas,
magias e habilidades, essa abordagem favoreceu a manutenção e a escalabilidade. Regras adicionais, como o cálculo da CA e do bônus de proficiência, também foram incluídas na biblioteca,
garantindo consistência e facilitando futuras atualizações caso o D&D sofra alterações.
Com base na Tabela 2, que define a relação entre valores de atributo e seus modificadores correspondentes, foi possível identificar um padrão que permitiu a criação de uma fórmula
simples e reutilizável para a biblioteca, conforme ilustrado na Figura 31.
Tabela 2 – Modificadores por valor de atributo
Valor do atributo Modificador
1
-5
-4
2–3
4–5
-3
6–7
-2
8–9
-1
10–11
0
12–13
+1
14–15
+2
16–17
+3
18–19
+4
20
+5
14

Figura 31 – Função responsável pelo cálculo
dos modificadores de atributo

Bibliotecas são estruturas de código reutilizável, geralmente localizadas no diretório lib/ em aplicações Rails, que concentram funcionalidades comuns separadas da camada de apresentação.

64

Adicionalmente, o sistema foi projetado para preservar, dentro do campo JSON armazenado no banco de dados, tanto o método escolhido quanto o estado atual da distribuição
de pontos. O código também foi estruturado para permitir, no futuro, que o mestre configure a
quantidade total de pontos disponíveis no método de compra de pontos (Point Cost), adaptando
a regra às necessidades específicas de sua campanha.
Apesar de ser uma etapa avançada do fluxo, a implementação da seleção de perícias
(skills) ocorreu de forma surpreendentemente fluida. Isso porque, até esse ponto, informações
essenciais como raça, classe e background já haviam sido coletadas e estruturadas, definindo
tanto as opções disponíveis quanto as escolhas obrigatórias.
O maior desafio foi planejar a criação de um componente genérico de listagem, que pudesse ser reutilizado não apenas nesta etapa, como também nas etapas de seleção de Cantrips
e Spells. A lógica comum entre elas foi abstraída conforme abaixo:
1. Uma lista de opções selecionadas, que incluía tanto as escolhidas manualmente
quanto aquelas concedidas automaticamente pelo background (identificadas por um
ícone de pergaminho) e pela raça (representadas por um ícone de hélice de DNA).
Essas opções automáticas não poderiam ser removidas pelo jogador;
2. Uma lista de opções válidas, contendo apenas as opções permitidas para aquele
personagem, conforme definido nas etapas anteriores;
3. Um placar de controle, responsável por informar as escolhas disponíveis.
A lógica de transição entre listas e atualização dinâmica foi implementada com Stimulus,
tendo como principal desafio a criação de animações suaves e o controle de estado. A listagem
de perícias exigiu um comportamento adicional: recalcular automaticamente o modificador da
habilidade com base no bônus de proficiência do personagem. Para isso, o cálculo foi centralizado na biblioteca recém-criada (lib/). A Tabela 3 apresenta a progressão oficial do bônus
por nível, enquanto a Figura 32 mostra sua implementação no sistema Themys.

Tabela 3 – Progressão do bônus de proficiência
conforme o nível
Nível do Personagem Bônus de Proficiência
1–4
+2
5–8
+3
9–12
+4
13–16
+5
17–20
+6

Figura 32 – Função responsável pelo cálculo do
bônus de proficiência

O resultado final da etapa pode ser visualizado na Figura 33. A tela da esquerda mostra
a interface de seleção, enquanto a da direita exibe a listagem completa de habilidades, com

65

estrelas indicando as Skills escolhidas pelo jogador. A interface é reativa: qualquer alteração
feita na seleção é refletida automaticamente na listagem.

Figura 33 – Tela de seleção de Skills seguida da listagem completa de Skills

Embora, à primeira vista, o componente de listagem possa parecer redundante, sua inclusão foi intencional. Pelas regras do jogo, qualquer personagem pode tentar realizar um teste
de perícia (skill check ) — a diferença é que apenas nas habilidades em que possui proficiência ele adiciona o bônus correspondente. Assim, ainda que repita informações já exibidas na
seleção, a listagem tem o propósito de oferecer contexto e reforçar ao jogador uma regra importante do SRD: seu personagem pode tentar utilizar qualquer Skill, mas só é proficiente em um
conjunto limitado delas.
As etapas de seleção de cantrips e spells reutilizaram o componente de listagem das
perícias, com a adição de um cabeçalho que exibia informações relevantes ao conjurador, calculadas com base na classe e nos atributos do personagem. A exibição dessas etapas era
condicional: personagens não conjuradores as ignoravam; os que possuíam apenas magias de
nível 1 visualizavam apenas a etapa de spells; e aqueles com acesso a cantrips passavam pelas
duas etapas.
Para economizar considerável tempo do jogador, foi implementado um modal informativo
que podia ser aberto ao clicar sobre o nome de qualquer magia na listagem. Esse modal exibia
todos os detalhes relevantes da magia, conforme ilustra a Figura 34.
Ainda que nem todos os detalhes — como o dano — fossem exibidos dinamicamente,
os demais dados acessíveis via modal já representaram um avanço significativo em clareza e
usabilidade para os jogadores.

66

Figura 34 – Modal de exibição dos detalhes de uma magia, acessível diretamente na etapa de
seleção

Como será possível visualizar pela Figura 35, a versão final das duas etapas divergiu
do protótipo original devido a limitações de tempo e escopo — especialmente quanto ao uso de
ícones individuais para cada magia, inviável diante das 84 magias cadastradas (todas de nível
0 e 1 do SRD).

Figura 35 – Tela de seleção de Cantrips (esq.) e Spells (dir.)

A etapa de confirmação marca a conclusão da criação de personagem, reunindo todas
as escolhas feitas pelo jogador, além de exibir dados derivados automaticamente — como velocidade, iniciativa e percepção passiva. Nessa fase, também foram introduzidos recursos para
facilitar a compreensão das regras, como o sistema de palavras-chave interativas.
O sistema de keywords, planejado desde as fases iniciais, foi implementado com sucesso e superou as expectativas. Inspirado na sintaxe do Markdown, permite marcar termos
com colchetes para gerar links automáticos — como [attack roll], que exibe o termo
diretamente, ou [spell]{a magical attack}, onde o texto “a magical attack ” abre o
modal explicativo para o termo “spell”.

67

Essa abordagem trouxe diversos benefícios, como a eliminação de repetições e a reutilização de uma mesma referência com diferentes formas de exibição. Também facilitou o controle semântico, permitindo que variações como [hit die], [hit dice] e [hit point

die] fossem associadas à mesma keyword. Além disso, ajudou a reduzir ambiguidades, pois
termos comuns, como help, só seriam tratados como keywords quando explicitamente decorados com colchetes.
A renderização era feita pelo keyword_linkify, um helper 15 responsável por transformar as marcações em links interativos. Ao clicar em uma keyword, um modal dinâmico exibia
a explicação da regra, permitindo navegação cruzada entre termos de forma contextualizada.
Esse sistema permite uma navegação informativa em cadeia: ao clicar em uma keyword
na ficha (como Saving Throws), um modal exibe sua explicação — que pode conter outras
keywords clicáveis (como Ability Score), permitindo aprofundamento progressivo, como mostrado na Figura 36.

Figura 36 – Encadeamento informativo entre palavras-chave: exibição na ficha, modal explicativo
e referências cruzadas
15

No contexto do Rails, helpers são métodos auxiliares usados para formatar ou transformar dados
exibidos nas views, facilitando a separação entre lógica e apresentação.

68

Além das palavras-chave, foi implementado um sistema de botões de ajuda, voltado à
explicação das regras e funcionalidades do sistema. Esses botões — exibidos como ícones
circulares com interrogação em telas estratégicas — são gerados a partir dos arquivos de tradução (i18n, abreviação de internationalization) e oferecem uma camada adicional de didatismo,
especialmente útil para jogadores iniciantes. Ao serem clicados, abrem um modal com explicações detalhadas sobre a seção correspondente, combinando regras do SRD com sua aplicação
prática no Themys. Esses textos podem incluir outras keywords clicáveis, permitindo uma navegação cruzada entre termos técnicos, conforme ilustrado na Figura 37.

Figura 37 – Exemplo de botão de ajuda no card de Skills e modal explicativo com links para
keywords

Com todos os elementos integrados, a etapa de confirmação consolidou não apenas os
dados do personagem, mas também a proposta central do Themys: atuar como um assistente
didático e acessível. Os sistemas de keywords e botões de ajuda cumpriram esse papel ao organizar o conteúdo de forma interativa, permitindo que o jogador revisasse suas escolhas com
clareza e apoio conceitual. Finalizada a validação, o sistema conduzia à submissão definitiva
do formulário, implementada por meio de um FormObject com lógica transacional. Esse processo foi responsável por criar, de forma segura e atômica, todas as entidades associadas ao
personagem — como atributos, habilidades, magias e vínculo com a campanha — garantindo
consistência e integridade dos dados.

6.6

Últimos Ajustes e Encerramento do Desenvolvimento
Após a conclusão do épico de criação de personagens, restaram ajustes finais indispen-

sáveis para a entrega do sistema como um produto funcional. Esta seção apresenta brevemente
os refinamentos e funcionalidades adicionais implementados nesse encerramento de ciclo.

6.6.1

Edição de Personagem pelo Mestre
Com o fluxo de criação finalizado, tornou-se necessário permitir que o mestre pudesse

editar personagens já criados — funcionalidade ainda mais relevante diante da decisão de não
automatizar os feats nesta versão inicial. A escolha de oferecer liberdade total de edição reflete

69

um princípio central do RPG: a autoridade narrativa do mestre, mesmo que isso implique ajustes
fora das regras do SRD.
Para viabilizar essa edição, foi necessário primeiro disponibilizar a visualização da ficha
dentro da campanha. Como a etapa final da criação já representava a Ficha de Personagem,
sua estrutura foi modularizada, permitindo reutilização tanto na área do jogador quanto na visão
do mestre. Nesta última, adicionou-se um cabeçalho exclusivo com o botão de edição, como
ilustrado na Figura 38.

Figura 38 – Cabeçalho de edição exibido na ficha de personagem para o mestre

Embora a proposta inicial contemplasse a edição direta na ficha do personagem (inline),
essa abordagem exigiria um nível de dinamismo mais avançado, inviável dentro do tempo disponível. Optou-se, portanto, por uma solução mais simples: uma página exclusiva de edição,
voltada ao uso administrativo do mestre. A interface, como mostra a Figura 39, priorizava a funcionalidade, com campos de entrada padrão e validações mínimas — suficientes para garantir
integridade básica sem limitar a flexibilidade necessária para ajustes manuais.

Figura 39 – Página de edição de personagem na visão do mestre, com edição livre de classe e
habilidades

70

Espera-se, em versões futuras, aplicar melhorias visuais para torná-la mais alinhada à
identidade geral do sistema — mas, para os fins deste trabalho, priorizou-se a funcionalidade
sobre a estética.
Para a edição de magias, foi criada uma página separada. Nela, o mestre visualiza todas
as 84 magias cadastradas no sistema — abrangendo todos os feitiços de nível 0 e 1 do SRD —
organizadas por nível e com um filtro adicional por classe. Dessa forma, mesmo que a classe
do personagem não tivesse acesso natural a certas magias, o mestre ainda podia adicioná-las
ou removê-las conforme julgasse necessário para sua campanha, conforme ilustra a Figura 40.

Figura 40 – Página de edição de magias na visão do mestre, com as magias agrupadas por nível
e opção de filtro por classe

Essa funcionalidade encerrou o desenvolvimento da edição de personagens, completando o ciclo iniciado no épico anterior. Embora o sistema não tenha utilizado atualizações
automáticas com Hotwire, como inicialmente planejado, os recursos entregues já permitiam que
jogadores e mestres utilizassem o sistema de forma flexível e funcional durante suas sessões.
Nas horas finais antes da liberação do sistema para testes, foram feitas diversas correções visuais e ajustes pontuais — incluindo um bug crítico de permissões, onde jogadores
podiam acessar fichas de outros personagens que não lhes pertenciam. Após a correção desse
problema, nenhum outro erro impeditivo foi identificado, permitindo o início do processo de testes com segurança.

6.6.2

Remoção de imagem gerada por AI
Durante os preparativos finais para a divulgação do sistema, o autor buscou comunida-

des ativas de jogadores de D&D onde pudesse apresentar o Themys e convidar participantes
para a etapa de testes. Uma das principais candidatas era uma grande comunidade online dedicada exclusivamente ao jogo, com dezenas de milhares de membros ativos. No entanto, ao

71

tentar submeter a proposta, foi solicitado que removesse a imagem principal da página, por se
tratar de uma arte gerada por inteligência artificial, conforme ilustrado na Figura 41.

Figura 41 – Versão anterior da página inicial do Themys, utilizando imagem gerada por inteligência artificial

Embora a imagem fosse apenas um placeholder, buscou-se diálogo com os moderadores da comunidade para esclarecer que seu uso era pontual e sem fins comerciais. Ainda assim,
os administradores mantiveram a proibição de imagens geradas por IA, levando à substituição
da arte pela versão exibida na Figura 42.

Figura 42 – Página inicial atualizada do Themys, sem utilizar nenhum conteúdo gerado por IA

Ao submeter a nova versão da página para reanálise, surgiu uma nova objeção por
parte dos moderadores da comunidade: desta vez, em relação à logomarca do sistema. A logo

72

do Themys — mostrada na Figura 43 — havia sido inicialmente gerada com auxílio de inteligência artificial, mas foi posteriormente modificada manualmente e escolhida por votação entre os
membros do grupo experimental, como mencionado anteriormente neste trabalho. Ainda assim,
os administradores mantiveram sua política e solicitaram a remoção da logo como condição
para permitir a divulgação.

Figura 43 – Logo do Themys, gerada com auxílio de IA e posteriormente modificada manualmente

Diante da limitação de tempo, da rigidez da moderação e da natureza acadêmica do
projeto, optou-se por não seguir com a divulgação naquela comunidade. Ainda que frustrante,
a experiência serviu como aprendizado sobre os desafios éticos e comunicacionais que cercam o desenvolvimento de um MVP experimental, especialmente em contextos sensíveis como
comunidades criativas e colaborativas.

6.7

Banco de Dados Final
Ao final do desenvolvimento, o banco de dados do sistema Themys consolidou-se como

uma estrutura robusta e coerente, capaz de dar suporte às funcionalidades previstas no escopo
do MVP. A Figura 44 apresenta o diagrama final da modelagem.
O modelo contempla um total de 35 tabelas, distribuídas entre entidades principais, tabelas de relacionamento e estruturas auxiliares. Entre os destaques, é possível observar:
• A presença de tabelas polimórficas, como o uso de EntityAbilityScore, que
permite representar os valores de atributos tanto para personagens quanto para outras
entidades futuras — como monstros e NPCs, que também compartilham a lógica de
atributos no sistema — oferecendo flexibilidade e escalabilidade à modelagem;
• A separação de certas entidades que, embora compartilhem estruturas quase idênticas, precisaram ser isoladas por representarem contextos distintos — como é o
caso de klass_primary_abilities e klass_saving_throws. Ambas associam uma classe a um atributo, mas a primeira indica os atributos fundamentais da

73

Figura 44 – Diagrama final do banco de dados do sistema Themys

classe (como força ou carisma), enquanto a segunda define os atributos nos quais a
classe possui testes de resistência aprimorados (saving throws);
• A existência de tabelas auxiliares, como keywords e character_creations,
que não estão diretamente ligadas a modelos centrais como personagens ou campanhas, mas desempenharam papéis fundamentais na organização do projeto e no suporte ao funcionamento de funcionalidades como o sistema de explicações contextuais
e o fluxo multi-etapas de criação de personagem.
Embora pudesse ser resumida em menos tabelas, a estrutura foi deliberadamente modelada de forma mais granular para facilitar futuras expansões. A separação das entidades
permite alterações incrementais, como novas colunas ou tabelas auxiliares, sem comprometer
a integridade do banco existente. Assim, funcionalidades futuras como evolução de personagens (level-up), ajustes de regras ou suporte a outras versões do D&D poderão ser integradas
de forma modular, preservando a base atual.
Dessa forma, o banco de dados final reflete não apenas as demandas práticas do projeto
entregue, mas também um cuidado técnico orientado à continuidade. Caso o sistema venha a
ser utilizado ou expandido após a conclusão deste trabalho acadêmico — o que está nos planos
do autor — sua estrutura estará preparada para crescer de maneira estável e organizada.

74

7 RESULTADOS
Este capítulo apresenta os resultados obtidos durante a fase final do projeto, com foco
na validação prática da ferramenta desenvolvida.

7.1

Sessão Real de Teste
Para validar o sistema em um ambiente prático e obter impressões concretas sobre

sua usabilidade, foi realizada uma sessão de jogo no dia 07 de junho de 2025 com um grupo
de jogadores. Esta foi a primeira vez em que o Themys foi utilizado em condições completas,
atuando tanto como ficha digital quanto como ferramenta de apoio ao mestre.
O grupo era composto por quatro pessoas: o mestre, com ampla experiência em D&D;
um jogador com experiência intermediária; um jogador sem experiência; e o autor deste trabalho. Os jogadores criaram seus personagens utilizando o sistema, enquanto o mestre utilizou a
funcionalidade de edição para promovê-los ao nível 2.
Durante a criação de personagens, dois dados chamaram atenção. O participante sem
experiência prévia levou 23 minutos e 13 segundos para concluir sua ficha, enquanto o participante com conhecimento intermediário, que já possuía uma ficha física pronta, levou 23 minutos e 34 segundos para transcrevê-la para o sistema1 .
Durante o processo de level up, o mestre utilizou o sistema para filtrar magias por classe
e exibir suas descrições, facilitando a escolha de novos feitiços. Como a listagem de magias
ainda não estava acessível na visão de Jogador, o grupo utilizou alternadamente o computador
do mestre para selecionar as magias diretamente na tela de edição. A dinâmica, sugerida espontaneamente pelo mestre, ocorreu de forma fluida, sendo bem recebida por todos os participantes. A filtragem de magias foi considerada uma das funcionalidades mais úteis da plataforma
e permitiu que o mestre concluísse a evolução dos três personagens em apenas 11 minutos e
40 segundos.
Os tempos mencionados nos parágrafos anteriores são bastante positivos, considerando
que a criação de fichas em D&D 5e costuma levar entre 1 a 3 horas para iniciantes e raramente
menos de 30 minutos para jogadores experientes2 . Nesse contexto, os resultados obtidos evidenciam a eficiência do sistema. Vale destacar que os participantes foram deixados à vontade
durante todo o processo, sem orientações diretas, o que incluiu pausas e conversas paralelas,
reforçando o realismo do ambiente de teste.
Um fato interessante observado durante a criação dos personagens envolveu o jogador
com conhecimento intermediário. Ao chegar na etapa de seleção de magias, ele notou que uma
1

2

Apesar de já ter a ficha pronta, esse jogador utilizou parte do tempo para explorar as opções e revisar
as funcionalidades do sistema antes de concluir o processo.
Embora não existam dados oficiais sobre isso, é possível encontrar relatos recorrentes em fóruns,
vídeos e comunidades online dedicadas ao D&D, como o Reddit (r/dnd) e grupos especializados
no Discord.

75

magia presente em sua ficha física não estava disponível na listagem oferecida pelo sistema.
O mestre, utilizando o próprio Themys, realizou uma busca pelas magias disponíveis para a
classe em questão e confirmou que, de fato, aquela magia não era compatível com a classe
escolhida, e que o jogador havia escolhido ela por engano. Além disso, o jogador percebeu que
havia anotado erroneamente uma Spell como se fosse um Cantrip, confundindo o nível real da
magia. Com o auxílio da ferramenta, foi possível corrigir ambos os equívocos antes do início da
sessão.
Também foi possível perceber que, mesmo com as limitações impostas pela ausência
do conteúdo completo do D&D, o sistema já demonstrava grande potencial por sua flexibilidade.
Durante a sessão, um dos jogadores quis utilizar uma raça que não está presente no SRD.
Para contornar essa limitação, o mestre sugeriu escolher a raça mais similar disponível, com
a promessa de que, posteriormente, ajustaria manualmente os atributos e características do
personagem para refletir fielmente os benefícios da raça originalmente desejada.
Durante a condução do jogo, o jogador iniciante manteve a ficha digital aberta durante
toda a sessão. Ele utilizou o sistema de forma recorrente para consultar magias, atributos e
habilidades, o que demonstrou a usabilidade da plataforma mesmo para quem tinha pouco
conhecimento prévio de D&D.
Além disso, os comentários dos jogadores reforçaram a utilidade das explicações contextuais e da estrutura clara da interface. O sistema de keywords e os modais de ajuda foram
especialmente elogiados por exibirem descrições completas ao selecionar magias. O jogador
com experiência intermediária destacou: “Uma das partes que mais achei interessante é quando
você vai selecionar as magias e já diz a descrição, isto ajuda muito”. Outro comentário relevante
foi: “Ajudou muito o iniciante, porque o sistema está muito pedagógico”.
Do ponto de vista do mestre, o sistema também se mostrou funcional e prático. A possibilidade de acessar as fichas completas permitiu verificar rapidamente informações como CA,
percepção passiva, bônus de atributos e lista de magias. Segundo relato: “O sistema me ajudou
bastante a ir checar as informações dos jogadores, principalmente as magias. Além de coisas
como CA, percepção passiva”.
Mesmo com essas vantagens, a sessão também serviu para identificar limitações e oportunidades de melhoria:
• A tela de seleção de magias apresentava um problema: ao salvar as escolhas com o
filtro de classe ativado, o sistema descartava as magias pertencentes a outras classes.
Isso foi contornado realizando a consulta com o filtro ativo, mas efetuando a seleção
com o filtro desativado;
• Faltavam descrições dos traits das subespécies (com exceção dos elfos), o que gerou
algumas dúvidas durante a criação dos personagens, exigindo complementação com
o livro;

76

• Os modais de magia não possuíam rolagem vertical, dificultando a leitura de magias
extensas em dispositivos móveis;
• Não havia campo para anotações durante a campanha, o que levou o mestre a recorrer
a ferramentas externas;
• Não era possível alterar rapidamente os pontos de vida atuais durante o combate.
Embora isso não tenha impedido o andamento da sessão, é um ponto que pode ser
aprimorado;
• Foi observado que os jogadores tendiam a preencher todos os campos da criação de
personagem como se fossem obrigatórios, o que indica a necessidade de sinalizar
com mais clareza quais campos são opcionais. Trata-se apenas de uma constatação
do autor, sem que isso tenha causado problemas durante a criação.
Mesmo com as limitações identificadas, o grupo se mostrou entusiasmado com o sistema e trouxe diversas sugestões de melhorias, muitas delas já previstas, o que serviu como
validação indireta das decisões adotadas no desenvolvimento. De forma geral, a sessão foi considerada um sucesso: o Themys cumpriu seu papel principal de apoiar tanto jogadores quanto
mestres, oferecendo uma experiência prática, fluida e intuitiva. As contribuições e observações
colhidas durante a sessão foram organizadas e documentadas, e servirão de base para aprimoramentos futuros do sistema.

7.2

Respostas do Formulário de Feedback
Para complementar a avaliação prática do sistema, foi disponibilizado um formulário no

próprio site do Themys, com um convite aberto à participação dos usuários. O objetivo principal
era colher impressões sobre a experiência de criação e edição de personagens, por meio de
perguntas qualitativas e quantitativas, com envio anônimo. Além disso, foram incluídas questões
opcionais sobre o uso de imagens geradas por inteligência artificial, com o objetivo de entender
como essa tecnologia pode influenciar a percepção de qualidade e credibilidade em projetos
digitais.
Apesar da possibilidade de explorar diversos aspectos do sistema por meio de questionamentos mais amplos, optou-se por limitar a quantidade de perguntas e priorizar questões
fechadas e objetivas. Essa decisão visou aumentar a taxa de resposta, considerando que formulários longos ou excessivamente detalhados tendem a desmotivar a participação voluntária
dos usuários.

77

7.2.1

Perfil dos participantes
No total, 29 pessoas responderam ao formulário, com idades entre 17 e 32 anos. Destas,

26 eram do Brasil, 2 da Polônia e 1 da Argentina. Entre os respondentes brasileiros, as respostas
vieram dos seguintes estados, por ordem de participação: Paraná, Santa Catarina, Rio Grande
do Sul e Pernambuco.
Em relação à forma de participação nas mesas de RPG, a maioria dos respondentes
afirmou jogar apenas como personagem, enquanto uma parcela significativa declarou atuar
tanto como jogador quanto como mestre. Um número menor indicou ainda não ter jogado, mas
demonstrou interesse em participar futuramente.
Quanto ao nível de familiaridade com a 5ª edição de D&D, os participantes apresentaram uma distribuição equilibrada: aproximadamente um terço declarou ter conhecimento “baixo”
ou “nenhum”, enquanto a maior parte indicou possuir “familiaridade média”. Um grupo menor
demonstrou “alta familiaridade”, refletindo um público diverso e representativo para a avaliação
de usabilidade proposta, conforme ilustrado na Figura 45.

Figura 45 – Distribuição do nível de familiaridade dos participantes com D&D 5e

7.2.2

Dados quantitativos
Além das perguntas abertas e de perfil, o formulário contou com uma série de questões

avaliativas que pediam aos participantes que atribuíssem notas de 1 a 5 a diferentes aspectos
do sistema, sendo “1” equivalente a “discordo totalmente” e “5” a “concordo totalmente”. Essa
estrutura permitiu uma análise quantitativa clara e objetiva da experiência de uso.
Os resultados foram amplamente positivos. A pergunta “A criação de personagens foi
intuitiva?” obteve uma média de “4,76”, indicando que a grande maioria considerou o processo
simples e bem estruturado. A percepção de ganho de tempo e esforço na criação do personagem foi ainda mais expressiva, com média de “4,86”.

78

As funcionalidades de suporte foram bem recebidas: tanto o sistema de keywords quanto
os botões de ajuda contextuais obtiveram média de “4,66”. A ficha de personagem teve a menor
média, com “4,38”, reflexo de seu estágio atual, embora funcional, ainda carece de melhorias
de usabilidade. A adoção de componentes como accordions poderia, por exemplo, tornar a
navegação mais fluida. O design da área do jogador foi ligeiramente melhor avaliado, com média
de “4,52”. Em contrapartida, entre as funcionalidades específicas, a filtragem de magias se
destacou, com média de “4,72”, demonstrando ser uma das ferramentas mais bem avaliadas do
sistema, mesmo ainda não estando implementada com todos os recursos planejados.
A recomendação do sistema foi bastante elevada: a maioria dos respondentes afirmou
que indicaria o Themys para outros jogadores ou mestres, resultando em uma média de 4,76.
Quanto à adoção futura, 20 dos 29 participantes (aproximadamente 69%) responderam que
incorporariam o Themys em suas campanhas de RPG do jeito que está. Os demais afirmaram
que o fariam apenas mediante melhorias significativas, o que, ainda assim, evidencia um forte
potencial de adoção, acompanhado de uma expectativa clara por evolução contínua do sistema,
conforme ilustrado na Figura 46.

Figura 46 – Intenção dos usuários em incorporar o Themys em campanhas futuras

Por fim, a avaliação geral do Themys recebeu uma média de 4,34, um resultado expressivo considerando que o projeto ainda se encontra em fase inicial de desenvolvimento. As notas
foram distribuídas conforme detalhado a seguir:
• Nota 5: 11 respostas;
• Nota 4: 17 respostas;
• Nota 3: 1 resposta
Os principais motivos citados para a adoção do sistema incluem a praticidade na criação
de personagens, a interface intuitiva e a centralização das informações da campanha. Muitos
usuários destacaram a utilidade do Themys especialmente para iniciantes, enfatizando como o

79

sistema descomplica etapas normalmente complexas do D&D. Outros elogiaram a economia de
tempo e a clareza das explicações fornecidas durante o processo.
Entre os pontos levantados pelos respondentes que condicionaram o uso a melhorias,
destacam-se a ausência de suporte a níveis mais altos de personagens, a limitação do conteúdo apenas ao SRD, a falta de recursos mais avançados para edição de ficha pelo jogador, e
o desejo por maior acessibilidade visual (como personalização de cores ou tamanhos de fonte).
Também foram mencionadas limitações como a falta de tradução para outros idiomas e a ausência de funcionalidades como exportação para PDF.

7.2.3

Percepção sobre uso de Inteligência Artificial
Embora a amostra não seja massiva, os resultados reforçam que a escolha de não

utilizar imagens geradas por IA foi prudente: 7 participantes (aproximadamente 24%) afirmaram
que poderiam ter deixado de testar o sistema ao se deparar com esse tipo de imagem. Isso
indica que, mesmo sem representar a maioria, existe uma parcela significativa de usuários cuja
decisão de experimentar a plataforma poderia ser negativamente influenciada pela presença de
conteúdo automatizado.
Além disso, os participantes foram questionados sobre o impacto que o uso de conteúdo
gerado por inteligência artificial poderia ter na percepção geral sobre a qualidade do sistema.
Embora a maioria tenha afirmado que isso não afetaria sua opinião, 9 dos 29 participantes
(cerca de 31%) responderam que o uso de IA reduziria sua percepção de qualidade, mesmo
sem comprometer diretamente sua decisão de utilizá-lo.
Ainda mais significativo foi o resultado da pergunta final, que avaliou a validade do uso
de imagens geradas por IA em projetos acadêmicos: 5 pessoas (cerca de 17%) consideraram
tal prática inadequada, mesmo em contextos educativos, exploratórios ou acadêmicos. Esse
dado revela que parte dos respondentes não diferencia o uso de IA em projetos de baixo ou alto
orçamento, demonstrando um posicionamento mais rígido diante da utilização dessa tecnologia,
possivelmente associado ao impacto negativo que a IA vem causando na vida de artistas e
criadores. Seja válida ou não essa postura, o resultado evidencia um ponto de atenção relevante
para quem busca a validação do público: ainda que representem uma minoria, tais opiniões
compõem uma parcela significativa que merece ser considerada no planejamento de futuras
interações e divulgações do sistema.
Apesar de os resultados oferecerem indícios relevantes, é importante observar que o
número de participantes foi relativamente baixo. Uma pesquisa mais ampla, com foco específico
na recepção de conteúdo gerado por inteligência artificial, poderia fornecer dados ainda mais
expressivos e precisos sobre a percepção do público em relação ao uso dessa tecnologia em
projetos acadêmicos e digitais.

80

Ainda que não tenha sido o foco central do formulário ou deste trabalho de conclusão,
a inclusão dessas questões forneceu percepções valiosas sobre a recepção do projeto em um
cenário cada vez mais atento ao uso de IA.

7.3

Métricas do Sistema
Com o objetivo de complementar os dados qualitativos e quantitativos apresentados an-

teriormente, esta seção traz um panorama das métricas coletadas por meio do monitoramento
do site oficial do Themys entre os dias 03/06/2025 e 18/06/2025.
Durante esse período, o sistema registrou 1.420 visualizações de página, distribuídas em
262 visitas, realizadas por 181 visitantes únicos. A diferença entre os dois últimos indicadores
reside no fato de que uma mesma pessoa pode realizar múltiplas visitas em momentos distintos,
gerando mais de uma sessão. A taxa de rejeição (bounce rate) foi de 39%, indicando que cerca
de 4 em cada 10 visitantes deixaram o site após visualizar apenas uma página.
Quanto às origens de tráfego, os principais canais de acesso foram o Instagram (com
50 visitantes únicos) e o Reddit (com 10 visitantes), além de acessos pontuais de mecanismos
como o próprio ChatGPT.
A análise por dispositivos revelou que 62% dos acessos ocorreram via dispositivos móveis, enquanto 34% vieram de computadores e 3% de tablets. Quanto aos sistemas operacionais, a maioria utilizou Android (49%), seguido de iOS (30%), Windows (22%), com pequenas
parcelas em Linux e macOS (ambos com 7%). Entre os navegadores, o Google Chrome se
destacou, representando 66% dos acessos.
Em termos geográficos, o público foi majoritariamente brasileiro, com 171 visitantes,
seguido por Estados Unidos (4), Canadá (2), e acessos isolados de Alemanha, Portugal, Polônia
e Irlanda.
No total, durante o período analisado, o sistema contou com:
• 77 usuários cadastrados;
• 35 campanhas criadas;
• 40 personagens registrados.
Adicionalmente, ao analisar a proporção entre visitantes únicos e usuários cadastrados,
observa-se um índice de engajamento bastante positivo: cerca de 42,5% dos visitantes efetivamente criaram uma conta no sistema. Esse dado evidencia tanto o interesse despertado pela
proposta do Themys quanto a efetividade da interface e do fluxo de apresentação na conversão
de visitantes em usuários ativos.

81

8 CONSIDERAÇÕES FINAIS
O desenvolvimento do Themys teve início com uma etapa de planejamento sólida, estruturada em torno de objetivos claros: oferecer uma ferramenta prática, acessível e fiel ao sistema
de regras do D&D 5.2.1, com foco na criação e gestão de personagens. A proposta era ambiciosa, ancorada em um cronograma viável, mas com um escopo que acabou sendo subestimado.
Ao longo da execução, diferentes fatores impactaram diretamente o fluxo de desenvolvimento. A complexidade conceitual do SRD, com suas exceções, dependências e lacunas,
revelou-se mais desafiadora do que o previsto. As inúmeras minúcias presentes nas entrelinhas
das regras, somadas a contratempos externos e às limitações de tempo, comprometeram o
avanço esperado.
A adaptabilidade e a capacidade de reagir às dificuldades foram fundamentais para a
conclusão do projeto, viabilizando uma entrega satisfatória por meio de uma estratégia baseada
no princípio de Pareto: priorizar os 20% de funcionalidades que entregariam 80% do valor percebido pelo usuário. Essa decisão permitiu reorientar os esforços e concluir uma versão funcional
do sistema. Embora reduzido em escopo, o MVP foi validado na prática por usuários reais, o que
representa um resultado mais significativo do que a implementação integral das funcionalidades
previstas, afinal, a completude técnica perde valor quando não está acompanhada de utilidade
real para o público-alvo. Essa utilidade, por sua vez, pôde ser observada de forma concreta na
avaliação prática do Themys, que demonstrou boa recepção por diferentes perfis de usuários,
incluindo jogadores sem familiaridade prévia com o D&D.
Adicionalmente, o monitoramento do site e o engajamento dos visitantes indicaram interesse real por parte da comunidade usuária, apesar de o projeto ainda estar em fase inicial. O
índice de conversão entre visitantes únicos e usuários cadastrados reforça esse potencial.
Este trabalho encerra-se com a entrega de um produto que, pelo potencial significativo
demonstrado, apresenta a ambição de vir a ser comercializado futuramente. Mesmo em versão
beta, o Themys se consolida como uma base validada para futuras evoluções — tanto técnicas
quanto conceituais — dentro do ecossistema de ferramentas digitais voltadas ao TTRPG. Ao
final desta etapa, cabe ao autor refletir sobre a trajetória percorrida, aplicar os aprendizados
obtidos e dar continuidade ao desenvolvimento do sistema conforme planejado — com a mesma
determinação que guiou este projeto do início ao fim.

82

REFERÊNCIAS

BOTELHO, M.; PETRONILHO, C.; DIAS, F. O roleplaying game (rpg) como ferramenta
dialógica para a promoção dos letramentos digital e literário. Lingu@ Nostr@ - Revista
Virtual de Estudos de Gramática e Linguística, v. 8, p. 277–294, 07 2023. Disponível
em: https://www.researchgate.net/publication/372673097_O_roleplaying_game_RPG_como_
ferramenta_dialogica_para_a_promocao_dos_letramentos_digital_e_literario.
CONSORTIUM, A. B. MoSCoW Prioritisation. 2024. Disponível em: https://www.agilebusiness.
org/dsdm-project-framework/moscow-prioririsation.html.
. [s.n.], 2018. p. 283–299.
HAMMER, J. et al. Learning and role-playing games. In:
ISBN 9781315637532. Disponível em: https://www.researchgate.net/publication/331764500_
Learning_and_Role-Playing_Games.
MARKS, A. Invention and Innovation in TTRPGs. 2024. Disponível em: https://
cannibalhalflinggaming.com/2024/08/15/invention-and-innovation-in-ttrpgs/.
PYE, L. Dungeons and dragons and the critical failure: A thematic analysis of the ttrpg
communities reception of the leaked ogl 1.1. The Motley Undergraduate Journal, v. 1, p.
82–108, 10 2023. ISSN 2817-2051. Disponível em: https://www.researchgate.net/publication/
375910074_Dungeons_and_Dragons_and_the_Critical_Failure_A_Thematic_Analysis_of_the_
TTRPG_Communities_Reception_of_the_Leaked_OGL_11/references.
SHI, Y. Feasibility of rpg for learning about empathy, creativity, and self-efficacy. Lecture Notes
in Education Psychology and Public Media, v. 42, p. 264–271, 03 2024. Disponível em:
https://www.researchgate.net/publication/378963746_Feasibility_of_RPG_for_Learning_about_
Empathy_Creativity_and_Self-efficacy/references.
SOMMERVILLE, I. Software Engineering. 10th. ed. Harlow, Essex: Pearson Education, 2018.
Authorized adaptation from the United States edition. ISBN 978-1-292-09613-1.
TURNER, N. How to play the “Buy a feature“ design game. 2011. Disponível em:
https://www.uxforthemasses.com/buy-the-feature/.

83

GLOSSÁRIO
Alignment A tendência moral e ética do personagem, comumente expressa em eixos como
Leal/Caótico e Bom/Mau. 7, 56
atributo Uma das características básicas que define a força, destreza, constituição, inteligência,
sabedoria e carisma do personagem. 15, 59, 60
CA Classe de Armadura (do inglês, Armor Class), uma medida da capacidade de um personagem de evitar ataques. 63, 75, 114, 116, 119
Campanha Uma série de sessões interligadas de um TTRPG, formando uma história contínua
com personagens recorrentes, desafios progressivos e desenvolvimento narrativo ao
longo do tempo. 13–16
Cantrip uma magia de nível zero que pode ser usada ilimitadamente. 6, 7, 15, 43–45, 55, 66,
75, 114, 115, 118
Charisma Um atributo que reflete a força de personalidade, persuasão e magnetismo do personagem. As vezes usado para definir a beleza de um personagem. 114
Class A ocupação ou papel principal do personagem, como mago, guerreiro ou clérigo, que
determina suas habilidades, magias e estilo de jogo. 58
Ficha de Personagem O conjunto organizado de informações que representam um personagem jogável, incluindo atributos, habilidades, equipamentos e demais características.
69
FormObject Padrão arquitetural utilizado em aplicações Ruby on Rails para encapsular a lógica
de formulários complexos em classes independentes do modelo principal, facilitando a
validação, organização e testabilidade dos dados submetidos pelo usuário. 54, 55
HP Pontos de Vida (do inglês, Health Points), uma medida da quantidade de dano que um
personagem pode suportar antes de cair inconsciente ou morrer. 114, 116
Inspiration Um recurso que concede vantagem em jogadas de dado, usado como recompensa
narrativa. 114
proficiência Representa a familiaridade e treinamento de um personagem com determinadas
armas, armaduras, ferramentas ou habilidades, concedendo bônus em jogadas relacionadas. 63, 65
Prone Uma condição em que o personagem está caído, dificultando ataques e movimento. 114
Skill Uma perícia que representa o conhecimento ou treinamento especializado de um personagem. 7, 15, 45, 59, 65, 68
Sleight of Hand Uma habilidade usada para realizar truques manuais e ações furtivas com
destreza. 114
Spell Um magia que pode ser conjurada, variando em efeitos e níveis. 6, 7, 15, 43, 44, 55, 66,
75, 114, 115

84

APÊNDICE A – Formulário Completo Utilizado na Pesquisa com Usuários

85

Este apêndice apresenta, na íntegra, o formulário estruturado utilizado na etapa de validação com os usuários. O documento foi elaborado com o objetivo de complementar as entrevistas inviáveis presencialmente, abordando temas essenciais para o desenvolvimento do
sistema. As questões estão organizadas em oito seções, conforme descrito no Capítulo 5.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

TCC - Themys - Levantamento de Requisitos
* Indica uma pergunta obrigatória

Introdução

Agradecimento
De antemão, gostaria de agradecer imensamente pela sua participação e disponibilidade em contribuir
com este projeto. Sua colaboração é fundamental para o sucesso desta iniciativa, pois os dados coletados
aqui (os quantitativos, não os seus dados de RPG) serão essenciais para definir os primeiros passos do
desenvolvimento do aplicativo.
Então, novamente, muito obrigado pela sua participação!

1 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

O que é Themys?
Salve, pessoal!
Meu nome é Adnir Andrade, estudante do quinto período de Tecnologia em Sistemas para Internet da
UTFPR - Câmpus Guarapuava. Você está prestes a iniciar o formulário de levantamento de requisitos
que ajudará a moldar o meu projeto de Trabalho de Conclusão de Curso: O Themys Project.
Mas o que é o Themys Project e o qual o propósito deste formulário?
De maneira resumida, o Themys será um assistente de TTRPG, provendo suporte para campanhas que
utilizem o sistema de regras (SRD) 5.2 do Dungeons & Dragons. O intuito dele não é ser um
virtualizador, mas sim um facilitador: tornando o fluxo do jogo mais fácil tanto para iniciantes quanto
para veteranos. O objetivo é que este web app melhore a experiência geral das sessões de jogo, fazendo
com que os jogadores passem menos tempo procurando por valores e regras e mais tempo arruinando os
planos do mestre com conversas desnecessárias com personagens secundários que estavam ali só por
estar.
E para garantir que o aplicativo em sua primeira versão possa agregar positivamente à experiência do
jogo, preciso assegurar que as funcionalidades estejam alinhadas com os problemas reais enfrentados
pelos jogadores de RPG. É aí que entra o levantamento de requisitos.
Portanto, ao responder esta série de perguntas, tenha em mente não apenas o que faz você mais gostar de
RPG, mas como também tudo o que faz você ter preguiça de jogar: Aquela classe que é muito
trabalhosa, aquela regra que é tão confusa que você simplesmente ignora o Livro do Jogador, aqueles
termos que fazem você abrir tantas vezes o glossário para entender o que significam, etc.
Ao final, as suas respostas ajudarão a compreender melhor as necessidades e expectativas dos usuários,
me permitindo criar um aplicativo que realmente atenda às demandas da comunidade de RPG e que
realmente seja útil para você ao final. Além do mais, todos que participarem deste processo inicial
receberão um aplicativo para poder usar em suas campanhas, porque eu quero me formar e agora tenho
que fazer isto aqui funcionar.
Enfim, agradeço novamente pelo seu tempo e a sua valiosa contribuição!
Agora rolem a iniciativa!
- Adnir Andrade

Perfil do Usuário
Seção para determinar o perfil do participante.

2 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

1.

I) Qual seu nome (opcional)

2.

II) Qual sua idade? *

3.

III) Qual seu gênero? *

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

Marcar apenas uma oval.
Masculino
Feminino
Outro:

4.

IV) Qual seu entendimento de inglês? *
(considere apenas leitura)
Marcar apenas uma oval.
Não consigo ler nada em inglês.
Quase nada, apenas o básico, como o nome das classes.
Entendo só os termos principais, como Armor Class, Health Points, Initiative, etc.
Não conheço termos específicos, mas considero que consigo me virar bem.
Consigo entender tudo, a não ser que seja uma palavra muito desconhecida.

Experiência com RPG
Seção para determinar a experiência e preferências do participante com RPG.

3 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

5.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

V) Há quanto tempo você joga RPG de Mesa? *
Marcar apenas uma oval.
Menos de 1 ano
1 a 2 anos
3 a 5 anos
6 a 10 anos
Mais de 10 anos

6.

VI) Há quanto tempo você joga Dungeons & Dragons? *
Marcar apenas uma oval.
Menos de 1 ano
1 a 2 anos
3 a 5 anos
6 a 10 anos
Mais de 10 anos

7.

VII) Com que frequência você joga RPG de mesa? *
Marcar apenas uma oval.
Raramente (menos de uma vez por mês)
Ocasionalmente (uma vez por mês)
Frequentemente (várias vezes por mês)
Muito frequentemente (semanalmente)
Sempre que posso (várias vezes por semana)

4 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

8.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

VIII) Quando consegue jogar, qual a média de tempo que joga em um
único dia?

*

Marcar apenas uma oval.
Menos de 1 hora
Entre 1 e 2 horas
Entre 2 e 4 horas
Entre 4 e 6 horas
Mais de 6 horas

9.

IX) Quando você joga, prefere o papel de Mestre ou Jogador? *
Marcar apenas uma oval.
Mestre
Jogador

10.

5 of 27

X) por qual motivo este é o seu papel preferido? *

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

11.

XI) Ainda baseado na pergunta IX, por qual motivo o outro papel não *
é o seu favorito?

12.

XII) Como geralmente você joga RPG? *
Marcar apenas uma oval.
Pessoalmente
Remotamente
Híbrido (algumas pessoas pessoalmente, outras remotamente, em uma única mesa)
Outro:

13.

XII) Qual formato de sessões você geralmente joga? *
Marcar apenas uma oval.
Campanha (uma aventura com começo, meio e fim que geralmente depende de várias
sessões)
One-Shots (uma aventura que geralmente leva uma ou duas sessões para se encerrar)
Outro:

6 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

14.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

*

XIV) Quais suas classes favoritas? (Selecione de 1 até 3)
Se sua classe favorita não está na lista, é porque ela não é suportada
pelo SRD 5.2
Marque todas que se aplicam.

Barbarian / Bárbaro
Bard / Bardo
Cleric / Clérigo
Druid / Druida
Fighter / Guerreiro
Monk / Monge
Paladin / Paladino
Ranger / Patrulheiro || Guardião
Rogue / Ladino
Sorcerer / Feiticeiro
Warlock / Bruxo
Wizard / Mago

7 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

15.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XV) Quais suas raças favoritas? (Selecione de 1 até 3)

*

Se sua raça favorita não está na lista, é porque ela não é suportada
pelo SRD 5.2
Marque todas que se aplicam.

Dwarf
Elf
Halfling
Human
Dragonborn
Gnome
Half-Elf
Half-Orc
Tiefling

Uso de Aplicativos Estabelecidos
Seção para determinar a experiência do participante com aplicativos de RPG/TTRPG já
consolidados no mercado.
OBSERVAÇÃO: As perguntas a seguir são baseadas no caso de você ter usado um aplicativo no
passado.
Caso não tenha usado, responda a primeira questão e siga para a próxima seção.

16.

XVI) Você já usou algum aplicativo para auxiliar em sessões de
RPG?

*

Marcar apenas uma oval.
Sim
Não

8 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

17.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XVII) Com que frequência você utiliza aplicativos para RPG?
Marcar apenas uma oval.
Raramente (apenas para situações extraordinárias)
Frequentemente (nem todas as sessões eu uso, mas de vez em quando estou precisando)
Sempre (toda sessão eu preciso abrir ele ao menos uma vez)

9 of 27

18.

XVIII) Caso lembre, cite quais aplicativos já utilizou:

19.

XIX) quais funcionalidades você mais utilizou nesses aplicativo?
(Criador/gerenciador de personagem; Criação de NPCs; Rolagem de
dados; Etc.)

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

20.

XX) Quais funcionalidades você sentiu falta nos aplicativos de RPG
que já utilizou?

21.

XXI) Quando utilizou estes aplicativos, qual o meio principal que usou
para acessá-los?
Marcar apenas uma oval.
Computador/Notebook
Dispositivo móvel

22.

10 of 27

XXII) Se deixou de usar algum destes aplicativos, cite quais foram os
maiores motivos que te levaram a esta decisão:

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

23.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XXIII) Se você pudesse escolher uma funcionalidade a ser
implementada para melhorar o seu aplicativo favorito, qual seria?

Problemas do Dungeons & Dragons e TTRPG
Seção para determinar a opinião do participante com relação as dificuldades do RPG.
Perguntas destinadas tanto para Mestres quanto para Jogadores. Existe uma pergunta opcional
apenas para mestres ao final desta seção.

11 of 27

24.

XXIV) Na sua opinião, quais são os maiores problemas na hora de
criar um personagem novo?

*

25.

XXV) Na sua opinião, quais são os maiores desafios na hora de
manter/gerenciar um personagem?

*

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

26.

XXVI) Na sua opinião, qual a maior dificuldade para marcar/fazer
sessões de RPG?

*

27.

XXVII) Marque da lista abaixo os itens que você mais precisa

*

verificar
Marque todas que se aplicam.

Pontos de Vida (Hit Points)
Classe de Armadura / Defesa (Armor Class)
Habilidades (Stats como Carisma, Inteligência, etc.)
Modificadores de habilidade (Ability Modifiers)
Habilidades (Skills)
Sentidos (Sensory Perception, como Percepção passiva, Investigação passiva, etc.)
Condições (Conditions como atordoado, paralisado, queimando)
Iniciativa (Initiative)
Ações (Actions)
Magias/Cantrips (Spells/Cantrips)
Equipamento atual (Current Equipment)
Inventário (Inventory)
Características e Traços (Features & Traits)
Informações do Background (Background Information)
Anotações (Notes)
Lista de Proficiência e Treinamento (Proficiency and Training List, como Idiomas,
treinamento com armas e armaduras)
Velocidade (Movement Speed)
Outro:

12 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

28.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XVIII) Marque da lista abaixo os itens que você menos precisa
verificar

*

Marque todas que se aplicam.

Pontos de Vida (Hit Points)
Classe de Armadura / Defesa (Armor Class)
Habilidades (Stats como Carisma, Inteligência, etc.)
Modificadores de habilidade (Ability Modifiers)
Habilidades (Skills)
Sentidos (Sensory Perception, como Percepção passiva, Investigação passiva, etc.)
Condições (Conditions como atordoado, paralisado, queimando)
Iniciativa (Initiative)
Ações (Actions)
Magias/Cantrips (Spells/Cantrips)
Equipamento atual (Current Equipment)
Inventário (Inventory)
Características e Traços (Features & Traits)
Informações do Background (Background Information)
Anotações (Notes)
Lista de Proficiência e Treinamento (Proficiency and Training List, como Idiomas,
treinamento com armas e armaduras)
Velocidade (Movement Speed)
Outro:

29.

13 of 27

XXIX) Na sua opinião, qual o seu maior problema com as regras do
D&Ds?

*

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

30.

XXX) Se você pudesse automatizar alguma regra, qual seria? *

31.

Apenas para Mestres:
XXXI) Qual seria hoje o principal problema que você enfrenta quando
precisa organizar uma sessão/campanha?

32.

Apenas para Mestres:
XXXII) Qual seria hoje o principal problema que você enfrenta
durante uma sessão/campanha?

14 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

33.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

Apenas para Mestres:
XXXIII) Você já sofreu e/ou sofre com trapaças por parte de
jogador(es)? Se sim, poderia citar um exemplo e como acabou por
descobrir?

34.

Apenas para Mestres:
XXXIV) Suponhamos que o sistema não consiga implementar, neste
primeiro momento, um sistema automático de Level Up, fazendo com
que você tivesse que fazer as alterações manualmente em cada
personagem. Isto seria um impeditivo para você utilizar O aplicativo?

15 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

Validações
Seção para determinar a importância de possíveis recursos pelos olhos do participante.
Observação: As respostas a seguir utilizam de uma escala para julgar o quanto você usaria ou não
determinado recurso. Eles variam em uma escala de 0 a 10, sendo 0 equivalente a "nunca usaria" e
10 equivalente a "usaria sempre".
Na dúvida, considere estas questões como "o quão importante você considera", visto que alguns
recursos você não usará com frequência, mas podem ser úteis e valiosos para você ao longo de
uma sessão/campanha.

35.

*

XXXV) Em uma escala de 0 a 10, o quanto você usaria:
Uma dashboard (painel de informações) com as informações de um
determinado personagem/NPC
Marcar apenas uma oval.
0

36.

1

2

3

4

5

6

7

8

9

10

*

XXXVI) Em uma escala de 0 a 10, o quanto você usaria:
Um sistema de diário para registrar eventos, observações, e anotações
em geral
Marcar apenas uma oval.
0

16 of 27

1

2

3

4

5

6

7

8

9

10

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

37.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XXXVII) Em uma escala de 0 a 10, o quanto você usaria:

*

Um gerenciador de inventário (adicionar, remover e transferir itens)
Marcar apenas uma oval.
0

38.

1

2

3

4

5

6

7

8

9

10

XXXVIII) Em uma escala de 0 a 10, o quanto você usaria:

*

Personalização de personagem (carregar imagem / trocar ícone /
trocar plano de fundo)
Marcar apenas uma oval.
0

39.

1

2

3

4

5

6

7

8

9

10

XXXIX) Em uma escala de 0 a 10, o quanto você usaria:

*

Agendador de Sessões
(sistema para que o mestre cadastre um dia e os jogadores votem se
podem ou não participar)
Marcar apenas uma oval.
0

17 of 27

1

2

3

4

5

6

7

8

9

10

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

40.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

*

XL) Em uma escala de 0 a 10, o quanto você usaria:
Soundboard
(sistema para usar sons durante a campanha, por mestres e jogadores)
Marcar apenas uma oval.
0

41.

1

2

3

4

5

6

7

8

9

10

XLI) Em uma escala de 0 a 10, o quanto você usaria:

*

Preset de Personagens
(Deixar um personagem de nível 1 pré-pronto para adicionar em
sessões futuras - No caso de jogadores que gostam de planejar seu
personagem com antecedência)
Marcar apenas uma oval.
0

42.

1

2

3

4

5

6

7

8

9

10

XLII) Em uma escala de 0 a 10, o quanto você usaria: *
Sistema de Level up automático
Marcar apenas uma oval.
0

18 of 27

1

2

3

4

5

6

7

8

9

10

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

43.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

XLIII) Em uma escala de 0 a 10, o quanto você usaria: *
Sistema de pesquisa de regras/magias/habilidades
Marcar apenas uma oval.
0

44.

1

2

3

4

5

6

7

8

9

10

XLIV) Em uma escala de 0 a 10, o quanto você usaria:

*

Sistema de consulta de keywords
(para poder clicar em uma palavra/termo específico do jogo e saber
o seu significado na hora)
Marcar apenas uma oval.
0

45.

1

2

3

4

5

6

7

8

9

10

XLV) Em uma escala de 0 a 10, o quanto você usaria: *
Sistema de criação de personagem
Marcar apenas uma oval.
0

19 of 27

1

2

3

4

5

6

7

8

9

10

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

46.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

*

XLVI) Em uma escala de 0 a 10, o quanto você usaria:
Sistema de gerenciamento de magias (spell slots, se a magia aguarda
um long ou short rest, controle de componentes)
Marcar apenas uma oval.
0

47.

1

2

3

4

5

6

7

8

9

10

XLVII) Em uma escala de 0 a 10, o quanto você usaria: *
Sistema de chat interno
Marcar apenas uma oval.
0

48.

1

2

3

4

5

6

7

8

9

10

XLVIII) Em uma escala de 0 a 10, o quanto você usaria: *
Sistema de rolagem de dados
Marcar apenas uma oval.
0

20 of 27

1

2

3

4

5

6

7

8

9

10

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

49.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

Apenas para mestres:
XLIX) Em uma escala de 0 a 10, o quanto você usaria:
Sistema de criação de NPCs
Marcar apenas uma oval.
0

1

2

3

4

5

6

7

8

9

10

Monetização
Seção para verificar a disposição do participante quanto a monetização do software.
Por envolver servidores centralizados, o aplicativo terá que gerar alguma receita para poder se
manter no ar.
As perguntas a seguir são referentes ao meio de monetização, e se você acharia justo ou não. Ao
final, terá uma pergunta quanto ao valor a ser pago.
OBSERVAÇÃO: Não serão utilizados como monetização todos os meios citados abaixo. Esta
seção é apenas para ajudar a escolher o meio de monetização. Possivelmente, apenas um ou dois
deles serão utilizados.

50.

L) publicidade pelo aplicativo com opção de compra única para
remoção de propagandas

*

Marcar apenas uma oval.
Não acho justo
Indiferente
Acho justo

21 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

51.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

LI) Assinatura mensal/anual *
Marcar apenas uma oval.
Não acho justo
Indiferente
Acho justo

52.

*

LII) Versão freemium
(Versão básica com suporte para apenas um personagem. Diferentes
níveis de versões pagas libera mais slots de personagens/campanhas,
etc.)
Marcar apenas uma oval.
Não acho justo
Indiferente
Acho justo

53.

LIII) Conteúdo exclusivo por assinatura
(pagamento libera funcionalidades mais específicas, como preset de
personagem, alteração da descrição de regras, etc.)

*

Marcar apenas uma oval.
Não acho justo
Indiferente
Acho justo

22 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

54.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

LIV) Auxílio/doações por ferramentas como patreon *
Marcar apenas uma oval.
Não acho justo
Indiferente
Acho justo

DISCLAIMER:
As perguntas a seguir são completamente hipotéticas. NÃO será cobrado de quem está participando
deste processo.
O plano é prover acesso gratuito para todos que participarem do começo ao fim deste processo de
desenvolvimento.
Ainda assim, sejam realistas - Pensem que vai existir custos para manter isto no ar, mas que vocês tem o
próprio orçamento de vocês. Pensem em um valor que vocês conseguiriam pagar e que seria justo para o
uso do aplicativo.

55.

LV) Qual é o máximo que você estaria disposto a pagar por mês por
determinado aplicativo?

*

Marcar apenas uma oval.
R$ 5,00
Entre R$ 5,00 a R$ 10,00
Entre R$ 10,00 a R$ 20,00
Entre R$ 20,00 a R$ 30,00
Entre R$ 30,00 a R$ 40,00

23 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

56.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

*

LVI) Qual é o máximo que você estaria disposto a pagar por ano por
determinado aplicativo? (este valor seria um pacote anual)
Marcar apenas uma oval.
R$ 50,00
Entre R$ 50,00 a R$ 100,00
Entre R$ 100,00 a R$ 200,00
Entre R$ 200,00 a R$ 300,00
Entre R$ 300,00 a R$ 400,00

57.

LVII) Você assinaria um plano "party" onde seria pago um valor mais *
alto para que você possa adicionar até 5 outras pessoas na mesma
conta?
(Em uma média, este tipo de plano, como visto no Spotify e
Duolingo, tendem a ser 50% a 70% mais caros do que o plano
individual, deixando ao usuário o planejamento de cobrar dos amigos/
familiares)
Marcar apenas uma oval.
Sim
Não

Considerações finais
Últimas perguntas e encerramento da pesquisa.

24 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

58.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

LVIII) Como você gostaria de reportar problemas ou sugerir
melhorias no aplicativo durante o período de desenvolvimento/teste?

*

Marque todas que se aplicam.

Diretamente pelo aplicativo
Grupo do Whatsapp
Grupo do Discord
E-mail
Outro:

25 of 27

59.

LIX) Você tem alguma sugestão ou comentário adicional sobre o
aplicativo?

*

60.

LX) Como você acha que o aplicativo pode melhorar a sua
experiência de jogo?

*

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

61.

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

*

LXI) Durante esta entrevista, foram utilizadas três fontes diferentes:
Uma para título, outra para descrição, outra para opções.
Você teve dificuldades para ler/entender o que estava escrito? Alguma
destas fontes te desagradou? Ou você não teve problemas com elas?
Comente abaixo:

Este conteúdo não foi criado nem aprovado pelo Google.

Formulários

26 of 27

2025-07-08, 1:08 p.m.

TCC - Themys - Levantamento de Requisitos

27 of 27

https://docs.google.com/forms/u/1/d/1JUz_4YycdsIytUwmHuLkE_1I3...

2025-07-08, 1:08 p.m.

113

APÊNDICE B – Requisitos Identificados por Meio de Pesquisa de
Formulário

114

B.1

Features para o TCC
1. Pesquisa de regras/magias/habilidades
a) Ao pesquisar por frase ou termo, retorna com as possíveis informações que
usuário está buscando
b) Possibilidade de adicionar tags para busca mais rápida
2. Sistema de Keywords para pesquisa
a) Na descrição de regras/magias/habilidades, palavras/termos que referenciem
outras regras/magias/habilidades estarão destacadas;
b) Ao clicar na palavra destacada, uma janela mostrará ao usuário a definição
da palavra/termo;
c) Exemplos de keywords: CA, HP, Charisma, Prone, Sleight of Hand, Inspiration, etc.
3. Gerenciamento de Magias I
a) Controle de quais magias um usuário pode ter/escolher dado determinado
nível/classe;
b) Valores de dano e efeito atualizados conforme atributos/bônus fixos do personagem.
4. Gerenciador de Inventário I
a) Adicionar e remover itens do inventário;
b) Sem controle de peso;
5. Criação de Characters I
a) Criação de Player Characters de nível 1;
b) Seleção de classe, raça, skills, e distribuição de atributos;
c) O Personagem criado aqui pode ser usado para Ficha de Jogador do Jogador
ou como um NPC para Mestre;
i. Para ser usado na Ficha de Jogador ou como NPC, é preciso completar
a tarefa “Dashboard de PCs e NPCs”.
d) A ordem das raças/classes liberadas para criação será definida de acordo
resultado da primeira pesquisa (formulário de requisitos);
e) Se o tempo permitir, ainda dentro desta tarefa, será possível implementar seleção de Spells e Cantrips baseado na classe escolhida.

115

6. Agendador de Sessões I
a) Mestre poderá escolher uma data para que Jogadores da sua campanha possam votar se podem participar ou não.
7. Dashboard de PCs e NPCs
a) Dashboard com informações gerais de NPC e Player Characters, como atributos, skills, Spells, Cantrips, etc.;
b) A Dashboard de NPC estará disponível após a conclusão da tarefa de criação
de NPCs;
c) A implementação das informações da Dashboard se dará conforme resultado
da primeira pesquisa (formulário de requisitos);
8. Soundboard (efeitos sonoros)
a) Soundboard básica com efeitos sonoros separados por categorias e pesquisáveis por tags;
9. Diário de campanha e personagens I
a) Área para o Jogador e Mestre criar e editar textos e anotações importantes.
10. Sistema de Level Up I
a) Ao aumentar de nível, Jogador poderá visualizar os benefícios e instruções
do que deve fazer para sua classe;
b) Alterações devem ser feitas manualmente pelo Mestre;
c) Multiclasse ainda não incluso.
11. Presets de Characters
a) Criar PCs ou NPCs para salvar na memória;
b) Personagens podem ser então carregados em slots de Characters (no caso
de um Jogador dentro de uma campanha) ou de NPCs reutilizáveis (no caso
de Mestres);
c) A liberação de NPCs será realizada após tarefa de inclusão de NPCs no sistema;
d) O nível dos personagens criados como preset dependerá diretamente da tarefa de Criação de Characters.
12. Personalização de Personagem I
a) Possibilidade de carregar imagem na Ficha de Personagem.

116

13. Rolagem de Dados I
a) Rolagem de dados dentro do sistema;
b) Animação básica em 2D;
c) Log de rolagens com data/horário.
14. Gerenciamento de Combate I
a) Controle de turno;
i. Mestre precisará adicionar os Jogadores envolvidos em determinado
combate e, manualmente, adicionar cada inimigo;
ii. Mestre precisará informar o resultado da iniciativa de cada um no momento da criação de um combate.
b) Controle básico de HP;
i. Os envolvidos no combate terão apenas tais informações:
A. Nome, para identificação;
B. CA;
C. HP, com um botão para “receber dano” ou “receber cura”.
c) Aplicações e controle de Condições.
i. A aplicação é manual;
ii. O controle da condição é automático, a não ser que específico.
15. Gerenciador de Equipamentos
a) Visualização de dano das armas somado aos modificadores
b) Visualização da CA concedida por cada equipamento;
i. Mestre terá que alterar a CA do Jogador manualmente, ou permitir edição.
c) Jogador poderá visualizar se pode ou não usar determinado equipamento/arma
16. Cronômetro I
a) Cronômetro compartilhado para controle de tempo;
b) Cronômetro aparecerá para todos os Jogadores para decisões que dependam
de tempo;
c) Cronômetro é controlado pelo Mestre (pausar, resetar, cancelar, adicionar
tempo).

117

17. Tutorial de uso do aplicativo
a) Tutorial do próprio aplicativo para utilização das funcionalidades;
b) Tutorial poderá ser ativado/desativado a qualquer momento.
18. Tradução e internacionalização do conteúdo
a) Tradução para PT-BR (idioma padrão do aplicativo é inglês)

B.2

Features para futuras versões (pós-TCC)
1. Soundboard (trilha sonora)
a) Verificação de implementação de trilha sonora:
i. Carregar músicas e utilizar o aplicativo como player;
ii. Ou integração com o Spotify.
2. Agendador de Sessões II
a) Usuário poderá cadastrar no aplicativo as datas que tem disponível para jogar;
b) O sistema verificará se existem datas livres nesse intervalo.
3. Diário de campanha e personagens II
a) Possibilidade do Mestre compartilhar anotações com todos.
4. Diário de campanha e personagens III
a) Integração com o Notion.
5. Gerenciamento de Magias II
a) Atualização de valores conforme nível e slots utilizados do personagem.
6. Gerenciamento de Magias III
a) Atualização focada exclusivamente nas magias, tornando o sistema completamente automatizado.
7. Gerenciador de Inventário II
a) Transferir itens entre Jogadores;
b) Controle de carga.
8. Criação de Characters II

118

a) Criação de NPCs aleatórios de nível 1, com classe, raças, atributos, skills,
magias e Cantrips (se aplicável).
9. Criação de Character III
a) Criação de PCs acima do nível 1;
b) Inclui multiclasse.
10. Criação de Character IV
a) Criação de NPCs aleatórios acima do nível 1;
b) Inclui multiclasse.
11. Sistema de Level Up II
a) Ao subir de nível, o Jogador poderá visualizar os benefícios da sua classe;
b) Caso tenha escolhas, como novas magias ou especialização de classe, poderá escolher entre elas;
c) Alterações serão feitas automaticamente, sem necessidade de entradas manuais.
d) Multiclasse ainda não incluso.
12. Sistema de Level Up III
a) Inclusão de multiclasse.
13. Personalização de Personagem II
a) Possibilidade de escolher a aparência através da criação de avatar;
b) Análise da possibilidade de carregar "assets"para modificar cabelo, olhos e
outras características disponíveis.
14. Rolagem de Dados II
a) Rolagens de dados em 3D;
b) Opção de escolher entre animação 2D ou 3D.
15. Chat Interno I
a) Criação de sistema de chat dentro da campanha.
16. Chat Interno II
a) Integração com o Discord.
17. Gerenciamento de Combate II

119

a) Devido à complexidade, necessário estudo para desenvolver um sistema completo de combate.
18. Cronômetro II
a) Cronômetro será integrado ao sistema de combate para acompanhar o tempo
(cada turno geralmente dura 6 segundos).
19. Gerenciador de Equipamentos II
a) Modificar a CA do usuário conforme o equipamento utilizado;
b) Alterar a movimentação e bônus de acordo com o equipamento equipado.
20. Integração com AI I
a) Integração com AI para geração de imagens a partir de prompts.
21. Integração com AI II
a) Geração de imagens de PCs e NPCs;
b) O sistema utilizará as informações da ficha para gerar as imagens, em vez de
prompts;
c) O Jogador/Mestre poderá escolher entre as opções de imagem geradas.
22. Integração com AI III
a) Integração com Chat AI, como o ChatGPT.
23. Acessibilidade I
a) Criar uma versão acessível para deficientes visuais.

ANEXOS

121

ANEXO A – Ficha Oficial de Personagem da 5a Edição de Dungeons &
Dragons, publicada pela Wizards of the Coast

CHARACTER NAME

CLASS & LEVEL

BACKGROUND

PLAYER NAME

RACE

ALIGNMENT

EXPERIENCE POINTS

INSPIRATION

STRENGTH
ARMOR
CLASS

PROFICIENCY BONUS

INITIATIVE

SPEED
PERSONALITY TRAITS

Hit Point Maximum

Strength
DEXTERITY

Dexterity
Constitution
Intelligence

CURRENT HIT POINTS

IDEALS

TEMPORARY HIT POINTS

BONDS

Wisdom
Charisma
CONSTITUTION

SAVING THROWS

Total

Acrobatics (Dex)

SUCCESSES

Animal Handling (Wis)

FAILURES

Arcana (Int)
INTELLIGENCE

HIT DICE

DEATH SAVES

FLAWS

Athletics (Str)
Deception (Cha)

NAME

History (Int)

ATK BONUS DAMAGE/TYPE

Insight (Wis)
Intimidation (Cha)
WISDOM

Investigation (Int)
Medicine (Wis)
Nature (Int)
Perception (Wis)
Performance (Cha)

CHARISMA

Persuasion (Cha)
Religion (Int)
Sleight of Hand (Dex)
Stealth (Dex)
Survival (Wis)
SKILLS

ATTACKS & SPELLCASTING

PASSIVE WISDOM (PERCEPTION)
CP

SP

EP

GP

PP

OTHER PROFICIENCIES & LANGUAGES

EQUIPMENT
TM & © 2014 Wizards of the Coast LLC. Permission is granted to photocopy this document for personal use.

FEATURES & TRAITS

CHARACTER NAME

AGE

HEIGHT

WEIGHT

EYES

SKIN

HAIR

NAME

SYMBOL

CHARACTER APPEARANCE

ALLIES & ORGANIZATIONS

ADDITIONAL FEATURES & TRAITS

CHARACTER BACKSTORY

TREASURE
TM & © 2014 Wizards of the Coast LLC. Permission is granted to photocopy this document for personal use.

SPELLCASTING
ABILITY

SPELLCASTING
CLASS

0

SPELL
LEVEL

CANTRIPS

SLOTS TOTAL

3

ED

PR

6

SLOTS EXPENDED

1
EPAR

SPELL SAVE DC

7
SPELL NAME

SPELLS KNOWN

4

8

2

5
9

TM & © 2014 Wizards of the Coast LLC. Permission is granted to photocopy this document for personal use.

SPELL ATTACK
BONUS

