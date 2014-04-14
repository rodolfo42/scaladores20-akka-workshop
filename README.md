## Spike com Akka

Clonado do [https://github.com/jcranky/samples/tree/master/scaladores20-akka-workshop](https://github.com/jcranky/samples/tree/master/scaladores20-akka-workshop)

Foi usado no [20o encontro dos Scaladores](http://scaladores.com.br/2013/09/23/20a-reuniao-como-foi/)

## Proposta

- Parte 1:
 - Main
  - criar DataSplitterActor
  - enviar mensagem requisitando processamento de dados (com nome do arquivo)
  - aguardar resultado, que deverá ser um mapa com "estado -> valor"

 - DataSplitterActor
  - ler informações sobre o arquivo / dados a serem processados
  - dividir pedaços a serem processados separadamente, por estado
  - enviar informações sobre os pedaços a atores filhos
  - os filhos deverão devolver a soma dos valores repassados às cidades do estado
  - quando receber todas as respostas, devolver resultado agregado ao sender
  
 - DataPieceSmasherActor
  - receber trechos a serem processados
  - calcular soma dos valores de repasse às cidades
  - devolver resultado ao sender


- Parte 2:  
*dica: o Scheduler do Akka vai ser útil nas tarefas abaixo*
  - no DataSmasher, criar timeout para verificar se um resultado foi obtido, para tentar denovo se for o caso
  - fazer a mesma coisa no splitter, para verificar se foi recebido o resultado de cada estado

- Parte 3:
  - alterar main para requisitar dados de todos os anos
  - alterar processo de verificação para garantir que foram recebidos os resultados de todos os anos
