# Desafio-batalha-naval-
Aluno: Mateus Borges de Souza //// Matricula : 202405315049


import random

# Inicializa o tabuleiro
def criar_tabuleiro(tamanho):
    return [["~"] * tamanho for _ in range(tamanho)]

# Exibe o tabuleiro
def mostrar_tabuleiro(tabuleiro):
    for linha in tabuleiro:
        print(" ".join(linha))

# Gera posição aleatória do navio
def gerar_navio(tamanho):
    linha = random.randint(0, tamanho - 1)
    coluna = random.randint(0, tamanho - 1)
    return (linha, coluna)

# Começa o jogo
def jogar_batalha_naval():
    tamanho = 5
    tabuleiro = criar_tabuleiro(tamanho)
    navio = gerar_navio(tamanho)
    tentativas = 5

    print("🌊 Bem-vindo ao Batalha Naval!")
    print("Você tem", tentativas, "tentativas para acertar o navio.\n")

    while tentativas > 0:
        mostrar_tabuleiro(tabuleiro)
        try:
            linha = int(input("Adivinhe a linha (0 a 4): "))
            coluna = int(input("Adivinhe a coluna (0 a 4): "))
        except ValueError:
            print("Digite números válidos!")
            continue

        if (linha, coluna) == navio:
            tabuleiro[linha][coluna] = "X"
            print("\n💥 Você acertou o navio! Parabéns!\n")
            break
        else:
            tabuleiro[linha][coluna] = "O"
            tentativas -= 1
            print("\n❌ Nada aqui! Tentativas restantes:", tentativas)

    if tentativas == 0:
        print("\n😢 Fim de jogo. O navio estava em:", navio)

    mostrar_tabuleiro(tabuleiro)

jogar_batalha_naval()

