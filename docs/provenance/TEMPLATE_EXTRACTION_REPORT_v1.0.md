# TEMPLATE_EXTRACTION_REPORT

## SOURCE_VERIFICATION

- **Arquivo efetivamente lido:** `Manual_Migracao_Manual_ChatGPT_A_para_B_v1.0.md`
- **Documento declarado internamente:** `Manual_Migracao_Manual_ChatGPT_A_para_B_v1.0`
- **Versão:** `1.0`
- **Conteúdo completo acessível:** SIM — 3.170 linhas foram lidas integralmente.
- **Fonte normativa usada:** exclusivamente o manual v1.0 anexado.
- **`Protocolo_Migracao_ChatGPT_Conta_A_para_B_v0.2.md` usado como fonte normativa:** NÃO.
- **Pacote anterior usado como fonte normativa:** NÃO.
- **Uso do pacote anterior:** somente comparação posterior para registrar regressões/diferenças.

A precedência aplicada foi:
1. manual v1.0 anexado;
2. instruções do pedido atual;
3. pacote anterior apenas para comparação;
4. contexto histórico apenas para explicar divergências.

## TEMPLATES_GENERATED

- `templates/00_MIGRATION_README.template.md`
- `templates/01_ACCOUNT_PROFILE.template.md`
- `templates/02_CUSTOM_INSTRUCTIONS.template.md`
- `templates/03_MEMORY_PORTABLE.template.md`
- `templates/04_NEGATIVE_KNOWLEDGE.template.md`
- `templates/05_INTERACTION_MODEL.template.md`
- `templates/06_PROJECT_INDEX.template.md`
- `templates/07_RELATIONSHIP_MAP.template.md`
- `templates/08_GLOBAL_DECISIONS.template.md`
- `templates/09_INFERENCE_CATALOG.template.md`
- `templates/10_CONVERSATION_INDEX.template.md`
- `templates/11_FILES_INDEX.template.md`
- `templates/12_DESTINATION_BOOTSTRAP.template.md`
- `templates/13_VALIDATION_SUITE.template.md`
- `templates/14_MIGRATION_MANIFEST.template.md`
- `templates/15_GAPS_AND_CONFLICTS.template.md`
- `templates/16_DO_NOT_MIGRATE.template.md`
- `templates/ARTIFACT_GRAPH.template.md`
- `templates/GPT_PORTABLE.template.md`
- `templates/MIGRATION_CAPSULE.template.md`
- `templates/MIGRATION_CHECKPOINT.template.md`
- `templates/MIGRATION_FINDINGS.template.md`
- `templates/PROJECT_STATE.template.md`
- `templates/VALIDATION_GOLD_SET.template.md`

- `templates/README.md`

## NON_MARKDOWN_TEMPLATES_GENERATED

Nenhum.

O manual v1.0 não contém ocorrências nem schemas canônicos `.csv`, `.json` ou `.jsonl`. Em particular, **não aparecem** no manual v1.0:
- `EVIDENCE_LEDGER.jsonl`;
- `FILES_MANIFEST.csv`;
- `FILES_MANIFEST.json`;
- índices de conversas canônicos em CSV/JSON.

Esses formatos pertenciam à extração anterior baseada em fonte diferente e não foram transportados para este pacote.

## TEMPLATES_NOT_GENERATED

### Artefatos da extração anterior removidos por ausência no manual v1.0

- `MEMORY_EXPORT_RECONCILIATION.template.md`
- `UNRESOLVED_ASSETS.template.md`
- `MIGRATION_DELTA_LOG.template.md`
- `EXPORT_MANIFEST.template.md`
- `EXPORT_STRUCTURE_REPORT.template.md`

Nenhum desses nomes aparece no manual v1.0. Mantê-los apenas por compatibilidade violaria a regra de precedência.

### `02_CUSTOM_INSTRUCTIONS_RAW.template.md`

O manual manda preservar uma cópia literal `02_CUSTOM_INSTRUCTIONS_RAW.md`, mas não define schema: trata-se de captura bruta, não de documento estruturado. Não foi criado um template público separado.

### Transcript de conversa

O manual define a convenção de nome `CONV-####_<titulo>_transcript.md`, mas determina preservar autoria, ordem e sequência; não define um schema de documento independente. Não foi criado template artificial.

## ADDITIONAL_TEMPLATES_FOUND

Além da lista-base solicitada, o manual v1.0 sustenta:

- `VALIDATION_GOLD_SET.template.md` — Fase 32 define `VALIDATION_GOLD_SET.md`, pontuação e 80 perguntas adaptáveis.
- `GPT_PORTABLE.template.md` — Fase 11 define o fallback `GPT_<nome>_PORTABLE.md` e especifica os campos de inventário, instruções, knowledge files e dependências.

Os artefatos relacionados a export/ZIP que haviam aparecido no pacote anterior **não** foram confirmados nesta fonte.

## PREVIOUS_EXTRACTION_DIFFERENCES

### Templates adicionados

- `GPT_PORTABLE.template.md`

### Templates removidos
- `EXPORT_MANIFEST.template.md` — ausente do manual v1.0.
- `EXPORT_STRUCTURE_REPORT.template.md` — ausente do manual v1.0.
- `MEMORY_EXPORT_RECONCILIATION.template.md` — ausente do manual v1.0.
- `MIGRATION_DELTA_LOG.template.md` — ausente do manual v1.0.
- `UNRESOLVED_ASSETS.template.md` — ausente do manual v1.0.

### Mudanças materiais de campos/estrutura

A extração anterior usava o protocolo v0.2 e, em vários arquivos, introduziu schemas que não correspondem ao Apêndice A / fases normativas do manual v1.0. O pacote foi regenerado, não patchado.

Principais correções:

- `00_MIGRATION_README`: substitui estrutura genérica anterior por **Estado / Regra central / Fontes canônicas / Próxima ação** do Apêndice A.1.
- `01_ACCOUNT_PROFILE`: substitui seções livres por tabelas de **preferências estáveis** e **preferências contextuais**, além de ferramentas/ambientes, critérios de qualidade e incertezas (A.2).
- `03_MEMORY_PORTABLE`: passa a usar **Snapshot de controles**, cópia literal do resumo, tabela de contexto recorrente, itens ausentes do resumo e incertezas (A.3).
- `04_NEGATIVE_KNOWLEDGE`: passa a usar a tabela normativa `NK_ID | Escopo | Erro a evitar | Correção | Evidência | Consequência | Fonte canônica` (A.4).
- `05_INTERACTION_MODEL`: passa a seguir as seções do Apêndice A.5.
- `06_PROJECT_INDEX`, `07_RELATIONSHIP_MAP`, `08_GLOBAL_DECISIONS`, `09_INFERENCE_CATALOG`: substituem estruturas narrativas anteriores pelos schemas tabulares definidos no Apêndice A.
- `10_CONVERSATION_INDEX`: remove campos oriundos do protocolo v0.2/export (`SOURCE_CONVERSATION_ID`, `message_count`, `branch_count`, `attachments` etc.) e usa o schema v1.0 `CONV_ID | Título | Data | Projeto | Classe | Privacidade | Método | Status`.
- `11_FILES_INDEX`: remove campos não presentes no template do v1.0 (`sha256`, `mime_type`, `exists_in_export` etc.) e usa `FILE_ID | Nome | Projeto | Origem | Versão | Canonicidade | Local? | B? | Validado?`.
- `12_DESTINATION_BOOTSTRAP`: passa a seguir o Apêndice A.12 e permanece explicitamente derivado.
- `13_VALIDATION_SUITE`: passa a usar o schema mínimo explícito da Fase 34, incluindo V0–V8 e tabela do Golden Set.
- `14_MIGRATION_MANIFEST`: passa a usar o template explícito da Fase 15, incluindo os estados permitidos do manual v1.0.
- `15_GAPS_AND_CONFLICTS`: passa a usar a tabela explícita do Apêndice A.13.
- `16_DO_NOT_MIGRATE`: passa a usar a tabela explícita da Fase 27.
- `PROJECT_STATE`: agora reflete integralmente as 14 seções e saídas `MIGRATION_MINIMUM`, `FILES_TO_TRANSFER`, `CONVERSATIONS_TO_TRANSFER`, `OPEN_GAPS` e `VALIDATION_QUESTIONS` de PRJ-01.
- `MIGRATION_CAPSULE`: agora reflete as 12 seções de CONV-01 e o pacote `MINIMUM_CONTEXT / FILES_REQUIRED / NEXT_ACTION / VALIDATION_QUESTIONS`.
- `MIGRATION_CHECKPOINT`: passa a seguir o template explícito da Fase 15.
- `MIGRATION_FINDINGS`: passa a seguir o template explícito da Fase 38.
- `ARTIFACT_GRAPH`: passa a seguir o Apêndice A.14.
- `VALIDATION_GOLD_SET`: agora contém a escala 0/1/2/N/A e as 80 perguntas adaptáveis definidas na Fase 32.

### Enumerações corrigidas

- **Estado do Manifest:** `NÃO_INVENTARIADO → INVENTARIADO → EM_AUDITORIA → PRONTO_PARA_MIGRAÇÃO → MIGRAÇÃO_PARCIAL → MIGRADO → CONTINUABLE → VALIDADO`.
- `VALIDATED` **não aparece** no manual v1.0 e não é usado.
- Classes de conversa: `A | B | C | D | E`.
- Privacidade: `NORMAL | SENSITIVE | HIGHLY_SENSITIVE`.
- Canonicidade de arquivo: `CANÔNICO | CANDIDATO_A_CANÔNICO | ATUAL | HISTÓRICO | AUXILIAR | OBSOLETO | DESCARTADO`.
- Urgência: `M0 | M1 | M2`.
- Importância operacional: `P0 | P1 | P2 | P3`; para projetos: `P0 | P1 | P2 | P3 | P4`.
- Validação: `V0` a `V8`.

### Correção de proveniência

O pacote anterior declarava ausência do manual final e usava o protocolo v0.2 como fonte principal. Este pacote corrige essa condição: o manual v1.0 anexado foi lido integralmente e é a única fonte normativa.

### Arquivos comuns com mudança estrutural detectada
- `00_MIGRATION_README.template.md` — estrutura/seções alteradas.
- `01_ACCOUNT_PROFILE.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `02_CUSTOM_INSTRUCTIONS.template.md` — estrutura/seções alteradas.
- `03_MEMORY_PORTABLE.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `04_NEGATIVE_KNOWLEDGE.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `05_INTERACTION_MODEL.template.md` — estrutura/seções alteradas.
- `06_PROJECT_INDEX.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `07_RELATIONSHIP_MAP.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `08_GLOBAL_DECISIONS.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `09_INFERENCE_CATALOG.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `10_CONVERSATION_INDEX.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `11_FILES_INDEX.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `12_DESTINATION_BOOTSTRAP.template.md` — estrutura/seções alteradas.
- `13_VALIDATION_SUITE.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `14_MIGRATION_MANIFEST.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `15_GAPS_AND_CONFLICTS.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `16_DO_NOT_MIGRATE.template.md` — estrutura/seções alteradas, campos de tabela alterados.
- `ARTIFACT_GRAPH.template.md` — estrutura/seções alteradas.
- `MIGRATION_CAPSULE.template.md` — estrutura/seções alteradas.
- `MIGRATION_CHECKPOINT.template.md` — estrutura/seções alteradas.
- `MIGRATION_FINDINGS.template.md` — estrutura/seções alteradas.
- `PROJECT_STATE.template.md` — estrutura/seções alteradas.
- `VALIDATION_GOLD_SET.template.md` — estrutura/seções alteradas.

## AMBIGUITIES_FOUND

1. **`02_CUSTOM_INSTRUCTIONS.md` não possui schema interno rígido.** O manual exige uma versão atual validada e uma cópia RAW separada, mas não fornece template completo. O template público foi mantido deliberadamente mínimo.
2. **Schemas compactos vs detalhados.** `06_PROJECT_INDEX`, `10_CONVERSATION_INDEX` e `11_FILES_INDEX` possuem schemas detalhados nas fases operacionais e versões compactas no Apêndice A (“Templates completos”). Os templates públicos seguem o Apêndice A como forma de apresentação e usam enumerações da fase operacional apenas para preencher campos já existentes; os campos extras não foram acrescentados silenciosamente.
3. **`VALIDATION_GOLD_SET.md` é um conjunto de perguntas, não um registro de respostas.** O registro de resultados pertence a `13_VALIDATION_SUITE.md`.
4. **`GPT_<nome>_PORTABLE.md` é parcialmente especificado.** O manual exige instruções, knowledge manifest e dependências e fornece inventário de GPT. O template adicional utiliza somente esses elementos explicitamente definidos.

## MANUAL_INCONSISTENCIES

1. **`03_MEMORY_PORTABLE.md`:** a Fase 3 manda registrar também `OTHER_MEMORY_CONTROLS`, `EVIDENCE_SCREENSHOT` e `NOTES`, enquanto o template “completo” do Apêndice A.3 omite esses campos. O template público segue o Apêndice A.3. Recomenda-se reconciliar o manual numa revisão futura.
2. **`04_NEGATIVE_KNOWLEDGE.md`:** MEM-03 pede `STATUS: CONFIRMADO | INFERIDO | CONFLITO`, mas o template do Apêndice A.4 não possui coluna `STATUS`. O template público segue A.4.
3. **`05_INTERACTION_MODEL.md`:** a Fase 6 inclui a seção `Evidência e escopo`, enquanto o Apêndice A.5 a omite e adiciona `Fontes e verificação`. O template público segue A.5.
4. **Índices compactos vs schemas detalhados:** Fases 7, 8 e 10 definem mais campos que os templates compactos A.6, A.10 e A.11. Isso é uma diferença de granularidade que deveria ser explicitada no manual.
5. **Nome de `DO_NOT_MIGRATE`:** a autoridade documental e o conjunto global usam `16_DO_NOT_MIGRATE.md`, enquanto a Fase 27 chama o artefato de `DO_NOT_MIGRATE.md`. O pacote usa o nome solicitado/canônico `16_DO_NOT_MIGRATE.template.md`, preservando o título interno `DO_NOT_MIGRATE`.
6. **Mistura intencional de idiomas em enumerações:** o manual combina estados em português (`VALIDADO`, `MIGRADO`) com termos operacionais em inglês (`CONTINUABLE`, `NORMAL`, `SENSITIVE`, `HIGHLY_SENSITIVE`, `PASS`, `FAIL`). Nenhuma normalização foi feita.
7. **`VALIDATED`:** diferentemente do relatório anterior, o termo não aparece no manual v1.0. O estado terminal explícito é `VALIDADO`; `CONTINUABLE` é estado anterior/provisório.

## PRIVACY_CHECK

Foi executada revisão explícita dos arquivos gerados procurando:

- nomes próprios reais;
- nomes de projetos pessoais;
- e-mails;
- telefones;
- usernames;
- caminhos locais;
- instituições;
- identificadores;
- credenciais;
- tokens;
- URLs privadas;
- dados médicos;
- dados jurídicos;
- dados financeiros;
- informações de terceiros.

Resultado: **APROVADO para publicação como pacote de templates genéricos**, sujeito à revisão humana final normal antes de commit.

Os arquivos usam apenas:
- `Conta A` / `Conta B`;
- IDs genéricos (`PRJ-0001`, `CONV-0001`, `FILE-0001` etc.);
- placeholders `<preencher>`;
- enumerações do manual;
- exemplos abstratos de relações entre artefatos.

## FIDELITY_CHECK

| Template | Base normativa no manual v1.0 | Resultado |
|---|---|---|
| `00_MIGRATION_README.template.md` | Apêndice A.1; Fase 5 | PASS |
| `01_ACCOUNT_PROFILE.template.md` | Apêndice A.2; MEM-01 | PASS |
| `02_CUSTOM_INSTRUCTIONS.template.md` | Fase 2; Fase 5; Autoridade documental | PASS |
| `03_MEMORY_PORTABLE.template.md` | Apêndice A.3; Fase 3 | PASS |
| `04_NEGATIVE_KNOWLEDGE.template.md` | Apêndice A.4; MEM-03 | PASS |
| `05_INTERACTION_MODEL.template.md` | Apêndice A.5; Fase 6 | PASS |
| `06_PROJECT_INDEX.template.md` | Apêndice A.6; Fase 7 | PASS |
| `07_RELATIONSHIP_MAP.template.md` | Apêndice A.7; MEM-02/MEM-05 | PASS |
| `08_GLOBAL_DECISIONS.template.md` | Apêndice A.8 | PASS |
| `09_INFERENCE_CATALOG.template.md` | Apêndice A.9; MEM-05 | PASS |
| `10_CONVERSATION_INDEX.template.md` | Apêndice A.10; Fase 8 | PASS |
| `11_FILES_INDEX.template.md` | Apêndice A.11; Fase 10 | PASS |
| `12_DESTINATION_BOOTSTRAP.template.md` | Apêndice A.12; BOOT-01 | PASS |
| `13_VALIDATION_SUITE.template.md` | Fase 34 | PASS |
| `14_MIGRATION_MANIFEST.template.md` | Fase 15 | PASS |
| `15_GAPS_AND_CONFLICTS.template.md` | Apêndice A.13 | PASS |
| `16_DO_NOT_MIGRATE.template.md` | Fase 27; Autoridade documental | PASS |
| `PROJECT_STATE.template.md` | PRJ-01 | PASS |
| `MIGRATION_CAPSULE.template.md` | CONV-01 | PASS |
| `MIGRATION_CHECKPOINT.template.md` | Fase 15 | PASS |
| `MIGRATION_FINDINGS.template.md` | Fase 38 | PASS |
| `ARTIFACT_GRAPH.template.md` | Apêndice A.14; Fase 10 | PASS |
| `VALIDATION_GOLD_SET.template.md` | Fase 32 | PASS |
| `GPT_PORTABLE.template.md` | Fase 11 | PASS |

### Verificações Q1–Q6

- **Q1 — Cobertura:** PASS. Todos os artefatos Markdown reutilizáveis com estrutura suficiente e nome/função explícitos foram avaliados; o pacote inclui os candidatos confirmados e os adicionais `VALIDATION_GOLD_SET` e `GPT_PORTABLE`.
- **Q2 — Fidelidade:** PASS com ambiguidades registradas. Campos foram derivados do manual v1.0.
- **Q3 — Não invenção:** PASS. Artefatos antigos ausentes do manual foram removidos; `02_CUSTOM_INSTRUCTIONS` foi mantido mínimo por falta de schema.
- **Q4 — Coerência:** PASS com inconsistências do próprio manual registradas acima.
- **Q5 — Privacidade:** PASS após varredura automatizada e revisão estrutural.
- **Q6 — Usabilidade:** PASS. Templates possuem placeholders e podem ser copiados para workspace privado.

## RECOMMENDED_REPOSITORY_CHANGES

1. Substituir integralmente o pacote anterior por este pacote regenerado; não fazer merge campo a campo com a extração baseada em v0.2.
2. Manter `MANUAL.md` / manual v1.0 como autoridade conceitual e registrar no repositório a versão de origem dos templates.
3. Em revisão futura do manual, reconciliar as inconsistências listadas em `MANUAL_INCONSISTENCIES`, especialmente MEMORY_PORTABLE, NEGATIVE_KNOWLEDGE, INTERACTION_MODEL e schemas compactos/detalhados.
4. Não adicionar `EVIDENCE_LEDGER`, `FILES_MANIFEST` ou templates de export apenas por compatibilidade histórica; eles exigiriam alteração normativa do manual.
5. Manter versões preenchidas dos templates fora do repositório público por padrão.
6. Antes de commit, executar revisão humana de privacidade e um diff entre `MANUAL.md` e `templates/` sempre que o manual mudar.
