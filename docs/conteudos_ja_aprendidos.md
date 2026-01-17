# Conteudos ja aprendidos (documento mestre)

Regra de escopo: avaliacoes futuras devem cobrar apenas conteudo registrado aqui (e/ou evidenciado no notebook do bloco atual).

Convencoes

- ID de bloco: CXXBYY (ex.: C03B01)
- Status: Planejado | Em andamento | Concluido
- Evidencia: notebook(s) e, quando existir, avaliacao/resolucao

---

## Capitulo C03 — Estruturas de dados embutidas, funcoes e arquivos

### C03B01 — Estruturas de dados e sequencias (Parte 1)

- Status: Concluido
- Data: 2026-01-17
- Evidencia:
  - Notebook (estudo): C03B01.ipynb
  - Notebook (avaliacao / respostas): C03B01_TEST.ipynb
- Pontuacoes desta etapa:
  - Checagem (apos aula): 8/10
  - Nota do notebook: 92/100
  - Nota da avaliacao do bloco: 94/100

Topicos e sub-topicos cobertos

1. Tuplas (tuple)
   - Criacao (com/sem parenteses); tupla de 1 elemento (virgula)
   - Indexacao (conceito) e uso como sequencia
   - Imutabilidade da tupla vs mutabilidade de objetos contidos (lista dentro da tupla)
   - Concatenacao (+) e repeticao (\*)
   - Metodos basicos (ex.: count)

2. Desempacotamento (unpacking)
   - Atribuicao multipla
   - Swap idiomatico (a, b = b, a)
   - Unpacking aninhado
   - Captura de excedentes com \*rest e descarte com \_
   - Iteracao desempacotando pares

3. Listas (list)
   - Criacao e materializacao com list(...) (ex.: range)
   - Operacoes mutaveis: append, insert, pop, remove
   - Teste de pertinencia: in / not in
   - Concatenacao com + (copia) vs extend (in-place)

4. Ordenacao e manutencao de ordem
   - list.sort() in-place; uso de key=... (ex.: len)
   - sorted(...) retornando nova lista
   - bisect / insort para ponto de insercao e insercao mantendo ordenacao

5. Slicing (fatiamento) avancado
   - start/stop/step; indices negativos
   - Reversao com [::-1]
   - Atribuicao por slice (substituicao de sublista)

6. Funcoes embutidas para sequencias
   - enumerate (indice + valor)
   - zip e "unzip" com zip(\*iterable)
   - reversed (iterador) vs slice reverso (copia) vs .reverse() (in-place)

Observacoes / pontos de atencao

- Diferenciar: reversed(seq) (iterador), seq[::-1] (copia), seq.reverse() (in-place).
- Em avaliacoes: nao alterar os "dados do enunciado" (listas/valores fornecidos).
