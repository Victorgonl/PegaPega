# Pega-Pega

<p style="font-size: 20px";>Universidade Federal de Lavras</p>

<p style="font-size: 16px";>GCC128 - Inteligência Artificial - 2023/1</p>

Professor: Eric Fernandes de Mello Araújo

Aluno: Victor Gonçalves Lima

Matrícula: 202020775

Turma: 10A

## WHAT IS IT?

Este modelo tem como objetivo simular o comportamento de crianças no tradicional jogo de *Pega-Pega*. O jogo consiste em crianças correndo em um campo fechado com obstáculos que elas não devem ser capazes de atravessar. Uma das crianças será escolhida como a pegadora, que irá perseguir as outras crianças. Quando uma criança é pega, ela se torna a pegadora e passa a perseguir as crianças. A simulação termina quando todas as crianças esgotam sua energia.

## HOW IT WORKS

Após a criação do cenário com os obstáculos, as crianças são colocadas no campo e uma delas é selecionada aleatoriamente como a `pegadora`. Dessa forma, as crianças da simulação poderão se comportar de duas maneiras diferentes: `fugir` ou `perseguir`.

As crianças que fogem possuem seu comportamento variando de acordo com a distância que elas estão do pegador. Existe um limite definido como a `distância de segurança`, que se refere a distância que a criança está do pegador para começar a se movimentar (de forma aleatória) pelo campo. Já um outro limite inferior definido como a `distância para fugir`, é o limiar que faz com que uma criança esteja de fato fugindo do pegador, definindo seu sentido para `correr` na direção oposta do mesmo. As crianças que estão em uma distância de segurança irão ficar paradas e, opcionalmente `descansando`, o que recupera sua energia que é cada sempre ao correr.

Uma criança pegadora irá sempre estar perseguindo uma criança não `imune` mais próxima dela. Por estar sempre correndo, nunca estará descansando, sendo assim a criança pegadora será a mais provável de esgotar sua energia e sair da brincadeira. Quando uma pegadora sai, outra criança entra em seu lugar como a pegadora, que reinicia a brincadeira e garante que haverá um fim na simulação com o esgotamento de todas as crianças.

As velocidades em que as crianças fogem são diretamente proporcinais com seu próprio atributo de `velocidade`, que é decidido aleatoriamente entre os parâmetros de `velocidade mínima` e `velocidade máxima`, e sua `energia`, que diminuem toda vez em que elas se movimentam.

Sempre que uma criança pegadora `pegar` outra criança, a última passa a ser a nova pegadora e a ex-pegadora se torna imune, o que significa que a pegadora atual não irá perseguí-la. A criança deixa de ser imune quando uma nova criança é pega, passando sua imunidade adiante. A imunidade garante que duas crianças não fiquem pegando uma a outra até a exaustão por estarem tão próximas.

Seguindo estas regras, o final da simulação é previsto com duas crianças sobrando no campo, uma sendo a pegadora e outra imune.

## HOW TO USE IT

É recomendado seguir as seguintes configurações:

- `multiplos-pegadores`: false

- `velocidade-minima`: 0.3

- `velocidade-maxima`: 0.3

- `numero-arvores`: 4

- `numero-paredes`: 3

- `tamanho-campo`: 25

- `numero-criancas`: 20

- `descansar?`: on

Após ajustadas, utilizar `SETUP` para criar o ambiente de simulação e `GO!` para iniciá-la.

A simulação irá parar quando todas as crianças esgotarem suas energias.

**OBSERVAÇÃO:** A geração aleatória de obstáculos (muros e árvores) pode resultar em objetos renderizados fora de áreas vazias.

## THINGS TO NOTICE

É possível perceber que o estado de pegador é o que mais gasta energia das crianças, por estar em constante movimento, desta maneira a criança pegadora ficará mais lenta, causando uma inevitável exaustão por não conseguir pegar outras crianças.

O jogo tem uma tendência de ir "esfriando" quando uma pegadora não é capaz de pegar outras crianças e "quente" quando uma nova pegadora é selecionada, onde as crianças estarão mais descansadas e consequentemente correndo mais rápido.

## THINGS TO TRY

É interessante ajustar os parâmetros disponíveis a fim de ver como as crianças se comportam em variáveis velocidades, tamanhos de campo e número de obstáculos no caminho.

## EXTENDING THE MODEL

O modelo tem grandes capacidades para melhorias e novos recursos.

Entre as possíveis melhorias, podemos citar:

- o comportamento das crianças perto dos obstáculos, que muitas vezes as deixam presas para fugir ou perseguir;

- o comportamento de fugir não tratar de decidir um caminho em grafo para tentar escapar;

- o comportamento da pegadora não traçar um caminho em grafo e ficar preso quando seu alvo está atrás de um obstáculo;

- a geração de obstáculos não tratar de sobrepor outros obstáculos;

- adicionar mais parâmetros configuráveis na interface do modelo.

O modelo também dá início a uma variação da simulação onde os pegadores são acumulados, levando ao jogo terminar quando todas as crianças são pegas. Está variação pode ser melhorada a fim de garantir um jogo mais competitivo.

Outra ideia de variação é uma simulação onde os jogadores pegos saem do jogo, o que mudaria a dinâmica de como as crianças se comportariam, já que se tornaria um jogo de múltiplas crianças VS uma criança pegadora.

## NETLOGO FEATURES

O modelo usa apenas um tipo de `turtle`, que podem variar suas características durante a simulação para decidir os comportamentos das crianças, assim como suas representações vizuais.

O modelo também manipula os `patches` a fim de simular um `obstáculo`, e varia suas cores para diferenciar `muros` e `arvores`.

No código é utilizado:

- `min-one-of` para selecionar a criança mais próxima do pegador;

- `one-of turtles with` para selecionar crianças com características específicas como `pegadora?` ou `imune?`;

- `patches in-radius` para saber se existe um obstáculo no ao redor de uma crinaça;

- `one-of other` para selecionar outra criança direfente da atual.

## RELATED MODELS

Dois modelos do `Models Library` do NetLogo da sessão `Code Examples` foram utilizados para auxiliar na implementação:

- `Bounce Example`: para entender a movimentação e reação das turtles próxima a paredes;

- `Look Ahead Example`: para entender como as turtles devem reagir com osbtáculos a frente.

## REFERENCES

- Wilensky, U. (1999). NetLogo. http://ccl.northwestern.edu/netlogo/. Center for Connected Learning and Computer-Based Modeling, Northwestern University, Evanston, IL.

- Wikipedia. Tag (game). Disponível em: https://wikipedia.org/wiki/Tag_(game). Acesso em: 24 jun. 2023.