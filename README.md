# Resolvendo o Termo com Álgebra Linear Computacional

## Visão Geral

Este projeto apresenta uma solução para o popular jogo de palavras [Termo](https://term.ooo/) (a versão em português do Wordle) utilizando a Decomposição em Valores Singulares (SVD), um conceito de Álgebra Linear. O objetivo é, a partir de um dicionário de palavras de 5 letras, fornecer ao jogador os melhores palpites para adivinhar a palavra secreta.

## Metodologia

A estratégia principal se baseia no artigo *Rank One Approximation as a Strategy for Wordle* de Michael Bonthron. A metodologia consiste em:

1.  **Construção do Espaço de Palpites:**
    * É utilizada uma lista de palavras de 5 letras da língua portuguesa (`palavrasde5letras.txt`).
    * Cada palavra é convertida em um vetor de 130 dimensões. Este vetor representa a presença de cada uma das 26 letras do alfabeto em cada uma das 5 posições da palavra.
    * Uma matriz `A` é criada, onde cada coluna corresponde a uma palavra do dicionário.

2.  **Aproximação e Sugestão de Palpites:**
    * A Decomposição em Valores Singulares (SVD) é aplicada à matriz `A`.
    * O primeiro vetor singular à esquerda (`u1`) é usado como uma aproximação do espaço de palavras. A palavra do dicionário que mais se aproxima desse vetor (medido pelo cosseno do ângulo entre os vetores) é o melhor palpite inicial.
    * Após cada palpite, a matriz `A` é atualizada para eliminar palavras que não são mais possíveis, com base nas cores (verde, amarelo, cinza) retornadas pelo jogo.
    * O processo de SVD e sugestão de palpites é repetido com a matriz reduzida até que a palavra correta seja encontrada.

## Como Executar

O projeto está contido no notebook Jupyter `Projeto1Finalizado.ipynb`. Para executá-lo:

1.  Certifique-se de ter o arquivo `palavrasde5letras.txt` no mesmo diretório do notebook.
2.  Abra o `Projeto1Finalizado.ipynb` em um ambiente Jupyter.
3.  Execute as células de código em ordem. A última célula irá iniciar um loop interativo no terminal para jogar o jogo.
4.  Siga as instruções no terminal:
    * Use um dos 5 palpites iniciais sugeridos.
    * Após a tentativa no [site do Termo](https://term.ooo/), informe a palavra que você usou e as cores retornadas para cada letra ('v' para verde, 'a' para amarelo e 'c' para cinza).
    * O programa irá fornecer uma nova lista de palpites sugeridos com base nas informações fornecidas.
    * Repita o processo até adivinhar a palavra.

## Dependências

* Python 3
* NumPy
* Jupyter Notebook

## Referências

* **Artigo Principal:** Bonthron, Michael. [*Rank One Approximation as a Strategy for Wordle*](https://arxiv.org/abs/2204.06324).
* **Vídeo 3Blue1Brown:** Uma abordagem mais sofisticada para resolver o Termo pode ser encontrada no vídeo do canal 3Blue1Brown: [Solving Wordle using information theory](https://www.youtube.com/watch?v=v68zYyaEmEA).
* **Aproximação de Posto Baixo:** Para uma explicação sobre o teorema da aproximação de posto baixo, assista: [Low-Rank Approximation (PCA)](https://www.youtube.com/watch?v=12K5aydB9cQ).
