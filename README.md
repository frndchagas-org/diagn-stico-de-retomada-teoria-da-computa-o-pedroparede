[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/zHqjFsRx)
# Diagnóstico de retomada - Teoria da Computação

Esta atividade serve para mapear o que você já domina sobre linguagens formais, autômatos, gramáticas e computabilidade.

Responda individualmente. Use suas palavras. Se usar IA depois da primeira tentativa, registre o uso na seção 7.

## 1. Mapa do que eu lembro

Marque cada tópico como: lembro bem, lembro parcialmente, não lembro, nunca vi ou não tenho certeza.

- alfabeto: lembro  bem
- cadeia: lembro bem
- linguagem: lembro bem
- gramática: lembro parcialmente
- autômato finito: lembro bem
- linguagem regular: lembro bem
- linguagem livre de contexto: não lembro
- linguagem sensível ao contexto: não lembro
- linguagem irrestrita: não lembro
- hierarquia de Chomsky: lembro parcialemente
- computabilidade: não tenho certeza (houve apenas uma pequena introdução ao tema até o momento, não foi possível aprofundá-lo)
- máquina de Turing: lembro bem

## 2. Definições com exemplo

Explique, com suas palavras e com um exemplo simples, usando o alfabeto `Sigma = {a, b}`.

1. O que é um alfabeto?

   Um alfabeto é um conjunto finito de símbolos.
   
3. O que é uma cadeia? 

   Uma cadeia é uma sequência de símbolos justapostos.
   
4. O que é uma linguagem?  

   Uma linguagem é um conjunto de palavras.
   
5. O que é uma gramática? 

   Conjunto de regras para gerar uma linguagem.

## 3. Linguagens

Considere as linguagens:

```text
L1 = { w em {0,1}* | w termina com 01 }
L2 = { a^n b^n | n >= 0 }
L3 = { a^n b^n c^n | n >= 0 }
```

Para cada linguagem:

1. escreva três palavras que pertencem à linguagem;

   Pertencem a linguagem L1: "01", "101", "1101".
   Pertencem a linguagem L2: "ab", "aabb", "aaabbb".
   Pertencem a linguagem L3: "abc", "aabbcc", "aaabbbccc".
   
3. escreva duas palavras que não pertencem;

   Não pertencem a linguagem L1: "10", "111".
   Não pertencem a linguagem L2: "a", "aab".
   Não pertencem a linguagem L3: "bc", "abcc"
   
4. diga, se souber, em qual classe ela provavelmente se encaixa;

   Todas elas se encaixam na classe de liguagens regulares.
   
6. explique o motivo em linguagem simples.

   O motivo disso é que elas podem ser lidas por um autômato finito determinístico.

Não há problema em dizer "não sei". Nesse caso, escreva o que te deixou em dúvida.

## 4. Autômato finito

Considere o autômato abaixo, sobre o alfabeto `{0,1}`:

```text
Estados: q0, q1, q2
Estado inicial: q0
Estado final: q2

Transições:
q0 --0--> q1
q0 --1--> q0
q1 --0--> q1
q1 --1--> q2
q2 --0--> q1
q2 --1--> q0
```

Responda:

1. Qual linguagem esse autômato parece reconhecer?
   Esse autômato reconhece a linguagem L = { w em {0,1}* | w termina com 01 }, pois o autômato somente chegará no estado final (q2) ao ter lido um 0 seguido de um 1, obrigatoriamente nesta ordem.
   
2. Execute manualmente as cadeias abaixo e diga se aceita ou rejeita:

   - `01`: (q0, 0) -> q1, (q1,  1) -> q2. Automato a aceita.
   - `101`: (q0, 1) -> q0, (q0, 0) -> q1, (q1,  1) -> q2. Automato a aceita.
   - `100`: (q0, 1) -> q0, (q0, 0) -> q1, (q1, 0) -> q1. Automato a rejeita.
   - `1101`: (q0, 1) -> q0, (q0, 1) -> q0, (q0, 0) -> q1, (q1,  1) -> q2. Automato a aceita.
   - `111`: (q0, 1) -> q0, (q0, 1) -> q0, (q0, 1) -> q0. Automato a rejeita
   
3. Monte uma tabela curta mostrando o caminho dos estados para pelo menos duas cadeias.

   "01" (aceita): 

   | (q0, 0) | -> | q1 |
   | (q1, 1) | -> | q2 |
   
   "100" (rejeita): 

   | (q0, 1) | -> | q0 |
   | (q0, 0) | -> | q1 |
   | (q1, 0) | -> | q1 |
   
## 5. Gramática

Considere a gramática:

```text
S -> aS
S -> b
```

Responda:

1. Gere cinco cadeias produzidas por essa gramática.

   É possível escrever estas cinco cadeias, produzidas pela gramática apresentada: "aa", "ab", "aab", "aaab", "a".
   
3. Descreva a linguagem em palavras.

   Pode-se escreve a linguagem gerada por essa gramática da seguinte forma: L = { w em {a,b}* | w termina em "b" e "b" aparece apenas uma vez}.
   
5. Essa gramática parece regular, livre de contexto ou outra classe? Justifique de forma simples.

   Essa linguagem parece ser regular, pois pode ser lida por um autômato finito.
   
   Por exemplo: 

      | (q0, a) | -> | q0 |
      | (q0, b) | -> | q1 |
   
   Onde q0 e q1 são os estados finais.

## 6. Ponto de dificuldade

Escolha um tópico da lista inicial e escreva:

1. o que você entende dele;

   Tópico escolhido: linguagem.
   Entendo que uma linguagem é um conjunto de cadeias em um alfabeto. Também entendo que uma linguagem regular é aquela que pode ser lida por um autômato finito.
   
3. onde você se confunde;

   Me confundo nas linguagens livres de contexto, sensíveis ao contexto e irrestritas. Não compreendo as definições de suas gramáticas e, portanto, não consigo definí-las.
   
5. que tipo de explicação ajudaria: desenho, exemplo, exercício guiado, analogia, prova passo a passo ou lista curta.

   Acredito que o que poderia auxiliar seria uma revisão da definição genérica de gramática, seguida de uma explicação das definições formais de gramática regular, livre de contexto, sensível ao contexto e irrestrita.
   Nisso, poderiam ser aplicados os métodos de "prova passo a passo" e "exemplos" e, também, "exercícios guiados" e "lista curta", para fixação.

## 7. Uso de IA, se houver

Se você usou IA depois da primeira tentativa, registre:

Não usei IA para responder as questões, mas li o livro "Linguagens Formais e Autômatos", do Menezes, e vi algumas vídeo aulas, para poder lembrar de alguns conceitos. 

```text
Pergunta feita:
Resumo da resposta:
Como eu verifiquei:
O que eu alterei na minha resposta:
O que ainda não entendi:
```

## Submissão no Moodle

Depois de finalizar, copie no Moodle:

```text
Repositório:
Commit final:
Autoavaliação: nível atual, maior dificuldade e tópico que precisa ser retomado.
```
