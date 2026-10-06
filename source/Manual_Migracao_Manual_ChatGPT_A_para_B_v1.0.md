---
title: "Manual de Migração Manual de Alta Fidelidade entre Contas ChatGPT"
subtitle: "Conta A → Conta B | Sem dependência do ZIP | Objetivo: continuidade operacional"
author: "Documento operacional gerado a partir do Prompt Mestre v1.0"
date: "2026-10-06"
lang: pt-BR
mainfont: "DejaVu Serif"
sansfont: "DejaVu Sans"
monofont: "DejaVu Sans Mono"
documentclass: report
papersize: a4
classoption:
  - openany
fontsize: 10pt
geometry:
  - margin=2.2cm
  - headheight=15pt
toc: true
toc-depth: 3
numbersections: true
colorlinks: true
linkcolor: blue
urlcolor: blue
header-includes:
  - |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhf{}
    \fancyhead[L]{\small Manual de Migração ChatGPT A → B}
    \fancyhead[R]{\small v1.0 — 2026-10-06}
    \fancyfoot[C]{\thepage}
  - |
    \usepackage{mdframed}
    \renewenvironment{quote}{\begin{mdframed}[backgroundcolor=black!3,linecolor=black!35,linewidth=0.6pt,roundcorner=2pt,skipabove=8pt,skipbelow=8pt,innerleftmargin=8pt,innerrightmargin=8pt,innertopmargin=7pt,innerbottommargin=7pt]}{\end{mdframed}}
  - |
    \usepackage{fvextra}
    \fvset{breaklines=true,breakanywhere=true}
  - |
    \usepackage{enumitem}
    \setlist{nosep,leftmargin=*}
  - |
    \usepackage{microtype}
  - |
    \usepackage{longtable,booktabs,tabularx}
  - |
    \widowpenalty=10000
    \clubpenalty=10000
---

\thispagestyle{empty}

# Escopo e objetivo do manual

**Conta A → Conta B**  
**Cenário primário: migração sem depender do ZIP de exportação**  
**Versão:** 1.0  
**Data de referência:** 2026-10-06  
**Status:** manual operacional completo

> **AVISO DE CENÁRIO**  
> Este manual assume `ZIP_DISPONÍVEL = NÃO`. Nenhuma etapa crítica depende da exportação oficial. Se o ZIP chegar depois, ele entra apenas como fonte complementar de auditoria, reconciliação e recuperação histórica.

> **OBJETIVO**  
> Fazer com que a Conta B funcione, tanto quanto tecnicamente possível, como continuação operacional da Conta A, reduzindo ao mínimo o contexto, conhecimento e trabalho intelectual que precisariam ser reconstruídos caso a Conta A deixe de estar disponível.

\clearpage

# Controle documental

| Campo | Valor |
|---|---|
| Documento | `Manual_Migracao_Manual_ChatGPT_A_para_B_v1.0` |
| Versão | 1.0 |
| Data | 2026-10-06 |
| Fonte autoritativa | Prompt Mestre v1.0 (arquivo Markdown anexado) |
| Conta de origem | Conta A |
| Conta de destino | Conta B |
| Premissa crítica | ZIP não disponível |
| Prioridade | qualidade > fidelidade > completude > rastreabilidade > clareza > executabilidade > concisão |
| Uso esperado | execução real, passo a passo |

## Convenções

- **[VERIFICAR NA INTERFACE ATUAL]**: o comportamento depende da versão da interface, do plano, da região ou de rollout.
- **[RECONCILIAR COM ZIP DEPOIS]**: etapa opcional futura; não bloqueia a migração atual.
- **M0/M1/M2**: urgência temporal.
- **P0/P1/P2/P3**: importância operacional da etapa.
- **P0/P1/P2/P3/P4** quando aplicado a projetos: criticidade do projeto.
- **A/B/C/D/E**: classe de migração de conversas.
- **CONFIRMADO / INFERIDO / CONFLITO / DESATUALIZADO? / NÃO RECUPERADO**: status epistemológico.

# Resumo executivo

A migração de uma conta ChatGPT para outra não deve ser tratada como cópia de chats. A continuidade depende de cinco camadas que precisam ser preservadas separadamente: **regras**, **memória/contexto**, **estado dos projetos**, **evidência histórica** e **artefatos**. Uma conversa copiada pode existir na Conta B e ainda assim ser incapaz de continuar o trabalho corretamente.

O princípio central deste manual é:

> **CONTINUABLE > COPIED**  
> O objetivo não é apenas fazer o conteúdo aparecer na Conta B, mas fazer com que a Conta B consiga retomar corretamente a próxima ação, as premissas, os arquivos, as decisões, as exceções e o conhecimento negativo necessário.

A ordem operacional recomendada é deliberadamente assimétrica. Primeiro, capture aquilo que só a Conta A ainda consegue fornecer com riqueza: memória, inferências, relações transversais, correções e estado vivo dos projetos. Depois inventarie e transfira o material bruto. Copiar centenas de chats antes de capturar o contexto semântico pode consumir o tempo restante de Plus e ainda deixar a Conta B com um arquivo histórico volumoso, porém pouco operacional.

## Fatos atuais que alteram a estratégia (verificados em 2026-10-06)

Estas observações vêm da documentação oficial atual da OpenAI e devem ser reinterpretadas se a interface mudar:

1. **Instruções personalizadas** existem em todos os planos, mas o limite documentado é de até **5.000 caracteres em Plus/Pro/Business/Enterprise/Edu** e **1.500 em Free/Go**. Isso torna a cópia integral das instruções da Conta A uma tarefa M0 se houver risco de downgrade. Não se presume que conteúdo excedente seja apagado após downgrade; a documentação consultada não garante esse comportamento.
2. **Projetos** existem em planos gratuitos e pagos. O limite atual de arquivos por projeto é **25 em Plus/Go** e **5 em Free**. Não se presume que arquivos acima do limite sejam apagados após downgrade; preserve-os porque o comportamento de uma conta já acima da cota não é especificado na fonte consultada.
3. **Library** existe em Free e Plus, mas a cota documentada é atualmente **20 GB em Plus** e **500 MB em Free**. Faça inventário e download local dos arquivos críticos ainda no Plus.
4. **Memória** pode usar chats, memórias, instruções, arquivos da Library e conteúdo de apps, dependendo do plano/conta. O **Resumo da memória não é integral**: ele captura os detalhes mais importantes, não tudo que o sistema pode usar.
5. **Shared Links** permitem que uma pessoa autenticada continue uma conversa compartilhada, criando uma **conversa separada e privada na conta destinatária**. Em contas pessoais, o link é um snapshot que não incorpora automaticamente mensagens posteriores. Excluir o link depois não remove a cópia já criada pelo destinatário.
6. **Projetos compartilhados** não são uma ponte neutra: ao serem compartilhados, passam a usar **memória somente do projeto** e deixam de acessar memórias/contexto externo dos membros. Não compartilhe um projeto P0 original apenas por conveniência sem avaliar esse efeito.
7. **Tarefas agendadas** podem, quando elegíveis, ser compartilhadas por link com instruções, agenda e fuso; o destinatário agenda uma cópia própria que usa sua conta, apps e permissões.
8. **Apps/conectores** são hoje organizados no ecossistema de **Plugins**. Conexões precisam ser revisadas e reautenticadas na Conta B; não trate credenciais como parte transferível do chat.
9. **GPTs personalizados** mudaram substancialmente: em contas pessoais, a criação/publicação de novos GPTs não está disponível na documentação atual. GPTs existentes podem continuar disponíveis e, em condições elegíveis, editáveis, enquanto a OpenAI migra esses fluxos para Plugins. Portanto, o plano antigo de “recriar um GPT na Conta B” pode ser impossível e deve ser substituído por preservação da configuração + migração para Plugin/fluxo equivalente quando a interface permitir.
10. A exportação oficial pode levar **até 7 dias** e o link de download expira **24 horas** após o recebimento. Isso reforça que o ZIP não deve ser a dependência da operação atual.

### Fontes oficiais verificadas

- [OpenAI — Memória no ChatGPT](https://help.openai.com/pt-br/articles/8590148-memory-in-chatgpt)
- [OpenAI — Instruções personalizadas](https://help.openai.com/en/articles/8096356-chatgpt-custom-instructions)
- [OpenAI — Projetos no ChatGPT](https://help.openai.com/pt-br/articles/10169521-using-projects-in-chatgpt)
- [OpenAI — Links compartilhados](https://help.openai.com/pt-br/articles/7925741-chatgpt-shared-links-faq)
- [OpenAI — Library](https://help.openai.com/pt-br/articles/20001052-using-library-to-manage-files-in-chatgpt)
- [OpenAI — Tarefas agendadas](https://help.openai.com/pt-br/articles/10291617-scheduled-tasks-in-chatgpt)
- [OpenAI — GPTs](https://help.openai.com/en/articles/8554407-gpts-in-chatgpt)
- [OpenAI — Criando/editando GPTs](https://help.openai.com/en/articles/8554397-creating-a-gpt.)
- [OpenAI — Apps conectados](https://help.openai.com/pt-br/articles/11487775-connected-apps-in-chatgpt)
- [OpenAI — Exportação de dados](https://help.openai.com/pt-br/articles/7260999-exporting-your-chatgpt-history-and-data)

# Como usar este manual

Use este documento como roteiro operacional e registro de controle. Não tente executar tudo em uma sessão longa sem checkpoints. A migração pode durar dias e deve continuar sendo auditável mesmo se for interrompida.

A cada bloco de trabalho:

1. abra `14_MIGRATION_MANIFEST.md`;
2. escolha a próxima tarefa pela combinação **urgência + importância**;
3. execute a etapa na Conta A e/ou Conta B;
4. salve o artefato local indicado;
5. registre evidência mínima: data, item, resultado, lacuna e próximo passo;
6. atualize o Manifest;
7. ao encerrar a sessão, gere um `MIGRATION_CHECKPOINT_vX.Y.md`.

> **FAÇA AGORA**  
> Antes de navegar por chats antigos, crie uma pasta local de migração, por exemplo `ChatGPT_Account_Migration_2026/`, e comece pelo snapshot da Conta A, pelas instruções personalizadas, pela memória e pelos prompts MEM-01 a MEM-LOSS-01.

# Mapa geral da migração

```text
Snapshot da Conta A
        ↓
Memória e inferências
        ↓
Inventário de projetos
        ↓
PROJECT_STATE
        ↓
Classificação de conversas
        ↓
Arquivos
        ↓
Configuração da Conta B
        ↓
Bootstrap
        ↓
Reconstrução de projetos
        ↓
Transferência de chats
        ↓
Validação
        ↓
Coexistência
        ↓
Reconciliação futura com ZIP
```

## Arquitetura de continuidade

```text
Regras estáveis          → Custom Instructions
Contexto recorrente      → Memory + MEMORY_PORTABLE
Como trabalhar           → INTERACTION_MODEL
Regras locais            → Project Instructions
Estado factual           → PROJECT_STATE
Histórico/evidência      → Conversations
Fontes                    → Files / Library
Relações                  → RELATIONSHIP_MAP
Decisões transversais     → GLOBAL_DECISIONS
Erros a não repetir       → NEGATIVE_KNOWLEDGE
Controle da migração      → MIGRATION_MANIFEST
Bootstrap                 → derivado das fontes acima
```

# Checklist mestre

- [ ] Snapshot da Conta A
- [ ] Instruções personalizadas copiadas integralmente
- [ ] Personalidade/estilo e configurações relevantes registradas
- [ ] Configurações de memória registradas
- [ ] Resumo da memória preservado
- [ ] MEM-01 concluído
- [ ] MEM-02 concluído
- [ ] MEM-03 concluído
- [ ] MEM-04 concluído
- [ ] MEM-05 concluído
- [ ] MEM-LOSS-01 concluído
- [ ] `NEGATIVE_KNOWLEDGE.md` criado
- [ ] `INTERACTION_MODEL.md` criado
- [ ] Documentos globais 00–16 criados ou marcados N/A
- [ ] Projetos inventariados e identificados com PRJ-####
- [ ] Projetos P0/P1 auditados
- [ ] `PROJECT_STATE` de cada P0/P1 criado
- [ ] Conversas inventariadas com CONV-####
- [ ] Conversas A/B classificadas
- [ ] Arquivos críticos inventariados com FILE-####
- [ ] Arquivos críticos baixados localmente
- [ ] Library auditada
- [ ] GPTs legados auditados
- [ ] Apps/Plugins inventariados
- [ ] Tarefas/automações inventariadas
- [ ] Conta B configurada
- [ ] Apps necessários reconectados na Conta B
- [ ] Bootstrap executado
- [ ] Projetos P0/P1 reconstruídos
- [ ] Chats classe A migrados
- [ ] Chats classe B selecionados migrados
- [ ] Arquivos críticos validados na Conta B
- [ ] Segunda auditoria de inferências concluída
- [ ] `DO_NOT_MIGRATE.md` aplicado
- [ ] V0–V8 executados nos P0/P1
- [ ] Golden Set executado
- [ ] Lacunas críticas = 0
- [ ] Conflitos críticos = 0
- [ ] Conta B adotada como primary
- [ ] Período de coexistência concluído
- [ ] Migração considerada validada
- [ ] [RECONCILIAR COM ZIP DEPOIS] quando/ se o ZIP chegar

# Rota de emergência — “se meu Plus terminar hoje”

**Urgência:** M0  
**Importância:** P0

A regra é preservar primeiro o que é **difícil de reconstituir semanticamente** e o que possui **limite maior em Plus**. Não comece copiando chats aleatórios.

## Cenário 1 — poucos minutos

1. Copie integralmente as instruções personalizadas para `02_CUSTOM_INSTRUCTIONS.md`.
2. Tire screenshots de Personalização/Memória/Controles de dados/Armazenamento e registre os toggles visíveis.
3. Copie o Resumo da memória, se disponível.
4. Abra um chat novo na Conta A e execute **MEM-LOSS-01**; salve a resposta localmente.
5. Execute **MEM-01** em seguida se houver tempo.
6. Abra a Library e baixe primeiro arquivos que não existem em outra fonte confiável.
7. Registre nomes dos projetos P0 que você não pode se dar ao luxo de esquecer.

> **NÃO FAÇA AINDA**  
> Não gaste esses minutos criando Shared Links para dezenas de conversas. Links e cópias são úteis, mas a extração semântica da Conta A tende a ser mais difícil de reconstruir.

## Cenário 2 — aproximadamente 1 hora

Além do cenário 1:

1. Execute MEM-01, MEM-02, MEM-03 e MEM-LOSS-01.
2. Gere `INTERACTION_MODEL.md` e `NEGATIVE_KNOWLEDGE.md`.
3. Faça um inventário rápido de todos os projetos com nome, prioridade e status.
4. Para cada P0, copie as instruções do projeto e execute PRJ-01.
5. Baixe arquivos P0 únicos da Library/projetos.
6. Registre GPTs existentes, apps/plugins conectados e tarefas ativas.
7. Salve `MIGRATION_CHECKPOINT_v0.1.md`.

## Cenário 3 — algumas horas

1. Complete todas as auditorias MEM.
2. Gere todos os `PROJECT_STATE` dos P0 e dos P1 mais caros de reconstruir.
3. Faça inventário de arquivos e Library.
4. Classifique conversas A dos projetos P0 e crie Migration Capsules.
5. Migre primeiro chats A sem conteúdo sensível via Shared Link, validando cada cópia.
6. Para sensíveis, use transcript privado ou reconstrução com cápsula.
7. Comece a preparar a Conta B com instruções, memória, apps e projetos.

## Cenário 4 — um dia

1. Complete a camada semântica global.
2. Complete `PROJECT_STATE` P0/P1.
3. Recrie os P0 na Conta B.
4. Transfira arquivos canônicos.
5. Transfira conversas A e B selecionadas.
6. Faça CONV-02 após cada migração relevante.
7. Execute a segunda auditoria MEM-06 na Conta A.
8. Rode V0–V6 nos P0.
9. Faça checkpoint antes do fim da sessão.

## Cenário 5 — vários dias

Execute o manual completo, usando checkpoints e buscando `SEMANTIC_SATURATION` antes de decidir que cada conversa histórica precisa ser copiada individualmente.

# Premissas e limitações

1. Conta A e Conta B são contas pessoais distintas.
2. Conta B é o destino operacional e deve permanecer independente da Conta A no fim.
3. O ZIP não está disponível no momento.
4. A interface do ChatGPT é mutável. Qualquer passo de UI deve ser confirmado visualmente.
5. A existência de um recurso no plano Free não implica os mesmos limites ou o mesmo comportamento do Plus.
6. Este manual não presume transferência automática de “memória” entre contas.
7. Shared Link não é mecanismo de backup privado; ele é um mecanismo de compartilhamento e exige classificação de privacidade.
8. Um projeto compartilhado altera o isolamento de memória do projeto. Use-o como ponte apenas deliberadamente.
9. Apps externos exigem autenticação própria na Conta B.
10. A migração não deve transportar inferências erradas só porque elas existem na Conta A.

# Terminologia e classificações

## Urgência

| Classe | Significado |
|---|---|
| M0 | fazer enquanto a Conta A Plus ainda está ativa |
| M1 | fazer antes de abandonar a Conta A |
| M2 | pode ser consolidado depois |

## Importância

| Classe | Significado |
|---|---|
| P0 | crítico |
| P1 | muito importante |
| P2 | relevante |
| P3 | baixo impacto |

## Status de migração

`NÃO_INVENTARIADO → INVENTARIADO → EM_AUDITORIA → PRONTO_PARA_MIGRAÇÃO → MIGRAÇÃO_PARCIAL → MIGRADO → CONTINUABLE → VALIDADO`

## Classes de privacidade

- **NORMAL**: pode ser compartilhado por link se o conteúdo for adequado para exposição a quem possuir o link.
- **SENSITIVE**: contém dados pessoais, profissionais, acadêmicos privados, documentos internos ou informações que não devem circular via link público por posse.
- **HIGHLY_SENSITIVE**: saúde, finanças, credenciais, dados jurídicos delicados, identificadores fortes, segredos, material confidencial de terceiros ou conteúdo cujo vazamento tenha impacto relevante.

# Autoridade documental

Evite duas “verdades” independentes sobre o mesmo fato. Quando houver divergência, corrija a fonte derivada, não crie uma terceira versão paralela.

| Tipo de informação | Fonte canônica recomendada |
|---|---|
| Preferências estáveis | `01_ACCOUNT_PROFILE.md` |
| Regras atuais | `02_CUSTOM_INSTRUCTIONS.md` |
| Memória portátil | `03_MEMORY_PORTABLE.md` |
| Conhecimento negativo | `04_NEGATIVE_KNOWLEDGE.md` |
| Como interagir | `05_INTERACTION_MODEL.md` |
| Índice de projetos | `06_PROJECT_INDEX.md` |
| Relações | `07_RELATIONSHIP_MAP.md` |
| Decisão transversal | `08_GLOBAL_DECISIONS.md` |
| Inferência | `09_INFERENCE_CATALOG.md` |
| Índice de conversas | `10_CONVERSATION_INDEX.md` |
| Índice de arquivos | `11_FILES_INDEX.md` |
| Bootstrap | `12_DESTINATION_BOOTSTRAP.md` — derivado, não fonte primária |
| Validação | `13_VALIDATION_SUITE.md` |
| Estado da migração | `14_MIGRATION_MANIFEST.md` |
| Lacunas/conflitos | `15_GAPS_AND_CONFLICTS.md` |
| Contexto a não migrar | `16_DO_NOT_MIGRATE.md` |
| Estado atual de projeto | `PROJECT_STATE_<projeto>.md` |

\clearpage

# PARTE I — Preservar a Conta A

## Fase 1 — Snapshot da Conta A

**OBJETIVO:** registrar o estado observável da Conta A antes de qualquer mudança.  
**POR QUE ISSO IMPORTA:** configurações, limites e recursos podem mudar após downgrade; screenshots também servem como evidência de como a conta estava configurada.  
**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P0

### Pré-requisitos

- pasta local de migração criada;
- relógio/data do sistema confiáveis;
- Conta A autenticada;
- editor de texto disponível.

### O que abrir

Na Conta A, revise **[VERIFICAR NA INTERFACE ATUAL]**:

- Configurações → Personalização;
- Instruções personalizadas;
- Memória;
- Personalidade/estilo;
- Controles de dados;
- Armazenamento/Library;
- Projects;
- Plugins/Apps;
- Scheduled/Tarefas;
- GPTs existentes, se houver;
- plano/faturamento apenas para registrar o estado, sem expor dados financeiros desnecessários.

### O que fazer na Conta A

1. Copie todo texto que puder ser copiado literalmente.
2. Capture screenshots de opções que não têm exportação textual.
3. Registre o nome exato dos toggles e seus estados.
4. Registre a data e o plano observado.
5. Não altere configurações ainda, especialmente memória e projetos, até terminar o snapshot.

### O que salvar localmente

```text
snapshot/
  2026-10-06_account_settings.md
  2026-10-06_personalization.png
  2026-10-06_memory.png
  2026-10-06_data_controls.png
  2026-10-06_storage.png
  2026-10-06_plugins_apps.png
  2026-10-06_scheduled.png
  2026-10-06_gpts.png
```

### Critério de conclusão

> **CRITÉRIO DE CONCLUSÃO**  
> Você consegue responder, sem abrir a Conta A, quais configurações estavam ativas, quais opções existiam, qual plano estava vigente e onde está a evidência visual/textual correspondente.

### Fallback

> **FALLBACK**  
> Se uma tela não existir, escreva `NÃO ENCONTRADO NA INTERFACE EM 2026-10-06` e faça screenshot da área onde esperava encontrá-la. Não substitua ausência por suposição.

## Fase 2 — Instruções personalizadas e preferências

**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P0

### O que fazer

1. Copie as instruções personalizadas **integralmente**.
2. Salve uma cópia literal em `02_CUSTOM_INSTRUCTIONS_RAW.md`.
3. Crie uma versão limpa em `02_CUSTOM_INSTRUCTIONS.md`, mas não elimine a RAW.
4. Registre personalidade/estilo selecionado e outras preferências visíveis.
5. Se o texto atual exceder 1.500 caracteres, marque no Manifest: `RISCO_DOWNGRADE_CUSTOM_INSTRUCTIONS = SIM`.

> **ATENÇÃO**  
> A documentação atual informa limites diferentes entre Plus e Free/Go. Preserve a versão integral antes do downgrade. Não faça “otimização” destrutiva agora; compactação pode ser feita depois usando a RAW como fonte.

## Fase 3 — Configurações de memória

**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P0

Registre em `03_MEMORY_PORTABLE.md`:

```text
MEMORY_ENABLED:
REFERENCE_SAVED_MEMORIES: [se exibido]
REFERENCE_CHAT_HISTORY: [se exibido]
MEMORY_SUMMARY_AVAILABLE:
PROJECT_MEMORY_OPTIONS:
OTHER_MEMORY_CONTROLS:
DATE:
EVIDENCE_SCREENSHOT:
NOTES:
```

### Procedimento

1. Abra Configurações → Personalização → Memória **[VERIFICAR NA INTERFACE ATUAL]**.
2. Copie integralmente o **Resumo da memória** se disponível.
3. Se houver visualização de memória salva, histórico, prioridades ou versões, registre o que estiver visível.
4. Não trate o resumo como exportação completa. Ele é uma visão condensada.
5. Antes de desligar qualquer opção de memória, termine as auditorias MEM abaixo.

> **NÃO FAÇA AINDA**  
> Não desative `Reference chat history` antes das auditorias. A documentação atual informa que desligá-lo pode iniciar exclusão de informações derivadas do histórico em até 30 dias, embora os chats originais permaneçam.

## Fase 4 — Auditorias de contexto da Conta A

**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P0

Execute cada prompt em um chat novo da Conta A. Não use apenas um prompt gigantesco: auditorias independentes reduzem omissões e permitem comparar resultados.

### MEM-01 — Perfil e preferências

```text
ID: MEM-01
OBJETIVO: produzir uma auditoria portátil do meu perfil de uso e preferências relevantes para continuidade entre contas.

Use somente contexto que você realmente consiga recuperar desta Conta A. Não invente detalhes. Não faça psicologização irrelevante. Quando houver dúvida, marque-a explicitamente.

Recupere e organize, quando houver evidência:
- preferências de resposta e estilo;
- profundidade e nível técnico esperados;
- idiomas e registros de linguagem;
- ambientes computacionais e sistemas operacionais relevantes;
- ferramentas e softwares recorrentes;
- padrões de documentação;
- convenções de Markdown, LaTeX e código;
- Git, GitHub, branches, commits e versionamento;
- uso de fontes, citações e critérios de evidência;
- critérios de qualidade e validação;
- padrões recorrentes de trabalho com o ChatGPT;
- preferências de organização de projetos e artefatos;
- correções recorrentes que eu faço ao ChatGPT;
- exceções importantes às preferências gerais.

Para CADA item use exatamente uma destas classificações:
[EXPLÍCITO]
[INFERIDO — ALTA CONFIANÇA]
[INFERIDO — MÉDIA CONFIANÇA]
[INFERIDO — BAIXA CONFIANÇA]
[POSSIVELMENTE DESATUALIZADO]
[CONFLITO]
[NÃO RECUPERADO]

Para itens inferidos, acrescente:
- evidência resumida;
- confiança;
- consequência prática se a Conta B usar essa informação.

Separe "preferência estável" de "preferência contextual". Não trate uma escolha feita em um projeto específico como regra global sem evidência.

Ao final, gere:
1. PROFILE_SUMMARY — síntese operacional curta;
2. PREFERENCES_CATALOG — catálogo detalhado;
3. UNCERTAINTIES — itens que precisam de validação humana;
4. CANDIDATES_FOR_ACCOUNT_PROFILE — itens adequados para 01_ACCOUNT_PROFILE.md;
5. CANDIDATES_FOR_CUSTOM_INSTRUCTIONS — regras adequadas para 02_CUSTOM_INSTRUCTIONS.md;
6. DO_NOT_OVERGENERALIZE — itens que não devem ser generalizados.
```

**Resultado esperado:** matéria-prima para `01_ACCOUNT_PROFILE.md`, `02_CUSTOM_INSTRUCTIONS.md` e `05_INTERACTION_MODEL.md`.

### MEM-02 — Projetos, relações e decisões

```text
ID: MEM-02
OBJETIVO: recuperar o mapa de projetos, relações, decisões e dependências que esta Conta A consegue reconstruir a partir de memória, histórico e contexto disponível.

Não invente projetos. Diferencie explicitamente fatos, inferências e lacunas.

Para cada projeto ativo, pausado ou historicamente relevante, recupere quando possível:
- nome e identidade;
- objetivo;
- status atual;
- escopo;
- pessoas relevantes e seus papéis, apenas quando operacionalmente necessários;
- arquivos e artefatos associados;
- softwares, ferramentas e ambientes;
- decisões importantes;
- justificativas das decisões;
- alternativas rejeitadas;
- dependências internas e externas;
- versões e status de canonicidade;
- próximas ações;
- riscos de perda de contexto;
- relações com outros projetos;
- relações derivadas de múltiplas conversas que não aparecem em um único chat.

Use em cada afirmação uma marca:
[CONFIRMADO]
[INFERIDO — ALTA CONFIANÇA]
[INFERIDO — MÉDIA CONFIANÇA]
[INFERIDO — BAIXA CONFIANÇA]
[CONFLITO]
[DESATUALIZADO?]
[NÃO RECUPERADO]

Depois produza:
1. PROJECT_CATALOG;
2. CROSS_PROJECT_RELATIONSHIPS;
3. GLOBAL_DECISIONS_CANDIDATES;
4. PROJECTS_NEEDING_IMMEDIATE_AUDIT;
5. HIDDEN_DEPENDENCIES;
6. QUESTIONS_FOR_HUMAN_VALIDATION.

Não transforme associação plausível em fato. Se uma relação parecer provável mas não estiver confirmada, mantenha-a como inferência.
```

### MEM-03 — Conhecimento negativo

```text
ID: MEM-03
OBJETIVO: extrair conhecimento negativo — aquilo que a Conta B precisa saber para não repetir erros, interpretações, versões ou abordagens já corrigidas.

Procure, quando houver evidência:
- interpretações que eu corrigi;
- hipóteses rejeitadas;
- abordagens testadas e abandonadas;
- termos ou nomes incorretos que já foram corrigidos;
- associações falsas;
- versões recentes que NÃO são canônicas;
- pressupostos que não devem ser feitos;
- exceções às minhas preferências gerais;
- erros recorrentes do ChatGPT ao trabalhar comigo;
- soluções tentadas e descartadas;
- decisões que parecem naturais mas foram deliberadamente recusadas;
- informações que devem permanecer históricas, sem continuar personalizando respostas.

Para cada item registre:
ID provisório;
STATUS: CONFIRMADO | INFERIDO | CONFLITO;
ERRO_A_EVITAR;
CORREÇÃO;
EVIDÊNCIA_RESUMIDA;
ESCOPO: global | projeto específico;
CONSEQUÊNCIA_SE_IGNORADO;
FONTE_CANÔNICA_SUGERIDA.

Ao final gere conteúdo pronto para 04_NEGATIVE_KNOWLEDGE.md e uma seção separada chamada DO_NOT_MIGRATE_CANDIDATES.

Não crie conhecimento negativo por dedução livre. Prefira omitir a inventar.
```

### MEM-04 — Temporalidade e obsolescência

```text
ID: MEM-04
OBJETIVO: separar contexto atual, histórico, substituído e conflitante antes da migração.

Procure:
- preferências antigas;
- decisões substituídas;
- projetos encerrados;
- informações desatualizadas;
- versões superseded;
- conflitos entre antigo e atual;
- inferências que perderam validade;
- mudanças de nomenclatura;
- mudanças de ferramenta, ambiente ou workflow.

Classifique cada item como uma destas categorias:
ATUAL
HISTÓRICO
SUPERSEDED
CONFLITO
INCERTO

Para cada item informe:
- assunto;
- classificação;
- estado antigo;
- estado atual, se conhecido;
- data aproximada da mudança, se recuperável;
- evidência resumida;
- impacto de migrar incorretamente o estado antigo;
- documento em que o estado atual deve ficar canônico.

Ao final produza:
1. CURRENT_STATE_CANDIDATES;
2. SUPERSEDED_REGISTER;
3. CONFLICTS_TO_RESOLVE;
4. DO_NOT_MIGRATE_CANDIDATES.
```

### MEM-05 — Inferências transversais

```text
ID: MEM-05
OBJETIVO: procurar relações e padrões que só aparecem ao combinar várias conversas, projetos, arquivos e correções desta Conta A.

Não faça perfil psicológico. Foque em informação operacional e epistemicamente útil.

Procure:
- padrões de trabalho recorrentes;
- dependências entre projetos;
- relações entre pessoas, arquivos, ferramentas e conversas;
- exceções contextuais;
- métodos recorrentes de análise;
- critérios de decisão;
- práticas de verificação;
- preferências condicionais do tipo "quando X, prefiro Y";
- contextos em que uma regra geral não se aplica;
- conceitos ou terminologia que conectam projetos;
- informações que a Conta A usa espontaneamente e que não parecem estar num único documento.

Para cada inferência inclua:
INFERENCE_ID;
DECLARAÇÃO;
CONFIANÇA: alta | média | baixa;
EVIDÊNCIA_RESUMIDA;
ESCOPO;
RISCO_DE_FALSO_POSITIVO;
CONSEQUÊNCIA_PRÁTICA;
DEVE_SER_MIGRADA?: sim | não | validar;
DESTINO_SUGERIDO: 09_INFERENCE_CATALOG.md | 07_RELATIONSHIP_MAP.md | PROJECT_STATE | outro.

Ao final, liste as 10 inferências transversais mais valiosas para continuidade e as 10 mais incertas que NÃO devem ser incorporadas como fatos.
```

### MEM-LOSS-01 — Loss Audit adversarial

```text
ID: MEM-LOSS-01
OBJETIVO: responder adversarialmente à pergunta: "Se esta conta desaparecesse agora, que contexto útil ainda não está adequadamente representado nos documentos de migração?"

Considere que eu já posso ter criado documentos de perfil, memória, projetos, decisões, relações, conversas e arquivos. Sua tarefa é procurar o que AINDA FALTA, não repetir o que já está bem representado.

Busque especificamente:
- relações implícitas;
- conhecimento não documentado;
- dependências ocultas;
- preferências contextuais;
- exceções;
- decisões sem justificativa registrada;
- arquivos esquecidos;
- inferências ainda não documentadas;
- conhecimento negativo ausente;
- contexto que esta Conta A usa espontaneamente, mas que ainda não foi explicitado;
- informações cuja perda obrigaria o usuário a reexplicar muito trabalho;
- detalhes que parecem pequenos, mas alteram decisões futuras;
- estados de projeto que não estão em nenhum PROJECT_STATE;
- conversas que funcionam como fonte primária de uma decisão.

Não invente lacunas apenas para preencher a lista. Para cada lacuna real, forneça:
LOSS_ID;
O_QUE_FALTA;
POR_QUE_IMPORTA;
ONDE_PROCURAR;
COMO_PRESERVAR_AGORA;
URGÊNCIA: M0 | M1 | M2;
IMPORTÂNCIA: P0 | P1 | P2 | P3;
CONFIANÇA;
CRITÉRIO_DE_RESOLUÇÃO.

Finalize com:
1. TOP_10_LOSS_RISKS;
2. M0_OPEN_ITEMS;
3. ITENS_QUE_DEPENDEM_DA_CONTA_A;
4. ITENS_QUE_PODEM_ESPERAR;
5. PRÓXIMA_AÇÃO_RECOMENDADA.
```

## Fase 5 — Consolidar documentos globais

**URGÊNCIA:** M0/M1  
**IMPORTÂNCIA:** P0

Crie os documentos abaixo. Eles são portáteis e devem permanecer localmente, mesmo que também sejam carregados na Conta B.

| Arquivo | Finalidade | Fonte de verdade | Momento |
|---|---|---|---|
| `00_MIGRATION_README.md` | índice e instruções da pasta | Manifest + estrutura real | início; atualizar sempre |
| `01_ACCOUNT_PROFILE.md` | perfil operacional estável | explícito + MEM-01 validado | M0 |
| `02_CUSTOM_INSTRUCTIONS.md` | regras atuais | cópia literal + revisão | M0 |
| `03_MEMORY_PORTABLE.md` | memória/contexto portável | resumo + auditorias | M0 |
| `04_NEGATIVE_KNOWLEDGE.md` | erros a não repetir | MEM-03 + projetos | M0 |
| `05_INTERACTION_MODEL.md` | como trabalhar | MEM-01/05 + evidência | M0/M1 |
| `06_PROJECT_INDEX.md` | catálogo de projetos | inventário manual | M1 |
| `07_RELATIONSHIP_MAP.md` | relações transversais | MEM-02/05 | M1 |
| `08_GLOBAL_DECISIONS.md` | decisões transversais | evidência primária | M1 |
| `09_INFERENCE_CATALOG.md` | inferências qualificadas | MEM-01/05 | M1 |
| `10_CONVERSATION_INDEX.md` | inventário de chats | navegação manual | M1 |
| `11_FILES_INDEX.md` | inventário de arquivos | Library/projetos/chats | M0/M1 |
| `12_DESTINATION_BOOTSTRAP.md` | pacote derivado para B | documentos canônicos | M1 |
| `13_VALIDATION_SUITE.md` | testes | Golden Set + VAL | M1/M2 |
| `14_MIGRATION_MANIFEST.md` | controle de estado | operação atual | desde o início |
| `15_GAPS_AND_CONFLICTS.md` | lacunas e divergências | auditorias/validação | sempre |
| `16_DO_NOT_MIGRATE.md` | conteúdo a não perpetuar | MEM-03/04 + revisão | antes do bootstrap |

### Regra de não duplicação

`12_DESTINATION_BOOTSTRAP.md` é uma **visão derivada**. Se ele divergir de `PROJECT_STATE`, `ACCOUNT_PROFILE` ou `NEGATIVE_KNOWLEDGE`, corrija o bootstrap; não altere a fonte canônica para fazê-la coincidir com o bootstrap.

## Fase 6 — Criar `INTERACTION_MODEL.md`

**URGÊNCIA:** M0/M1  
**IMPORTÂNCIA:** P0

Estrutura recomendada:

```markdown
# INTERACTION_MODEL

## Evidência e escopo
- Somente regras sustentadas por evidência.
- Não transformar preferência contextual em regra universal.

## Forma de resposta
- tom;
- profundidade;
- estrutura;
- idiomas;
- quando ser conciso vs detalhado.

## Rigor epistemológico
- como separar fato, hipótese, inferência e opinião;
- como declarar incerteza;
- quando verificar fontes;
- quando questionar premissas.

## Artefatos
- quando Markdown é suficiente;
- quando LaTeX/PDF é preferível;
- versionamento;
- nomes de arquivos;
- critérios de canonicidade.

## Projetos
- como organizar estado;
- como manter PROJECT_STATE;
- como registrar decisões e alternativas rejeitadas.

## Tarefas científicas
- modelo mínimo;
- hipóteses;
- ordem de grandeza;
- fontes;
- validação.

## Tarefas computacionais
- ambiente;
- Git;
- testes;
- riscos;
- rollback.

## Simplificações a evitar
- ...

## Regras condicionais
- Quando X, fazer Y.
```

> **CRITÉRIO DE CONCLUSÃO**  
> Uma nova conta, lendo apenas `ACCOUNT_PROFILE`, `CUSTOM_INSTRUCTIONS`, `MEMORY_PORTABLE`, `NEGATIVE_KNOWLEDGE` e `INTERACTION_MODEL`, consegue reproduzir de forma razoável o estilo de colaboração sem fingir que conhece fatos que não foram preservados.


\clearpage

# PARTE II — Inventariar o que precisa atravessar

## Fase 7 — Inventário manual dos projetos

**OBJETIVO:** construir um catálogo completo dos projetos visíveis na Conta A.  
**POR QUE ISSO IMPORTA:** projetos concentram instruções, arquivos, chats e contexto local; perder o contêiner pode destruir relações mesmo quando os itens isolados sobrevivem.  
**URGÊNCIA:** M0 para identificação; M1 para detalhamento.  
**IMPORTÂNCIA:** P0.

### Procedimento

1. Percorra visualmente a barra lateral e a área de Projects.
2. Não filtre apenas por “ativo”. Inclua projetos pausados e históricos com alto custo de reconstrução.
3. Atribua IDs sequenciais sem significado semântico: `PRJ-0001`, `PRJ-0002`, ...
4. Registre em `06_PROJECT_INDEX.md`.
5. Faça screenshot da lista para ter evidência de cobertura.
6. Marque projetos que possuam muitos arquivos, instruções longas, memória de projeto ou chats difíceis de reproduzir.

### Schema mínimo

```text
PROJECT_ID:
NOME:
OBJETIVO:
STATUS:
ATIVO?:
DATA_APROXIMADA:
INSTRUÇÕES:
ARQUIVOS:
CONVERSAS_PRINCIPAIS:
DEPENDÊNCIAS:
RELAÇÕES:
IMPORTÂNCIA_PROJETO: P0 | P1 | P2 | P3 | P4
CUSTO_DE_RECONSTRUÇÃO: alto | médio | baixo
MEMÓRIA_DO_PROJETO: padrão | somente_do_projeto | desconhecido
PRECISA_SER_RECRIADO?: sim | não | talvez
EVIDÊNCIA:
OBSERVAÇÕES:
```

### Classificação objetiva de projetos

| Classe | Critério recomendado |
|---|---|
| P0 — crítico | trabalho ativo, alto custo de reconstrução, decisões/arquivos únicos, dependências atuais |
| P1 — importante | útil e recorrente, mas reconstruível com custo moderado |
| P2 — relevante | valor contextual/histórico, pouca urgência |
| P3 — histórico | registro útil, não necessário para operação imediata |
| P4 — dispensável operacionalmente | baixo valor, duplicado, teste ou descartado |

Use três perguntas para evitar classificação emocional:

1. Se desaparecer hoje, **quanto tempo intelectual** preciso gastar para reconstruir?
2. A perda muda decisões, resultados, versões ou próximos passos?
3. Existe fonte primária equivalente fora do ChatGPT?

## PRJ-01 — Auditoria de projeto P0/P1

Execute dentro de cada projeto P0/P1, preferencialmente em um chat novo do próprio projeto.

```text
ID: PRJ-01
OBJETIVO: produzir PROJECT_STATE deste projeto para permitir continuidade em outra conta sem depender de memória implícita.

Use apenas o contexto que este projeto realmente oferece: instruções do projeto, chats acessíveis, arquivos, memória/contexto disponível e informações explicitamente recuperáveis. Não invente lacunas.

Produza um documento chamado PROJECT_STATE_<nome_curto>.md com as seções abaixo:

1. IDENTIDADE
- nome do projeto;
- propósito;
- escopo;
- status;
- prioridade sugerida P0/P1/P2/P3/P4.

2. CONTEXTO E OBJETIVO
- problema que o projeto resolve;
- resultado esperado;
- restrições relevantes.

3. ESTADO ATUAL
- o que já está concluído;
- o que está em andamento;
- o que ainda não começou;
- última posição operacional conhecida.

4. HISTÓRICO ÚTIL
- somente acontecimentos que explicam o estado atual;
- não fazer resumo cronológico indiscriminado.

5. ENTREGÁVEIS E ARTEFATOS
Para cada artefato:
- nome;
- versão;
- papel;
- canonicidade;
- arquivo/fonte de origem;
- conversa relacionada.

6. VERSÕES E CANONICIDADE
Use:
CANÔNICO
CANDIDATO_A_CANÔNICO
ATUAL
HISTÓRICO
AUXILIAR
OBSOLETO
DESCARTADO

Lembre que "mais recente" não significa "canônico".

7. DECISÕES
Para cada decisão:
- decisão;
- justificativa;
- evidência;
- alternativas rejeitadas;
- impacto;
- ainda válida?

8. HIPÓTESES ABERTAS E INCERTEZAS
- hipótese;
- evidência;
- como testar/confirmar.

9. TERMINOLOGIA E CORREÇÕES
- termos definidos;
- nomes corretos;
- ambiguidades resolvidas.

10. CONHECIMENTO NEGATIVO
- o que não assumir;
- abordagens rejeitadas;
- versões não canônicas;
- erros recorrentes;
- exceções.

11. DEPENDÊNCIAS E RELAÇÕES
- pessoas;
- ferramentas;
- arquivos;
- outros projetos;
- serviços externos;
- decisões transversais.

12. CONVERSAS IMPORTANTES
- título/data aproximada;
- função;
- se deve ser migrada nativamente ou consolidada.

13. PRÓXIMAS AÇÕES
Ordene por dependência e prioridade. Para cada ação, diga qual contexto/arquivo é necessário.

14. RISCOS DE PERDA DE CONTEXTO
- o que existe implicitamente;
- o que depende da Conta A;
- o que ainda precisa ser preservado.

Em toda afirmação material, use quando necessário:
[CONFIRMADO]
[INFERIDO]
[CONFLITO]
[DESATUALIZADO?]
[NÃO RECUPERADO]

Ao final gere também:
- MIGRATION_MINIMUM: conjunto mínimo para o projeto ser CONTINUABLE na Conta B;
- FILES_TO_TRANSFER;
- CONVERSATIONS_TO_TRANSFER;
- OPEN_GAPS;
- VALIDATION_QUESTIONS: 5–10 perguntas para testar a Conta B depois.
```

> **CRITÉRIO DE CONCLUSÃO**  
> Um projeto P0/P1 só está “pronto para migração” quando existe um `PROJECT_STATE` revisado e o conjunto mínimo `MIGRATION_MINIMUM` está explícito.

## Fase 8 — Inventário manual das conversas

**URGÊNCIA:** M1; chats cuja semântica depende fortemente da Conta A podem virar M0.  
**IMPORTÂNCIA:** P0/P1.

### Procedimento eficiente sem ZIP

1. Percorra primeiro conversas dentro de cada projeto.
2. Depois percorra conversas fora de projetos.
3. Use busca por chat quando disponível para localizar termos, entregáveis e nomes de projetos.
4. Registre título exatamente como aparece e data aproximada.
5. Associe a um `PROJECT_ID` ou `GLOBAL`.
6. Marque chats que geraram arquivos, decisões, correções, versões ou branches relevantes.
7. Não assuma que títulos iguais são duplicatas; confira função/contexto.
8. Não leia integralmente cada conversa na primeira passagem. Faça triagem e volte apenas às A/B.

### Schema

```text
CONV_ID:
TÍTULO:
DATA_APROXIMADA:
PROJECT_ID:
CLASSE: A | B | C | D | E
PRIVACIDADE: NORMAL | SENSITIVE | HIGHLY_SENSITIVE
VALOR_FACTUAL: 0-3
VALOR_OPERACIONAL: 0-3
VALOR_INFERENCIAL: 0-3
VALOR_HISTÓRICO: 0-3
DEPENDÊNCIA_DA_SEQUÊNCIA: 0-3
CUSTO_DE_RECONSTRUÇÃO: 0-3
GEROU_ARQUIVO?:
CONTÉM_DECISÃO?:
CONTÉM_CORREÇÃO?:
BRANCH_RELEVANTE?:
CONTEXTO_EXTERNO?:
MÉTODO_SUGERIDO:
STATUS_MIGRAÇÃO:
NOTAS:
```

### Classes de conversa

- **A — MIGRAR NATIVAMENTE:** sequência, decisões, contexto ou continuidade tornam o histórico importante.
- **B — MIGRAÇÃO NATIVA DESEJÁVEL:** a cópia integral ajuda, mas existe fallback consolidado.
- **C — CONSOLIDAR + PRESERVAR:** conteúdo útil, porém a sequência completa não agrega valor suficiente.
- **D — BAIXA PRIORIDADE:** histórico consultável; migração pode esperar.
- **E — DISPENSÁVEL OPERACIONALMENTE:** teste, duplicata, conversa sem valor futuro ou contexto explicitamente descartado.

### Heurística de pontuação

Some os seis eixos `valor_factual + valor_operacional + valor_inferencial + valor_historico + dependencia_da_sequencia + custo_de_reconstrucao` (0–18). Use apenas como apoio:

- 14–18: candidato forte a A;
- 10–13: A/B;
- 6–9: B/C;
- 3–5: C/D;
- 0–2: D/E.

A pontuação não substitui julgamento. Um chat curto pode conter a decisão crítica de um projeto inteiro.

## Árvore de decisão — devo migrar este chat?

```text
Quero preservar este chat
        │
        ├─ É fonte primária de decisão/correção/estado?
        │      ├─ sim → A ou B
        │      └─ não
        │
        ├─ A sequência de mensagens é necessária para entender o resultado?
        │      ├─ sim → preferir migração nativa
        │      └─ não → consolidar pode bastar
        │
        ├─ Ele contém contexto implícito que A usa e B perderia?
        │      ├─ sim → gerar Migration Capsule; A/B
        │      └─ não
        │
        ├─ Existem anexos/arquivos únicos?
        │      ├─ sim → preservar arquivos separadamente; A/B/C
        │      └─ não
        │
        ├─ É duplicado ou superseded?
        │      ├─ sim → C/D/E + DO_NOT_MIGRATE se necessário
        │      └─ não
        │
        └─ O custo de reconstrução é baixo?
               ├─ sim → C/D
               └─ não → B
```

## Fase 9 — Classificação de privacidade

**URGÊNCIA:** antes de qualquer Shared Link.  
**IMPORTÂNCIA:** P0.

### NORMAL

Use Shared Link se o conteúdo puder ser visto por qualquer pessoa que obtenha o link. Mesmo links “anônimos” não são privados no sentido de acesso autenticado restrito por padrão em conta pessoal.

### SENSITIVE

Prefira transcript privado, arquivo local ou reconstrução por cápsula. Se um Shared Link for usado excepcionalmente, revise toda a prévia, minimize dados e remova o link após a cópia; isso reduz exposição futura, mas não apaga cópias já feitas.

### HIGHLY_SENSITIVE

Não use Shared Link. Mova apenas o mínimo necessário e preferencialmente por arquivos locais privados ou reconstrução controlada. Remova credenciais, tokens, segredos e dados de terceiros quando não forem necessários para continuidade.

## CONV-01 — Migration Capsule

Crie a cápsula **antes** de gerar o Shared Link final, transcript ou cópia.

```text
ID: CONV-01
OBJETIVO: produzir uma Migration Capsule fiel desta conversa para que outra conta consiga interpretar e continuar o trabalho mesmo se a sequência completa ou a memória implícita não forem preservadas.

Não resuma genericamente. Extraia o estado operacional e diferencie fato, decisão, inferência, hipótese e lacuna.

Produza as seções:

1. IDENTIDADE DA CONVERSA
- título;
- projeto relacionado;
- objetivo original;
- data aproximada, se recuperável.

2. CONTEXTO NECESSÁRIO
- apenas o contexto necessário para entender o trabalho;
- contexto externo à conversa;
- memórias/inferências relevantes que parecem ter sido usadas.

3. ESTADO ATUAL
- último resultado válido;
- o que está concluído;
- o que está pendente;
- próxima ação concreta.

4. DECISÕES
Para cada decisão: decisão, justificativa, evidência, alternativas rejeitadas, validade atual.

5. CORREÇÕES E CONHECIMENTO NEGATIVO
- interpretações corrigidas;
- termos corrigidos;
- abordagens rejeitadas;
- pressupostos proibidos;
- versões que não devem ser tratadas como canônicas.

6. ARQUIVOS E ARTEFATOS
- nome;
- papel;
- versão;
- canonicidade;
- origem;
- se precisa ser reanexado na Conta B.

7. VERSÕES
- mapa de versões;
- qual é atual;
- qual é canônica;
- ambiguidades.

8. QUESTÕES ABERTAS
- pergunta;
- evidência disponível;
- próximo passo para resolver.

9. RELAÇÕES
- projeto;
- pessoas, apenas se relevantes;
- outros chats;
- ferramentas;
- arquivos;
- decisões globais.

10. PREMISSAS IMPLÍCITAS
Liste apenas as que têm evidência razoável e marque [INFERIDO] quando necessário.

11. RISCOS DE INTERPRETAÇÃO
- erros que uma nova conta provavelmente cometeria ao ler apenas o transcript;
- detalhes que devem ser lidos no PROJECT_STATE/NEGATIVE_KNOWLEDGE.

12. PACOTE DE CONTINUIDADE
- MINIMUM_CONTEXT;
- FILES_REQUIRED;
- NEXT_ACTION;
- VALIDATION_QUESTIONS (3–7).

Não invente memórias nem preencha lacunas por plausibilidade. Use [NÃO RECUPERADO] quando necessário.
```

## Fase 10 — Inventário manual de arquivos

**URGÊNCIA:** M0 para arquivos únicos e Library acima dos limites de Free; M1 para o restante.  
**IMPORTÂNCIA:** P0/P1.

Identifique arquivos em:

- Library;
- fontes de Projects;
- anexos de chats;
- outputs gerados pelo ChatGPT;
- downloads locais relacionados aos projetos;
- GPT knowledge files existentes;
- imagens/screenshots que servem como evidência.

### IDs e schema

```text
FILE_ID: FILE-0001
NOME:
TIPO:
PROJECT_ID:
ORIGEM: Library | Project | Chat | GPT | local | app
VERSÃO:
CANONICIDADE:
DEPENDÊNCIAS:
CONVERSAS_RELACIONADAS:
FONTE_PRIMÁRIA?: sim | não
EXISTE_FORA_DA_CONTA_A?: sim | não | desconhecido
TRANSFERIDO?:
VALIDADO?:
HASH_LOCAL: [opcional]
NOTAS:
```

### Status de canonicidade

```text
CANÔNICO
CANDIDATO_A_CANÔNICO
ATUAL
HISTÓRICO
AUXILIAR
OBSOLETO
DESCARTADO
```

> **ATENÇÃO**  
> `mais recente ≠ necessariamente canônico`. Canonicidade vem de decisão/evidência, não do timestamp do arquivo.

### Grafo de dependências

Crie `ARTIFACT_GRAPH.md` quando o projeto tiver pipeline de artefatos. Exemplos:

```text
PDF fonte
→ transcrição confirmada
→ LaTeX editável
→ PDF final
```

```text
dataset bruto
→ script de limpeza
→ dataset processado
→ script de análise
→ gráfico
→ relatório
```

A pergunta operacional é: **quais nós precisam atravessar para que o resultado possa ser reproduzido, auditado ou continuado?**

## Árvore de decisão — este arquivo precisa ser transferido?

```text
Arquivo identificado
    │
    ├─ É fonte primária única? ─ sim → transferir P0
    │
    ├─ É canônico/necessário para continuar? ─ sim → transferir P0/P1
    │
    ├─ Pode ser reproduzido exatamente a partir de fontes já preservadas?
    │      ├─ não → transferir
    │      └─ sim → pode ser M2, mas preserve receita/dependências
    │
    ├─ É obsoleto/descartado?
    │      ├─ sim → não carregar em B; manter arquivo histórico local se útil
    │      └─ não
    │
    └─ É grande e facilmente obtido de fonte externa confiável?
           ├─ sim → registre URL/fonte/checksum; download local opcional
           └─ não → transferir
```

## Fase 11 — GPTs personalizados legados

**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P1 ou P0 se algum workflow depender deles.

A documentação oficial atual informa que **novos GPTs não podem ser criados/publicados em contas pessoais** e que GPTs existentes estão em processo de substituição por Plugins. Portanto, para duas contas pessoais, não assuma que a Conta B conseguirá “recriar o GPT” literalmente.

### Inventarie cada GPT existente na Conta A

```text
GPT_ID_LOCAL:
NOME:
DESCRIÇÃO:
INSTRUÇÕES:
CONVERSATION_STARTERS:
KNOWLEDGE_FILES:
CAPACIDADES:
APPS/ACTIONS:
FUNÇÃO:
PROJETOS_DEPENDENTES:
EDITÁVEL_NA_CONTA_A?:
MIGRAÇÃO_PARA_PLUGIN_DISPONÍVEL?: [VERIFICAR NA INTERFACE ATUAL]
```

### Procedimento recomendado

1. Se o GPT ainda for editável, copie toda configuração textual e faça screenshots.
2. Baixe knowledge files que não existam em outro repositório.
3. Registre capacidades/actions/apps.
4. **[VERIFICAR NA INTERFACE ATUAL]** procure opção oficial de migração GPT → Plugin.
5. Se houver migração, faça uma cópia/teste antes de abandonar o GPT.
6. Se não houver, preserve um pacote portátil `GPT_<nome>_PORTABLE.md` contendo instruções, knowledge manifest e dependências.
7. Na Conta B, implemente o comportamento por Plugin quando disponível, ou por Project + instructions + files como fallback.

> **FALLBACK**  
> Um Project bem configurado com instruções e arquivos pode preservar grande parte do comportamento intelectual de um GPT, mas não necessariamente Actions, permissões, integrações ou UI específica.

## Fase 12 — Apps, Plugins e conectores

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P1.

A partir de 2026, o diretório de Plugins é a principal superfície de descoberta para workflows que podem incluir apps conectados. Trate “app”, “connector” e “plugin” como objetos relacionados, mas registre exatamente o que a interface mostra.

### Inventário

```text
PLUGIN/APP:
CONTA_EXTERNA:
FUNÇÃO:
PROJETOS_DEPENDENTES:
PERMISSÕES_RELEVANTES:
USA_DADOS_EXTERNOS_COMO_CONTEXT?:
PRECISA_REAUTENTICAR_EM_B?: sim
STATUS_EM_B:
TESTE_DE_CONEXÃO:
```

### Checklist de reconexão

- [ ] Gmail
- [ ] Google Drive
- [ ] Google Calendar
- [ ] GitHub
- [ ] Outros plugins/apps observados
- [ ] Permissões revisadas
- [ ] Conta externa correta confirmada
- [ ] Um teste de leitura/ação não destrutiva executado
- [ ] Projetos dependentes revalidados

> **ATENÇÃO**  
> Nunca copie tokens, cookies, senhas ou segredos de uma conta para outra. Reconecte pelo fluxo oficial de autenticação.

## Fase 13 — Library

**URGÊNCIA:** M0  
**IMPORTÂNCIA:** P0/P1.

A documentação atual informa 20 GB para Plus e 500 MB para Free. Isso torna a auditoria de Library um dos melhores usos do tempo restante no Plus, embora a documentação consultada não diga que arquivos excedentes serão apagados após downgrade.

### Procedimento

1. Abra Library **[VERIFICAR NA INTERFACE ATUAL]**.
2. Ordene/filtre por data e projeto quando possível.
3. Priorize arquivos únicos, canônicos e fontes primárias.
4. Baixe uma cópia local.
5. Registre no `11_FILES_INDEX.md`.
6. Associe cada arquivo a `PROJECT_ID` e, quando possível, `CONV_ID`.
7. Não presuma que um arquivo visível em um chat migrado aparecerá automaticamente na Library da Conta B.

## Fase 14 — Automações e tarefas

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P1.

### Inventário mínimo

```text
TASK_ID_LOCAL:
TÍTULO:
PROMPT/INSTRUÇÕES:
HORÁRIO:
FREQUÊNCIA:
FUSO:
CONDIÇÃO/GATILHO:
APPS:
DEPENDÊNCIAS:
ATIVA?:
ÚLTIMA_EXECUÇÃO_RELEVANTE:
```

### Método preferido quando disponível

A documentação atual permite compartilhar tarefas agendadas elegíveis. O link inclui título, instruções, agenda e fuso; a Conta B autenticada pode agendar uma cópia própria, sujeita às próprias permissões e apps.

1. Na Conta A, revise a tarefa e qualquer dado sensível.
2. Compartilhe **[VERIFICAR NA INTERFACE ATUAL]**.
3. Na Conta B, abra o link autenticado.
4. Confira prompt, agenda e fuso.
5. Conecte apps necessários na Conta B.
6. Agende a cópia.
7. Compare a tarefa B com o inventário local.
8. Faça um teste seguro.
9. Remova o link de compartilhamento se não for mais necessário.

### Fallback

Recrie manualmente usando o registro local. Não migre apenas o título: preserve a instrução completa, condição, agenda, fuso e dependências.

## Fase 15 — Manifest e checkpoints

Crie `14_MIGRATION_MANIFEST.md` no início e mantenha-o vivo.

### Template do Manifest

```markdown
# MIGRATION_MANIFEST

## Metadados
- MIGRATION_ID: MIG-2026-10-A-B
- SOURCE: Conta A
- DESTINATION: Conta B
- ZIP_AVAILABLE: NÃO
- START_DATE:
- LAST_UPDATE:

## Estados permitidos
NÃO_INVENTARIADO
INVENTARIADO
EM_AUDITORIA
PRONTO_PARA_MIGRAÇÃO
MIGRAÇÃO_PARCIAL
MIGRADO
CONTINUABLE
VALIDADO

## Itens
| ID | Tipo | Nome | Urgência | Importância | Privacidade | Estado | Evidência | Lacuna | Próxima ação |
|---|---|---|---|---|---|---|---|---|---|

## M0 abertos
- ...

## Lacunas críticas
- ...

## Conflitos críticos
- ...

## Último checkpoint
- arquivo:
- data:
```

### Template de checkpoint

```markdown
# MIGRATION_CHECKPOINT_v0.X

DATA:
SESSÃO:

## Estado geral
- ...

## Projetos processados
- ...

## Chats migrados
- ...

## Arquivos transferidos/validados
- ...

## IDs criados
- ...

## Lacunas
- ...

## Conflitos
- ...

## M0 ainda abertos
- ...

## Próxima ação exata
- ...
```

\clearpage

# PARTE III — Preparar a Conta B

## Fase 16 — Ordem de configuração

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P0.

Ordem recomendada:

1. configurações básicas;
2. memória;
3. instruções personalizadas;
4. apps/plugins;
5. workflows legados de GPT necessários;
6. projetos;
7. arquivos;
8. bootstrap;
9. chats.

### Por que essa ordem

A Conta B deve receber primeiro o **ambiente interpretativo** e só depois o histórico. Caso contrário, chats importados podem ser lidos sem as regras, relações e correções que dão significado a eles. Apps também precisam estar conectados antes de validar tarefas que dependem de dados externos.

## Fase 17 — Configurações básicas da Conta B

1. Faça snapshot inicial da Conta B vazia.
2. Configure personalidade/estilo conforme a fonte canônica.
3. Configure Controles de dados deliberadamente; não copie por hábito.
4. Confirme idioma/região/fuso quando relevante.
5. Registre mudanças no Manifest.

> **VERIFIQUE**  
> A Conta B não precisa replicar configurações antigas que foram marcadas `SUPERSEDED`, `CONFLITO` ou `DO_NOT_MIGRATE`.

## Fase 18 — Memória da Conta B

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P0.

### Princípios

- Não tente “memorizar tudo” em uma única mensagem.
- Use memória para contexto recorrente; use documentos para fatos auditáveis.
- Use `PROJECT_STATE` para estado de projeto.
- Use conversas para histórico/evidência.
- Use `NEGATIVE_KNOWLEDGE` para evitar regressões.
- Use memória de projeto de forma deliberada.

### Procedimento

1. Abra Personalização → Memória **[VERIFICAR NA INTERFACE ATUAL]**.
2. Configure os controles pretendidos.
3. Compare com o snapshot da Conta A.
4. Não force igualdade se a interface/recursos forem diferentes.
5. Carregue/forneça documentos portáteis no contexto adequado.
6. Use o bootstrap para ensinar B a interpretar esses documentos.

### Memória global vs memória de projeto

- **Padrão:** pode permitir relação com contexto mais amplo, conforme plano/conta.
- **Somente do projeto:** isola o projeto; chats não consultam memórias externas e chats externos não consultam o projeto.
- **Projeto compartilhado:** atualmente força memória somente do projeto.

Escolha por projeto. Para projetos sensíveis ou autocontidos, o isolamento pode ser vantagem. Para projetos que dependem fortemente do perfil global, pode ser desvantagem.

## Fase 19 — Instruções personalizadas da Conta B

1. Cole a versão atual validada de `02_CUSTOM_INSTRUCTIONS.md`.
2. Compare com a RAW para garantir que nenhuma regra importante foi perdida.
3. Não copie material marcado `DO_NOT_MIGRATE`.
4. Faça teste simples: peça à Conta B para explicar como deve responder e quais limites ela vê, sem pedir que invente memórias.
5. Salve screenshot da configuração final.

## Fase 20 — Apps/Plugins na Conta B

1. Reconecte apenas apps necessários para os P0/P1.
2. Confirme a identidade da conta externa conectada.
3. Revise permissões.
4. Faça um teste não destrutivo por app.
5. Só depois recrie tarefas que usam esses apps.

## Fase 21 — Workflows de GPT na Conta B

**[VERIFICAR NA INTERFACE ATUAL]**

Como novas criações de GPT em contas pessoais estão atualmente indisponíveis, use esta prioridade:

1. Plugin oficial/migração de GPT, se oferecida à conta;
2. Project com instruções + arquivos + apps;
3. chat bootstrap dedicado;
4. preservar pacote `GPT_*_PORTABLE.md` para migração futura.

Não declare equivalência total sem teste. Actions e permissões podem não existir no fallback.

## Fase 22 — Criar projetos na Conta B

Para cada P0/P1:

1. crie o projeto com nome reconhecível;
2. escolha memória padrão ou somente do projeto deliberadamente;
3. copie instruções do projeto;
4. carregue arquivos canônicos mínimos;
5. carregue ou cole `PROJECT_STATE_<projeto>.md`;
6. adicione documentos auxiliares estritamente necessários;
7. só então migre chats A/B selecionados;
8. execute validação V0–V8;
9. marque `CONTINUABLE`/`VALIDADO` no Manifest.

> **ATENÇÃO**  
> Se o projeto da Conta A estiver compartilhado, não presuma que isso transfere propriedade, memória global ou arquivos para um projeto privado da Conta B. Use o compartilhamento como ponte, não como estado final.

## BOOT-01 — Bootstrap da Conta B

Crie na Conta B uma conversa chamada **“🔁 Bootstrap — Continuidade da Conta A”** e use o prompt abaixo depois de disponibilizar os documentos portáteis relevantes.

```text
ID: BOOT-01
TÍTULO RECOMENDADO: 🔁 Bootstrap — Continuidade da Conta A

OBJETIVO: usar o pacote de migração fornecido para estabelecer continuidade operacional com a Conta A sem inventar memórias, fatos ou relações ausentes.

Você está na Conta B. Os documentos fornecidos são uma representação portátil e auditável da Conta A, mas não são uma licença para tratar inferências como fatos.

REGRAS DE INTERPRETAÇÃO:

1. FONTES CANÔNICAS
Respeite a autoridade documental indicada no pacote.
- ACCOUNT_PROFILE: preferências estáveis;
- CUSTOM_INSTRUCTIONS: regras atuais;
- MEMORY_PORTABLE: contexto portável;
- NEGATIVE_KNOWLEDGE: erros e pressupostos a evitar;
- INTERACTION_MODEL: como trabalhar com o usuário;
- PROJECT_STATE: estado atual de cada projeto;
- GLOBAL_DECISIONS: decisões transversais;
- INFERENCE_CATALOG: inferências com confiança;
- RELATIONSHIP_MAP: relações;
- MIGRATION_MANIFEST: estado operacional da migração.
Bootstrap e resumos derivados não substituem essas fontes.

2. EPISTEMOLOGIA
- não transforme [INFERIDO] em [CONFIRMADO];
- preserve níveis de confiança;
- preserve [CONFLITO];
- preserve [DESATUALIZADO?];
- diga [NÃO RECUPERADO] quando faltarem dados;
- não preencha lacunas por plausibilidade.

3. TEMPORALIDADE
- diferencie ATUAL, HISTÓRICO, SUPERSEDED, CONFLITO e INCERTO;
- quando houver estado atual em PROJECT_STATE, não use estado histórico como se fosse vigente;
- "mais recente" não significa automaticamente "canônico".

4. CONHECIMENTO NEGATIVO
Antes de propor ação em um projeto, verifique se existe regra, abordagem rejeitada, versão não canônica ou pressuposto proibido em NEGATIVE_KNOWLEDGE, DO_NOT_MIGRATE ou no PROJECT_STATE local.

5. PROJETOS
Para estado atual, use PROJECT_STATE. Para histórico, use conversas e arquivos. Para regras locais, use Project Instructions. Não transfira regras de um projeto para outro sem evidência.

6. RELAÇÕES
Preserve relações entre projetos, pessoas, arquivos, ferramentas, decisões e conversas somente quando documentadas ou qualificadas como inferências.

7. INCERTEZA
Quando duas fontes conflitarem:
- identifique o conflito;
- informe quais fontes divergem;
- priorize a fonte canônica explicitamente designada;
- peça validação humana se a autoridade não resolver.

8. COMPORTAMENTO
Use INTERACTION_MODEL e CUSTOM_INSTRUCTIONS para o modo de colaboração, mas não trate estilo como evidência factual.

9. GAPS
Nunca invente a parte ausente de uma migração. Registre lacunas em formato:
GAP_ID | assunto | impacto | fonte necessária | urgência | importância | ação sugerida.

10. OBJETIVO FINAL
O objetivo é tornar esta Conta B CONTINUABLE, não apenas parecer familiar.

TAREFA DE INICIALIZAÇÃO:
A. Leia os documentos disponibilizados.
B. Produza um BOOTSTRAP_AUDIT com:
   - fontes recebidas;
   - fontes ausentes;
   - conflitos detectados;
   - inferências de baixa confiança;
   - projetos P0/P1 reconhecidos;
   - M0/M1 ainda abertos;
   - 10 perguntas de validação que NÃO sejam respondidas por adivinhação.
C. Não grave como fato nada que esteja em conflito ou com baixa confiança.
D. Espere os PROJECT_STATE antes de alegar conhecer o estado de um projeto específico.
```

### Resultado esperado

A Conta B deve identificar corretamente o que recebeu e, igualmente importante, o que **não** recebeu.

> **CRITÉRIO DE CONCLUSÃO**  
> O bootstrap está aprovado quando B reconhece as fontes canônicas, não inventa lacunas e consegue listar corretamente os projetos/limitações que o pacote realmente sustenta.


\clearpage

# PARTE IV — Transferir conteúdo e reconstruir continuidade

## Fase 23 — Escolher o método de transferência por conversa

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P0/P1.

Não existe um único método ótimo. A escolha depende de privacidade, importância da sequência, anexos, contexto externo e custo de reconstrução.

### Ordem recomendada dos métodos

| Método | Quando preferir | Fidelidade | Privacidade | Custo |
|---|---|---:|---:|---:|
| A — Shared Link → continuar/copiar | chat NORMAL, sequência importa, recurso funciona | alta para o snapshot | média/baixa | baixo |
| B — Projeto compartilhado temporário | conjunto coerente de chats/arquivos; ponte deliberada | alta no projeto | média | médio |
| C — Transcript privado | SENSITIVE/HIGHLY_SENSITIVE; precisa preservar sequência | alta | alta | alto |
| D — Novo chat + Capsule + estado | sequência completa não é necessária | semântica alta | alta | médio |
| E — Combinação | casos com anexos, privacidade mista ou contexto complexo | máxima se bem feita | configurável | maior |

### Árvore de decisão — qual método usar?

```text
Conversa selecionada
    │
    ├─ HIGHLY_SENSITIVE? ─ sim → C ou D; NÃO Shared Link
    │
    ├─ SENSITIVE? ─ sim → C/D; Shared Link só excepcionalmente
    │
    ├─ Sequência é essencial? ─ sim → A ou C
    │
    ├─ Há muitos chats/arquivos fortemente acoplados? ─ sim → B como ponte + cópia final
    │
    ├─ Estado consolidado basta? ─ sim → D
    │
    └─ Há elementos mistos? ─ sim → E
```

## Método A — Shared Link → Conta B → cópia privada

A documentação atual informa que continuar uma conversa compartilhada cria uma conversa separada e privada na conta do destinatário. Isso torna Shared Link uma boa ponte para chats NORMAL, desde que a prévia seja revisada.

### Procedimento padrão

```text
Conta A
  ↓
auditar conversa
  ↓
gerar CONV-01 Migration Capsule
  ↓
criar/atualizar Shared Link
  ↓
revisar prévia e privacidade
  ↓
abrir autenticado como Conta B
  ↓
continuar/copiar para gerar conversa privada em B
  ↓
confirmar que a cópia existe em B
  ↓
renomear
  ↓
mover para projeto correto [VERIFICAR NA INTERFACE ATUAL]
  ↓
reanexar/validar arquivos críticos
  ↓
executar CONV-02
  ↓
registrar no Manifest
  ↓
remover Shared Link quando desnecessário
```

### Limitações e riscos

- Em conta pessoal, o Shared Link é um snapshot; mensagens posteriores não entram automaticamente até o link ser atualizado.
- Quem obtiver o link pode ver o conteúdo compartilhado; trate como link por posse, não como arquivo privado.
- O conteúdo compartilhado pode incluir imagens/arquivos compatíveis, mas isso não substitui inventário e reupload/validação de anexos críticos.
- Excluir o link depois reduz acesso futuro pelo link, mas não apaga a cópia privada já criada na Conta B.
- Instruções personalizadas e memória da Conta A não “viajam” com a conversa.

> **CRITÉRIO DE CONCLUSÃO**  
> O chat só conta como migrado quando a conversa privada existe na Conta B, está no projeto correto, os arquivos necessários foram verificados e o CONV-02 foi aprovado.

## Método B — Projeto compartilhado temporariamente

Use com cautela. A documentação atual informa que um projeto compartilhado passa automaticamente para **memória somente do projeto** e deixa de acessar contexto/memórias externas dos membros.

### Regra de segurança operacional

> **NÃO FAÇA AINDA**  
> Não compartilhe um projeto P0 original apenas para “transferi-lo” se alterar sua memória puder afetar trabalho ainda em andamento na Conta A.

### Estratégia preferida

1. Crie um projeto-ponte específico, se a interface permitir copiar/adicionar os itens sem alterar o original.
2. Compartilhe o projeto-ponte com a Conta B.
3. Na Conta B, use-o para inspecionar chats/arquivos e criar cópias privadas/consolidadas.
4. Recrie o projeto definitivo na Conta B com a configuração de memória pretendida.
5. Não trate o projeto compartilhado como destino final, salvo se essa for intencionalmente a arquitetura desejada.

### Quando usar

- muitos chats e arquivos estreitamente ligados;
- necessidade de acesso temporário coordenado;
- conteúdo com privacidade compatível com compartilhamento entre as duas contas;
- benefício claro de manter a estrutura enquanto se reconstrói B.

### Quando evitar

- P0 ainda ativo cuja memória global é importante;
- conteúdo altamente sensível;
- quando não há certeza de como mover/copiar chats para fora do projeto compartilhado;
- quando a ponte adiciona mais complexidade do que Shared Links + `PROJECT_STATE`.

## Método C — Transcript privado

Para SENSITIVE/HIGHLY_SENSITIVE ou quando Shared Link falhar.

### Procedimento

1. Gere CONV-01.
2. Copie o conteúdo necessário para arquivo local privado, preferencialmente Markdown.
3. Remova somente segredos/credenciais que não sejam necessários para continuidade; registre a redação.
4. Nomeie `CONV-####_<titulo>_transcript.md`.
5. Na Conta B, carregue o transcript no projeto correto ou use-o como fonte.
6. Reanexe arquivos separadamente.
7. Execute CONV-02.

Não altere trechos só para “deixar bonito”. Preserve autoria, ordem e distinção entre usuário/assistente quando a sequência for relevante.

## Método D — Novo chat + Capsule + estado consolidado

Ideal para classe C e parte dos B.

1. Crie novo chat no projeto da Conta B.
2. Forneça `PROJECT_STATE`.
3. Forneça a Migration Capsule.
4. Anexe apenas arquivos canônicos necessários.
5. Instrua B a listar lacunas antes de continuar.
6. Execute CONV-02.

Vantagem: menor ruído e melhor separação entre estado atual e histórico. Desvantagem: perde a sequência original como experiência nativa.

## Método E — Combinação

Exemplo de caso complexo:

- Shared Link para preservar o raciocínio geral NORMAL;
- transcript privado para uma subseção sensível;
- arquivos reanexados diretamente;
- Capsule para explicitar contexto externo;
- `PROJECT_STATE` como autoridade atual.

## Fase 24 — COPIED ≠ CONTINUABLE

Definições operacionais:

```text
COPIED
= conteúdo existe na Conta B.
```

```text
CONTINUABLE
= a Conta B possui:
  conteúdo necessário;
  arquivos necessários;
  projeto correto;
  contexto explícito;
  estado atual;
  conhecimento negativo necessário;
  relações/dependências relevantes;
  próxima ação;
  capacidade demonstrada de continuar corretamente.
```

Um chat pode ser `COPIED` e ainda falhar porque:

- o arquivo citado não foi migrado;
- a versão “mais nova” foi tomada como canônica, mas não era;
- uma correção importante ficou em outra conversa;
- o projeto não recebeu as instruções locais;
- B desconhece uma decisão transversal;
- uma inferência de A virou “fato” em B;
- o histórico migrou, mas a próxima ação não está clara.

## CONV-02 — Migration Check por conversa

```text
ID: CONV-02
OBJETIVO: verificar se esta conversa migrada para a Conta B está realmente CONTINUABLE, sem recontar todo o histórico.

Use somente as fontes atualmente disponíveis neste projeto/chat. Não invente o que estiver faltando.

Responda:

1. Qual é o objetivo desta conversa?
2. Qual é o estado atual válido?
3. Qual é a próxima ação concreta?
4. Quais decisões continuam vigentes?
5. Quais alternativas já foram rejeitadas?
6. Quais correções/conhecimento negativo eu preciso respeitar?
7. Quais arquivos são necessários para continuar?
8. Quais versões são canônicas, atuais, históricas ou incertas?
9. De quais outros projetos/conversas/decisões esta conversa depende?
10. Que premissas você NÃO deve assumir?
11. Há conflito entre transcript, Migration Capsule e PROJECT_STATE?
12. O que está [NÃO RECUPERADO]?

Depois classifique:
- INTEGRIDADE: PASS | FAIL
- ESTADO: PASS | FAIL
- ARQUIVOS: PASS | FAIL
- DECISÕES: PASS | FAIL
- CONHECIMENTO_NEGATIVO: PASS | FAIL
- PRÓXIMA_AÇÃO: PASS | FAIL
- CONTINUABLE: SIM | NÃO

Se NÃO, produza uma lista mínima de correções em ordem de prioridade. Não preencha lacunas por inferência livre.
```

## Fase 25 — Transferência de arquivos

**URGÊNCIA:** M0/M1  
**IMPORTÂNCIA:** P0/P1.

### Regras

1. Transfira fontes primárias e canônicas primeiro.
2. Preserve nome e versão; se renomear, registre alias.
3. Mantenha cópia local independente das duas contas.
4. Para arquivos críticos, use hash local opcional (`SHA-256`) para provar identidade.
5. Reanexe arquivos nos projetos/chats em que são operacionalmente necessários.
6. Valide abertura e conteúdo depois do upload.
7. Não sobrecarregue projetos com históricos obsoletos se isso dilui contexto; mantenha-os localmente e no índice.

### Verificação mínima de arquivo

```text
FILE_ID:
LOCAL_PRESENT: sim/não
B_PRESENT: sim/não
SIZE_MATCH: sim/não/n.a.
HASH_MATCH: sim/não/n.a.
OPENS_IN_B: sim/não
ROLE_UNDERSTOOD_BY_B: sim/não
DEPENDENCIES_PRESENT: sim/não
STATUS: VALIDADO | PARCIAL | FALHA
```

## Fase 26 — Reconstrução completa dos projetos P0/P1

Para cada projeto:

1. criar projeto na Conta B;
2. configurar memória deliberadamente;
3. copiar instruções locais;
4. carregar arquivos canônicos mínimos;
5. inserir `PROJECT_STATE`;
6. inserir `NEGATIVE_KNOWLEDGE` local, se houver;
7. inserir decisões/relações relevantes;
8. migrar chats A;
9. migrar chats B selecionados;
10. executar CONV-02 nos chats críticos;
11. executar VAL-01 e V0–V8;
12. atualizar Manifest.

### Árvore de decisão — este projeto precisa ser recriado?

```text
Projeto A
  │
  ├─ Trabalho ativo ou retomada provável? ─ sim → recriar
  │
  ├─ Contém estado/arquivos/decisões únicos? ─ sim → recriar ou arquivar portavelmente
  │
  ├─ Serve só como histórico, sem dependência futura?
  │      ├─ sim → P2/P3; pode ficar como pacote local
  │      └─ não
  │
  ├─ É duplicado/abandonado e sem valor histórico? ─ sim → P4; não recriar
  │
  └─ Há dúvida? → preserve PROJECT_STATE + índice; decidir em M2
```

## MEM-06 — Segunda auditoria de inferências

Execute na Conta A **depois** de migrar os principais projetos. O objetivo é capturar o que só ficou evidente após ver o que B ainda não sabe.

```text
ID: MEM-06
OBJETIVO: executar uma segunda auditoria de inferências após a migração inicial dos projetos principais, procurando apenas contexto ainda ausente ou incorretamente representado na Conta B.

Não repita catálogos completos. Procure diferenças residuais.

Considere, quando fornecido, o resumo dos gaps encontrados na Conta B e procure na Conta A:
- novas relações entre projetos;
- exceções ainda não documentadas;
- padrões transversais;
- contexto que a Conta B ainda não recebeu;
- conhecimento negativo ausente;
- pressupostos que a Conta B tenderia a errar;
- informações agora percebidas como obsoletas;
- justificativas de decisões que migraram sem causa;
- dependências ocultas de arquivos/conversas;
- termos ou nomes cuja correção não atravessou.

Para cada achado:
RESIDUAL_ID;
TIPO;
DECLARAÇÃO;
EVIDÊNCIA_RESUMIDA;
CONFIANÇA;
IMPACTO;
DESTINO_CANÔNICO;
AÇÃO_CORRETIVA;
URGÊNCIA;
IMPORTÂNCIA.

Finalize com:
- RESIDUAL_CRITICAL_GAPS;
- UPDATES_TO_NEGATIVE_KNOWLEDGE;
- UPDATES_TO_RELATIONSHIP_MAP;
- UPDATES_TO_PROJECT_STATE;
- ITEMS_ALREADY_SATURATED;
- RECOMMENDATION_TO_STOP_OR_CONTINUE.
```

## Fase 27 — `DO_NOT_MIGRATE.md`

A Conta B pode ficar **melhor** que uma clonagem se erros antigos não forem perpetuados.

Registre:

- preferências substituídas;
- inferências incorretas;
- estados obsoletos;
- projetos abandonados;
- associações falsas;
- informação histórica que deve continuar arquivada, mas não personalizando respostas;
- versões superseded;
- hábitos antigos que não devem ser tratados como atuais.

Template:

```markdown
# DO_NOT_MIGRATE

| ID | Escopo | Item | Motivo | Evidência | Substituído por | Manter histórico? |
|---|---|---|---|---|---|---|
| DNM-0001 | global/projeto | ... | ... | ... | ... | sim/não |
```

## Fase 28 — Critério de saturação semântica

Não é obrigatório migrar individualmente todos os chats. Considere `SEMANTIC_SATURATION` quando uma amostra sucessiva de chats remanescentes deixa repetidamente de acrescentar:

- fatos;
- decisões;
- inferências;
- relações;
- arquivos;
- correções;
- conhecimento negativo;
- próxima ação;
- evidência necessária para validar o estado atual.

### Procedimento

1. Escolha 5–10 chats ainda não migrados do mesmo agrupamento.
2. Audite o que cada um acrescentaria aos documentos canônicos.
3. Se 3 lotes sucessivos não trouxerem novidade material, marque `SEMANTIC_SATURATION_CANDIDATE`.
4. Faça uma amostra adversarial de chats antigos/diferentes.
5. Se nada crítico surgir, pare a migração individual e deixe o restante para `[RECONCILIAR COM ZIP DEPOIS]` ou arquivo histórico.

Saturação não significa “nada mais existe”; significa “o custo marginal de migrar chat a chat não se justifica para continuidade operacional”.

\clearpage

# PARTE V — Validar A × B × evidência

## Fase 29 — Princípio de validação triangular

Nunca valide apenas perguntando “A e B respondem igual?”. Ambas podem repetir o mesmo erro.

Use:

```text
Conta A ↔ Conta B ↔ evidência primária
```

Evidência primária pode ser:

- mensagem explícita do usuário;
- arquivo original;
- decisão escrita;
- `PROJECT_STATE` validado;
- documentação canônica;
- script/dataset de origem;
- screenshot de configuração.

## Fase 30 — Níveis V0–V8

| Nível | O que testa | Critério de aprovação |
|---|---|---|
| V0 — Integridade | item existe e abre | nenhum artefato crítico ausente/corrompido |
| V1 — Estrutura | projeto/chats/arquivos estão no lugar certo | estrutura e IDs coerentes |
| V2 — Factual | fatos centrais | B coincide com evidência primária |
| V3 — Temporal | atual vs histórico | B não usa estado superseded como atual |
| V4 — Relacional | dependências e relações | B conecta entidades corretas sem inventar |
| V5 — Decisional | decisões e justificativas | B sabe o que foi decidido e por quê |
| V6 — Conhecimento negativo | o que não fazer/assumir | B evita erros já corrigidos |
| V7 — Comportamental | modo de colaboração | B segue Interaction Model e regras atuais |
| V8 — Continuidade real | execução | B consegue realizar a próxima tarefa correta |

Um projeto só é `VALIDADO` depois de V8. Antes disso, pode estar `MIGRADO` ou `CONTINUABLE` provisoriamente.

## VAL-01 — Teste de continuidade real

```text
ID: VAL-01
OBJETIVO: testar se este projeto na Conta B consegue continuar o trabalho real, não apenas resumir o passado.

Use PROJECT_STATE, arquivos, conversas e documentos canônicos disponíveis. Não consulte a Conta A durante a primeira tentativa.

Responda:

1. Qual é a próxima ação concreta deste projeto?
2. Quais premissas precisam estar verdadeiras antes de executá-la?
3. Quais arquivos exatos são necessários?
4. Quais dependências externas existem?
5. Quais decisões anteriores restringem a solução?
6. Quais abordagens/versões já foram rejeitadas?
7. O que você NÃO deve assumir?
8. Quais riscos ou incertezas ainda estão abertos?
9. Qual evidência confirmaria que a próxima ação foi executada corretamente?
10. Se eu pedir para continuar agora, qual seria seu primeiro passo e qual fonte você usaria?

Depois classifique:
V0_INTEGRIDADE: PASS/FAIL
V1_ESTRUTURA: PASS/FAIL
V2_FACTUAL: PASS/FAIL
V3_TEMPORAL: PASS/FAIL
V4_RELACIONAL: PASS/FAIL
V5_DECISIONAL: PASS/FAIL
V6_NEGATIVE_KNOWLEDGE: PASS/FAIL
V7_COMPORTAMENTAL: PASS/FAIL
V8_CONTINUIDADE_REAL: PASS/FAIL

Para cada FAIL:
- evidência ausente;
- impacto;
- fonte necessária;
- correção mínima.

Não compense informação ausente com adivinhação.
```

## Fase 31 — Métricas de continuidade

Defina três métricas distintas. Não reduza migração a “percentual de chats copiados”.

### `C_D` — continuidade documental

Percentual ponderado de fontes/artefatos necessários que estão preservados e recuperáveis.

Exemplo simples:

```text
C_D = Σ(peso_i × preservado_i) / Σ(peso_i)
```

Use peso maior para P0/canônico/fonte primária.

### `C_S` — continuidade semântica

Capacidade da Conta B de compreender corretamente:

- relações;
- estado atual;
- decisões;
- temporalidade;
- conhecimento negativo;
- próxima ação.

Pode ser medida pelo Golden Set e V2–V6.

### `C_E` — continuidade espontânea

Capacidade de B usar o contexto correto sem você precisar relembrar explicitamente a cada tarefa.

Não exija `C_E = 100%`. Memória e interfaces não são cópias bit a bit. O sucesso prático é B ser confiável e ter fontes portáteis para recuperar o que não evoca espontaneamente.

## Fase 32 — Golden Set de validação

Crie `VALIDATION_GOLD_SET.md`. Execute primeiro na Conta A, salve a resposta, depois na Conta B sem mostrar a resposta A. Compare ambos contra evidência primária.

### Regra de pontuação

Para cada pergunta:

- **2 — correto e qualificado**;
- **1 — parcialmente correto / incompleto**;
- **0 — errado, inventado ou não recuperado quando deveria estar disponível**;
- **N/A — não aplicável**.

Marque separadamente **alucinação**: resposta confiante sem suporte é pior que `NÃO RECUPERADO`.

### Golden Set — 80 perguntas adaptáveis

#### A. Perfil e preferências

1. Qual nível de profundidade costuma ser esperado em tarefas técnicas?
2. Em que situações uma resposta curta é preferível?
3. Como fatos, hipóteses, inferências e opiniões devem ser distinguidos?
4. Como incertezas relevantes devem ser tratadas?
5. Quando premissas do usuário devem ser questionadas?
6. Qual é a preferência sobre listas/tabelas versus prosa?
7. Quais idiomas e registros são recorrentes?
8. Que convenções existem para Markdown?
9. Quando LaTeX é preferível a Markdown?
10. Como arquivos versionados devem ser nomeados?

#### B. Interação e qualidade

11. O que significa “qualidade” no modo de trabalho preservado?
12. Como lidar com pedidos em que falta informação crítica?
13. Quando usar fontes externas?
14. Como tratar afirmações recentes ou mutáveis?
15. Quais simplificações devem ser evitadas?
16. Como registrar riscos e trade-offs?
17. Como evitar validar automaticamente a interpretação do usuário?
18. Como organizar respostas técnicas em camadas?
19. Qual é a expectativa sobre rastreabilidade de decisões?
20. Como diferenciar regra global de preferência contextual?

#### C. Ferramentas e ambiente

21. Quais sistemas operacionais/ambientes são relevantes?
22. Quais ferramentas recorrentes precisam ser lembradas?
23. Que convenções existem para Git/GitHub?
24. Que cuidado específico existe em relação a branches/commits?
25. Que formatos de artefato são preferidos em diferentes tarefas?
26. Que ferramentas externas precisam ser reconectadas?
27. Que apps/plugins são críticos para projetos ativos?
28. Quais dados externos nunca devem ser tratados como “transferidos” sem reautenticação?
29. Quais arquivos existem apenas na Library?
30. Que limitações de plano podem alterar o workflow após downgrade?

#### D. Projetos

31. Quais são os projetos P0 atuais?
32. Qual é o objetivo do projeto P0 mais importante?
33. Qual é o estado atual desse projeto?
34. Qual é a próxima ação correta?
35. Quais arquivos canônicos ele exige?
36. Quais decisões restringem sua próxima etapa?
37. Quais dependências externas existem?
38. Que pessoas são operacionalmente relevantes e em qual papel?
39. Que relações existem entre dois projetos específicos?
40. Qual projeto parece semelhante a outro, mas não deve ser confundido?

#### E. Decisões e versões

41. Cite uma decisão global ainda vigente e sua justificativa.
42. Cite uma decisão de projeto e a alternativa rejeitada.
43. Qual arquivo é canônico em um projeto importante?
44. Existe versão mais recente que não seja canônica? Qual?
45. Que versão está marcada como histórica?
46. Qual decisão foi superseded e pelo quê?
47. Que conflito de versão continua aberto?
48. Como a Conta B deve agir quando “mais recente” e “canônico” divergem?
49. Em que documento está a autoridade para estado atual?
50. Em que documento deve ficar uma decisão transversal?

#### F. Relações e inferências

51. Dê uma inferência transversal de alta confiança e sua evidência resumida.
52. Dê uma inferência de baixa confiança que não deve virar fato.
53. Que relação entre projetos depende de múltiplas conversas?
54. Que arquivo aparece em mais de um projeto e com papéis diferentes?
55. Que preferência é condicional, não global?
56. Que relação parece plausível, mas está marcada como não confirmada?
57. Existe dependência oculta identificada pelo Loss Audit?
58. Que item precisa de validação humana antes de ser memorizado?
59. Que relação temporal é importante para não usar contexto obsoleto?
60. Que inferência deve permanecer apenas no `INFERENCE_CATALOG`?

#### G. Conhecimento negativo

61. O que você NÃO deve assumir em um projeto P0?
62. Que abordagem já foi tentada e rejeitada?
63. Que termo/nome já foi corrigido?
64. Que associação plausível seria incorreta?
65. Que versão recente NÃO deve ser tratada como canônica?
66. Que preferência antiga não deve continuar personalizando respostas?
67. Que projeto foi abandonado e não deve ser tratado como ativo?
68. Que erro recorrente do ChatGPT precisa ser evitado?
69. Que informação é histórica, mas não atual?
70. O que está explicitamente em `DO_NOT_MIGRATE`?

#### H. Arquivos, continuidade e gaps

71. Quais arquivos são fontes primárias do projeto selecionado?
72. Qual cadeia de dependência produz o artefato final?
73. Que arquivo crítico ainda não foi validado na Conta B?
74. Que conversa depende de contexto externo não contido nela?
75. Qual chat classe A ainda não foi migrado?
76. Qual item está apenas `COPIED`, não `CONTINUABLE`?
77. Quais lacunas críticas permanecem?
78. Quais conflitos críticos permanecem?
79. Se a Conta A desaparecer hoje, qual é o maior risco residual?
80. Qual é a próxima ação global da migração e por quê?

### Critério sugerido

- P0/P1: nenhuma resposta crítica pode receber 0 por erro factual ou temporal.
- Alucinação em item crítico = falha automática do nível relacionado.
- `NÃO RECUPERADO` é aceitável quando a fonte realmente não foi migrada; deve abrir gap, não inventar.

## Fase 33 — Testes negativos obrigatórios

Inclua perguntas que testem se B sabe **não responder demais**:

```text
O que você NÃO deveria assumir neste projeto?
Quais versões são recentes, mas não estão confirmadas como canônicas?
Quais inferências têm confiança baixa?
Que informações parecem desatualizadas?
Que abordagens já foram rejeitadas?
Que associação plausível seria incorreta?
Que fatos você não consegue confirmar com as fontes atuais?
Que contexto histórico não deve continuar personalizando respostas?
```

## Fase 34 — `13_VALIDATION_SUITE.md`

Estrutura mínima:

```markdown
# VALIDATION_SUITE

## Escopo
- Conta A:
- Conta B:
- Data:

## Projetos P0/P1
| PROJECT_ID | V0 | V1 | V2 | V3 | V4 | V5 | V6 | V7 | V8 | Estado |
|---|---|---|---|---|---|---|---|---|---|---|

## Golden Set
| Q | Categoria | A | B | Evidência | Score | Alucinação? | Gap |
|---|---|---|---|---|---:|---|---|

## Falhas críticas
- ...

## Correções
- ...
```


\clearpage

# PARTE VI — Encerrar, coexistir e reconciliar

## Fase 35 — Rota A: Conta A Plus ainda ativa

Esta é a rota principal e deve concentrar os esforços M0.

### Prioridade operacional

1. snapshot de configurações e instruções;
2. memória e resumo de memória;
3. MEM-01 a MEM-LOSS-01;
4. download de arquivos críticos/Library;
5. inventário de projetos;
6. PRJ-01 nos P0/P1;
7. inventário e cápsulas de chats A/B;
8. GPTs legados e workflows;
9. apps/plugins e tarefas;
10. reconstrução da Conta B;
11. validação;
12. MEM-06 residual.

### O que pode esperar

- migração de chats C/D históricos;
- organização estética final de pastas;
- deduplicação minuciosa de arquivos que já têm cópia segura;
- reconciliação cronológica completa;
- auditoria via ZIP.

## Fase 36 — Rota B: Plus da Conta A já expirou, mas a conta continua acessível

**URGÊNCIA:** M1  
**IMPORTÂNCIA:** P0.

Não assuma perda total. A documentação atual mostra que projetos, Library, upload de arquivos e outros recursos continuam existindo em Free, porém com limites menores; recursos específicos de memória, modelos, ferramentas e edição de GPTs podem variar.

### Primeiro: verificar, não inferir

Na Conta A, registre **[VERIFICAR NA INTERFACE ATUAL]**:

- chats continuam acessíveis?
- projetos continuam acessíveis?
- arquivos existentes continuam abrindo?
- Library permite download?
- resumo/memória continua visível?
- instruções personalizadas continuam legíveis?
- apps/plugins continuam conectados?
- tarefas continuam acessíveis?
- GPTs existentes continuam utilizáveis/editáveis?

### Mudança de prioridade após downgrade

1. **Preserve o que ainda está acessível**; não perca tempo lamentando recursos ausentes.
2. Faça screenshot de qualquer mensagem de limite/cota.
3. Se houver projetos com mais arquivos do que o limite atual, não altere-os até entender o comportamento observado.
4. Baixe arquivos críticos que ainda puder baixar.
5. Execute auditorias MEM que ainda funcionarem.
6. Continue a reconstrução na Conta B Plus.
7. Se uma função de A estiver limitada, use documentos locais e a Conta B para consolidação.

### Fallbacks por categoria

| Recurso limitado em A | Fallback |
|---|---|
| modelo/capacidade inferior | use A apenas como fonte; consolide em B |
| upload bloqueado | baixe/extraia conteúdo de A, faça upload em B |
| memória menos acessível | use resumo já salvo + chats + MEM anteriores |
| projeto acima da cota | não mexa; preserve por downloads e inventário |
| edição de GPT indisponível | use screenshots/configuração previamente salva; Plugin/Project em B |
| tarefa não editável | use inventário local e recrie em B |

> **ATENÇÃO**  
> Não transforme ausência de uma opção de UI em conclusão de que os dados foram apagados. Registre o observado e escolha fallback.

## Fase 37 — Rota C: ZIP chegou posteriormente

**URGÊNCIA:** M2  
**IMPORTÂNCIA:** P1.

O modelo de trabalho é:

```text
migração manual existente
+
ZIP
→
auditoria de lacunas
```

Não reinicie a migração do zero.

### Usos recomendados do ZIP

- encontrar chats esquecidos;
- conferir datas;
- localizar histórico não inventariado;
- detectar arquivos/nomes mencionados;
- revisar classificações A–E;
- identificar gaps;
- recuperar trechos históricos;
- validar se houve cobertura suficiente;
- reconciliar IDs locais com dados exportados.

### Procedimento

1. Preserve o ZIP original, sem editar.
2. Faça hash opcional do arquivo.
3. Crie uma cópia de trabalho.
4. Gere um inventário do ZIP separado do Manifest atual.
5. Compare `CONVERSATION_INDEX`, `FILES_INDEX` e `PROJECT_INDEX` com a exportação.
6. Para itens ausentes, classifique importância/urgência antes de migrar.
7. Não substitua documentos canônicos atuais por snapshots históricos sem validação temporal.
8. Atualize `15_GAPS_AND_CONFLICTS.md`.
9. Feche apenas gaps materialmente relevantes.

> **[RECONCILIAR COM ZIP DEPOIS]**  
> Itens D/E e histórico de baixo impacto podem permanecer apenas na exportação, desde que estejam localizáveis e a continuidade operacional já esteja validada.

## Fase 38 — Período de coexistência

Depois que B estiver funcional:

```text
Conta B = primary
Conta A = reference / read mostly
```

Mantenha esse regime por alguns dias ou pelo tempo necessário para atravessar tarefas reais representativas.

### Crie `MIGRATION_FINDINGS.md`

```markdown
# MIGRATION_FINDINGS

## FIND-0001
Problema:
A entendia algo que B não entendeu.

Causa:
...

Fonte ausente:
...

Impacto:
...

Correção:
...

Documento canônico atualizado:
...

Teste de regressão:
...
```

### O que observar

- necessidade de reexplicar contexto que A usava espontaneamente;
- respostas que usam versão histórica;
- ausência de arquivo;
- confusão entre projetos;
- perda de correções;
- mudança de estilo que afeta produtividade;
- app ou tarefa que usa conta externa errada;
- regras do projeto que não foram reconstruídas.

Cada finding relevante deve resultar em correção de uma **fonte canônica**, não em um prompt improvisado perdido num chat.

## Fase 39 — Critério de conclusão

A migração pode ser considerada satisfatória quando:

- todos os projetos P0/P1 estão `CONTINUABLE` ou `VALIDADO`;
- arquivos críticos existem localmente e na Conta B quando necessários;
- chats classe A necessários foram transferidos;
- instruções globais e locais foram reconstruídas;
- memória portátil existe;
- `INTERACTION_MODEL.md` existe;
- `NEGATIVE_KNOWLEDGE.md` existe;
- relações principais estão documentadas;
- `DO_NOT_MIGRATE.md` foi aplicado;
- lacunas críticas = 0;
- conflitos críticos = 0;
- B executa corretamente tarefas reais representativas;
- Golden Set crítico não contém erro/alucinação material;
- eventual ZIP posterior é complemento, não condição para continuidade.

### Critério de encerramento administrativo

Antes de abandonar A:

- [ ] Manifest atualizado;
- [ ] último checkpoint salvo;
- [ ] Shared Links desnecessários removidos;
- [ ] arquivos locais verificados;
- [ ] apps da Conta B testados;
- [ ] tarefas da Conta B testadas;
- [ ] A marcada como reference/read mostly;
- [ ] data de revisão futura definida, se necessária.

\clearpage

# Apêndice A — Templates completos

## A.1 `00_MIGRATION_README.md`

```markdown
# Migração Conta A → Conta B

## Estado
- Fonte: Conta A
- Destino: Conta B
- ZIP disponível: NÃO
- Início:
- Última atualização:
- Último checkpoint:

## Regra central
CONTINUABLE > COPIED.

## Fontes canônicas
- 01_ACCOUNT_PROFILE.md
- 02_CUSTOM_INSTRUCTIONS.md
- 03_MEMORY_PORTABLE.md
- 04_NEGATIVE_KNOWLEDGE.md
- 05_INTERACTION_MODEL.md
- 06_PROJECT_INDEX.md
- 07_RELATIONSHIP_MAP.md
- 08_GLOBAL_DECISIONS.md
- 09_INFERENCE_CATALOG.md
- 10_CONVERSATION_INDEX.md
- 11_FILES_INDEX.md
- 12_DESTINATION_BOOTSTRAP.md
- 13_VALIDATION_SUITE.md
- 14_MIGRATION_MANIFEST.md
- 15_GAPS_AND_CONFLICTS.md
- 16_DO_NOT_MIGRATE.md

## Próxima ação
- ...
```

## A.2 `01_ACCOUNT_PROFILE.md`

```markdown
# ACCOUNT_PROFILE

## Preferências estáveis confirmadas
| ID | Preferência | Evidência | Escopo | Data de revisão |
|---|---|---|---|---|

## Preferências contextuais
| ID | Condição | Preferência | Confiança | Não generalizar para |
|---|---|---|---|---|

## Ferramentas/ambientes recorrentes
- ...

## Critérios de qualidade
- ...

## Incertezas
- ...
```

## A.3 `03_MEMORY_PORTABLE.md`

```markdown
# MEMORY_PORTABLE

## Snapshot de controles
MEMORY_ENABLED:
REFERENCE_SAVED_MEMORIES:
REFERENCE_CHAT_HISTORY:
MEMORY_SUMMARY_AVAILABLE:
PROJECT_MEMORY_OPTIONS:
DATE:

## Resumo da memória — cópia literal
...

## Contexto recorrente validado
| ID | Item | Status | Evidência | Escopo | Temporalidade |
|---|---|---|---|---|---|

## Itens não representados pelo resumo
- ...

## Incertezas
- ...
```

## A.4 `04_NEGATIVE_KNOWLEDGE.md`

```markdown
# NEGATIVE_KNOWLEDGE

| NK_ID | Escopo | Erro a evitar | Correção | Evidência | Consequência | Fonte canônica |
|---|---|---|---|---|---|---|
```

## A.5 `05_INTERACTION_MODEL.md`

```markdown
# INTERACTION_MODEL

## Forma de resposta
...

## Rigor epistemológico
...

## Fontes e verificação
...

## Projetos e estado
...

## Artefatos e versionamento
...

## Tarefas científicas
...

## Tarefas computacionais
...

## Regras condicionais
...

## Simplificações a evitar
...
```

## A.6 `06_PROJECT_INDEX.md`

```markdown
# PROJECT_INDEX

| PROJECT_ID | Nome | Status | Prioridade | Custo reconstrução | Memória | PROJECT_STATE | Recriar? |
|---|---|---|---|---|---|---|---|
```

## A.7 `07_RELATIONSHIP_MAP.md`

```markdown
# RELATIONSHIP_MAP

| REL_ID | Origem | Relação | Destino | Status | Confiança | Evidência | Impacto |
|---|---|---|---|---|---|---|---|
```

## A.8 `08_GLOBAL_DECISIONS.md`

```markdown
# GLOBAL_DECISIONS

| DEC_ID | Decisão | Data aprox. | Justificativa | Alternativas rejeitadas | Evidência | Vigente? |
|---|---|---|---|---|---|---|
```

## A.9 `09_INFERENCE_CATALOG.md`

```markdown
# INFERENCE_CATALOG

| INF_ID | Inferência | Confiança | Evidência resumida | Escopo | Consequência | Migrar? |
|---|---|---|---|---|---|---|
```

## A.10 `10_CONVERSATION_INDEX.md`

```markdown
# CONVERSATION_INDEX

| CONV_ID | Título | Data | Projeto | Classe | Privacidade | Método | Status |
|---|---|---|---|---|---|---|---|
```

## A.11 `11_FILES_INDEX.md`

```markdown
# FILES_INDEX

| FILE_ID | Nome | Projeto | Origem | Versão | Canonicidade | Local? | B? | Validado? |
|---|---|---|---|---|---|---|---|---|
```

## A.12 `12_DESTINATION_BOOTSTRAP.md`

```markdown
# DESTINATION_BOOTSTRAP

> Documento derivado. Não é autoridade primária.

## Fontes que devem ser lidas
- ...

## Regras de interpretação
- não inventar lacunas;
- preservar temporalidade;
- respeitar canonicidade;
- consultar conhecimento negativo;
- qualificar inferências.

## Projetos P0/P1
- ...

## Gaps conhecidos
- ...
```

## A.13 `15_GAPS_AND_CONFLICTS.md`

```markdown
# GAPS_AND_CONFLICTS

| ID | Tipo: GAP/CONFLICT | Escopo | Descrição | Impacto | Evidência necessária | Urgência | Importância | Estado |
|---|---|---|---|---|---|---|---|---|
```

## A.14 `ARTIFACT_GRAPH.md`

```markdown
# ARTIFACT_GRAPH

## Grafo
- FILE-0001 fonte → FILE-0002 derivado → FILE-0003 final

## Nós críticos
- ...

## Dependências ausentes
- ...
```

# Apêndice B — Árvores de decisão obrigatórias

## B.1 Devo migrar este chat?

```text
Fonte de decisão/estado? ─ sim → A/B
          │ não
Sequência necessária? ─ sim → A/B nativo
          │ não
Contexto único/inferencial? ─ sim → Capsule + B/C
          │ não
Arquivo único? ─ sim → preservar arquivo; B/C
          │ não
Duplicado/descartado? ─ sim → D/E
          │ não
Custo reconstrução alto? ─ sim → B
          │ não → C/D
```

## B.2 Qual método usar?

```text
HIGHLY_SENSITIVE → Transcript/Capsule
SENSITIVE → Transcript/Capsule; link só excepcional
NORMAL + sequência essencial → Shared Link
Conjunto fortemente acoplado → Projeto-ponte + cópias
Estado basta → Novo chat + Capsule + PROJECT_STATE
Misto → Combinação
```

## B.3 Este arquivo precisa ser transferido?

```text
Fonte primária única? → sim
Canônico/necessário? → sim
Não reprodutível? → sim
Obsoleto/descartado? → não carregar em B
Reprodutível + histórico? → M2/local
```

## B.4 Este projeto precisa ser recriado?

```text
Ativo/retomada provável? → sim
Estado/arquivos/decisões únicos? → sim ou pacote portátil
Somente histórico? → P2/P3, não necessariamente
Duplicado/abandonado sem valor? → P4, não
Dúvida? → preservar PROJECT_STATE e decidir depois
```

## B.5 Devo confiar nesta informação?

```text
Há evidência primária explícita?
  ├─ sim → CONFIRMADO, salvo conflito posterior
  └─ não
Há fonte canônica designada?
  ├─ sim → usar com temporalidade
  └─ não
É inferência documentada?
  ├─ alta → usar como inferência, não fato
  ├─ média/baixa → manter qualificada
  └─ não
Há conflito? → CONFLITO; não resolver por plausibilidade
Está desatualizada? → HISTÓRICO/SUPERSEDED
Falta fonte? → NÃO RECUPERADO
```

## B.6 Esta versão é canônica?

```text
Há declaração explícita de canonicidade? → sim → CANÔNICO
Não:
  ├─ é apenas a mais recente? → insuficiente
  ├─ PROJECT_STATE indica outra? → seguir PROJECT_STATE
  ├─ decisão explícita indica outra? → seguir decisão
  ├─ há conflito? → CANDIDATO/CONFLITO; validar
  └─ sem evidência → ATUAL ou INCERTO, não CANÔNICO
```

## B.7 Devo esperar pelo ZIP?

```text
A tarefa pode ser feita manualmente agora? → sim → NÃO espere
Depende de contexto vivo/memória/Plus? → faça agora M0
É auditoria histórica não urgente? → pode esperar M2
Conta A pode ficar inacessível antes? → preserve manualmente agora
ZIP já chegou? → use para reconciliar, não reiniciar
```

## B.8 Este item é M0, M1 ou M2?

```text
Pode ficar indisponível/limitado quando Plus terminar? → M0
Depende de contexto vivo/inferência da Conta A? → M0
Precisa ser feito antes de abandonar A, mas não do Plus? → M1
Pode ser refeito com fontes locais/B/ZIP sem perda material? → M2
```

# Apêndice C — Troubleshooting operacional

## C.1 Shared Link não permite continuar/copiar

1. Confirme que está autenticado na Conta B.
2. Atualize o link na Conta A **[VERIFICAR NA INTERFACE ATUAL]**.
3. Teste em janela privada/perfil separado para evitar abrir A por engano.
4. Se ainda falhar, use transcript privado + CONV-01.
5. Registre `METHOD_FALLBACK = C/D` no Manifest.

## C.2 A cópia existe em B, mas perdeu o contexto

- forneça `PROJECT_STATE`;
- forneça Migration Capsule;
- anexe arquivos necessários;
- rode CONV-02;
- corrija a fonte canônica que faltava.

## C.3 Projeto compartilhado mudou o comportamento

Provável causa: projeto compartilhado usa memória somente do projeto. Pare de tratá-lo como equivalente ao projeto privado original. Recrie o projeto final na Conta B com a configuração de memória desejada e use o compartilhado apenas como ponte.

## C.4 Arquivo citado não aparece em B

1. Consulte `FILES_INDEX`.
2. Baixe da Conta A/Library se possível.
3. Reenvie na Conta B.
4. Valide abertura.
5. Atualize dependências do chat/projeto.

## C.5 B inventa relações que A “parecia saber”

- pare a validação;
- procure evidência em `RELATIONSHIP_MAP`/MEM-05;
- se não houver, marque `NÃO RECUPERADO`;
- não “ensine” a relação apenas porque parece plausível.

## C.6 Memória da Conta B está “cheia de tudo” e piorou as respostas

Reduza o uso da memória como banco de dados. Deixe:

- regras estáveis em Custom Instructions;
- contexto recorrente em Memory;
- estado em `PROJECT_STATE`;
- detalhes em arquivos/conversas;
- relações qualificadas em `RELATIONSHIP_MAP`;
- erros em `NEGATIVE_KNOWLEDGE`.

## C.7 Há duas versões conflitantes de um documento

Não escolha pela data. Procure decisão explícita, `PROJECT_STATE`, changelog, conversa de aprovação ou outra evidência. Até resolver, marque `CONFLITO` ou `CANDIDATO_A_CANÔNICO`.

## C.8 Plus expirou no meio da migração

Mude imediatamente para Rota B. Não reinicie inventários. Continue a partir do Manifest e preserve o que ainda estiver acessível.

## C.9 ZIP chegou no meio da migração

Não mude para uma estratégia totalmente nova. Termine o lote atual, faça checkpoint e depois use o ZIP como auditoria de gaps.

## C.10 GPT antigo não pode ser recriado em B

Isso é compatível com a documentação atual para contas pessoais. Extraia configuração na Conta A, procure migração oficial para Plugin **[VERIFICAR NA INTERFACE ATUAL]** e use Project + instruções + arquivos como fallback. Registre capacidades que o fallback não reproduz.

# Apêndice D — Auditoria editorial e operacional do próprio processo

Antes de declarar a migração concluída, responda SIM/NÃO:

### Independência do ZIP

- [ ] Alguma etapa crítica ainda depende do ZIP?
- [ ] Se o ZIP nunca chegar, B permanece operacional?

### Semântica

- [ ] Memória portátil existe?
- [ ] Inferências foram qualificadas?
- [ ] Conhecimento negativo existe?
- [ ] `DO_NOT_MIGRATE` foi aplicado?
- [ ] Temporalidade foi preservada?

### Projetos

- [ ] P0/P1 têm PROJECT_STATE?
- [ ] Arquivos canônicos estão presentes?
- [ ] Conversas A essenciais foram migradas?
- [ ] Próximas ações são explícitas?

### Validação

- [ ] V0–V8 foram executados?
- [ ] Golden Set foi executado?
- [ ] Testes negativos passaram?
- [ ] Lacunas críticas = 0?
- [ ] Conflitos críticos = 0?

### Segurança

- [ ] Links compartilhados desnecessários foram removidos?
- [ ] Conteúdo altamente sensível não foi transferido por Shared Link?
- [ ] Credenciais/tokens não foram copiados?
- [ ] Apps foram reautenticados oficialmente?

# Apêndice E — Quick Reference

## E.1 Prompts

| ID | Função | Onde executar | Quando |
|---|---|---|---|
| MEM-01 | perfil e preferências | Conta A, chat novo | M0 |
| MEM-02 | projetos/relações/decisões | Conta A, chat novo | M0 |
| MEM-03 | conhecimento negativo | Conta A, chat novo | M0 |
| MEM-04 | temporalidade/obsolescência | Conta A, chat novo | M0 |
| MEM-05 | inferências transversais | Conta A, chat novo | M0 |
| MEM-LOSS-01 | auditoria adversarial de perda | Conta A, chat novo | M0 |
| PRJ-01 | PROJECT_STATE | dentro de cada P0/P1 | M0/M1 |
| CONV-01 | Migration Capsule | conversa antes da transferência | M1 |
| CONV-02 | Migration Check | Conta B após transferência | M1 |
| MEM-06 | auditoria residual | Conta A depois dos P0/P1 em B | M0/M1 |
| BOOT-01 | bootstrap global | Conta B | M1 |
| VAL-01 | continuidade real | Conta B, por projeto | M1/M2 |

## E.2 Prioridades

```text
Urgência:
M0 = enquanto A Plus está ativa
M1 = antes de abandonar A
M2 = consolidar depois

Importância:
P0 = crítico
P1 = muito importante
P2 = relevante
P3 = baixo impacto
```

## E.3 Projetos

```text
P0 crítico
P1 importante
P2 relevante
P3 histórico
P4 dispensável operacionalmente
```

## E.4 Conversas

```text
A = migrar nativamente
B = migração nativa desejável
C = consolidar + preservar
D = baixa prioridade
E = dispensável operacionalmente
```

## E.5 Privacidade

```text
NORMAL
SENSITIVE
HIGHLY_SENSITIVE
```

## E.6 Canonicidade de arquivo

```text
CANÔNICO
CANDIDATO_A_CANÔNICO
ATUAL
HISTÓRICO
AUXILIAR
OBSOLETO
DESCARTADO
```

## E.7 Estado do Manifest

```text
NÃO_INVENTARIADO
INVENTARIADO
EM_AUDITORIA
PRONTO_PARA_MIGRAÇÃO
MIGRAÇÃO_PARCIAL
MIGRADO
CONTINUABLE
VALIDADO
```

## E.8 Validação

```text
V0 Integridade
V1 Estrutura
V2 Factual
V3 Temporal
V4 Relacional
V5 Decisional
V6 Conhecimento negativo
V7 Comportamental
V8 Continuidade real
```

## E.9 Ordem mínima M0

```text
1. Instruções personalizadas
2. Snapshot de configurações/memória
3. Resumo da memória
4. MEM-01/02/03/04/05/LOSS
5. Arquivos únicos da Library
6. Inventário dos projetos
7. PROJECT_STATE P0
8. GPTs/workflows legados
9. Apps/tarefas críticas
10. Checkpoint
```

## E.10 Regra de confiança

```text
Evidência primária > fonte canônica validada > inferência qualificada > reconstrução plausível
```

Nunca promova reconstrução plausível a fato sem evidência.

# Apêndice F — Checklist final de encerramento

- [ ] `ZIP_DISPONÍVEL = NÃO` não impediu nenhuma etapa crítica
- [ ] Snapshot A completo
- [ ] Custom Instructions preservadas integralmente
- [ ] Memória e resumo preservados
- [ ] MEM-01 a MEM-LOSS-01 executados
- [ ] Documentos globais criados
- [ ] Projetos inventariados
- [ ] P0/P1 com PROJECT_STATE
- [ ] Conversas classificadas
- [ ] Migration Capsules criadas onde necessário
- [ ] Arquivos críticos locais e em B
- [ ] GPTs/workflows preservados/migrados por fallback
- [ ] Apps/plugins reconectados
- [ ] Tarefas recriadas/validadas
- [ ] Bootstrap executado
- [ ] Chats A essenciais migrados
- [ ] MEM-06 executado
- [ ] DO_NOT_MIGRATE aplicado
- [ ] V0–V8 executados
- [ ] Golden Set executado
- [ ] Coexistência B-primary/A-reference realizada
- [ ] Findings corrigidos em fontes canônicas
- [ ] Lacunas críticas = 0
- [ ] Conflitos críticos = 0
- [ ] Shared Links desnecessários removidos
- [ ] Último checkpoint salvo
- [ ] Manifest = VALIDADO para P0/P1

# Nota final

O sucesso desta migração não é medido pelo número de chats copiados. A melhor migração é aquela em que a Conta B consegue **explicar corretamente o estado atual, localizar as fontes, respeitar decisões e correções, reconhecer o que não sabe e executar a próxima tarefa real sem exigir que o usuário reconstrua manualmente o contexto intelectual acumulado**.

O ZIP, se chegar, deve aumentar a confiança e reduzir lacunas históricas. Ele não deve ser necessário para tornar a Conta B operacional.

