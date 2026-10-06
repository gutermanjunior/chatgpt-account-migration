# Templates

Estes arquivos são **templates públicos derivados do manual v1.0** de migração manual de alta fidelidade entre contas ChatGPT.

A autoridade conceitual continua sendo o manual v1.0 / `MANUAL.md`. Os templates não substituem o manual e não devem introduzir regras novas.

## Como usar

1. **Copie** os templates necessários para um workspace **privado** de migração.
2. Renomeie as cópias conforme o manual.
3. Preencha somente as cópias privadas.
4. Trate versões preenchidas como potencialmente sensíveis.
5. **Não faça commit automático** de versões preenchidas no repositório público.
6. Revise privacidade antes de publicar qualquer derivado.
7. Quando houver dúvida de interpretação, volte ao manual v1.0.

> **ATENÇÃO**
> Um template vazio pode ser público. A versão preenchida pode conter dados pessoais, arquivos privados, inferências, histórico de projetos, informações de terceiros ou outros conteúdos confidenciais.

## Formatos estruturados

O manual v1.0 lido para esta extração **não define templates canônicos CSV, JSON ou JSONL**. Portanto, este pacote não cria formatos estruturados paralelos por conveniência. Se uma versão futura do manual definir esses formatos, eles devem ser extraídos novamente a partir dessa fonte.

## Proveniência

| Template | Finalidade | Origem no manual | Contém dados sensíveis quando preenchido? |
|---|---|---|---|
| 00_MIGRATION_README.template.md | Índice e estado básico do workspace de migração | Apêndice A.1; Fase 5 | Sim |
| 01_ACCOUNT_PROFILE.template.md | Perfil operacional e preferências | Apêndice A.2; MEM-01 | Sim |
| 02_CUSTOM_INSTRUCTIONS.template.md | Versão atual validada das instruções personalizadas | Fase 2; Fase 5; Autoridade documental | Sim |
| 03_MEMORY_PORTABLE.template.md | Snapshot e contexto portável de memória | Apêndice A.3; Fase 3 | Sim |
| 04_NEGATIVE_KNOWLEDGE.template.md | Erros, pressupostos e correções a preservar | Apêndice A.4; MEM-03 | Sim |
| 05_INTERACTION_MODEL.template.md | Como colaborar com o usuário | Apêndice A.5; Fase 6 | Sim |
| 06_PROJECT_INDEX.template.md | Catálogo dos projetos | Apêndice A.6; Fase 7 | Sim |
| 07_RELATIONSHIP_MAP.template.md | Relações transversais | Apêndice A.7; MEM-02/MEM-05 | Sim |
| 08_GLOBAL_DECISIONS.template.md | Decisões transversais | Apêndice A.8 | Sim |
| 09_INFERENCE_CATALOG.template.md | Inferências qualificadas | Apêndice A.9; MEM-05 | Sim |
| 10_CONVERSATION_INDEX.template.md | Índice de conversas | Apêndice A.10; Fase 8 | Sim |
| 11_FILES_INDEX.template.md | Índice de arquivos | Apêndice A.11; Fase 10 | Sim |
| 12_DESTINATION_BOOTSTRAP.template.md | Pacote derivado para inicializar a Conta B | Apêndice A.12; BOOT-01 | Sim |
| 13_VALIDATION_SUITE.template.md | Registro da validação A × B × evidência | Fase 34 | Sim |
| 14_MIGRATION_MANIFEST.template.md | Controle operacional da migração | Fase 15 | Sim |
| 15_GAPS_AND_CONFLICTS.template.md | Lacunas e conflitos | Apêndice A.13 | Sim |
| 16_DO_NOT_MIGRATE.template.md | Contexto que não deve ser perpetuado | Fase 27; Autoridade documental | Sim |
| PROJECT_STATE.template.md | Estado portável de projeto P0/P1 | PRJ-01 | Sim |
| MIGRATION_CAPSULE.template.md | Cápsula de continuidade de conversa | CONV-01 | Sim |
| MIGRATION_CHECKPOINT.template.md | Checkpoint entre sessões | Fase 15 | Sim |
| MIGRATION_FINDINGS.template.md | Achados durante coexistência A/B | Fase 38 | Sim |
| ARTIFACT_GRAPH.template.md | Dependências entre artefatos | Apêndice A.14; Fase 10 | Sim |
| VALIDATION_GOLD_SET.template.md | Conjunto fixo de perguntas de validação | Fase 32 | Sim |
| GPT_PORTABLE.template.md | Fallback portável para GPT legado | Fase 11 | Sim |

## Regra de fidelidade

- Preserve enumerações e estados exatamente como definidos no manual.
- Não normalize silenciosamente português/inglês.
- Não trate uma visão derivada como fonte canônica.
- Não preencha lacunas do manual por plausibilidade.
- Consulte `TEMPLATE_EXTRACTION_REPORT.md` para ambiguidades e inconsistências encontradas durante a extração.
