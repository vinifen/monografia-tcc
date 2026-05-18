# e-museu-tcc-escrita

Repositório de apoio à **monografia de TCC (Trabalho de Conclusão de Curso 2)** do curso de **Tecnologia em Sistemas para Internet**, UTFPR — Campus Guarapuava.

## Para assistentes de IA (Cursor)

- **Regra activa:** `.cursor/rules/tcc-monografia.mdc` (`alwaysApply: true`) — lê-a **em conjunto** com este `README.md` antes de propor mudanças largas.
- **Etapa actual do texto:** ver secção [**Evolução da redação (monografia TCC 2)**](#evolução-da-redação-monografia-tcc-2) — indica em que capítulos estamos a trabalhar e o que já foi feito neste repositório.
- **Histórico de alterações:** este repo tem **Git**; antes de editar capítulos longos, consultar `git log` e `git diff` (comandos na mesma secção) para não contradizer mudanças recentes.
- **Ordem sugerida:** `README.md` (este ficheiro) → regra em `.cursor/rules/` → secção “Evolução da redação” → pastas de consulta em “Pastas de apoio”.
- **Onde escrever o PDF do TCC:** **apenas** `tcc-overleaf-vinicius-ferreira-novacoski-monografia/`; o resto é **contexto e evidências**.
- **Transcrições de conversas:** índice em [`chats/README.md`](chats/README.md).
- **Compilar o LaTeX:** Overleaf, `latexmk` ou distribuição TeX local — o assistente deve manter o documento **compilável** quando editar `.tex` / `.bib`.
- **Autonomia do PDF:** o texto entregue deve bastar a quem só lê a monografia. Material fora de `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` é **insumo** (síntese no LaTeX), **não** substituto de redacção nem referência directa ao “exterior” no corpo; excepções (citações, anexos) entram **copiadas ou incorporadas** na pasta LaTeX. Detalhe: `.cursor/rules/tcc-monografia.mdc` secção 2.1.
- **Padrão UTFPR + colegas (GP_COINT):** ao propor estrutura, tom ou formalismos, contrastar com o **template já usado** em `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` e com **trabalhos de referência recentes** em `referencias/` (lista na secção **Pastas de apoio → `referencias/`**). O objectivo é **alinhar expectativas da banca** (ABNT, capítulos, prosa académica) ao que é habitual no curso — **sem copiar** conteúdo alheio.

O documento principal tem por título **Refatoração e Implementação de Novas Funcionalidades no E-Museu**: trabalho acadêmico que acompanha e formaliza a evolução do projeto de software **E-Museu** (museu virtual de informática), incluindo decisões técnicas, arquitetura, implementação e resultados, em formato exigido pela instituição (LaTeX, normas UTFPR/ABNT).

- **Autor:** Vinicius Ferreira Novacoski  
- **Título:** *Refatoração e Implementação de Novas Funcionalidades no E-Museu* (*Refactoring and Implementation of New Features in the E-Museu*)  
- **Orientação:** Dra. Sediane Carmem Lunardi Hernandes  
- **Coorientação:** Dr. Diego Marczal  
- **Esforço:** o trabalho no conjunto (implementação do E-Museu, infraestrutura — por exemplo Coolify —, documentação e atividades do TCC) levou **mais de 250 horas**, segundo o registo do autor (inclui o diário em `notion-historico/notion-tcc-historico.md`).

Este repositório **não substitui** o código-fonte publicado no GitHub; serve para **redação**, **referências** e **material de consulta** enquanto se escreve a monografia. A implementação em que o TCC se apoia — o **E-Museu desenvolvido pelo autor** — está refletida na cópia local **`e-museu-v2_0_0-ultima-versao-viniciusfn/`** (projeto principal de software; ver secção abaixo).

**Estado actual (foco do repositório):** o **software do E-Museu já está finalizado** (funcionalidades, deploy, entregas à UTFPR). A parte de **texto da fase projeto** (proposta, capítulos iniciais) **já existia** no LaTeX e foi **reorganizada para a estrutura da monografia TCC 2** (ver [evolução abaixo](#evolução-da-redação-monografia-tcc-2)). O trabalho corrente neste repositório é **redigir e fechar** os capítulos da monografia — com **ênfase recente em Materiais e Métodos** e **redacção iniciada em Desenvolvimento e Conclusões**. **A fase actual é a do texto**, não a de novas implementações no código.

**Intenção perante a banca / orientação:** o autor pretende que o texto **deixe claro o trabalho realizado** — o que foi feito, com que rigor e que suporte (histórico GitHub, diário, deploy, decisões), para os professores perceberem **a dimensão e a exigência** do projeto, **sem exageros** nem tom publicitário: factos verificáveis, linguagem académica e moderação nos adjetivos.

## Evolução da redação (monografia TCC 2)

Registo do **processo neste repositório** (`e-museu-tcc-escrita`), para o autor e para assistentes de IA saberem **em que etapa do texto estamos**. O histórico do **código** do E-Museu continua no GitHub da aplicação; aqui o Git documenta sobretudo **LaTeX, bibliografia e apoio à redacção**.

### O que já passámos

1. **Arranque do repo de escrita** (`b02c10c`, 2026-05-15): concentração do projeto LaTeX e do material de consulta num único sítio.
2. **De projeto → monografia** (`23c31d9`, 2026-05-17): actualização do texto da **fase projeto** para a **estrutura da monografia** — `main.tex` com ordem alinhada a trabalhos GP_COINT (introdução, trabalhos relacionados, referencial, materiais e métodos, desenvolvimento, conclusões); criação/expansão de `cap-desenvolvimento.tex` e `cap-conclusoes.tex`; remoção de `cap-resultados-parciais.tex`; capítulos só de projeto (`cap-proposta`, etc.) **comentados** no `main.tex` para não entrarem no PDF final.
3. **Materiais e Métodos** (`eee4ada` e revisões seguintes, inclusive em sessão com IA): expansão forte de `cap-materiais-e-metodos.tex` (tecnologias, Docker, Coolify, Git/GitFlow, ferramentas de qualidade, etc.), entradas em `main.bib`, ajustes de tom e formatação (ex.: ramos `main`/`develop`, ambientes de *staging* e produção).
4. **Agora:** **Desenvolvimento** e **Conclusões** em redacção activa; introdução, trabalhos relacionados e referencial com base da fase anterior, sujeitos a revisão quando o núcleo estiver fechado.

### Etapa actual por capítulo

Ordem no PDF (`main.tex`):

| Capítulo | Ficheiro | Estado (Maio/2026) |
|----------|----------|-------------------|
| Introdução | `capitulos/cap-introducao.tex` | Base herdada; revisões pontuais |
| Trabalhos relacionados | `capitulos/cap-trabalhos-relacionados.tex` | Na estrutura monografia; pode alargar |
| Referencial teórico | `capitulos/cap-referencial-teorico.tex` | Idem |
| **Materiais e Métodos** | `capitulos/cap-materiais-e-metodos.tex` | **Muito trabalhado recentemente; ainda em polimento** |
| **Desenvolvimento** | `capitulos/cap-desenvolvimento.tex` | **Em redacção** |
| **Conclusões** | `capitulos/cap-conclusoes.tex` | **Em redacção** |
| Só fase projeto | `cap-proposta.tex`, `cap-conceitos.tex`, … | Fora do `main.tex` activo |

**Para a IA:** se o autor não indicar o capítulo, assumir foco em **Materiais e Métodos** (revisão), **Desenvolvimento** e **Conclusões**. Não reestruturar `main.tex` nem reactivar capítulos de projeto sem pedido explícito.

### Consultar a evolução pelo Git

```bash
# Visão geral dos commits deste repo
git log --oneline

# Histórico só dos capítulos LaTeX
git log --oneline -- tcc-overleaf-vinicius-ferreira-novacoski-monografia/capitulos/

# O que mudou desde o último commit
git diff
git diff -- tcc-overleaf-vinicius-ferreira-novacoski-monografia/capitulos/cap-materiais-e-metodos.tex

# Detalhe de um commit (substituir HASH)
git show HASH --stat
git show HASH -p -- tcc-overleaf-vinicius-ferreira-novacoski-monografia/
```

**Commits de referência** (até Maio/2026):

| Hash | Mensagem | Conteúdo principal |
|------|----------|-------------------|
| `b02c10c` | start | Criação do repositório de escrita |
| `0b1af28` | Comeback | Retomada do trabalho no repo |
| `23c31d9` | Estruturacao monografia | Projeto → estrutura monografia; desenvolvimento e conclusões |
| `eee4ada` | melhora em materis e metodos | Cap. materiais/métodos, bib, desenvolvimento |

**Boas práticas:** o autor deve fazer **commits com mensagens claras** ao fechar blocos de capítulo (ex.: “cap-desenvolvimento: seção deploy”, “cap-materiais: revisão Coolify”); a IA deve **ler `git log` / `git diff`** ao retomar uma conversa longa ou antes de reescrever secções extensas.

*Actualizar esta secção quando mudar a prioridade (ex.: passar a Resultados, revisão global, pré-texto).*

---

## Repositórios no GitHub (E-Museu e documentação de workflow)

| | |
|--|--|
| **Organização (upstream)** | [**e-museu-utfpr-gp/e-museu**](https://github.com/e-museu-utfpr-gp/e-museu) |
| Issues | [github.com/e-museu-utfpr-gp/e-museu/issues](https://github.com/e-museu-utfpr-gp/e-museu/issues) |
| Pull requests | [github.com/e-museu-utfpr-gp/e-museu/pulls](https://github.com/e-museu-utfpr-gp/e-museu/pulls) |
| Wiki | [github.com/e-museu-utfpr-gp/e-museu/wiki](https://github.com/e-museu-utfpr-gp/e-museu/wiki) |
| **Fork do autor (beta)** | [**vinifen/e-museu-2.1.0-beta**](https://github.com/vinifen/e-museu-2.1.0-beta) |
| Wiki (fork) | [github.com/vinifen/e-museu-2.1.0-beta/wiki](https://github.com/vinifen/e-museu-2.1.0-beta/wiki) |
| **GitFlow / workflow GitHub (autor)** | [**vinifen/gitflow-documentation**](https://github.com/vinifen/gitflow-documentation) — repositório com guia, topologia de branches, convenções de commits, templates de issues/PRs e perfis *full* vs *simple*; no E-Museu o autor adotou o **perfil *full*** (branches no estilo `@dev/…`, commits com emoji e tipo, templates completos). A wiki inclui um resumo em [`all-github-docs/wiki/Gitflow-Documentation.md`](all-github-docs/wiki/Gitflow-Documentation.md). |

---

## Onde se trabalha de verdade

### `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` — **único local do texto final**

É aqui que está o **projeto LaTeX** (template UTFPR) que gera o **PDF** do trabalho. Já contém o que foi escrito para a **fase do projeto** (por exemplo proposta e capítulos iniciais); **essa parte do texto do projeto já está feita**. O **código do E-Museu já foi concluído**; neste momento o autor concentra-se na **monografia da disciplina TCC 2** — completar, alargar e polir o **texto** (capítulos, revisões, bibliografia, figuras) até à entrega final à UTFPR. Toda a edição académica deve continuar **nesta pasta**.

Estrutura resumida:

| Caminho | Função |
|--------|--------|
| `main.tex` | Entrada principal do documento; inclui capítulos e configurações. |
| `variaveis.tex` | Dados do autor, título, orientadores, palavras-chave, licença CC, etc. |
| `configuracoes.tex` | Ajustes do template e do documento. |
| `main.bib` | Referências bibliográficas (BibTeX). |
| `utfpr.cls` | Classe LaTeX da UTFPR. |
| `capitulos/` | Capítulos do texto (`cap-introducao.tex`, `cap-proposta.tex`, `cap-trabalhos-relacionados.tex`, etc.). |
| `PreTexto/` | Resumo, abstract, agradecimentos, listas, epígrafe, errata, logos em `PreTexto/arquivos/`, etc. |
| `PosTexto/` | Apêndices, anexos, glossário, ilustrações legais, etc. |
| `readme.md` | Notas do template Overleaf/UTFPR (documentação do próprio modelo). |

O fluxo típico é: editar `.tex` / `.bib` aqui → compilar (Overleaf, `latexmk` ou TeX local) → gerar o PDF da monografia.

**Âmbito das edições no LaTeX:** se for **necessário para coerência** com o que ficou documentado no repositório (PRs, issues, diário, orientações, versão final do sistema), podem alterar-se **quaisquer ficheiros** na pasta `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` — por exemplo alinhar `capitulos/` com `PreTexto/` e `PosTexto/`, actualizar `main.bib`, `variaveis.tex`, `configuracoes.tex` ou inclusões em `main.tex`. **Recomendação:** não alterar **`utfpr.cls`** salvo pedido explícito (template institucional).

**Todo o resto do repositório** existe para **informar** a redação da monografia (histórico, evidências, literatura e cópias de código), **não** como substituto do `main.tex`.

**Autonomia do PDF (projecto “fechado”):** imagina `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` como o **único sítio do entregável** — um **projecto LaTeX desacoplado** do resto do repo no sentido em que **a banca não deve precisar** de Notion, Discord, `chats/`, `all-github-docs/` nem de pastas de código para entender o trabalho. Esse material serve de **fonte de conteúdo** para **sintetizar e escrever** no `.tex` (prosa académica, dados, conclusões), **não** para colar conversas, “como disseram no chat…” ou referências directas ao exterior como se o PDF fosse um índice. Se for **obrigatório** citar literalmente ou anexar algo que hoje está só fora da pasta LaTeX, esse conteúdo deve ser **incorporado** em `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` (figuras, `PosTexto/`, PDF em anexo, etc.), para o conjunto ser **único** do ponto de vista de quem recebe o trabalho.

---

## Pastas de apoio (só informação)

### `all-github-docs/`

Exportações em **Markdown** a partir do GitHub, para consulta rápida no editor e para contextualizar o que foi feito no software sem depender só do site.

| Subpasta | Conteúdo |
|----------|-----------|
| `pull-requests/` | Descrições dos PRs exportados de [**e-museu-utfpr-gp/e-museu**](https://github.com/e-museu-utfpr-gp/e-museu/pulls) e [**vinifen/e-museu-2.1.0-beta**](https://github.com/vinifen/e-museu-2.1.0-beta/pulls), com metadados no cabeçalho de cada ficheiro. |
| `issues/` | Issues reais de [**e-museu-utfpr-gp/e-museu**](https://github.com/e-museu-utfpr-gp/e-museu/issues) e [**vinifen/e-museu-2.1.0-beta**](https://github.com/vinifen/e-museu-2.1.0-beta/issues) (entradas que são só PR foram excluídas para não duplicar `pull-requests/`). |
| `wiki/` | Cópia em `.md` das wikis ([upstream](https://github.com/e-museu-utfpr-gp/e-museu/wiki), [fork](https://github.com/vinifen/e-museu-2.1.0-beta/wiki)). Inclui `Home.md`, `Database.md` e **`Gitflow-Documentation.md`** — documentação **escrita pelo autor** para o projeto seguir **GitFlow** e o workflow no GitHub no **modo *full*** (ver [**vinifen/gitflow-documentation**](https://github.com/vinifen/gitflow-documentation): branches `@dev/…`, commits com emoji, issues/PRs, labels, templates). |

### `referencias/`

Material de **bibliografia e comparação**: monografias e projetos de colegas (GP_COINT), TCC antigo do E-Museu, etc.

- Ficheiros **`.md`**: texto extraído de PDFs (`pdftotext`, UTF-8) para leitura e pesquisa no editor; cada ficheiro indica em YAML o **`source_pdf`** correspondente.  
- **`original-pdfs/`**: cópias dos PDFs originais (fonte fiel para **citação**, **figuras** e conferência de metadados).

**Padrão institucional e trabalhos de colegas:** o PDF oficial do autor deve seguir o **template UTFPR** em `tcc-overleaf-vinicius-ferreira-novacoski-monografia/` (`utfpr.cls`, `variaveis.tex`, estrutura de capítulos e normas do curso). Para **calibrar estrutura, extensão, tom e formalismos** (sem substituir orientação nem plagiar), usam-se também monografias e **projetos** de colegas do mesmo contexto (GP_COINT), em especial os **mais recentes** abaixo — o mesmo tipo de alinhamento que se faz ao comparar capítulos com outros `.md` já presentes nesta pasta (ex.: 2025/1, 2025/2).

**Referências recentes (GP_COINT — texto em `.md` + PDF em `original-pdfs/`):**

| Trabalho | `.md` (extraído) | PDF original |
|----------|------------------|--------------|
| Beatriz Freccia Amante — monografia 2025/2 | [`referencias/GP_COINT_2025_2_BEATRIZ_FRECCIA_AMANTE_MONOGRAFIA.md`](referencias/GP_COINT_2025_2_BEATRIZ_FRECCIA_AMANTE_MONOGRAFIA.md) | [`referencias/original-pdfs/GP_COINT_2025_2_BEATRIZ_FRECCIA_AMANTE_MONOGRAFIA.pdf`](referencias/original-pdfs/GP_COINT_2025_2_BEATRIZ_FRECCIA_AMANTE_MONOGRAFIA.pdf) |
| Pablo de Paula Correia — monografia 2025/2 | [`referencias/GP_COINT_2025_2_PABLO_DE_PAULA_CORREIA_MONOGRAFIA.md`](referencias/GP_COINT_2025_2_PABLO_DE_PAULA_CORREIA_MONOGRAFIA.md) | [`referencias/original-pdfs/GP_COINT_2025_2_PABLO_DE_PAULA_CORREIA_MONOGRAFIA.pdf`](referencias/original-pdfs/GP_COINT_2025_2_PABLO_DE_PAULA_CORREIA_MONOGRAFIA.pdf) |
| Vinicius Domingues Pereira — projeto 2024/2 | [`referencias/GP_COINT_2024_2_VINICIUS_DOMINGUES_PEREIRA_PROJETO.md`](referencias/GP_COINT_2024_2_VINICIUS_DOMINGUES_PEREIRA_PROJETO.md) | [`referencias/original-pdfs/GP_COINT_2024_2_VINICIUS_DOMINGUES_PEREIRA_PROJETO.pdf`](referencias/original-pdfs/GP_COINT_2024_2_VINICIUS_DOMINGUES_PEREIRA_PROJETO.pdf) |

Outros `.md` de GP_COINT e o TCC antigo do E-Museu permanecem na mesma pasta para consulta (formato, literatura, comparação de secções).

### `notion-historico/`

- **`notion-tcc-historico.md`:** diário de atividades do TCC convertido a partir do export HTML do Notion (cronologia do que foi feito no dia a dia).  
- **`html/`:** export HTML de backup do Notion; a versão usada para leitura contínua no projeto é o `notion-tcc-historico.md`.

### `chats/`

Índice das transcrições: [`chats/README.md`](chats/README.md).

#### `chats/sediane/`

Transcrições **sanitizadas** de conversas com a **orientadora** (Profª. Sediane): cronologia de alinhamentos, VM/UTFPR, instalação do E-Museu, pedidos de chamados, etc. Útil para **metodologia**, **desenvolvimento do trabalho** ou **relação com a orientação** na monografia. Os ficheiros **não** reproduzem senhas, links de Meet completos nem chaves Pix.

- Exemplo: `chats/sediane/historico-marco-abril-2026.md`.

#### `chats/server-tcc-vinicius/`

Transcrições **sanitizadas** do **canal público do Discord** do TCC, com **orientadora (Sediane)** e **coorientador (Diego Marczal)** — proposta, referências de livros, feedback formal ao texto (ClickUp, escopo, objetivos) e combinação de prazos.

- Exemplo: `chats/server-tcc-vinicius/historico-ago-set-2025.md`.

### `e-museu-tankensho-primeira-versao-feita/`

Referência de **código** da **primeira versão** do E-Museu (**legado**, não é o projeto principal atual do autor), útil para comparar “antes e depois” com a refatoração descrita na monografia.

### `e-museu-v2_0_0-ultima-versao-viniciusfn/` — **projeto principal de software (feito por mim)**

Esta pasta é a cópia local do **E-Museu desenvolvido pelo autor**: é o **projeto principal** no sentido de **implementação** — a versão **atual** do sistema web objeto da monografia (refatoração, funcionalidades, deploy, etc.). Enquanto a monografia vive no LaTeX, **este é o código em que o trabalho técnico se materializa** e o que deve ser citado ou descrito ao tratar de arquitetura, módulos, decisões de implementação ou resultados no software. O histórico público correspondente está em [**e-museu-utfpr-gp/e-museu**](https://github.com/e-museu-utfpr-gp/e-museu) (e, quando aplicável, no fork [**vinifen/e-museu-2.1.0-beta**](https://github.com/vinifen/e-museu-2.1.0-beta)).

A pasta `e-museu-tankensho-primeira-versao-feita/` serve sobretudo como **contraste com o legado**; já **`e-museu-v2_0_0-ultima-versao-viniciusfn/`** é a linha de trabalho **do autor** e **recente**, alinhada ao TCC.

*(A fonte de verdade para histórico e colaboração é o GitHub — em especial [**e-museu-utfpr-gp/e-museu**](https://github.com/e-museu-utfpr-gp/e-museu) e o fork [**vinifen/e-museu-2.1.0-beta**](https://github.com/vinifen/e-museu-2.1.0-beta); esta pasta é cópia local para consulta junto do texto do TCC.)*

### `secret-e-museu-utfpr-gp/` — **pacote para continuidade (Coolify + backups, sem senhas)**

Conjunto preparado para **entrega em pen drive à orientação** (UTFPR), com o objetivo de **facilitar a recuperação ou a reconfiguração** do ambiente **Coolify** e do **E-Museu** se alguém tiver de refazer deploy ou infraestrutura no futuro. A ideia é ter **num só sítio** documentação e artefactos úteis, numa variante **sem palavras-passe** nos ficheiros de texto exportados.

Conteúdo típico (estrutura actual):

| Caminho | Descrição |
|---------|------------|
| `txt/coolify/` | Textos exportados com configurações **staging** e **production** (aplicação principal, MySQL, Redis, MinIO) e ficheiros de contexto (subdomínio, perfil, webhooks GitHub, versões). |
| `txt/env-local-v-2_0_0.txt` | Referência de variáveis de ambiente (versão sanitizada). |
| `txt/keys.txt` | Chaves ou placeholders conforme a versão preparada para entrega (verificar sempre antes de partilhar ou de fazer push para repositórios públicos). |
| `data/emuseu_dump.sql` | **Dump SQL** do estado da base de dados para restauro ou análise offline. |
| `data/items/` | **Backups de ficheiros** associados a itens do catálogo (ex.: pastas por ID). |
| `projects/` | Arquivos compactados do projeto (**`e-museu-full-v2_0_0.tar.gz`**, **`e-museu-github-v2_0_0.zip`**) — cópia “completa” / cópia alinhada ao GitHub para reinstalação sem depender só da rede; a variante *full* pode incluir **`node_modules`** e restantes dependências para instalação offline. |

Esta pasta **não** substitui o repositório GitHub nem o `e-museu-v2_0_0-ultima-versao-viniciusfn/` para desenvolvimento diário; serve de **arquivo operacional e de continuidade institucional**, citável na monografia quando descreveres **entrega**, **disaster recovery** ou **documentação de implantação**.

**Cuidado:** dumps, ficheiros de chaves e arquivos do projeto podem conter **dados pessoais ou segredos** se a versão não for rigorosamente sanitizada. Não commits esta pasta a repositórios públicos sem revisão.

---

## Resumo

| Local | Papel |
|-------|--------|
| **`tcc-overleaf-vinicius-ferreira-novacoski-monografia/`** | **Monografia LaTeX — texto entregue à UTFPR; inclui o que já foi feito na fase do *projeto*; foco actual: fechar a monografia do TCC 2.** |
| **`e-museu-v2_0_0-ultima-versao-viniciusfn/`** | **Código do E-Museu pelo autor — implementação já finalizada; consulta para escrever a monografia.** |
| **`secret-e-museu-utfpr-gp/`** | **Pacote pen drive / continuidade:** Coolify (texto sem senhas), dump SQL, backups de `items/`, arquivos do projeto — para a UTFPR refazer configuração se necessário. |
| Demais pastas | **Contexto:** `all-github-docs/`, `referencias/`, `notion-historico/`, `chats/`, legado (`e-museu-tankensho-…`). |

---

## Licença e template

O projeto LaTeX segue o **template UTFPR** (classe `utfpr.cls`, orientações em `variaveis.tex` e no `readme.md` dentro da pasta Overleaf). A licença Creative Commons do trabalho acadêmico está configurada em `variaveis.tex` (ex.: CC BY), conforme regras do curso e orientação.
