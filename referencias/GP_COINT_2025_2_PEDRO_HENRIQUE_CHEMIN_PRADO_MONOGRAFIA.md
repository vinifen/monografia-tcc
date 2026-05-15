---
source_pdf: referencias/GP_COINT_2025_2_PEDRO_HENRIQUE_CHEMIN_PRADO_MONOGRAFIA.pdf
extracted_with: pdftotext (UTF-8)
---

UNIVERSIDADE TECNOLÓGICA FEDERAL DO PARANÁ

PEDRO HENRIQUE CHEMIN PRADO

RODEI - APLICATIVO MÓVEL PARA GESTÃO FINANCEIRA DE CAMINHÕES

GUARAPUAVA
2025

PEDRO HENRIQUE CHEMIN PRADO

RODEI - APLICATIVO MÓVEL PARA GESTÃO FINANCEIRA DE CAMINHÕES

Rodei – A Mobile App for Truck Financial Management

Trabalho de Conclusão de Curso de Graduação
apresentado como requisito para obtenção do
título de Tecnólogo em Tecnologia em Sistemas
para Internet do Curso Superior de Tecnologia
em Sistemas para Internet da Universidade
Tecnológica Federal do Paraná.
Orientador: Prof. Dr. Andres Jessé Porfirio
Coorientador: Prof. Dr. Diego Marczal

GUARAPUAVA
2025

4.0 Internacional

Esta licença permite compartilhamento, remixe, adaptação e criação a partir do trabalho, mesmo para fins comerciais, desde que sejam atribuídos créditos ao(s) autor(es).
Conteúdos elaborados por terceiros, citados e referenciados nesta obra não são cobertos pela licença.

PEDRO HENRIQUE CHEMIN PRADO

RODEI - APLICATIVO MÓVEL PARA GESTÃO FINANCEIRA DE CAMINHÕES

Trabalho de Conclusão de Curso de Graduação
apresentado como requisito para obtenção do
título de Tecnólogo em Tecnologia em Sistemas
para Internet do Curso Superior de Tecnologia
em Sistemas para Internet da Universidade
Tecnológica Federal do Paraná.

Data de aprovação: 19/novembro/2025

Andres Jessé Porfirio
Doutor
Universidade Tecnológica Federal do Paraná - Campus Guarapuava

Diego Marczal
Doutor
Universidade Tecnológica Federal do Paraná - Campus Guarapuava

Luciano Ogiboski
Doutor
Universidade Tecnológica Federal do Paraná - Campus Guarapuava

Dênis Lucas Silva
Mestre
Universidade Tecnológica Federal do Paraná - Campus Guarapuava
GUARAPUAVA
2025

AGRADECIMENTOS
A conclusão deste trabalho marca o fim de uma importante etapa da minha trajetória,
mas também o início de muitas outras que ainda estão por vir. Cada desafio superado, aprendizado adquirido e conquista alcançada servem como motivação para continuar evoluindo, buscando sempre novos conhecimentos e oportunidades de crescimento pessoal e profissional.
A realização deste trabalho representa o encerramento de uma fase significativa da minha vida, e nada disso teria sido possível sem o apoio e a presença de pessoas especiais que,
de diferentes formas, contribuíram para minha caminhada.
Mesmo que nem todos possam ser mencionados individualmente, deixo aqui meu sincero agradecimento a cada um que, com gestos, palavras ou incentivos, fez parte dessa trajetória.
Agradeço primeiramente à minha família, por todos esses anos de apoio incondicional.
Em especial à minha mãe, Danielle, e ao meu pai, Manolo, por sempre acreditarem em mim e
nunca duvidarem das minhas escolhas. Também não posso deixar de expressar minha gratidão
à Letícia, o amor da minha vida, por todo o carinho, paciência e motivação durante esse período.
Meu reconhecimento se estende aos professores, que tornaram possível cada conquista
ao longo da formação. Agradeço especialmente os meus orientadores, Prof. Dr. Andres Jessé
Porfirio e Prof. Dr. Diego Marczal, por todo o apoio, dedicação e amizade. Vocês foram fundamentais na construção deste trabalho.
Estendo meus agradecimentos ao Prof. Dr. Eleandro Maschio e à Profa. Dra. Renata
Stange, com os quais tive o privilégio de trabalhar em suas disciplinas. Os aprendizados adquiridos com vocês serão levados por toda a vida. A todos os demais docentes do curso de
Sistemas para Internet, meu muito obrigado por se dedicarem diariamente a formar profissionais competentes e humanos.
Por fim, mas não menos importante, agradeço aos meus amigos de infância Viniccius
Ferreira, Nicolas Veiga e Eduardo Kowalczyk, que estiveram ao meu lado durante toda a jornada
acadêmica. Também deixo um agradecimento especial às amizades construídas ao longo do
curso. Ainda que não seja possível mencionar todas, saibam que cada uma delas teve papel
essencial em me incentivar a seguir em frente e a buscar sempre o meu melhor.

RESUMO
O Rodei é um aplicativo móvel desenvolvido para auxiliar na gestão financeira de caminhões,
oferecendo maior controle, eficiência e clareza nas operações de transporte. A partir da observação da rotina de motoristas e gestores, identificou-se que a administração de informações
financeiras e operacionais ainda é feita, em muitos casos, de forma manual e desorganizada,
o que dificulta o acompanhamento dos gastos e a comunicação entre as partes envolvidas.
Neste contexto, a implementação de um aplicativo para centralizar essas informações torna-se
essencial. O Rodei surge com o propósito de organizar todas as despesas de maneira
transparente, facilitando a troca de informações entre gestor e motorista e permitindo um
controle mais eficaz das operações. Essa solução digital não apenas traz mais segurança e
organização à rotina de trabalho, mas também contribui para otimizar o tempo dos gestores,
possibilitando que se concentrem em decisões estratégicas enquanto os motoristas contam
com uma ferramenta prática e acessível para o registro de suas atividades financeiras.
Palavras-chave: aplicativo móvel; gestor e motorista; gestão financeira; controle operacional;
eficiência.

ABSTRACT
Rodei is a mobile application developed to assist in the financial management of trucks, offering
greater control, efficiency, and clarity in transportation operations. Based on the observation
of the daily routines of drivers and fleet managers, it was identified that the management of
financial and operational information is still often carried out manually and in a disorganized
manner, making it difficult to track expenses and communicate between the involved parties.
In this context, the implementation of an application to centralize this information becomes
essential. Rodei was created with the purpose of organizing all expenses in a transparent way,
facilitating the exchange of information between manager and driver, and enabling more effective
operational control. This digital solution not only brings more security and organization to daily
work routines but also helps optimize managers’ time, allowing them to focus on strategic decisions while drivers benefit from a practical and accessible tool for recording their financial activities.
Keywords: mobile application; financial management; manager and driver; operational control;
efficiency.

LISTA DE FIGURAS

Figura 1 – Documento Eletrônico de Transporte. . . . . . . . . . . . . . . . . . . .

13

. . . . . . . . . . . . . . . . . . . . . . . . .

20

Figura 3 – Levantamento de requisitos - MoSCoW (requisitos globais). . . . . . . .

22

Figura 4 – Levantamento de requisitos - MoSCoW (requisitos do Gestor). . . . . .

22

Figura 5 – Levantamento de requisitos - MoSCoW (requisitos do Motorista). . . . .

22

Figura 6 – Interface aplicativo móvel; área do gestor (minhas frotas). . . . . . . . .

26

Figura 7 – Interface aplicativo móvel; área do gestor (detalhes do caminhão). . . .

27

Figura 8 – Interface aplicativo móvel; área do gestor (histórico de viagens). . . . .

28

Figura 9 – Interface aplicativo móvel; área do gestor (balanço financeiro e perfil). .

29

. . . . . . . . . .

30

Figura 2 – Ciclo de desenvolvimento.

Figura 10 – Interface aplicativo móvel; área do motorista (home).

Figura 11 – Interface aplicativo móvel; área do motorista (balanço financeiro pessoal e perfil). . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

31

Figura 12 – Tabelas users, managers e drivers. . . . . . . . . . . . . . . . . . . . . .

32

. . . . . . . . . . . . . . . . . . . . . . . . . . .

33

Figura 14 – Tabelas freights e expenses. . . . . . . . . . . . . . . . . . . . . . . . .

34

Figura 15 – Repositório do Projeto no GitHub. . . . . . . . . . . . . . . . . . . . . .

36

Figura 16 – Build de Desenvolvimento do Aplicativo. . . . . . . . . . . . . . . . . .

36

Figura 17 – Telas de Login e Registro do Aplicativo. . . . . . . . . . . . . . . . . . .

37

. . . . . . . . . . . . . . . . . . . . . . . . . . . . .

38

Figura 19 – Tela Minhas Frotas e suas Opções. . . . . . . . . . . . . . . . . . . . . .

39

Figura 20 – Telas Minhas Frotas e Adicionar Caminhão. . . . . . . . . . . . . . . . .

40

Figura 13 – Tabelas fleets e trucks.

Figura 18 – Tela Minhas Frotas.

Figura 21 – Telas Detalhes do Caminhão, Editar Caminhão e Opção Alterar Motorista. 41
. . . . . . . . . . . . . . . . . . . .

42

Figura 23 – Telas Alterar Senha e Opção Alterar Nome. . . . . . . . . . . . . . . . .

43

Figura 24 – Telas Adicionar Frete, Histórico de Fretes e Detalhes do Frete (Gestor).

44

Figura 25 – Telas Inicial, Histórico de Fretes e Detalhes do Frete (Motorista). . . . .

45

Figura 22 – Telas de Perfil (Gestor e Motorista).

Figura 26 – Telas Reportar Despesa, Detalhes do Frete (Listagem de Despesas) e
Editar Despesa.

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

46

Figura 27 – Telas Reportar Despesa e Detalhes do Frete (Listagem de Despesas)
para o Motorista. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

47

Figura 28 – Opção de Anexar Documento para o Frete e Despesa . . . . . . . . . .

48

Figura 29 – Seletor de Imagem e Opção de Download do Documento . . . . . . . .

49

Figura 30 – Balanço Financeiro do Motorista . . . . . . . . . . . . . . . . . . . . . .

50

Figura 31 – Balanço Financeiro do Caminhão . . . . . . . . . . . . . . . . . . . . . .

51

. . . . . . . . . . . . . . . . . . . . . . .

52

Figura 33 – Arquitetura do Sistema . . . . . . . . . . . . . . . . . . . . . . . . . . .

53

Figura 34 – Diagrama da Modelagem de Banco de Dados. . . . . . . . . . . . . . . .

60

Figura 32 – Balanço Financeiro do Gestor

SUMÁRIO
1

INTRODUÇÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

9

1.1

Objetivos

10

1.1.1

Objetivo geral

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

10

1.1.2

Objetivos específicos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

10

1.2

Justificativa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

11

2

CONTEXTUALIZAÇÃO . . . . . . . . . . . . . . . . . . . . . . . . . . . .

12

3

O RODEI . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

3.1

Escopo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

3.2

Descrição dos Usuários . . . . . . . . . . . . . . . . . . . . . . . . . . .

15

3.2.1

Gestor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

16

3.2.2

Motorista . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

16

4

MATERIAIS E MÉTODOS . . . . . . . . . . . . . . . . . . . . . . . . . . .

17

4.1

Materiais . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

17

4.2

Métodos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

18

5

RESULTADOS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

21

5.1

Levantamento e priorização de requisitos . . . . . . . . . . . . . . . . .

21

5.2

Histórias de usuário . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

23

5.2.1

Requisitos globais . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

23

5.2.2

Gestor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

24

5.2.3

Motorista . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

5.3

Protótipos de telas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

25

5.3.1

Área do Gestor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

26

5.3.2

Área do Motorista . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

29

5.4

Modelagem do banco de dados . . . . . . . . . . . . . . . . . . . . . . .

31

5.5

Desenvolvimento . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

34

5.5.1

Início do Projeto . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

35

5.5.2

Autenticação do Usuário . . . . . . . . . . . . . . . . . . . . . . . . . . . .

36

5.5.3

Frotas

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

38

5.5.4

Caminhões . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

39

5.5.5

Perfil de Usuário . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

41

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

5.5.6

Fretes

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

44

5.5.7

Despesas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

45

5.5.8

Documentos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

47

5.5.9

Balanço Financeiro . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

49

5.5.10

Considerações Finais do Desenvolvimento . . . . . . . . . . . . . . . . . .

52

6

CONSIDERAÇÕES FINAIS . . . . . . . . . . . . . . . . . . . . . . . . . .

55

6.1

Trabalhos Futuros

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

55

REFERÊNCIAS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

56

APÊNDICES

58

APÊNDICE A – MODELAGEM COMPLETA DO BANCO DE DADOS . . .

60

9

1 INTRODUÇÃO
Em fevereiro de 2025, a Secretaria Nacional de Trânsito divulgou que a frota brasileira
de caminhões é composta por aproximadamente 4,1 milhões de veículos (SENATRAN, 2025).
Estes são responsáveis por cerca de 75% de todas as mercadorias movimentadas no território
nacional (TRC, 2020). Em 2023, segundo levantamento do Instituto de Logística e Supply Chain,
os custos de transporte representaram 9,3% do Produto Interno Bruto (PIB), que neste período,
totalizou 10,9 trilhões de reais (ILOS, 2024; IBGE, 2024).
De acordo com a pesquisa realizada pela Fundação Dom Cabral, que contou com a participação de 130 empresas brasileiras, os custos logísticos representaram, em média, 12,37%
da receita bruta dessas organizações. Os números são ainda maiores para setores como mineração (26,1%), papel e celulose (21,7%), agronegócio (20,7%) e indústria da construção (18%)
(FDC, 2018). Vale destacar que os custos logísticos abrangem diferentes componentes, como
armazenagem, estoque, movimentação e transporte. No entanto, o transporte se destaca como
o principal responsável por esse percentual. Segundo aponta a pesquisa (FDC, 2018) de Paulo
Resende, coordenador do Núcleo de Infraestrutura e Logística da Fundação Dom Cabral:
"Em linhas gerais, o transporte incluindo operações de longa e média distância, somada à distribuição urbana, continua sendo um fator muito presente
na composição do custo logístico. Basta ver, por exemplo, que as empresas
consideraram em média que tal item corresponde a 63,5% do custo logístico
total."
Esses dados evidenciam o peso significativo que a logística exerce sobre as empresas,
especialmente em um país de dimensões continentais como o Brasil, onde o modal rodoviário
predomina. Mesmo grandes corporações enfrentam desafios para conter esses custos e, como
estratégia, muitas optam pela terceirização de frotas e serviços logísticos, buscando maior eficiência e redução de despesas operacionais (FDC, 2018).
Quando o olhar se volta para pequenos e médios gestores de caminhões, muitas vezes terceirizados por grandes empresas, percebe-se uma realidade desafiadora no cotidiano
da gestão. Em muitos casos, esses profissionais não contam com ferramentas adequadas para
acompanhar e organizar suas atividades com eficiência, o que intensifica os obstáculos já existentes.
A operação logística no transporte rodoviário de cargas envolve uma série de etapas
e responsabilidades, como planejamento de rotas, controle de documentos fiscais, acompanhamento de despesas e manutenção dos veículos. Ao observar a rotina de caminhoneiros e
gestores, bem como compreender a organização de uma frota familiar, percebe-se como essas
tarefas se acumulam e tornam a gestão cada vez mais complexa.
Enquanto o gestor concentra funções estratégicas, como alocação de recursos, decisões operacionais e controle financeiro, o motorista lida com os desafios práticos da estrada.

10

Além de cumprir prazos e zelar pela manutenção dos veículos, o motorista gerencia as despesas operacionais, como pagamentos e combustível, realizando o uso dos recursos conforme
orientações do gestor. Essa dinâmica exige uma comunicação ágil e eficiente entre as partes.
Nesse cenário, a gestão financeira da frota se torna um ponto crucial para a sustentabilidade das operações. Contudo, à medida que o número de veículos cresce, os desafios
administrativos também se multiplicam. Sem um sistema organizado e claro, o gestor gasta
tempo com tarefas repetitivas, o que pode ocasionar erros, e consequentemente, comprometer
a sua operação.
O presente trabalho propôs um aplicativo móvel, nomeado "Rodei", voltado à gestão financeira de frotas de caminhões, com objetivo de oferecer maior controle sobre as operações
e otimizar o tempo dedicado pelo gestor a tarefas operacionais. Além disso, ao centralizar e
organizar esses dados de forma acessível e transparente, o sistema busca fortalecer a tomada
de decisões, oferecendo um processo mais claro e eficiente que impacta diretamente a rentabilidade e a confiança nas operações.
1.1

Objetivos
Nessa seção, serão descritos os objetivos necessários para o desenvolvimento do pro-

jeto aqui apresentado.
1.1.1

Objetivo geral
Desenvolver um aplicativo móvel para a gestão financeira de caminhões, proporcionando

maior controle, eficiência e clareza nas operações, bem como facilitar a troca de informações
operacionais entre gestor e motorista.
1.1.2

Objetivos específicos
• Implementar a funcionalidade de cadastro de caminhões e agrupamento em frotas;
• Implementar o cadastro de fretes com informações provenientes do Documento Eletrônico de Transporte (DT-e);
• Implementar a funcionalidade de registro de despesas relacionadas aos fretes, permitindo que gestores e motoristas relatem os custos operacionais durante o transporte;
• Implementar a consulta ao histórico de fretes dos caminhões, possibilitando o acompanhamento das operações realizadas;
• Implementar a visualização do balanço financeiro geral e individual de cada caminhão,
oferecendo ao gestor acesso facilitado às informações econômicas da frota.

11

1.2

Justificativa
Os fretes fazem parte da rotina de gestores e motoristas, sendo essenciais para a ge-

ração de renda de ambos. Cada deslocamento representa uma oportunidade de lucro, mas
também envolve riscos e custos que, se não forem bem gerenciados, podem resultar em prejuízos financeiros.
Diante disso, em um país com dimensões continentais como o Brasil, onde o transporte
rodoviário predomina, as viagens frequentemente cruzam diversos estados e acumulam despesas como combustível, pedágios e manutenções. A ausência de um sistema claro para o
repasse dessas informações, especialmente em operações com múltiplas viagens antes de um
contato presencial, pode prejudicar a comunicação e a relação de confiança entre gestor e motorista, já que, sem registros formais, ambos ficam mais expostos a erros ou questionamentos.
Com isso, podem haver impactos nas decisões e finanças das operações.
Nesse contexto, um aplicativo móvel que centralize e registre as informações de cada
frete contribui para uma gestão mais transparente, organizada e segura. Além de facilitar a
rotina, ele atua como uma forma de proteção para ambos: o gestor passa a contar com dados
confiáveis para auditoria e planejamento, enquanto o motorista tem suas despesas e ações
formalmente registradas, o que fortalece a confiança entre as partes.
Além disso, à medida que a quantidade de caminhões aumenta, a complexidade da
operação também cresce. Isso faz com que o gestor precise lidar com um volume maior de
tarefas administrativas, muitas vezes repetitivas e demoradas. O uso do sistema vem justamente
para auxiliar nesse processo, permitindo o cadastro de registros, facilitando o acompanhamento
das atividades e economizando tempo.
Com informações organizadas e acessíveis, o gestor consegue tomar decisões mais
acertadas, contribuindo diretamente para a sustentabilidade da operação a longo prazo. Embora
o sistema tenha sido desenvolvido com foco em pequenas e médias frotas, acredita-se que seus
benefícios possam refletir além desse escopo. Dessa forma, mesmo atuando em uma parte
específica da logística, o aplicativo pode colaborar indiretamente para a redução de custos no
setor de transporte rodoviário como um todo.

12

2 CONTEXTUALIZAÇÃO
O transporte rodoviário de cargas no Brasil tem sua história ligada com o próprio desenvolvimento do país. Durante o governo de Juscelino Kubitschek, entre 1956 e 1961, o Brasil
vivenciou uma grande expansão de sua malha rodoviária, com o objetivo de conectar o vasto
território nacional e promover a integração das regiões. O Plano de Metas, idealizado por Kubitschek, foi fundamental para impulsionar a construção de rodovias e aumentar a utilização dos
caminhões como meio de transporte de mercadorias (ASSIS, 2020).
Esse modelo de transporte se consolidou nas décadas seguintes, transformando-se no
principal modal para o escoamento de produtos pelo país. Contudo, apesar de sua importância, o transporte rodoviário enfrenta desafios significativos. Os custos operacionais são elevados, especialmente com o aumento do preço do combustível e as despesas com manutenções
dos caminhões. Além disso, a infraestrutura rodoviária ainda carece de melhorias, segundo
uma pesquisa feita pela Confederação Nacional do Transporte (CNT), foram avaliados 111.853
quilômetros de rodovias brasileiras, sendo 67% classificadas como regular, ruim ou péssima.
Rodovias com problemas na pavimentação, além de aumentarem os riscos de acidentes, geram desgastes adicionais e aumento no consumo de combustível (CNT, 2024).
Nesse cenário, empresas, gestores de frotas e caminhoneiros têm suas finanças diretamente impactadas. Além das dificuldades enfrentadas nas estradas, eles ainda devem se preocupar com a parte administrativa e financeira, , o que pode gerar problemas de organização,
transparência, demanda de tempo e relação gestor-motorista.
Para entender a origem desses problemas, vamos entender como funciona uma operação logística no transporte rodoviário de cargas. A operação começa com a emissão do DT-e
cuja sua finalidade principal é unificar informações das operações de transporte de carga (MTR,
2024). O DT-e contém informações essenciais sobre o frete, como os dados do contratante, do
transportador, do motorista, da carga, e os detalhes sobre a origem e destino da mercadoria.
Além disso, nele constam informações financeiras, como o valor acordado para o transporte, o
peso da carga, valor por tonelada e porcentagem de adiantamento. A Figura 1 apresenta um
exemplo de DT-e, com os dados sensíveis omitidos.

13

Figura 1 – Documento Eletrônico de Transporte.
Fonte: Autoria própria.

Uma peça fundamental para a operação é o adiantamento, que é uma parcela do valor
acordado para o serviço, paga antecipadamente ao motorista ou transportador. Esse adiantamento visa cobrir parte das despesas iniciais da viagem, como combustível e outras necessidades.
Em algumas situações, o valor do pedágio já está incluído no DT-e, especialmente
quando a transportadora paga antecipadamente por meio de sistemas de pedágio eletrônico,
como o SemParar1 , o que facilita o processo e evita que o motorista precise se preocupar com
esses custos durante a viagem. Entretanto, despesas como alimentação do motorista são acordadas entre ele e o gestor, sendo responsabilidade de ambos decidirem como serão pagas.
A jornada do motorista começa quando ele recebe o DT-e e segue para o local de carga.
Ao longo do trajeto, ele pode se deparar com despesas variáveis, como combustível e manutenções. O combustível é uma despesa recorrente, especialmente em viagens longas, onde
é comum que o motorista precise reabastecer várias vezes. As manutenções preventivas ou
emergenciais, como troca de pneus ou ajustes no sistema de freios, também fazem parte do
custo da operação e precisam ser gerenciadas com cuidado para evitar prejuízos financeiros.
Uma vez que a carga chega ao destino, o motorista realiza a entrega da mercadoria,
e o valor restante acordado no DT-e é depositado ao transportador conforme estipulado. Esse
pagamento final fecha a operação e encerra a relação financeira entre as partes. Em alguns
1

O SemParar é uma empresa que oferece serviço de liberação automática de cancelas (SEMPARAR,
2025).

14

casos, após essa etapa ainda ocorre o pagamento da comissão do motorista, de acordo com
os critérios combinados entre ele e o gestor.
A complexidade da operação logística se encontra no controle adequado de todas essas
despesas e na garantia de que tanto o gestor quanto o motorista tenham um acompanhamento
transparente de todos os custos envolvidos. Sem uma ferramenta ou sistema adequado, o risco
de erros nos cálculos e o aumento de custos operacionais são altos, o que pode levar a prejuízos.
A falta de um controle claro e de registros formais pode gerar problemas de confiança,
especialmente em operações que envolvem múltiplos fretes ou quando o contato entre o gestor
e o motorista não é frequente. Se não houver uma forma eficiente de registrar as despesas,
ambos ficam vulneráveis a erros de cálculo e questionamentos sobre os valores pagos ou recebidos. Além disso, sem uma visão rápida e precisa da situação financeira, o gestor acaba sendo
prejudicado na tomada de decisões estratégicas.
Neste contexto, a implementação de um aplicativo para centralizar essas informações
torna-se essencial. Esse aplicativo poderia organizar todas as despesas e garantir que todos
os registros sejam feitos de forma transparente, facilitando a comunicação e as tomadas de
decisões tanto para o gestor quanto para o motorista. O aplicativo Rodei surge justamente
com esse propósito: oferecer uma solução prática para o controle financeiro das operações
de transporte rodoviário de cargas. Essa solução digital não apenas traria mais segurança e
organização à operação, mas também ajudaria a otimizar o tempo dos gestores, permitindo que
se concentrem mais nas questões estratégicas e menos nas tarefas burocráticas.

15

3 O RODEI
O objetivo deste capítulo é apresentar o aplicativo Rodei, trazendo detalhes sobre o
objetivo a ser alcançado com o seu desenvolvimento. Na seção 3.1, será detalhado o escopo
do aplicativo, ou seja, as funcionalidades e utilização do aplicativo móvel. Por fim, a seção 3.2 é
destinada à descrição dos usuários, especificando o papel de cada um.
3.1

Escopo
O aplicativo tem como objetivo auxiliar na gestão financeira de caminhões, contribuindo

para um controle mais eficiente das operações logísticas no transporte rodoviário de cargas. A
proposta é oferecer uma ferramenta que permita aos gestores de frota organizar informações
essenciais da operação, como fretes, despesas e dados dos veículos, tornando a gestão mais
clara, estruturada e eficaz.
O aplicativo será utilizado como meio de registro e consulta de informações operacionais. Por meio dele, os gestores poderão cadastrar caminhões e organizá-los em frotas, registrar
fretes e suas respectivas despesas. Já os motoristas poderão visualizar os detalhes dos fretes
em que estiverem envolvidos e registrar as despesas ocorridas durante o trajeto, como abastecimentos, pedágios e manutenções emergenciais. Essas ações contribuem diretamente para a
eficiência da gestão, pois proporcionam uma comunicação mais ágil entre gestor e motorista,
ao mesmo tempo que mantêm os dados da operação centralizados e organizados.
Além disso, o sistema oferecerá duas visões complementares para o acompanhamento
da operação: o histórico, que reúne informações detalhadas sobre as viagens realizadas por
cada caminhão, e o balanço financeiro, que apresenta dados de ganhos e despesas, tanto de
forma geral quanto individual por veículo. Com isso, os gestores poderão identificar rapidamente
se uma determinada operação está sendo lucrativa ou gerando prejuízos, facilitando intervenções estratégicas e contribuindo para tomadas de decisão mais assertivas.
3.2

Descrição dos Usuários
O Rodei possuirá dois tipos de usuários: (1) Gestores, que abrange o resposável pelas

frotas e (2) Motoristas, que abrange os motoristas dos caminhões. Cada um desses usuários
receberá um acesso específico conforme seu papel e sua necessidade dentro do aplicativo. Os
tipos de usuários serão definidos a seguir.

16

3.2.1

Gestor
O usuário do tipo Gestor será responsável por gerenciar as operações de transporte,

podendo criar frotas, cadastrar caminhões e registrar fretes. Também poderá relatar despesas
relacionadas às operações. Além disso, terá acesso ao histórico de cada caminhão, incluindo
informações sobre fretes e custos, bem como aos balanços financeiros. O gestor poderá ainda
visualizar e editar os dados do próprio perfil, como nome e senha de acesso.
3.2.2

Motorista
Por sua vez, os usuários do tipo Motorista poderão acessar as informações do caminhão

e do frete na qual estão envolvidos, além de registrar despesas que surgirem ao longo do trajeto.
Também poderão visualizar e editar os dados do seu perfil, como nome e senha de acesso.

17

4 MATERIAIS E MÉTODOS
Neste capítulo, são apresentados os materiais e métodos empregados no planejamento
e desenvolvimento do projeto. O conteúdo está dividido em duas seções. Na seção 4.1 é especificado cada material utilizado, enquanto na seção 4.2 são descritos os métodos utilizados nas
etapas de planejamento e desenvolvimento.
4.1

Materiais
Nesta seção, são apresentados os materiais e tecnologias utilizadas no desenvolvimento

do aplicativo proposto.
Figma: O Figma é uma ferramenta multiplataforma de prototipação de telas, podendo
ser acessada pela Web, via navegadaores, ou instalada como aplicativo nas versões desktop
para Windows e MacOS, além de contar com uma versão móvel. Essa flexibilidade permite que
os protótipos sejam testados em diferentes dispositivos, destacando-se em dispositivos móveis
pela fidelidade com que simula a experiência de uso real (FIGMA, 2025).
DBDiagram: DBDiagram é uma ferramenta que permite a criação de diagramas de
entidade-relacionamento por meio da escrita de código. DBDiagram utiliza Linguagem de Marcação de Banco de Dados, do inglês Database Markup Language (DBML), uma linguagem
própria desenvolvida para a documentação facilitada de estruturas de banco de dados, como
tabelas, atributos, tipagens e relacionamentos (HOLISTICS, 2025).
Git: O Git (GIT, 2025) é um sistema de controle de versões que registra todas as alterações realizadas no código-fonte. Ele oferece recursos que permitem o trabalho colaborativo
entre desenvolvedores, a criação e gerenciamento de repositórios, bem como o retorno a versões anteriores do projeto, garantindo segurança, organização e escalabilidade.
GitHub: Já o GitHub (GITHUB, 2025) é uma plataforma online que hospeda repositórios
tanto públicos quanto privados e disponibiliza uma interface que facilita a execução de tarefas
diárias do desenvolvedor. Entre suas funcionalidades, destacam-se a criação de pull requests e
a automação de processos através da configuração de CI/CD. Além disso, o GitHub conta com
o recurso Projects, que permite organizar as tarefas de desenvolvimento utilizando quadros no
estilo Kanban, facilitando o acompanhamento do progresso e a gestão das atividades.
React Native e Expo: React Native é um framework JavaScript destinado ao desenvolvimento de aplicativos móveis. Este framework é utilizado em conjunto com o Expo, uma
plataforma que disponibiliza mecanismos que favorecem a visualização, desenvolvimento e deploy de aplicativos móveis (REACTNATIVE, 2025; EXPO, 2025a).
Laravel: Laravel é um framework PHP, projetado para o desenvolvimento de aplicações
Web e APIs (Interface de Programação de Aplicação, do inglês Application Programming Interface). Seu ecossistema oferece ferramentas que facilitam tarefas comuns do backend, como roteamento, autenticação, migração de banco de dados e testes automatizados. O Laravel busca

18

proporcionar uma experiência de desenvolvimento agradável, combinando elegância, simplicidade e clareza no código (LARAVEL, 2025b).
4.2

Métodos
Nesta seção, serão apresentado os métodos adotados para o desenvolvimento do pro-

jeto, buscando organização, eficiência e clareza ao longo do processo. Os métodos serão estruturados em etapas baseadas em princípios da engenharia de software e da metodologia ágil,
com o objetivo de alcançar um resultado final consistente.
Etapa 1: Como ponto de partida, será definido o público-alvo do sistema e serão identificadas as principais necessidades que o aplicativo pretende atender. Para isso, serão realizadas
entrevistas com representantes desse público, com o objetivo de coletar informações relevantes.
A partir dos dados obtidos, será feito o levantamento dos requisitos do sistema.
Etapa 2: Em seguida, é realizada a priorização dos requisitos. Para isso, será utilizada
a técnica MoSCoW (CONSORTIUM, 2025), que os classifica em quatro categorias:
• Must: requisitos essenciais para o sistema. Devem obrigatoriamente ser implementados para que o aplicativo funcione corretamente;
• Should: requisitos importantes, mas não vitais. A aplicação ainda é viável sem eles,
embora seu valor agregado seja alto;
• Could: requisitos desejáveis, com menor impacto. São incluídos apenas se houver
tempo e recursos suficientes;
• Won’t: requisitos que não serão desenvolvidos nesta versão, podendo ser considerados no futuro.
Etapa 3: A partir dos requisitos mais priorizados, são elaboradas as User Stories, ou Histórias de Usuário, com o objetivo de detalhar melhor as funcionalidades esperadas do sistema.
Cada história descreve uma necessidade sob a perspectiva do usuário, facilitando a compreensão dos requisitos. Para isso, adota-se o formato proposto por Mike Cohn (COHN, 2025), que
segue o padrão: “Como [tipo de usuário], quero [ação], para que [benefício]”.
Para complementar as User Stories, também é utilizada a sintaxe Gherkin (CUCUMBER,
2025), afim de descrever os critérios de aceitação de forma clara e orientada a comportamento.
Essa abordagem segue o padrão: "Dado que [contexto], Quando [ação], Então [resultado esperado]", proporcionando um melhor alinhamento entre os requisitos e o desenvolvimento no
sistema.
Etapa 4: Com base nas etapas anteriores, será utilizada a ferramenta Figma para o
desenvolvimento dos protótipos de telas. Esta etapa tem o objetivo de validar a interface do

19

sistema e o fluxo de navegação, além de auxiliar na estimativa do tempo necessário para o
desenvolvimento.
Etapa 5: Posteriormente, será utilizada a ferramenta DBDiagram para a modelagem
do banco de dados, definindo-se as entidades, atributos e relacionamentos necessários. Essa
etapa visa proporcionar uma melhor compreensão da estrutura dos dados, facilitando a implementação das funcionalidades e da interface.
Etapa 6: Em seguida, as tarefas de desenvolvimento serão estruturadas com base nos
resultados das etapas anteriores. Cada tarefa será estimada conforme sua complexidade e organizada em Sprints, de acordo com a metodologia Scrum Sprints (ATLASSIAN, 2025b). Essa
abordagem permite que o projeto seja desenvolvido em pequenas entregas, facilitando o controle do progresso e a adaptação a mudanças ao longo do processo. Para a criação e organização das Sprints, será utilizada a ferramenta Projects do GitHub.
Etapa 7: Por fim, será dado início à etapa de desenvolvimento do aplicativo. Para o
controle de versão e organização do código será utilizado o Git e GitHub, adotando o padrão
Git Feature Branch Workflow (ATLASSIAN, 2025a), que consiste na criação de ramificações
específicas para cada funcionalidade, facilitando a colaboração e o controle de mudanças.
No contexto deste projeto, seguindo o padrão, cada ramificação (branch) será
destinada ao desenvolvimento de uma tarefa previamente definida nas etapas anteriores. Essas ramificações seguirão uma padronização de nomenclatura, no formato @git-user/local-mobile|backend/issue-number/feature-name, visando garantir clareza e organização durante o desenvolvimento. Após a finalização de cada
tarefa, será criada uma pull request para revisão. Somente após essa etapa o código será integrado à branch principal, ou retornado para ajustes, caso necessário. A Figura 2 apresenta um
exemplo visual dos processos citados.

20

Figura 2 – Ciclo de desenvolvimento.
Fonte: Autoria própria.

O desenvolvimento do aplicativo será realizado com as ferramentas React Native e Expo,
voltado à criação do aplicativo proposto. Já o framework Laravel, será utilizado na construção
da API que fornecerá os dados e funcionalidades para o aplicativo móvel.

21

5 RESULTADOS
Neste capítulo, são apresentados os resultados obtidos. O conteúdo está organizado em
seções, que descrevem as etapas realizadas para o desenvolvimento do projeto. Na Seção 5.1,
é detalhado o processo de levantamento e priorização dos requisitos. Em seguida, na Seção
5.2, são descritas as histórias de usuário. A Seção 5.3 apresenta os protótipos de telas do
aplicativo. Na Seção 5.4, é especificada a modelagem do banco de dados. Por fim, a seção 5.5
aborda o processo de desenvolvimento do projeto.
5.1

Levantamento e priorização de requisitos
Para o levantamento de requisitos, foi realizada uma entrevista com um gestor de frota

que vivencia diariamente os desafios da área, complementada pela experiência pessoal do
Autor, adquirida enquanto desempenhava funções de gestão na frota da família do proponente
deste trabalho. O relato do entrevistado forneceu uma perspectiva valiosa sobre o processo
de gerenciamento das operações, sendo essencial para a compreensão do problema e para a
definição das funcionalidades da aplicação.
Com a entrevista, foi possível identificar as tarefas diárias pelas quais o gestor de frota é
responsável, como a gestão de documentos relacionados às operações, como o DT-e e cupons
fiscais; cálculos financeiros, como o total de gastos, lucros e comissões; tomada de decisões
e comunicação com o motorista; e o controle das manutenções do caminhão, especialmente
o controle dos pneus, além de trocas de óleo e outras manutenções recorrentes. O relato do
entrevistado revelou um acúmulo de tarefas atribuídas ao gestor, muitas vezes repetitivas e
demoradas, além da descentralização na organização de documentos e informações.
Com isso, foram definidos os requisitos do projeto, assim como foi efetuada a priorização desses requisitos. Priorizaram-se os requisitos do tipo Must, de forma a atender ao objetivo
geral do projeto. Requisitos relacionados aos processos financeiros, porém não vitais, foram
classificados como Should. Funcionalidades secundárias, que não são essenciais para o funcionamento básico do sistema, foram consideradas Could. Por fim, demais requisitos foram
considerados fora do escopo deste trabalho e, portanto, categorizados como Won’t. A seguir,
serão apresentados estes requisitos e suas devidas priorizações, organizados em:
• Requisitos globais: aqueles que serão comuns a todos os usuários;
• Requisitos do Gestor: aqueles que serão de uso apenas dos gestores;
• Requisitos do Motorista: aqueles que serão de uso apenas dos motoristas.
A Figura 3 apresenta o levantamento de requisitos globais.

22

Figura 3 – Levantamento de requisitos - MoSCoW (requisitos globais).

Fonte: Autoria própria.

Na Figura 4, é detalhado o levantamento de requisitos referente ao gestor.
Figura 4 – Levantamento de requisitos - MoSCoW (requisitos do Gestor).

Fonte: Autoria própria.

A Figura 5 apresenta o levantamento de requisitos referente ao motorista.
Figura 5 – Levantamento de requisitos - MoSCoW (requisitos do Motorista).

Fonte: Autoria própria.

23

5.2

Histórias de usuário
Neste capítulo, será apresentada a aplicação de um dos princípios do Desenvolvimento

Orientado a Comportamento: as User Stories, ou Histórias de Usuário. Elas serão utilizadas
para representar os casos de uso das funcionalidades do aplicativo, organizadas conforme a
prioridade de implementação, e foram elaboradas com base nas conclusões obtidas durante
o levantamento e a priorização dos requisitos do projeto. Cada história descreve um requisito
específico, conforme a identificação atribuída a ele na Seção 5.1.
Como o aplicativo possui diferentes funcionalidades para cada tipo de usuário, a apresentação das histórias de usuário foi estruturada de acordo.
5.2.1

Requisitos globais

Feature: Cadastros de despesas (RF03)
Como um usuário logado, quero poder cadastrar as despesas da viagem, para que eu
possa manter o histórico da operação.
Dado que sou um usuário logado
Quando cadastro as despesas de uma viagem
Então eu devo ter acesso da despesa no histórico.
Feature: Envio de documentos ou fotos (RF04)
Como um usuário logado, quero poder enviar documentos ou fotos durante o cadastro
de viagens ou despesas, para que eu possa comprovar e manter o acesso ao documento
oficial.
Dado que sou um usuário logado
Quando cadastro uma viagem ou despesa
Então eu devo ter a opção de fazer o envio de documentos ou fotos.
Feature: Perfil (RF05)
Como um usuário autenticado logado, quero poder acessar meu perfil, para que eu
possa visualizar e editar os dados da conta.
Dado que sou um usuário logado
Quando acesso o meu perfil
Então eu devo visualizar os meus dados e uma opção de edição.

24

5.2.2

Gestor

Feature: Criação de frotas (RF07)
Como um usuário autenticado com o perfil de Gestor, quero poder criar frotas, para que
eu possa organizar os meus caminhões.
Dado que sou um usuário autenticado com o perfil de Gestor
Quando cria uma nova frota
Então eu devo ser capaz de vê-la listada no aplicativo.
Feature: Cadastro de caminhões (RF08)
Como um usuário autenticado com o perfil de Gestor, quero poder cadastrar meus caminhões, para que eu possa registrar minhas viagens e despesas.
Dado que sou um usuário autenticado com o perfil de Gestor
Quando cadastro um novo caminhão
Então eu devo ser capaz de vê-lo listado no aplicativo.
Feature: Cadastro de fretes (RF09)
Como um usuário autenticado com o perfil de Gestor, quero poder cadastrar os fretes
realizadas pelos meus caminhões, para que eu possa manter o histórico operacional e
registrar as despesas correspondentes.
Dado que sou um usuário autenticado com o perfil de Gestor
Quando crio um novo frete
Então eu devo ser capaz de vê-la listada no histórico do caminhão.
Feature: Histórico (RF10)
Como um usuário autenticado com o perfil de Gestor, quero poder acessar o histórico
de fretes e despesas dos meus caminhões, para que eu possa ter mais controle e tomar
decisões mais assertivas.
Dado que sou um usuário autenticado com o perfil de Gestor
Quando acesso os detalhes do caminhão
Então eu devo ser capaz de ver o histórico.

25

Feature: Balanço financeiro (RF11)
Como um usuário autenticado com o perfil de Gestor, quero poder acessar o balanço
financeiro geral e individual de um caminhão, para que eu possa consultar rapidamente
os dados financeiros e acompanhar o desempenho.
Dado que sou um usuário autenticado com o perfil de Gestor
Quando acesso o balanço geral ou detalhes do caminhão
Então eu devo ser capaz de ver o balanço financeiro.

5.2.3

Motorista

Feature: Balanço financeiro do motorista (RF16)
Como um usuário autenticado com o perfil de Motorista, quero poder acessar o balanço
financeiro pessoal, para que eu possa acompanhar meu desempenho financeiro.
Dado que sou um usuário autenticado com o perfil de Motorista
Quando acesso os meus ganhos
Então eu devo visualizar meu balanço financeiro.
Feature: Histórico do motorista (RF17)
Como um usuário autenticado com o perfil de Motorista, quero poder acessar o histórico
de fretes e despesas, para que eu possa acompanhar minhas atividades.
Dado que sou um usuário autenticado com o perfil de Motorista
Quando acesso o histórico
Então eu devo visualizar as viagens e despesas relatadas.

5.3

Protótipos de telas
Nesta seção, será apresentado e descrito o protótipo das telas do aplicativo. A apresen-

tação das telas está estruturada em seções, onde em cada seção, foram detalhadas algumas
funcionalidades e parte do fluxo de navegação entre telas.

26

5.3.1

Área do Gestor
Após autenticar-se com o perfil de Gestor, o usuário é redirecionado à tela inicial do sis-

tema, intitulada “Minhas Frotas” (Figura 6). Nessa interface, são exibidas as frotas cadastradas,
bem como os caminhões vinculados a elas. A partir dessa tela, é possível criar, editar ou excluir
frotas, além de adicionar caminhões às frotas existentes.
Figura 6 – Interface aplicativo móvel; área do gestor (minhas frotas).

Fonte: Autoria própria.

Ao selecionar um caminhão na listagem, o usuário é direcionado para a tela “Detalhes
do Caminhão” (Figura 7), onde são apresentadas as informações específicas do veículo, incluindo seu balanço financeiro. Nessa tela, o gestor pode alterar o motorista vinculado, editar
os dados do caminhão ou até mesmo removê-lo do sistema. Além disso, é possível acessar
funcionalidades, como o cadastro de novas viagens, o registro de despesas e a visualização do
histórico de atividades do veículo.

27

Figura 7 – Interface aplicativo móvel; área do gestor (detalhes do caminhão).

Fonte: Autoria própria.

A partir da tela "Detalhes do Caminhão", o gestor poderá acessar o histórico de viagens
do veículo ao selecionar a opção correspondente no menu. Em seguida, será redirecionado
para a tela de listagem de viagens. Ao selecionar uma viagem, ele será levado à tela "Detalhes da Viagem", onde poderá visualizar as informações relacionadas àquela viagem, realizar
o download de documentos associados, caso disponíveis, e consultar o histórico de despesas
vinculadas. Nessa mesma tela, representada na Figura 8, o gestor terá a possibilidade de editar
as informações da viagem, excluir a viagem se necessário, além de editar ou remover despesas
relacionadas.

28

Figura 8 – Interface aplicativo móvel; área do gestor (histórico de viagens).

Fonte: Autoria própria.

Por fim, o gestor também terá acesso à tela "Balanço Financeiro", onde são apresentadas informações sobre suas finanças. Nessa tela, representada pela Figura 9, é possível
visualizar o balanço geral das operações realizadas, incluindo ganhos, despesas, lucro total e
lucro obtido no último mês. Além disso, o gestor poderá acessar seu perfil por meio da tela "Meu
Perfil", onde serão exibidas as informações da conta e oferecida a opção de alterar nome de
usuário e senha.

29

Figura 9 – Interface aplicativo móvel; área do gestor (balanço financeiro e perfil).

Fonte: Autoria própria.

5.3.2

Área do Motorista
Após autenticar-se com o perfil de Motorista, o usuário é redirecionado à tela inicial do

sistema, intitulada “Home” (Figura 10). Nessa interface, são exibidas as informações do caminhão designado e da viagem atual, bem como o histórico de despesas relatadas. A partir dessa
tela, o motorista pode acessar a tela de registro de despesas e acessar seu balanço financeiro
e perfil por meio do menu localizado no canto superior direito.

30

Figura 10 – Interface aplicativo móvel; área do motorista (home).

Fonte: Autoria própria.

Por fim, o motorista também terá acesso à tela “Balanço Financeiro”, onde são apresentadas informações financeiras relacionadas à sua atuação no sistema. Nessa interface, é
possível visualizar o número total de viagens realizadas, as despesas registradas, bem como
os ganhos de comissão acumulados e os ganhos obtidos no último mês. Essa tela está representada na Figura 11(a).
Além disso, o motorista poderá acessar seu perfil por meio da tela “Meu Perfil”, representada na Figura 11(b), onde são exibidas as informações da conta e disponibilizadas opções
para alterar o nome de usuário e a senha.

31

Figura 11 – Interface aplicativo móvel; área do motorista (balanço financeiro pessoal e perfil).

(a) Balanço financeiro pessoal

(b) Perfil do motorista

Fonte: Autoria própria.

5.4

Modelagem do banco de dados
Nesta seção, será apresentada a modelagem do banco de dados do aplicativo. A mode-

lagem foi elaborada com base nas funcionalidades anteriormente previstas, e pode ser observada integralmente no Apêndice A.
Considerando a existência de dois tipos de usuários no sistema, Gestor e Motorista, a
tabela users foi modelada para armazenar os dados comuns a ambos os perfis, como nome,
CPF, e-mail e senha. Para representar os diferentes papéis e permitir uma futura extensão de
informações específicas, foram criadas as tabelas managers e drivers, ambas relacionadas à
tabela users. Essa separação facilita a organização dos dados e permite, por exemplo, que
gestores venham a ter atributos únicos que não se aplicam aos motoristas, e vice-versa. A
Figura 12 apresenta a estrutura das tabelas mencionadas.

32

Figura 12 – Tabelas users, managers e drivers.

Fonte: Autoria própria.

Para viabilizar a organização dos caminhões, foi criada a tabela fleets, que se relaciona
diretamente com o Gestor responsável, permitindo que ele crie e gerencie diferentes frotas. Os
caminhões são armazenados na tabela trucks, que guarda informações como marca, modelo,
placa, cor e o percentual de comissão atribuído ao motorista. Essa tabela está relacionada tanto
com a frota quanto com o motorista designado (tabela drivers). A Figura 13 ilustra a modelagem
da tabela fleets e sua relação com a tabela trucks.

33

Figura 13 – Tabelas fleets e trucks.

Fonte: Autoria própria.

Com o intuito de registrar os fretes realizados pelos caminhões, foi modelada a tabela
freights, responsável por armazenar informações relevantes como endereço de origem e destino, peso da carga, valor por tonelada, valores de adiantamento e o valor total da viagem. Além
desses dados, essa tabela também possui relacionamentos com a frota à qual a viagem pertence, com o caminhão utilizado e com o motorista responsável. Essa estrutura garante um
histórico consistente e confiável, permitindo, por exemplo, que mesmo que o motorista de um
caminhão seja alterado futuramente, a viagem continue vinculada ao motorista originalmente
designado, preservando a rastreabilidade das operações.
As despesas relacionadas aos fretes são gerenciadas por meio da tabela expenses,
responsável por armazenar informações como o tipo, valor, local e data da despesa, além de
sua associação direta com uma viagem específica. A estrutura do relacionamento permite que
múltiplas despesas estejam vinculadas a uma única viagem. A seguir, a Figura 14 apresenta a
modelagem das tabelas explicadas anteriormente.

34

Figura 14 – Tabelas freights e expenses.

Fonte: Autoria própria.

A forma como o banco de dados foi estruturado também facilita a construção de históricos personalizados para os dois perfis de usuários. Como tanto os gestores quanto os motoristas mantêm relações diretas com a tabela freights e, por consequência, com a tabela expenses,
é possível obter com facilidade um panorama completo dos fretes realizadas, despesas associadas e demais informações pertinentes ao desempenho individual de cada perfil no sistema.
5.5

Desenvolvimento
O desenvolvimento do Rodei foi conduzido de acordo com os materiais e métodos des-

critos no Capítulo 4, sendo guiado pelos requisitos funcionais levantados. Durante esse processo, algumas adaptações foram realizadas com o objetivo de aprimorar a experiência do
usuário e otimizar o desenvolvimento do sistema, as quais serão detalhadas nas subseções
seguintes.

35

Para garantir a qualidade, segurança e organização do código, foram adotadas ao longo
de todo o projeto algumas práticas fundamentais. No backend foram utilizadas policies1 para
controle de acesso e autorização, bem como, a organização da lógica de negócio por meio do
padrão de actions2 e a implementação de testes automatizados para validar as funcionalidades implementadas. No lado cliente, foi adotada a utilização da biblioteca Zod 3 para garantir a
consistência entre os schemas do aplicativo móvel e as resources do backend.
A descrição do desenvolvimento está organizada conforme as principais funcionalidades do aplicativo, abrangendo desde a configuração inicial do projeto até a implementação de
módulos específicos. Cada subseção apresenta as funcionalidades implementadas, decisões
tomadas e alterações realizadas em relação ao planejamento original, sempre relacionando as
funcionalidades aos requisitos funcionais correspondentes.
5.5.1

Início do Projeto
O desenvolvimento do Rodei teve início com a configuração dos ambientes de trabalho

e das ferramentas utilizadas. No repositório do projeto, foram organizados dois diretórios principais: backend/, destinado ao código da API desenvolvida em Laravel, e mobile-app/,
responsável pelo aplicativo móvel criado com React Native e Expo. Essa estrutura facilitou a
manutenção do código e o desenvolvimento paralelo entre as duas partes do sistema.
O controle de versão foi realizado por meio do Git, com o repositório hospedado no
GitHub. Para organizar o desenvolvimento, adotou-se o fluxo de trabalho Git Feature Branch
Workflow (ATLASSIAN, 2025a), que permite o desenvolvimento paralelo de novas funcionalidades em branches específicas. O gerenciamento de tarefas foi conduzido no GitHub Projects.
Ainda nessa etapa, foi configurado o GitHub Actions, responsável pela integração contínua (CI) do projeto. Esse mecanismo automatiza a execução dos testes e a verificação do
código antes da integração das alterações na branch4 principal.
Além disso, foi gerada uma build de desenvolvimento do Expo, possibilitando que o
aplicativo fosse testado de forma contínua em dispositivos físicos durante o processo de implementação.
As Figuras 15 e 16 ilustram, respectivamente, o repositório do projeto no GitHub e a
build de desenvolvimento criada.
1
2
3
4

Policies são regras que controlam o acesso e autorização dos usuários para realizar determinadas
ações dentro do sistema (LARAVEL, 2025a).
Actions são classes responsáveis por executar uma única tarefa ou ação específica, promovendo a
separação de responsabilidades, facilitando a manutenção e os testes do código.
Zod é uma biblioteca para definição e validação de schemas de dados, que permite manter a consistência e tipagem (ZOD, 2025).
Branch: do português raiz, representa uma ramificação no projeto.

36

Figura 15 – Repositório do Projeto no GitHub.

Fonte: Autoria própria.

Figura 16 – Build de Desenvolvimento do Aplicativo.

Fonte: Autoria própria.

5.5.2

Autenticação do Usuário
A primeira funcionalidade desenvolvida no projeto foi o sistema de autenticação de usuá-

rios, composto pelas telas de Login e Registro no aplicativo móvel, atendendo aos Requisitos
Funcionais RF01 e RF02 definidos na seção 5.1. Essas telas foram implementadas seguindo
o design proposto na prototipação, conforme registrado nas Pull Requests #7, #12 e #17. A
Figura 17 apresenta a aparência final das telas de autenticação desenvolvidas.

37

Figura 17 – Telas de Login e Registro do Aplicativo.

(a) Tela de Login

(b) Tela de Registro
Fonte: Autoria própria.

No backend, foram criadas as rotas responsáveis por autenticar e registrar usuários,
utilizando o Laravel Sanctum5 para a geração e gerenciamento de tokens6 de autenticação.
A autenticação é realizada por meio da validação das credenciais do usuário e, em caso de
sucesso, é retornado um token que permite o acesso às rotas protegidas do sistema.
5
6

O Laravel Sanctum é um pacote oficial do framework Laravel que fornece um sistema simples de
autenticação por tokens para aplicações SPA (Single Page Application) e mobile (LARAVEL, 2025c).
Um token de autenticação é uma chave digital temporária que identifica e autoriza o usuário em
requisições subsequentes à API, sem a necessidade de reenviar suas credenciais (LARAVEL, 2025c).

38

No aplicativo móvel, após o processo de autenticação, o token retornado pela API é
armazenado de forma segura no Secure Store7 , permitindo que o usuário permaneça conectado
sem a necessidade de autenticação manual a cada sessão.
5.5.3

Frotas
Nesta fase, desenvolveu-se a funcionalidade de gerenciamento de frotas, contemplando

o RF07. Essa implementação está documentada nas Pull Requests #9 e #22 do repositório do
aplicativo.
No aplicativo, foi criada a tela Minhas Frotas, onde o gestor pode visualizar sua lista de
frotas. Nesta tela, estão disponíveis as ações para criar uma nova frota, editar informações de
frotas existentes e excluir frotas que não sejam mais necessárias. As Figuras 18 e 19 ilustram a
tela e as funcionalidades implementadas no aplicativo.
Figura 18 – Tela Minhas Frotas.

(a) Tela Minhas Frotas

(b) Opção de Adicionar Frota
Fonte: Autoria própria.

7

O Secure Store é um módulo do Expo que permite armazenar dados sensíveis de forma criptografada
no dispositivo, garantindo maior segurança das informações do usuário. (EXPO, 2025b)

39

Figura 19 – Tela Minhas Frotas e suas Opções.

(c) Opção de Editar Frota

(d) Opção de Excluir Frota
Fonte: Autoria própria.

No backend, foram criadas as rotas responsáveis por listar, criar, editar e excluir frotas.
Para garantir a segurança e integridade dos dados, foi criada uma policy que restringe o acesso
às operações somente aos usuários autorizados, assegurando que cada gestor possa gerenciar
apenas suas próprias frotas.
5.5.4

Caminhões
Para permitir que o gestor controle os caminhões associados às suas frotas, foi im-

plementado o gerenciamento veículos dentro do aplicativo. Essa funcionalidade garante que
cada caminhão possa ser criado, editado, vinculado a uma frota e ter seu motorista atualizado

40

conforme necessário, atendendo ao Requisito Funcional RF08. As implementações correspondentes podem ser consultadas nas Pull Requests #11 e #24.
Na interface do aplicativo, foi adicionada a listagem de caminhões dentro da tela Minhas
Frotas, permitindo que o gestor visualize os veículos associados a cada frota. Foram criadas
telas específicas para a adição, edição e exclusão de caminhões, além de uma tela de detalhes
que apresenta informações individuais de cada caminhão. Também foi disponibilizada uma funcionalidade para alterar o motorista responsável pelo veículo. Nas Figuras 20 e 21, observam-se
as telas e opções desenvolvidas.
Figura 20 – Telas Minhas Frotas e Adicionar Caminhão.

(a) Tela Minhas Frotas (Listagem de Caminhões)
Fonte: Autoria própria.

(b) Tela Adicionar Caminhão

41

Figura 21 – Telas Detalhes do Caminhão, Editar Caminhão e Opção Alterar Motorista.

(c) Tela Detalhes do Caminhão

(d) Tela Editar Caminhão

(e) Opção Alterar Motorista

Fonte: Autoria própria.

Na API, foram desenvolvidas as rotas necessárias para suportar as operações de criação, edição, exclusão, visualização e atualização do motorista dos caminhões. Como a lógica
foi organizada por meio do padrão de actions, a atribuição do motorista ao caminhão ocorre
de forma separada da criação do veículo, o que possibilita a reutilização da action na rota de
alteração do motorista do caminhão.
5.5.5

Perfil de Usuário
Posteriormente, desenvolveu-se o módulo de perfil de usuário, que permite aos usuá-

rios visualizar e atualizar suas próprias informações, conforme previsto no Requisito Funcional
RF05. As alterações implementadas podem ser consultadas na Pull Request #35.
No aplicativo móvel, foram criadas telas para visualização e edição do perfil, permitindo
que o usuário altere informações como nome e senha. Essas funcionalidades estão disponíveis
tanto para gestores quanto para motoristas. Abaixo, as Figuras 22 e 23 representam a tela de
Perfil e suas opções.

42

Figura 22 – Telas de Perfil (Gestor e Motorista).

(a) Tela Perfil (Gestor)

(b) Tela Perfil (Motorista)
Fonte: Autoria própria.

43

Figura 23 – Telas Alterar Senha e Opção Alterar Nome.

(c) Tela Alterar Senha

(d) Opção Alterar Nome
Fonte: Autoria própria.

No backend, foram desenvolvidas rotas específicas para obter e atualizar os dados do
perfil, garantindo a sincronização das informações com o aplicativo móvel.
Durante o desenvolvimento, foi identificada uma oportunidade de otimização no fluxo de
trabalho com Git. Na seção 4.2, Etapa 7, foi definido que as alterações para o backend e para
o aplicativo móvel seriam enviadas em branches e pull requests separadas, o que dificultava a
integração e aumentava o tempo de revisão. Para melhorar esse processo, passou-se a consolidar as mudanças em uma única branch e pull request que contemplam modificações em
ambos os ambientes, agilizando a entrega e facilitando a revisão do código.

44

5.5.6

Fretes
Para estruturar o controle operacional, foi desenvolvido o gerenciamento e acompanha-

mento dos fretes. Essa etapa permitiu que gestores administrassem os fretes associados aos
seus caminhões e que motoristas acompanhassem o histórico das viagens realizadas. As funcionalidades implementadas contemplam, de forma parcial, os Requisitos Funcionais RF09 e
RF10 no que se refere ao histórico de fretes. Todas as alterações dessa etapa podem ser consultadas na Pull Request #36.
Para o gestor, foram adicionadas funcionalidades completas de gerenciamento de fretes, incluindo a criação, edição, exclusão, visualização do histórico de fretes de um caminhão
específico e acesso aos detalhes de cada frete. A seguir, a Figura 24 mostra a interface criada.
Figura 24 – Telas Adicionar Frete, Histórico de Fretes e Detalhes do Frete (Gestor).

(a) Tela Adicionar Frete

(d) Tela Histórico de Fretes

(c) Tela Detalhes do Frete

Fonte: Autoria própria.

Já para o motorista, foram disponibilizadas informações relevantes em sua tela inicial,
como os dados do caminhão designado e o último frete realizado, atendendo o RF18. Em uma
adaptação ao planejamento inicial, o histórico de fretes e despesas foi retirado da tela inicial do
motorista e realocado em telas específicas de Histórico de Fretes e Detalhes do Frete, contendo
apenas informações pertinentes ao seu perfil, atendendo parcialmente ao RF17, no que se
refere ao histórico de fretes. A Figura 25 representa a funcionalidade de Fretes para o motorista.

45

Figura 25 – Telas Inicial, Histórico de Fretes e Detalhes do Frete (Motorista).

(a) Tela Inicial

(d) Tela Histórico de Fretes

(c) Tela Detalhes do Frete

Fonte: Autoria própria.

É importante destacar que, enquanto o gestor possui permissão para gerenciar todos os
aspectos dos fretes, o motorista tem acesso restrito apenas à visualização dos seus próprios
fretes.
No backend, foram criadas rotas para essas funcionalidades, respeitando as regras de
autorização estabelecidas para cada tipo de usuário.
5.5.7

Despesas
Dando continuidade ao controle operacional iniciado com o módulo de fretes, foi imple-

mentado o gerenciamento de despesas, consolidando o fluxo completo de registro e acompanhamento das operações realizadas pelos motoristas e gestores. Esse módulo complementa
diretamente as funcionalidades anteriores, permitindo registrar gastos associados a cada frete
e garantindo uma visão aos custos envolvidos. As funcionalidades implementadas atendem ao
Requisito Funcional RF03 e as alterações desta etapa podem ser consultadas na Pull Request
#38.
As despesas podem ser relatadas tanto por gestores quanto por motoristas, porém com
permissões distintas: os motoristas possuem acesso restrito para apenas relatar e visualizar
despesas, sem a possibilidade de editar ou excluir registros. Já os gestores detêm controle

46

completo sobre as despesas, podendo criar, editar, excluir e visualizar todas as informações
relacionadas.
A listagem das despesas associadas a um frete é exibida na tela de Detalhes do Frete,
deixando completa a implementação do RF10 e RF17. A Figura 26 representa as telas do
Gestor, enquanto a Figura 27 representa as telas do Motorista.
Figura 26 – Telas Reportar Despesa, Detalhes do Frete (Listagem de Despesas) e Editar Despesa.

(a) Tela Reportar Despesa

(b) Listagem de Despesas
Fonte: Autoria própria.

(c) Tela Editar Despesa

47

Figura 27 – Telas Reportar Despesa e Detalhes do Frete (Listagem de Despesas) para o Motorista.

(a) Tela Reportar Despesa

(b) Listagem de Despesas
Fonte: Autoria própria.

Na API, foram criadas as rotas necessárias para as funcionalidades, com as devidas
políticas de autorização para garantir que cada tipo de usuário acesse apenas as operações
permitidas.
5.5.8

Documentos
Também foi desenvolvido o recurso de envio e gerenciamento de documentos, disponível

tanto para fretes quanto para despesas, atendendo ao RF04. A implementação deste recurso
pode ser visualizada na Pull Request #40.
Através do aplicativo, usuários gestores e motoristas podem anexar e baixar documentos
relacionados, sendo que, até o momento, o sistema suporta apenas o envio de imagens.

48

Embora ambos os perfis possam anexar e realizar download, somente os gestores possuem permissão para excluir documentos, garantindo maior controle sobre os arquivos armazenados. Abaixo, isso é demonstrado pelas Figuras 28 e 29.
Figura 28 – Opção de Anexar Documento para o Frete e Despesa

(a) Opção Anexar Documento do Frete e
Despesa (Gestor)

(b) Opção Anexar Documento da Despesa
(Motorista)

Fonte: Autoria própria.

49

Figura 29 – Seletor de Imagem e Opção de Download do Documento

(c) Seletor de Imagem

(d) Opção de Download
Fonte: Autoria própria.

No backend, foram criadas rotas específicas para upload, download e exclusão de documentos, respeitando as políticas de autorização que diferenciam os perfis de usuário.
5.5.9

Balanço Financeiro
Por fim, foram implementadas as funcionalidades relacionadas ao balanço financeiro,

esse módulo complementa o ciclo de operações iniciado com fretes e despesas, reunindo os resultados financeiros obtidos. A implementação atende aos Requisitos Funcionais RF11 e RF16,
e encontra-se disponível Pull Request #42.

50

Para o motorista, devido à remoção do histórico de despesas e fretes da tela inicial, o
balanço financeiro foi realocado para essa mesma tela, eliminando a necessidade de uma tela
específica para essa funcionalidade. A Figura 30 demonstra a funcionalidade implementada.
Figura 30 – Balanço Financeiro do Motorista

Fonte: Autoria própria.

Foi adicionado o balanço financeiro do caminhão na tela de detalhes do veículo, permitindo que o gestor tenha acesso a informações detalhadas sobre o desempenho financeiro de
cada caminhão. A Figura 31 demonstra o balanço financeiro do caminhão no aplicativo.

51

Figura 31 – Balanço Financeiro do Caminhão

Fonte: Autoria própria.

Para o gestor, foi implementado o balanço financeiro geral, oferecendo uma visão consolidada da situação financeira de todas as suas frotas. A Figura 32 representa o balanço financeiro geral do gestor.

52

Figura 32 – Balanço Financeiro do Gestor

Fonte: Autoria própria.

Na API, foram implementadas rotas que permitem consultar e gerenciar as informações
financeiras, garantindo o acesso conforme as permissões de cada usuário.
5.5.10

Considerações Finais do Desenvolvimento
Ao longo do ciclo de desenvolvimento do Rodei, o sistema passou por um processo

contínuo de construção e refinamento. A implementação exigiu atenção a detalhes técnicos e
ajustes recorrentes para garantir a consistência da solução.
Nesse contexto, alguns desafios técnicos se tornaram particularmente relevantes. Um
deles esteve relacionado ao comportamento da navegação utilizando o Expo Router 8 . Em de8

Ferramenta de roteamento do ecossistema Expo para gerenciamento de navegação com base em
estrutura de diretórios.

53

terminados momentos, redirecionamentos não funcionaram conforme o esperado, exigindo investigações adicionais e um tempo maior de implementação para assegurar o fluxo correto
entre as telas. Outro ponto importante foi a integração do Image Picker 9 durante o desenvolvimento da funcionalidade de Documentos. Devido à versão do Expo utilizada pelo aplicativo,
essa integração demandou soluções alternativas e maior esforço.
Com todas as funcionalidades descritas implementadas, o sistema alcançou sua primeira versão funcional, apta para testes e validação em um ambiente real. A arquitetura resultante, apresentada na Figura 33, fornece uma visão geral dos principais componentes utilizados.
Figura 33 – Arquitetura do Sistema

Fonte: Autoria própria.

Do ponto de vista quantitativo, o projeto contou com um total de 22 Pull Requests finalizadas, somando 180 commits e um saldo 33.500 linhas de código (37.398 adicionadas e 3.898
removidas). No que diz respeito à garantia de qualidade, o sistema contou com 137 testes automatizados, que ao todo executaram 389 assertions10 .
Por fim, é importante destacar que o desenvolvimento do Rodei não se restringiu às
disciplinas de Trabalho de Conclusão de Curso. O projeto foi construído ao longo de 6 disciplinas
diretamente relacionadas, em um período de 1 ano e 6 meses de desenvolvimento. Outras
9
10

Biblioteca do Expo utilizada para acessar a câmera e a galeria do dispositivo.
Uma assertion (ou asserção) é uma verificação feita durante um teste automatizado para garantir que
determinado valor ou comportamento esteja conforme o esperado.

54

disciplinas, ainda que de forma indireta, também contribuíram para a base de conhecimentos
aplicada ao sistema. Dessa forma, esta primeira versão representa não apenas o resultado
técnico alcançado, mas todo o percurso de aprendizagem consolidado ao longo desse ciclo de
desenvolvimento.

55

6 CONSIDERAÇÕES FINAIS
Em conclusão, nota-se que as atividades de gerenciamento de caminhões, feita por
gestores, podem apresentar obstáculos, afetando diretamente na sustentabilidade das operações. Mesmo que, dentro de um setor importantíssimo para o país, essas dificuldades não tem
a atenção devida. Neste trabalho, estes obstáculos foram apresentados, procurando mostrar
como podem ter impacto nos gestores e motoristas de caminhões.
Dentre os principais problemas identificados ao longo do trabalho, destacam-se a falta
de organização com os registros das viagens, a dificuldade no controle de despesas, a ausência
de uma comunicação eficiente entre gestor e motorista e a sobrecarga de tarefas administrativas
com o aumento da frota. Esses fatores aumentam os riscos de prejuízo, dificultam o planejamento e podem gerar instabilidades na relação entre gestor e motorista.
A motivação para o desenvolvimento deste projeto surgiu a partir da experiência pessoal
na gestão de uma pequena frota familiar. Após análises e conversas com profissionais da área,
foi possível identificar diversas dificuldades no processo de gestão. Isso gerou a motivação de
propor uma solução para a gestão, com o objetivo de torná-la mais controlada e transparente,
minimizando erros e proporcionando uma maior sustentabilidade financeira.
6.1

Trabalhos Futuros
Para o desenvolvimento deste sistema, foram priorizadas as funcionalidades mínimas

necessárias para garantir um desempenho correto e uma implementação efetiva. Por essa razão, algumas funcionalidades e melhorias previstas no escopo inicial não foram implementadas
nesta primeira versão.
Dentre as funcionalidades não contempladas, estão os relatórios detalhados e aprimoramentos importantes, como filtros no balanço financeiro, que poderiam proporcionar uma visão
mais ampla e personalizada para o gestor. Além disso, considera-se a implementação de uma
trilha de auditoria, permitindo registrar e exibir o histórico de alterações realizadas no sistema,
por exemplo, quando um frete foi criado ou atualizado e por qual usuário.
Portanto, espera-se que o sistema seja ampliado em trabalhos futuros, com a inclusão
dessas funcionalidades e melhorias, além de disponibilizar o aplicativo nas lojas.

56

REFERÊNCIAS

ASSIS, J. F. A história do transporte rodoviário no brasil. Revista Faces da História, 2020.
Disponível em: https://pem.assis.unesp.br/index.php/facesdahistoria/article/view/2473/2054.
ATLASSIAN. Git feature branch workflow. 2025. Disponível em: https://www.atlassian.com/
git/tutorials/comparing-workflows/feature-branch-workflow. Acesso em: 11 jun. 2025.
ATLASSIAN. Scrum Sprints: Everything You Need to Know. 2025. Disponível em:
https://www.atlassian.com/agile/scrum/sprints. Acesso em: 11 jun. 2025.
CNT. A Pesquisa CNT de Rodovias 2024. 2024. Disponível em: https://cnt.org.br/documento/
cbf59b9e-fd1a-41fc-b230-172c4dc42100. Acesso em: 21 abr. 2025.
COHN, M. User Stories. 2025. Disponível em: https://www.mountaingoatsoftware.com/agile/
user-stories. Acesso em: 11 jun. 2025.
CONSORTIUM, A. B. MoSCoW Prioritisation. 2025. Disponível em: https://www.agilebusiness.
org/dsdm-project-framework/moscow-prioririsation.html. Acesso em: 5 jun. 2025.
CUCUMBER. Gherkin Language Reference. 2025. Disponível em: https://cucumber.io/docs/
gherkin/reference. Acesso em: 11 jun. 2025.
EXPO. Expo and EAS are an ecosystem of tools that help you develop, review and
deploy. 2025. Disponível em: https://expo.dev/. Acesso em: 5 jun. 2025.
EXPO. Expo SecureStore. 2025. Disponível em: https://docs.expo.dev/versions/latest/sdk/
securestore. Acesso em: 3 nov. 2025.
FDC. Custo logístico tem um aumento de cerca de 15,5 bilhões da receita das
empresas entre 2015 e 2017. 2018. Disponível em: https://www.fdc.org.br/conhecimento-site/
nucleos-de-pesquisa-site/centro-de-referencia-site/Materiais/Custos_Logisticos_2018.pdf.
Acesso em: 20 abr. 2025.
FIGMA. Think bigger. Build faster. 2025. Disponível em: https://www.figma.com/. Acesso em:
5 jun. 2025.
GIT. Everything is local. 2025. Disponível em: https://git-scm.com/. Acesso em: 5 jun. 2025.
GITHUB. Build and ship software on a single, collaborative platform. 2025. Disponível em:
https://github.com/. Acesso em: 5 jun. 2025.
HOLISTICS. Draw Entity-Relationship Diagrams, Painlessly. 2025. Disponível em:
https://dbdiagram.io/home. Acesso em: 5 jun. 2025.
IBGE. PIB cresce 2,9% em 2023 e fecha o ano em R$ 10,9 trilhões. 2024. Disponível em:
https://agenciadenoticias.ibge.gov.br/agencia-sala-de-imprensa/2013-agencia-de-noticias/
releases/39303-pib-cresce-2-9-em-2023-e-fecha-o-ano-em-r-10-9-trilhoes. Acesso em: 10
abr. 2025.
ILOS. Estoque rouba a cena nos custos logísticos do Brasil em 2023. 2024. Disponível em:
https://ilos.com.br/estoque-rouba-a-cena-nos-custos-logisticos-do-brasil-em-2023. Acesso
em: 10 abr. 2025.
LARAVEL. Authorization. 2025. Disponível em: https://laravel.com/docs/12.x/authorization.
Acesso em: 08 dez. 2025.

57

LARAVEL. Build and ship software with tools crafted for productivity. 2025. Disponível em:
https://laravel.com. Acesso em: 5 jun. 2025.
LARAVEL. Laravel Sanctum. 2025. Disponível em: https://laravel.com/docs/12.x/sanctum.
Acesso em: 3 nov. 2025.
MTR. Documento Eletrônico de Transporte - DT-e. 2024. Disponível em: https:
//www.gov.br/transportes/pt-br/assuntos/transporte-terrestre_/dt-e. Acesso em: 21 abr. 2025.
REACTNATIVE. Learn once, write anywhere. 2025. Disponível em: https://reactnative.dev/.
Acesso em: 5 jun. 2025.
SEMPARAR. O que é o serviço Sem Parar? 2025. Disponível em: https://ajuda.semparar.com.
br/hc/pt-br/articles/360047425951-O-que-%C3%A9-o-servi%C3%A7o-Sem-Parar. Acesso em:
23 abr. 2025.
SENATRAN. Frota de veículos - 2025. 2025. Disponível em: https://www.gov.br/transportes/
pt-br/assuntos/transito/conteudo-Senatran/frota-de-veiculos-2025. Acesso em: 10 abr. 2025.
TRC. Transporte Rodoviário de Cargas. 2020. Disponível em: https://www.gov.br/transportes/
pt-br/assuntos/transporte-terrestre/transporte-rodoviario-de-cargas. Acesso em: 10 abr. 2025.
ZOD. Zod. 2025. Disponível em: https://zod.dev. Acesso em: 08 dez. 2025.

APÊNDICES

59

APÊNDICE A – Modelagem Completa do Banco de Dados

60

A Figura 34 representa a modelagem completa do banco de dados do aplicativo Rodei.
Figura 34 – Diagrama da Modelagem de Banco de Dados.

Fonte: Autoria própria (2025)

