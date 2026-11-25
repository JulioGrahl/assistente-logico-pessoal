# Assistente Lógico Pessoal

> Atividade da disciplina Linguagem de Programação e Paradigmas · UNIDAVI · 2026/2

**Aluno(a):** Julio Max Grahl
**Linguagem do sistema:** Python

## O que é

Uma base de conhecimento em Prolog (`meus_dados.pl`) com fatos e regras sobre mim e um assistente em linha de comando que consulta essa base pela ponte (`prolog.py`).

## Como executar

Requisitos: SWI-Prolog no PATH e Python 3.

```bash
# testar a ponte
python teste_ponte.py      # no Windows, também: py teste_ponte.py

# executar o assistente
python assistente.py       # no Windows, também: py assistente.py
```

## Minha base

- Fatos: `eu/1`, `cursa/3`, `compromisso/3`, `sabe/2`, `gosta/2`
- Regras: `ocupado/2`, `livre/2`, `o_que_faco/3`, `pode_ensinar/1`, `dia_cheio/1` e a minha regra abaixo

## Minha regra (R6)

```prolog
horario_para_estudar(Linguagem, Dia, Turno) :-
    sabe(Linguagem, basico),
    livre(Dia, Turno).
```

**O que ela significa:** indica quando posso estudar uma linguagem que ainda preciso melhorar. O primeiro subobjetivo (`sabe`) seleciona as linguagens em que estou no nível básico, e o segundo (`livre`) encontra os dias e turnos sem aula ou compromisso.

## Saída real do assistente

Trechos de uma execução (o menu repetido foi omitido, indicado por `[...]`):

```text
PS C:\Users\windows 10\Downloads\lpp\assistente-logico-pessoal> py assistente.py

=== Assistente pessoal de julio ===
1. Minhas disciplinas
2. Agenda de um dia
3. Horários livres
4. Estou livre em...?
5. Linguagens que posso ensinar
6. Meus gostos por categoria
7. Dias cheios
8. Horários para estudar (minha regra)
0. Sair
> 2
Qual dia? (segunda, terca, quarta, quinta, sexta, sabado): segunda

== Agenda de segunda ==
  - noite: redes
  - manha: trabalho
  - tarde: trabalho
[...]
> 4
Dia: sabado
Turno (manha, tarde, noite): tarde

Sim! sabado de tarde está livre.
[...]
> 8

== Horários para estudar ==
  - javascript: sabado de tarde
[...]
> 2
Qual dia? (segunda, terca, quarta, quinta, sexta, sabado): seg unda!
Ops: Digite só letras minúsculas, números e _ (sem acento).
[...]
> 0
Até mais!
```
