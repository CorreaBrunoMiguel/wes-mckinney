# Ementa Geral (OFICIAL)

last_updated: 2026-01-29

Regra central de escopo: avaliações futuras só podem cobrar conteúdos registrados aqui (ementa oficial do capítulo) e/ou pré-requisitos explicitamente listados aqui.

Como inserir novos blocos (B8)

- O patch de um bloco deve começar em `### Bloco: CXXBYY — ...` e terminar no separador `---`.
- Ao aplicar o patch, cole o novo bloco dentro do capítulo correspondente, acima do marcador `<!-- NEXT_BLOCK_CXX: ... -->` do capítulo.

Sumário (capítulos e blocos)

- C03: C03B01, C03B02, C03B03, C03B04
- C04: C04B01, C04B02

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
2. Hashable
   - O que significa ser “hashable”
   - Por que listas/dicts/sets não podem ser chaves
   - Tuplas como chaves (quando apropriado)
3. Conjuntos (set)
   - Criação: set(iterável); literal {…}; set vazio: set()
   - Deduplicação e membership
   - Operações: união (|), interseção (&), diferença (-), diferença simétrica (^)
   - Hashable: por que listas/dicts/sets não entram como elementos; uso de tuplas quando necessário
4. Comprehensions
   - List / set / dict comprehensions com filtro (if)
   - Comprehensions aninhadas (flatten + filtro)
   - Critérios de legibilidade: quando virar for explícito
5. Agregação por chave
   - dict.setdefault
   - collections.defaultdict(list)

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

<!-- NEXT_BLOCK_C03: C03B05 (se aplicável) -->

---

## Capítulo: C04 — Básico sobre o NumPy: arrays e processamento vetorizado

### Bloco: C04B01 — O ndarray do NumPy (criação, dtypes, aritmética, indexação/slicing)

Status: concluído em 2026-01-29

Objetivos do bloco

- Compreender o que é `ndarray` e suas propriedades principais (`ndim`, `shape`, `dtype`) e a restrição de homogeneidade.
- Criar arrays via `np.array`, `np.asarray`, `np.zeros`, `np.ones`, `np.empty`, `np.arange` (incluindo formatos multidimensionais via tuplas).
- Interpretar/selecionar `dtypes`; converter tipos com `astype` e entender truncamento e custos de cópia.
- Realizar aritmética vetorizada e comparações elementwise; entender noções de broadcasting (principalmente escalar e atribuições em fatias).
- Usar indexação e slicing em arrays 1D/2D/3D, entendendo “views” vs “copies”, e quando usar `.copy()`.

Tópicos e sub-tópicos

1. NumPy e vetorização
   - Motivação: performance/memória; operações “em lote” sem `for`
   - Convenção `import numpy as np`; evitar `from numpy import *` (colisões de namespace)
2. `ndarray` (array N-dimensional)
   - Dados homogêneos; metadados `dtype`
   - Dimensionalidade e formato: `ndim`, `shape`
3. Criação de arrays
   - `np.array(seq)` e inferência de dtype
   - Sequências aninhadas → array multidimensional
   - `np.asarray` (não copia se a entrada já for `ndarray`)
   - `np.zeros(shape[, dtype])`, `np.ones`, `np.empty` (valores não inicializados)
   - `np.arange(start, stop, step[, dtype])`
   - Funções \*\_like: `zeros_like`, `ones_like`, `empty_like`
4. Tipos de dados (dtypes)
   - Convenção de nomes (int/float + bits) e códigos de tipo
   - Cast/conversão: `astype(...)` (sempre cria cópia)
   - Truncamento de float → int
   - Strings em NumPy: tamanho fixo (`numpy.string_`) e risco de truncamento
5. Aritmética com arrays
   - Operações elementwise entre arrays do mesmo `shape`
   - Operações com escalares (broadcast)
   - Comparações retornam arrays booleanos
   - Operações com `shapes` distintos: conceito de broadcasting (referência ao apêndice)
6. Indexação básica e fatiamento
   - Indexação 1D; slices `start:stop:step`
   - Atribuição em fatias: broadcast de escalar
   - Slices são views; efeitos colaterais no array original
   - Como obter cópia: `.copy()`
   - 2D: acesso por linha; indexação com vírgula `arr[i, j]`
   - 3D: redução de dimensão ao omitir índices finais; atribuições em subarrays

Evidências (artefatos do bloco)

- Notebook: C04B01.ipynb
- Descritivas + respostas: C04B01_DESC.ipynb
- Avaliação do bloco + respostas: C04B01_TEST.ipynb
- Aula/revisão/avaliação/correções: geradas no chat (C04B01)

Observações de domínio

- Atenções recorrentes:
  - `np.empty` pode conter “lixo” (memória não inicializada).
  - Slices são views; use `.copy()` quando precisar isolar dados.
  - `astype` sempre aloca um novo array (cópia).
  - Casting float → int trunca a parte decimal.

### Bloco: C04B02 — Indexação avançada no NumPy (boolean/fancy) + transposição e eixos

Status: concluído em 2026-02-02

Objetivos do bloco

- Consolidar slicing em 1D/2D (redução de dimensão, `start:stop:step`, step negativo) e impacto em view/cópia.
- Filtrar arrays por indexação booleana (máscaras), combinando condições com `&`, `|`, `~` e uso obrigatório de parênteses.
- Entender compatibilidade de máscara com o eixo indexado e aplicar atribuição via máscara (`A[mask] = ...`) com segurança.
- Aplicar fancy indexing para seleção/reordenação e distinguir “seleção de linhas” vs “pares (i,j)” quando há duas listas no mesmo `[...]`.
- Obter submatriz retangular (produto cartesiano rows×cols) via abordagem correta (`np.ix_` ou seleção em duas etapas).
- Manipular eixos com `transpose`/`.T` e `swapaxes`, prevendo `shape` e aplicando em `dot`/`@`.

Tópicos e sub-tópicos

1. Slicing e dimensionalidade

- `A[i]` vs `A[i:i+1]` (redução/preservação de dimensão)
- step e slicing reverso (`[::-1]`) e implicações de strides/contiguidade

2. Indexação booleana

- máscaras elementwise; `A[mask]` retorna 1D dos elementos selecionados
- compatibilidade de máscara com o eixo filtrado (incompatível → erro)
- combinação de condições com `&`, `|`, `~` e precedência (parênteses obrigatórios)
- atribuição via máscara e efeito no array original

3. Fancy indexing (inteiros)

- seleção/reordenação por listas/arrays de índices
- duas listas no mesmo `[...]` ⇒ pares coordenados (zip) ⇒ resultado 1D
- submatriz retangular: produto cartesiano rows×cols (`np.ix_` / duas etapas)

4. Transposição e eixos

- `A.T`/`transpose()` em 2D; `transpose(order)` em nD (permutação de eixos)
- `swapaxes(i,j)` para troca pontual
- compatibilidade de shapes em `dot`/`@` (colunas do 1º = linhas do 2º)

Evidências (artefatos do bloco)

- Notebook: C04B02.ipynb
- Descritivas + respostas: C04B02_DESC.ipynb
- Avaliação do bloco + respostas: C04B02_TEST.ipynb
- Aula/revisão/avaliação/correções: geradas no chat (C04B02)

Observações de domínio

- Atenções recorrentes:
  - Máscara booleana deve ser compatível com o eixo filtrado (incompatível → erro).
  - Em fancy indexing 2D, `A[rows, cols]` seleciona pares (row_i, col_i), não uma submatriz.
  - Para submatriz retangular, usar produto cartesiano (`np.ix_`) ou seleção em duas etapas.
  - Slicing reverso tende a ser view, mas frequentemente não é contíguo (strides negativos).

---

## Conteúdos já aprendidos — consolidado até C04B02

- C03B01: tuplas vs listas; unpacking; operações e slicing de listas; enumerate/zip/reversed; bisect/insort.
- C03B02: dict (get/pop/iteração/update); hashable; set (operações e membership); comprehensions; setdefault/defaultdict para agregação.
- C03B03: LEGB e shadowing; funções como objetos (key=); lambda e critérios; partial; iterável vs iterador; geradores; itertools (groupby + ordenação); try/except/else/finally.
- C03B04: open/modos; texto vs binário (str/bytes + encoding); leitura/escrita; with; seek/tell; exceções de I/O; reprodutibilidade de notebooks com arquivos.
- C04B01: NumPy ndarray (ndim/shape/dtype); criação (array/asarray/arange/zeros/ones/empty e \*\_like); dtypes e casts (astype com cópia, truncamento, strings de tamanho fixo); aritmética vetorizada e comparações; noções de broadcasting; indexação e slicing (views vs copy; 1D/2D/3D).
  `- C04B02: slicing avançado (dimensionalidade, step e reverso); indexação booleana (máscaras compatíveis, &/|/~ e parênteses, atribuição); fancy indexing 2D (linhas vs pares (i,j), submatriz retangular com rows×cols); transpose/swapaxes e impacto em shape; compatibilidade em dot/@.`
