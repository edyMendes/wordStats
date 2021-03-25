# wordStats

                                         Sistemas Operativos I
                                      ENGENHARIA INFORMÁTICA (EI)

                                   Projeto - script bash wordStats.sh

1 - Introdução

  Pretende-se que elabore o script wordStats.sh. O script destina-se a ser executado através da shell bash, no ambiente Linux da máquina virtual disponibilizada para a UC de Sistemas Operativos.
  O script wordStats.sh destina-se a produzir um conteúdo de texto, produzindo análise estatística e resultados gráficos sobre esse mesmo conteúdo. A análise estatística deve incluir:
  - listagem de todas as palavras ordenadas pela respectiva frequência de ocorrência;
  - Criação de uma página HTML e de um gráfico de barras referente ao número de ocorrência das N palavras mais frequentes.

2 - Visão geral

  O funcionamento do script wordStats.sh é muito simples: 
  1. Receção do conteúdo a processar (ficheiro de texto ou PDF, sendo que o PDF deve ser convertido 
pelo script em texto);
  2. Processamento do conteúdo e criação de resultados;
  3. Apresentação dos resultados.

3 - Stop-words

  Quando se efetua a análise de textos é comum retirar as palavras de ligação, como os artigos in/definidos (um, uns, uma, umas, o, a, os, as, etc.) e afins. A designação Anglo-Saxónica para essas palavras é stop-words, sendo que, obviamente, as stop-words variam consoante as línguas. Os ficheiros de stop-words para a língua portuguesa e inglesa encontram-se no Moodle. 
  O script wordStats.sh deve estar preparado para funcionar com ou sem stop-words, cabendo ao utilizador especificar o modo pretendido, conforme descrito na secção seguinte. Os ficheiros de stop-words a serem considerados pelo script deve estar no subdiretório StopWords do diretório onde se localiza o script wordStats.sh.

4 - Modos de operação e formatos de saída 

  O wordStats.sh tem três modos de operação: c/C (count), p/P (plot) e t/T (top). Os comandos em minúsculas (c, p ou t) indicam que se pretende utilizar o modo de remoção stop-words, ao passo que a especificação de um comando com letra maiúscula (C, P ou T) analisa todas as palavras do ficheiro indicado pelo utilizador. Seguidamente, são descritos esses modos de operação, bem como os respetivos formatos de saída. 
  O modo é especificado através de uma das seguintes letras na linha de comando:
  
  -Modo c/C: o script efetua a contagem (C=count) de ocorrências de cada palavra, guardando a lista ordenada de forma crescente num ficheiro de texto. O nome do ficheiro corresponde ao nome do recurso de entrada acrescentado com o prefixo “result---“. Por exemplo, caso o recurso de entrada seja “a.txt”, o ficheiro de resultado chamar-se-á “result---a.txt”. Caso já exista um ficheiro com o mesmo nome do ficheiro de saída, o ficheiro existente é substituído pelo novo ficheiro. 

  -Modo p/P: o script efetua a contagem de ocorrências de cada palavra, produzindo um gráfico (P=plot) de barras com as N palavras que ocorrem com maior frequência. O gráfico é guardado num ficheiro PNG, cujo nome segue as regras definidas para o modo c/C (prefixado com “result---" e reescrito caso já exista). Para apresentação do gráfico (ficheiro PNG), deve ser criado um ficheiro HTML cujo nome obedece às mesmas regras do ficheiro PNG. Neste modo o script deve mostrar o ficheiro PNG do gráfico antes de terminar. O valor de N é definido pela variável do ambiente WORD_STATS_TOP. Caso essa variável não se encontre definida ou não corresponda a um número, deve ter assumido para N o valor 10.
 
  - Modo t/T: o script efetua a contagem de ocorrências de cada palavra mostrando na saída padrão do terminal o “Top” das palavras, isto é, as N palavras que ocorrem com maior frequência. De forma similar aos restantes comandos, é criado um ficheiro de texto com os resultados. O ficheiro segue as mesmas regras de nome definida para os outros modos. Similarmente, o valor de N segue as mesmas regras do que o indicado para o modo p/P.

5 - Parâmetros da linha de comando

  A sintaxe do script wordStats.sh é a seguinte:

  wordStats.sh <MODE> <INPUT> <ISO3166>

  Cada elemento deve obedecer às seguintes regras:
  - <MODE> é um dos possíveis três modos, isto é, c/C, p/P ou t/T. Caso não seja especificado um desses modos, o script deve terminar, com uma apropriada mensagem de erro (ver Secção 6 - - Exemplos de uso). 
  - <INPUT> corresponde ao nome de um ficheiro local em formato TXT ou PDF.
  - <ISO3166> corresponde ao código que indica qual a língua em que se encontram o conteúdo especificado pelo parâmetro INPUT. Os valores suportados são ‘pt’ e ‘en’, respetivamente para português e inglês. Este parâmetro é opcional, sendo que quando não é especificado, deve assumir-se que o conteúdo está em língua inglesa.

6 - Exemplos de uso

  NOTA:
  i) Nos exemplos seguintes ficha01.pdf corresponde ao ficheiro PDF da 1ª ficha prática da UC;
  ii) Os resultados (top, contagem de palavras, etc.) podem diferir consoante a metodologia seguida (por exemplo, incluir ou não, um número como 2021 na listagem de palavras, etc.). Assim, caso os resultados uma implementação sejam (ligeiramente) diferentes dos aqui apresentados, não significa que a implementação esteja errada.

Exemplo 1 – modo “c”
./word_stats.sh c ficha01.pdf pt
'ficha01.pdf': PDF file
[INFO] Processing 'ficha01.pdf.txt'
STOP WORDS will be filtered out
StopWords file 'pt': 'StopWords/pt.stop_words.txt' (205 words)
COUNT MODE
 1    73    diretoria
 2    64    ficheiro
 3    61    comando
 4    37    utilizador
 5    34    ficheiros
 6    33    comandos
 7    32    sistema
(…)
RESULTS: 'result---ficha01.pdf.txt'
-rw-rw-r-- 1 user user 15479 Mar 10 23:14 result---ficha01.pdf.txt
912 distinct words
























