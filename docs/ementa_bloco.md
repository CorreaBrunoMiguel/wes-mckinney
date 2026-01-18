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
