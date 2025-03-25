Explicação do código:
Inicialização do Tabuleiro:

O tabuleiro de 10x10 é inicializado com 0s, representando água. O tabuleiro pode ser alterado com os navios e áreas afetadas pelas habilidades.

Posicionamento dos Navios:

Dois navios são posicionados, um horizontalmente e outro verticalmente, utilizando funções posicionarNavioHorizontal e posicionarNavioVertical.

Criação das Matrizes de Habilidade:

Três matrizes representam as áreas de efeito das habilidades:

Cone: Representa uma área de efeito que se expande para baixo em forma de cone.

Cruz: Representa uma área de efeito em forma de cruz.

Octaedro: Representa uma área de efeito em forma de losango (octaedro visto de frente).

Aplicação das Habilidades:

A função aplicarHabilidade coloca as áreas de efeito sobre o tabuleiro, com o valor 5 marcando as áreas afetadas pelas habilidades. O ponto de origem das habilidades é especificado diretamente no código.

Exibição do Tabuleiro:

A função exibirTabuleiro imprime o tabuleiro na tela com diferentes símbolos: 0 para água, 3 para navios e 5 para áreas afetadas pelas habilidades.

Resultado esperado:
Ao rodar o programa, você verá o tabuleiro com os navios posicionados e as áreas afetadas pelas habilidades representadas como 5s no console. Cada habilidade terá sua área de efeito aplicada corretamente, com base no ponto de origem especificado.
