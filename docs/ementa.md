# ementa.md (OFICIAL) — Capítulo 03

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
   - Indexação e uso como sequência
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
- Avaliação do bloco: gerada no chat (C03B01)
- Resolução da avaliação: C03B01_TEST.ipynb

Observações de domínio

- Ficou sólido: distinção tuple vs list; unpacking (swap, \*rest); operações principais de listas; slicing; zip/unzip; bisect/insort.
- Atenção recorrente: diferenciar reversed(seq) (iterador), seq[::-1] (cópia), seq.reverse() (in-place). Em avaliação, manter os “dados do enunciado” sem alterar.

---

### Bloco: C03B02 — Estruturas de dados e sequências (Parte 2)

Status: concluído em 2026-01-20

Objetivos do bloco

- Modelar dados com dict (chave→valor) e operar com segurança (get, pop com default).
- Iterar dicionários corretamente (keys, values, items) e realizar merge/atualização (update) entendendo sobrescrita.
- Compreender “hashable” e restrições de chaves (imutabilidade).
- Usar set para deduplicação, membership eficiente e operações de conjuntos (união, interseção, diferença, dif. simétrica).
- Construir coleções com comprehensions (list/set/dict) e avaliar legibilidade (quando evitar aninhadas).
- Aplicar setdefault e defaultdict(list) para padrões de agregação por chave.

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

- Pontos sólidos: merge/update, agregação por chave (setdefault/defaultdict), set para deduplicação, operações de conjunto, uso de comprehensions.
- Atenções recorrentes:
  - Merge sem modificar original: ordem importa (ex.: a | b).
  - Membership: set é O(1) médio; list é O(n).
  - Legibilidade: definir critérios objetivos para não exagerar em comprehensions aninhadas.

---

### Bloco: C03B03 — Funções, iteradores/geradores e itertools

Status: concluído em 2026-01-25

Objetivos do bloco

- Entender namespaces e escopo (LEGB) e implicações práticas (shadowing; evitar `global`).
- Tratar funções como objetos de primeira classe (passar/retornar funções; usar `key=`).
- Usar `lambda` com critério de legibilidade; preferir `def` quando a lógica cresce.
- Aplicar `functools.partial` para pré-configurar funções e adaptar assinaturas.
- Diferenciar iterável vs iterador; entender consumo e exaustão de iteradores.
- Construir e consumir geradores (`yield`) e generator expressions com foco em eficiência.
- Usar `itertools` para pipelines com iteradores (ex.: `count`, `takewhile`, `groupby`).
- Aplicar tratamento de exceções com `try/except/else/finally`, capturando exceções específicas.

Tópicos e sub-tópicos

1. Namespaces e escopo (LEGB)
   - Local vs global; shadowing
   - `global` (efeitos colaterais) e alternativas: retorno, classe, closures (`nonlocal`)
2. Funções como objetos
   - Passagem como argumento; retorno de função
   - `sorted(..., key=...)` e chaves compostas (tuplas) para desempate
3. `lambda` e critérios de uso
   - Uso pontual (key/callback simples) vs prejuízo de legibilidade
4. Aplicação parcial
   - `functools.partial` para fixar argumentos e adaptar assinatura
5. Iteráveis, iteradores e exaustão
   - Protocolo de iteração (`iter`, `next`, `__iter__`, `__next__`)
   - Consumo único; recriar iterador vs materializar dados
6. Geradores
   - `yield`, lazy evaluation, consumo com `for`, `list`, `sum`
7. itertools
   - `count`, `takewhile`, `chain`, `islice` (quando aplicável)
   - `groupby`: agrupamento por elementos consecutivos; necessidade de ordenar por chave
8. Exceções
   - `try/except/else/finally`
   - Captura específica (ex.: `ValueError`) vs `Exception`

Evidências (artefatos do bloco)

- Notebook: C03B03.ipynb
- Descritivas + respostas: C03B03_DESC.ipynb
- Avaliação do bloco + respostas: C03B03_TEST.ipynb
- Aula/revisão/avaliação/correções: geradas no chat (C03B03)

Observações de domínio

- Pontos sólidos: generators (`yield`), uso de `partial`, `groupby` com ordenação, estrutura `try/except/else/finally`.
- Atenções recorrentes:
  - `itertools.groupby` não é “SQL GROUP BY”; agrupa apenas consecutivos.
  - Iteradores/geradores são consumíveis (exaurem após consumo); para reutilizar, recriar iterador ou materializar dados.
  - Ordenação com desempate: chave composta (tupla), ex.: `(idade, nome)`.
  - Capturar exceções específicas (ex.: `ValueError`) evita mascarar bugs.

---

### Bloco: C03B04 — Arquivos e I/O (introdução)

Status: concluído em 2026-01-27

Objetivos do bloco

- Abrir arquivos com `open()` e escolher corretamente o modo (`r`, `w`, `x`, `a`, e variações com `+`).
- Diferenciar modo texto vs binário (`str`/`bytes`) e entender o papel de `encoding`.
- Ler e escrever arquivos usando `read`, `read(n)`, iteração por linhas, `write` e `writelines`.
- Usar `with` para garantir fechamento/flush mesmo em caso de exceção.
- Usar `seek`/`tell` com entendimento correto (principalmente em modo binário).
- Reconhecer exceções comuns de I/O e aplicar tratamento específico quando necessário.
- Tornar notebooks reprodutíveis quando dependem de arquivos/dados externos.

Tópicos e sub-tópicos

1. Abertura de arquivos
   - `open(path, mode=..., encoding=...)`
   - Modos: `r`, `w`, `x`, `a`, `r+`, `w+`, `a+`
2. Texto vs binário
   - Texto (`"r"`, `"w"`): `str` + decode/encode via `encoding`
   - Binário (`"rb"`, `"wb"`): `bytes` sem encoding/decoding
3. Leitura
   - `read()`, `read(n)`, `readline()`, `readlines()`
   - Iteração eficiente: `for line in f`
   - Limpeza de linha: `rstrip("\n")` vs `rstrip()` vs `strip()`
4. Escrita
   - `write()` e `writelines()` (não adicionam `\n`)
   - Flush e fechamento via `with`
5. Posição no arquivo
   - `tell()` e `seek(offset, whence)`; `whence` 0/1/2
   - Diferenças práticas entre modo texto e binário
6. Exceções comuns
   - `FileNotFoundError`, `PermissionError`, `UnicodeDecodeError`, `FileExistsError`
7. Reprodutibilidade
   - Declarar pré-requisitos (arquivos/diretórios)
   - Checar e criar diretório `data/` quando necessário
   - Prover dataset mínimo ou instruções de obtenção

Evidências (artefatos do bloco)

- Notebook: C03B04.ipynb
- Descritivas + respostas: C03B04_DESC.ipynb
- Avaliação do bloco + respostas: C03B04_TEST.ipynb
- Arquivos de apoio (pré-requisitos): `data/segismundo.txt`

Observações de domínio

- Atenções recorrentes:
  - `write`/`writelines` não inserem newline; inserir `\n` manualmente quando o formato depende de linhas.
  - `tell/seek` em texto pode ser “opaco”; para offset em bytes, demonstrar em `rb`.
  - Declarar pré-requisitos evita “notebook funciona só na minha máquina”.

---

## Conteúdos já aprendidos — consolidado até C03B04

- C03B01: tuplas vs listas; unpacking; operações e slicing de listas; enumerate/zip/reversed; bisect/insort.
- C03B02: dict (get/pop/iteração/update); hashable; set (operações e membership); comprehensions; setdefault/defaultdict para agregação.
- C03B03: LEGB e shadowing; funções como objetos (key=); lambda e critérios; partial; iterável vs iterador; geradores; itertools (groupby + ordenação); try/except/else/finally.
- C03B04: open/modos; texto vs binário (str/bytes + encoding); leitura/escrita; with; seek/tell; exceções de I/O; reprodutibilidade de notebooks com arquivos.
