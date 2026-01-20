# ementa_bloco.md (OFICIAL) — Capítulo 03

Regra central de escopo: avaliações futuras só podem cobrar conteúdos registrados aqui (ementa oficial do capítulo) e/ou pré-requisitos explicitamente listados aqui.

---

## Capítulo: C03 — Estruturas de dados embutidas, funções e arquivos

### Bloco: C03B01 — Estruturas de dados e sequências (Parte 1)

Status: concluído em 2026-01-17

Objetivos do bloco

- Diferenciar tuplas (imutáveis) e listas (mutáveis) e usar cada uma adequadamente.
- Aplicar desempacotamento (unpacking) para atribuição múltipla, swap e iteração em pares.
- Executar operações essenciais em listas (inserção, remoção, concatenação, ordenação).
- Utilizar slicing (leitura e escrita) para extrair e substituir sublistas com precisão.
- Empregar built-ins para sequências (enumerate, sorted, zip, reversed) e o módulo bisect para manutenção de ordem.

Tópicos e sub-tópicos

1. Tuplas (tuple)
   - Criação (com/sem parênteses); tupla de 1 elemento (vírgula)
   - Conceito de indexação e uso como sequência
   - Imutabilidade da tupla vs mutabilidade de objetos contidos (lista dentro da tupla)
   - Concatenação (+) e repetição (\*)
   - Métodos básicos (ex.: count)

2. Desempacotamento (unpacking)
   - Atribuição múltipla
   - Swap idiomático (a, b = b, a)
   - Unpacking aninhado
   - Captura de excedentes com \*rest e descarte com \_
   - Iteração desempacotando pares

3. Listas (list)
   - Criação e materialização com list(...) (ex.: range)
   - Operações mutáveis: append, insert, pop, remove
   - Teste de pertinência: in / not in
   - Concatenação com + (cópia) vs extend (in-place)

4. Ordenação e manutenção de ordem
   - list.sort() in-place; uso de key=... (ex.: len)
   - sorted(...) retornando nova lista
   - bisect / insort para ponto de inserção e inserção mantendo ordenação

5. Slicing (fatiamento) avançado
   - start/stop/step; índices negativos
   - Reversão com [::-1]
   - Atribuição por slice (substituição de sublista)

6. Funções embutidas para sequências
   - enumerate (índice + valor)
   - zip e “unzip” com zip(\*iterable)
   - reversed (iterador) vs slice reverso (cópia) vs .reverse() (in-place)

Evidências (artefatos do bloco)

- Notebook: C03B01.ipynb
- Aula + descritivas: geradas no chat (C03B01)
- Avaliação geral do bloco: gerada no chat (C03B01)
- Resolução da avaliação: C03B01_TEST.ipynb

Observações de domínio

- Ficou sólido: distinção tuple vs list; unpacking (swap, \*rest); operações principais de listas; slicing; zip/unzip; bisect/insort.
- Atenção recorrente: diferenciar reversed(seq) (iterador), seq[::-1] (cópia), seq.reverse() (in-place). Em avaliação, manter os “dados do enunciado” sem alterar.

Notas do bloco (CORE v3.0)

- notebook: 92/100
- descritivas: 80/100 (convertido de 8/10)
- avaliação_bloco: 94/100
- final_bloco: 90/100 (0.25*92 + 0.25*80 + 0.50\*94)

---

### Bloco: C03B02 — Estruturas de dados e sequências (Parte 2)

Status: concluído em 2026-01-20

Objetivos do bloco

- Modelar dados com `dict` (chave→valor) e operar com segurança (`get`, `pop` com default).
- Iterar dicionários corretamente (`keys`, `values`, `items`) e realizar merge/atualização (`update`) entendendo sobrescrita.
- Compreender “hashable” e restrições de chaves (imutabilidade).
- Usar `set` para deduplicação, membership eficiente e operações de conjuntos (união, interseção, diferença, dif. simétrica).
- Construir coleções com comprehensions (list/set/dict) e avaliar legibilidade (quando evitar aninhadas).
- Aplicar `setdefault` e `defaultdict(list)` para padrões de agregação por chave.

Tópicos e sub-tópicos

1. Dicionários (dict)
   - Criação (literal e dict(...) a partir de pares)
   - Acesso: d[k] (KeyError) vs d.get(k, default)
   - Inserção/atualização: d[k] = v
   - Remoção: del, pop (com default)
   - Iteração e visões: keys(), values(), items()
   - Merge in-place: update (sobrescreve chaves repetidas)
   - Construção a partir de sequências: dict(zip(keys, values)) e loop com zip
   - Armadilha do zip: trunca no menor comprimento

2. Defaults e agregação por chave
   - setdefault(k, default) para inicializar coleções acumuladoras
   - collections.defaultdict(list) (criação automática ao acessar chave ausente; efeito colateral de criar entradas)

3. Conjuntos (set)
   - Criação: set(iterável); literal {…}; set vazio: set()
   - Deduplicação e membership
   - Operações: união (|), interseção (&), diferença (-), diferença simétrica (^)
   - Hashable: por que listas/dicts/sets não entram como elementos; uso de tuplas quando necessário

4. Comprehensions
   - List / set / dict comprehensions com filtro (if)
   - Comprehensions aninhadas (flatten + filtro)
   - Critérios de legibilidade: quando virar for explícito

Evidências (artefatos do bloco)

- Notebook: C03B02.ipynb
- Descritivas + respostas: C03B02_DESC.ipynb
- Avaliação do bloco + respostas: C03B02_TEST.ipynb
- Aula/revisão/avaliação/correções: geradas no chat (C03B02)

Observações de domínio

- Pontos sólidos: merge/update, agrupamento por chave (setdefault/defaultdict), set para deduplicação, operações de conjunto, uso de comprehensions.
- Atenções recorrentes:
  - Merge sem modificar original: ordem importa (ex.: a | b).
  - Membership: set é O(1) médio; list é O(n).
  - Legibilidade: definir critérios objetivos para não exagerar em comprehensions aninhadas.

Notas do bloco (CORE v3.0)

- notebook: 91/100
- descritivas: 73/100
- avaliação_bloco: 90/100
- final_bloco: 86/100 (0.25*91 + 0.25*73 + 0.50\*90)
