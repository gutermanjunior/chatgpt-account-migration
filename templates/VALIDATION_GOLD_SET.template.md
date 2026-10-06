# VALIDATION_GOLD_SET

## Regra de pontuação
- **2 — correto e qualificado**
- **1 — parcialmente correto / incompleto**
- **0 — errado, inventado ou não recuperado quando deveria estar disponível**
- **N/A — não aplicável**

Marque separadamente **alucinação**: resposta confiante sem suporte é pior que `NÃO RECUPERADO`.

## A. Perfil e preferências
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

## B. Interação e qualidade
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

## C. Ferramentas e ambiente
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

## D. Projetos
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

## E. Decisões e versões
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

## F. Relações e inferências
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

## G. Conhecimento negativo
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

## H. Arquivos, continuidade e gaps
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

## Critério sugerido
- P0/P1: nenhuma resposta crítica pode receber 0 por erro factual ou temporal.
- Alucinação em item crítico = falha automática do nível relacionado.
- `NÃO RECUPERADO` é aceitável quando a fonte realmente não foi migrada; deve abrir gap, não inventar.
