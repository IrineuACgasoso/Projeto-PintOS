Você é avaliado pela proporção de testes que passam, só os de alarm-* e mlfqs-*. Os testes priority-* falham de propósito e não contam.
Compilar: cd src/threads && make
Rodar tudo: cd build && make check
Rodar um teste só: make tests/threads/alarm-multiple.result (ou pintos --qemu -- run alarm-multiple)
Antes de começar, no Make.vars troque SIMULATOR = --bochs por --qemu. Sem isso, quase tudo falha.


Rodar um teste específico (de dentro de src/threads/build):

make tests/threads/alarm-multiple.result


Rodar o PintOS com o escalonador MLFQS ativado (você vai usar quando começar a Tarefa 2):

pintos --qemu -- -q -mlfqs run mlfqs-load-1


Você não precisa rodar make check inteiro a cada mudança. Use só os testes que importam, de dentro de src/threads/build:

# Alarm Clock
make tests/threads/alarm-single.result
make tests/threads/alarm-multiple.result
make tests/threads/alarm-simultaneous.result
make tests/threads/alarm-zero.result
make tests/threads/alarm-negative.result

# MLFQS (um por vez, são lentos)
make tests/threads/mlfqs-load-1.result