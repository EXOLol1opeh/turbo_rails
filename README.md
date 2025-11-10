BDD com Cucumber
================


Nesta tarefa você vai escrever histórias de usuário descrevendo um recurso de um aplicativo, transformar essas histórias em testes de aceitação executáveis com o Cucumber e rodar os testes contra a aplicação.

Especificamente, você vai escrever cenários que cobrem os caminhos felizes das três partes da tarefa anterior, na qual foi acrescentado filtro e ordenação à tela de listagem de filmes.

O código em `rottenpotatoes` traz uma solução de referência da tarefa anterior, além do esqueleto necessário para os primeiros cenários.

Crie um repositório e comece enviando esse esqueleto. Recomendo um commit a cada parte que funcionar. Como ajuda extra, o controle de versão permite marcar commits com nomes simbólicos: logo após um commit, dá para marcar aquele ponto e, depois, comparar o estado atual com ele usando o nome, sem decorar o identificador. Lembre que, para enviar as marcações ao repositório remoto, existe um comando específico de envio de etiquetas. Servidores de deploy ignoram etiquetas.

**Parte 1: criar um passo declarativo para cadastrar filmes**

O objetivo do desenvolvimento guiado por comportamento é expressar tarefas de comportamento, e não operações de baixo nível.

O pano de fundo de todos os cenários exige que o banco tenha alguns filmes. Seria contra a proposta escrever cenários detalhando cada interação necessária para cadastrar um filme, já que cadastrar filmes não é o assunto desses cenários.

Lembre que os passos iniciais de uma história descrevem o estado do sistema: não importa como ele chegou lá. Então, na parte 1, você vai criar uma definição de passo que corresponda ao passo do bloco de contexto presente nos dois arquivos de funcionalidade. (Adiante no curso será mostrado como evitar repetição desses blocos.)

Escreva o código no arquivo de definições de passo. Pode usar chamadas diretas da camada de persistência para inserir filmes no banco; ignorar a interface de cadastro é aceitável aqui, porque não é isso que os cenários testam.

Sucesso é quando todos os passos de contexto dos cenários dos dois arquivos estiverem verdes.

**Parte 2: caminhos felizes do filtro de filmes**

1. Complete o cenário de restringir a filmes com as classificações indicadas, no arquivo de filtro. Você pode usar definições de passo existentes para marcar e desmarcar caixas, enviar o formulário e conferir se os filmes corretos aparecem — e, tão importante quanto, se os filmes com outras classificações não aparecem.

2. Como é chato repetir o passo de marcar cada caixa, crie uma definição que corresponda a um passo único informando as classificações desejadas. Essa definição deve marcar só as caixas indicadas e deixar as demais como estavam. Dica: ela pode reaproveitar os passos existentes.

3. No cenário de todas as classificações marcadas, seria chato usar uma verificação por filme. Isso atrapalharia o objetivo de expressar a intenção do usuário. Para resolver, crie uma definição que corresponda ao passo de ver todos os filmes, com a dica de contar as linhas da tabela e comparar com o valor esperado, falhando o teste quando não bater. Atualização: não é mais preciso implementar o cenário sem classificação selecionada.

4. Use as novas definições para completar o cenário. Sucesso é quando todos os cenários do arquivo de filtro passarem com todos os passos verdes.

**Parte 3: caminhos felizes da ordenação por título e por data**

1. Como os cenários de ordenação precisam verificar posição relativa, crie uma definição que corresponda a um passo que afirma que um filme aparece antes de outro na listagem.

### DICAS

  * A biblioteca de teste de página devolve um objeto que representa a página entregue pelo servidor. Com ele dá para fazer verificações de conteúdo e, mais importante, buscar elementos por seletores CSS ou expressões de caminho.
  * O corpo da página pode ser lido como uma única string.
  * Uma expressão regular consegue capturar se um texto aparece antes de outro numa string maior, mas não é a única estratégia.

2. Use a definição criada para completar os cenários de ordem alfabética e de ordem crescente de data de lançamento.

**SUCESSO** é todos os passos de todos os cenários dos dois arquivos ficarem verdes.

**Entrega**

Envie um arquivo compactado contendo apenas a pasta de funcionalidades. Em ambiente unix, estando na raiz da aplicação, use o comando de compactação apontando para essa pasta.

Garanta que a pasta apareça dentro do arquivo: ao descompactar, deve ser criada uma pasta com esse nome no diretório atual, e não os arquivos soltos.