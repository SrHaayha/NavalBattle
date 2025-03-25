@@ -0,0 +1,147 @@
#include <stdio.h>

#define TAMANHO_TABULEIRO 10
#define TAMANHO_NAVIO 3
#define TAMANHO_HABILIDADE 5

// Função para inicializar o tabuleiro com 0 (representando água)
void inicializarTabuleiro(int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO]) {
    for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
        for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
            tabuleiro[i][j] = 0;
        }
    }
}

// Função para exibir o tabuleiro
void exibirTabuleiro(int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO]) {
    for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
        for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
            if (tabuleiro[i][j] == 0) {
                printf(" 0 "); // Água
            } else if (tabuleiro[i][j] == 3) {
                printf(" 3 "); // Navio
            } else if (tabuleiro[i][j] == 5) {
                printf(" 5 "); // Área afetada pela habilidade
            }
        }
        printf("\n");
    }
}

// Função para posicionar um navio horizontalmente
int posicionarNavioHorizontal(int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO], int linha, int coluna) {
    if (coluna + TAMANHO_NAVIO <= TAMANHO_TABULEIRO) {
        for (int i = 0; i < TAMANHO_NAVIO; i++) {
            if (tabuleiro[linha][coluna + i] != 0) {
                return 0;
            }
            tabuleiro[linha][coluna + i] = 3;
        }
        return 1;
    }
    return 0;
}

// Função para posicionar um navio verticalmente
int posicionarNavioVertical(int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO], int linha, int coluna) {
    if (linha + TAMANHO_NAVIO <= TAMANHO_TABULEIRO) {
        for (int i = 0; i < TAMANHO_NAVIO; i++) {
            if (tabuleiro[linha + i][coluna] != 0) {
                return 0;
            }
            tabuleiro[linha + i][coluna] = 3;
        }
        return 1;
    }
    return 0;
}

// Função para criar a área de efeito do Cone
void gerarHabilidadeCone(int habilidade[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE]) {
    int meio = TAMANHO_HABILIDADE / 2;
    for (int i = 0; i < TAMANHO_HABILIDADE; i++) {
        for (int j = 0; j < TAMANHO_HABILIDADE; j++) {
            if (i >= j && i + j <= TAMANHO_HABILIDADE - 1) {
                habilidade[i][j] = 1;
            } else {
                habilidade[i][j] = 0;
            }
        }
    }
}

// Função para criar a área de efeito da Cruz
void gerarHabilidadeCruz(int habilidade[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE]) {
    int meio = TAMANHO_HABILIDADE / 2;
    for (int i = 0; i < TAMANHO_HABILIDADE; i++) {
        for (int j = 0; j < TAMANHO_HABILIDADE; j++) {
            if (i == meio || j == meio) {
                habilidade[i][j] = 1;
            } else {
                habilidade[i][j] = 0;
            }
        }
    }
}

// Função para criar a área de efeito do Octaedro
void gerarHabilidadeOctaedro(int habilidade[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE]) {
    int meio = TAMANHO_HABILIDADE / 2;
    for (int i = 0; i < TAMANHO_HABILIDADE; i++) {
        for (int j = 0; j < TAMANHO_HABILIDADE; j++) {
            if (i + j >= meio && i + j <= TAMANHO_HABILIDADE + meio - 1) {
                habilidade[i][j] = 1;
            } else {
                habilidade[i][j] = 0;
            }
        }
    }
}

// Função para aplicar uma habilidade no tabuleiro
void aplicarHabilidade(int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO], int habilidade[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE], int linhaOrigem, int colunaOrigem) {
    for (int i = 0; i < TAMANHO_HABILIDADE; i++) {
        for (int j = 0; j < TAMANHO_HABILIDADE; j++) {
            int linhaTabuleiro = linhaOrigem + i - TAMANHO_HABILIDADE / 2;
            int colunaTabuleiro = colunaOrigem + j - TAMANHO_HABILIDADE / 2;

            if (linhaTabuleiro >= 0 && linhaTabuleiro < TAMANHO_TABULEIRO && colunaTabuleiro >= 0 && colunaTabuleiro < TAMANHO_TABULEIRO) {
                if (habilidade[i][j] == 1) {
                    tabuleiro[linhaTabuleiro][colunaTabuleiro] = 5; // Marca as áreas afetadas pela habilidade
                }
            }
        }
    }
}

// Função principal
int main() {
    int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO];
    int habilidadeCone[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE];
    int habilidadeCruz[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE];
    int habilidadeOctaedro[TAMANHO_HABILIDADE][TAMANHO_HABILIDADE];

    // Inicializar o tabuleiro com 0
    inicializarTabuleiro(tabuleiro);

    // Posicionar alguns navios
    posicionarNavioHorizontal(tabuleiro, 2, 3);
    posicionarNavioVertical(tabuleiro, 5, 7);

    // Gerar as matrizes de habilidades
    gerarHabilidadeCone(habilidadeCone);
    gerarHabilidadeCruz(habilidadeCruz);
    gerarHabilidadeOctaedro(habilidadeOctaedro);

    // Aplicar habilidades no tabuleiro
    aplicarHabilidade(tabuleiro, habilidadeCone, 3, 3);    // Ponto de origem do Cone
    aplicarHabilidade(tabuleiro, habilidadeCruz, 5, 5);    // Ponto de origem da Cruz
    aplicarHabilidade(tabuleiro, habilidadeOctaedro, 7, 7); // Ponto de origem do Octaedro

    // Exibir o tabuleiro com navios e habilidades aplicadas
    printf("Tabuleiro com Habilidades Aplicadas:\n");
    exibirTabuleiro(tabuleiro);

    return 0;
}
