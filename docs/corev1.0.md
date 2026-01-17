# Plano de Avaliação por Capítulos (Notebook → Avaliações)

## 1. Objetivo

Padronizar a revisão técnica de um notebook (.ipynb) e a geração de avaliações (exercícios, provas e projetos) por capítulo do livro, com consistência de estilo, critérios de correção e progressão estrita de conteúdo (somente tópicos já estudados).

## 2. Unidade de organização

Um **Capítulo** pode ser dividido em **Blocos**.

* **Bloco**: conjunto coeso de tópicos (ex.: Indexação, Missing Data, GroupBy, Merge/Join, Time Series).
* Um capítulo pode ter **N blocos**.

## 3. Entradas

Para cada capítulo/bloco, você fornece:

1. Arquivo .ipynb (ou trecho relevante) produzido por você ao estudar o livro
2. Identificação: CXXBYY (ex.: C01B01) + nome curto do bloco
3. Escopo (opcional): tópicos a incluir/excluir
4. Nível (opcional): iniciante/intermediário/avançado
5. Restrições (opcional): tempo alvo (ex.: 30 min), foco (pandas/NumPy/plot), proibir certas funções etc.

Além disso, para garantir progressão correta, você mantém um arquivo/lista de Conteúdos já aprendidos até o momento (capítulos/blocos concluídos).

* Eu ajudo a manter essa lista: após cada bloco eu retorno um inventário de tópicos e sub-tópicos cobertos.
* Essa lista é usada para impedir que as avaliações cobrem tópicos ainda não estudados.

## 4. Saídas

### 4.1 Revisão técnica do notebook (por capítulo/bloco)

Entregáveis:

* **Checklist de qualidade** (ver seção 6)
* **Anotações por célula/seção**: correto/incorreto, melhoria, armadilhas, performance, estilo
* **Correções sugeridas** (quando aplicável): o que ajustar e por quê
* **Resumo do que você demonstrou** (competências cobertas)

### 4.2 Avaliação do Bloco (dever de casa, extensa)

Formato padrão (linha dura, estilo universidade):

* 12–25 questões por bloco (ajustável pelo tamanho do bloco; pode subir quando o bloco for grande).
* Predominância de aplicação e diagnóstico, com encadeamento quando fizer sentido.
* Enunciados com subtarefas (ex.: 01a…01j) para forçar prática repetida e fixação.

Distribuição típica:

* 20–30% entendimento (conceitos/definições objetivas)
* 50–65% aplicação (transformações, filtros, groupby, joins, reshaping, etc., conforme o bloco)
* 15–30% diagnóstico (interpretar erro/saída, corrigir bug, explicar comportamento)

Entregáveis (sempre sem gabarito):

* Enunciado (sem respostas)
* Rubrica e pontos por questão (com critérios de parcial)
* Lista de armadilhas/erros comuns esperados
* Nota do bloco (0–100), calculada após correção das suas respostas

Atualização de Conteúdos já aprendidos:

* Ao final de cada bloco, eu listo detalhadamente tópicos e sub-tópicos efetivamente cobertos (baseado no seu notebook e no que foi exigido na avaliação).
* Você adiciona essa lista ao documento mestre de Conteúdos já aprendidos.

### 4.3 Avaliação do Capítulo (nota final)

A nota do capítulo é composta por duas metades:

* 50%: média aritmética das avaliações de todos os blocos do capítulo.

  * Se o capítulo tem N blocos e cada bloco gera uma nota xi, então:

    * NotaBlocos = (x1 + x2 + ... + xN) / N
* 50%: Projeto final do capítulo, cobrindo exclusivamente o conteúdo dos blocos daquele capítulo (e, quando apropriado, pré-requisitos já estudados listados em Conteúdos já aprendidos).

Fórmula:

* NotaCapítulo = 0.5 * NotaBlocos + 0.5 * NotaProjeto

Entregáveis do capítulo:

* Enunciado do projeto (sem respostas)
* Rubrica detalhada e checklist de entrega
* Critérios de avaliação e pontuação
* Nota do projeto (0–100), calculada após correção da sua entrega

Observação: posso produzir uma solução de referência apenas para validação interna da avaliação; ela não é entregue junto com o enunciado, salvo se você solicitar explicitamente depois de entregar sua resolução.

### 4.4 Projeto “grande” (opcional por capítulo ou por módulo)

Estrutura sugerida:

* Problema realista com dataset (público ou sintético)
* Requisitos de qualidade: limpeza, EDA, validação, baseline, conclusões
* Itens de avaliação: correção, clareza, reprodutibilidade, organização

## 5. Padrão de estilo (como vou escrever as avaliações)

* Linguagem direta, técnica, sem passos extras não pedidos.
* Enunciados com input/condição e output esperado bem definidos.
* Sempre indicar:

  * Restrições (se existirem)
  * Forma de entrega (ex.: função, célula, resposta textual curta)
  * Critério de correção (o que vale ponto)
* Regra de escopo: cobrar somente o que consta no notebook do bloco/capítulo e/ou na lista de Conteúdos já aprendidos. Não introduzir tópicos novos.

## 6. Checklist de qualidade (revisão do notebook) de qualidade (revisão do notebook)

1. Correção conceitual
2. Demonstração mínima e suficiente (exemplo prova o ponto?)
3. Uso apropriado de API (pandas/NumPy)
4. Armadilhas relevantes citadas (SettingWithCopy, dtype, index alignment, etc.)
5. Reprodutibilidade (seed quando necessário, ordem de execução, dependências)
6. Leitura/estilo (nomes, comentários, separação de seções)
7. Performance (quando relevante: vectorization, evitar loops, joins)

## 7. Tipos de questão (biblioteca)

* Conceito: “explique diferença entre X e Y com 1 exemplo”
* Previsão de saída: “qual o resultado de…”
* Implementação: “escreva operação pandas que…”
* Debug: “por que isso dá erro? corrija mantendo o objetivo”
* Refatoração: “reescreva para ficar mais idiomático/performático”

## 8. Rubrica padrão (exemplo)

Escala de nota: 0–100.

Regra de entrega:

* Nunca entregar gabarito/respostas junto com enunciados.
* A correção e a pontuação ocorrem somente após você enviar suas soluções (via CORRIJA).

Correção por questão (padrão):

* Cada questão tem pontos definidos (ex.: 2, 5, 10).
* Permite parcial: frações como 1/3, 1/2, 2/3, conforme rubrica da questão.
* Critérios típicos de parcial (quando aplicável):

  * Ideia correta, execução incompleta.
  * Resultado correto com método inadequado frente a restrições explícitas.
  * Resultado parcialmente correto (casos de borda, tipos, ordenação, etc.).

Tolerâncias e comparação (padrão, salvo enunciado em contrário):

* Ordem de linhas: não importa.
* Ordem de colunas: importa apenas se o enunciado exigir.
* Dtypes: não são penalizados salvo quando o enunciado exigir.
* Valores numéricos: tolerância quando houver floating point (padrão: aceitar erro absoluto/relativo pequeno), explicitado no enunciado quando relevante.

Uso de técnicas fora do conteúdo estudado:

* Se o enunciado proibir explicitamente uma técnica e ela for usada: penalizar conforme rubrica.
* Se o enunciado não restringir e a técnica não foi estudada ainda: não penalizar; registrar parecer positivo pela iniciativa, mas apontar que está fora do escopo estudado.

## 9. Fluxo de trabalho proposto de trabalho proposto

1. Você envia `.ipynb` + identifica capítulo/bloco
2. Eu entrego revisão técnica + avaliação do bloco
3. Você resolve
4. Você envia respostas com `CORRIJA:` (ou o formato que preferir)
5. Ao fechar todos os blocos do capítulo: eu entrego a prova/mini-projeto do capítulo

## 10. Convenção de prompts

* `EXPLICA:` explicar trecho teórico/código
* `CORRIJA:` corrigir respostas/exercícios
* `PERGUNTA:` resposta direta/técnica
* `DUVIDA:` esclarecimento

## 11. Campos que você pode padronizar (opcional)

* Tempo alvo por bloco/prova
* Dificuldade
* Percentual por tipo de questão
* Se permite usar `.apply`, loops, ou exige vectorização
