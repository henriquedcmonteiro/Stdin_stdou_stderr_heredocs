<h2 p align="center" > STREAMS </h2></p>

## Passo 1 - STANDARD INPUT.

<p> Geralmente STDIN é a entrada de dados pelo teclado, mas também pode ser reconhecido por <b>"0<"</b> ou apenas <b>"<" </b> que pode ser utilizado para passar arquivos como input ao invés da entrada padrão do teclado.
</p>

![Passo 1](img/Passo_1.png)

<p> Na prática é como se tivessemos feito "cat numeros", mas de forma tecnica nós passamos o valor de input que é numeros para o comando cat. </p>

![Passo 2](img/Passo_2.png)

<p> Podemos utilizar outros comandos que esperam um input como sort. </p>

![Passo 3](img/Passo_3.png)

<p> Por sua vez pode ser continuado o comando com outras estruturas como pipe, colocando os números em ordem e mostrando apenas os números de forma única do conteudo arquivo números. </p>

## Passo 2 - STANDARD OUTPUT.

<p> Podemos identificar STDOUT como <b>"1>"</b> ou <b>">"</b>, onde atráves de um input direcionamos para uma saída padrão. </p>

![Passo 4](img/Passo_4.png)

<p> STDOUT difere do STDERR que falaremos mais a frente, para reconhecer uma saída bem sucedida fora de um script podemos utilizar o comando "echo $?" logo em sequência. </p>

![Passo 5](img/Passo_5.png)

<p> Saída do comando "echo $? for "0" quer dizer que o comando foi bem sucedido e é uma saída padrão. Qualquer número diferente do 0 é uma saída de erro (STDERR). </p>

<p> Observe que usamos > para sobreescrever um arquivo e >> para adicionar algo uma linha abaixo do arquivo direcionado. </p>

![Passo 6](img/Passo_6.png)

<p> Neste exemplo a primeira vez que utilizamos o comando cat no arquivo a nossa saída abcd. </p>

<p> Podemos ver que utilizando o ">" com os valores 123 nós sobrescrevemos o conteúdo anterior do arquivo e sua nova saída com o cat é "123".</p>

<p> Já utilizando ">>" com o conteúdo abcd, podemos ver que adicionamos esse novo texto abaixo do último conteúdo existente no arquivo. E sua nova saída fica: <br>123<br>abcd<br> Esta são as diferenças utilizando > e >>. </p>

## Passo 3 - STANDARD ERROR.

<p> Qualquer saída que gere um erro é considerado STDERR. </p>

![Passo 7](img/Passo_7.png)

<p> No primeiro comando "ls" temos uma saída bem sucedida, mostrando os arquivos no diretório que estamos. </p>
<p> Agora no nosso segundo comando utilizamos uma flag que não existe "-j", nos dando uma saída de erro. </p>

![Passo 8](img/Passo_8.png)

<p> Utilizamos o 2> para redirecionar a saída de erro para um arquivo. Da mesma forma que a STDOUT, podemos usar 2> e 2>>, para sobrescrever e adicionar respectitivamente. </p>

## Passo 4 - REDIRECIONANDO SAÍDAS.

<p> No exemplo asseguir criei um simples script com o seguinte conteúdo: <br><br>
echo "Hello"<br>
ls -j<br><br>

Ao executa-lo teremos ambas as saídas, STDOUT e STDERR. </p>

![Passo 9](img/Passo_9.png)

<p> Se tentarmos redirecionar a saída como STDOUT para um arquivo, teriamos um problema. </p>

![Passo 10](img/Passo_10.png)

<p> Perceba que ao direcionar a saída do script para o arquivo saida.txt ainda continuamos com o erro em questão como output do comando, e ao utilizar o cat no arquivo saida.txt notamos que apenas a saída bem sucedida foi salva dentro dele. </p>

![Passo 11](img/Passo_11.png)

<p> Podemos ter o resutado oposto utilizando uma saida STDERR "2>", agora o conteúdo de uma saída de erro foi salvo no arquivo saidaerr.txt e a saída bem sucedida apareceu no terminal sendo a string "Hello". </p>

<p> Mas como podemos salvar ambas as saídas em um arquivo só, ou melhor salvar cada saída em seu respectitivo tipo. </p>
<p> Podemos utilizar a seguinte lógica a seguir. </p>

![Passo 12](img/Passo_12.png)

<p> Caso queira salvar ambas as saídas em um arquivo só utilizamos a seguinte estrtura: <br>
./script.sh > saida_e_saidaerr.txt, onde eu direciono o conteudo da saída bem sucedidade para o arquivo em questão e ao final da sintaxe eu estou pedindo para que a saida de erro também seja direcionada para a saída bem sucedida com o comando 2>&1. </p>

<p> Desta forma com o comando cat podemos ver que salvamos os dois tipos de saída em um arquivo só. </p>

![Passo 13](img/Passo_13.png)

<p> Utilizando > e 2> podemos direcionar cada tipo de saída para um determinado arquivo como no exemplo acima. </p>

## Passo 5 - HEREDOCS.

<p> Existem situações em que precisamos escrever scripts simples de mais de uma linha sem precisar entrar dentro de um editor de texto, podemos para isso utilizar o HereDocs. </p>

![Passo 14](img/Passo_14.png)

<p> Esta seria uma forma lenta e repetitiva de inserir linha após linha dentro de um arquivo atráves do append, o que a torna inviavel para a maioria das situações. </p>

![Passo 15](img/Passo_15.png)

<p> Utilizando o heredocs isso fica bem mais simples e dinâmico. Sua estrutura é simples. Você consegue digitar multiplas linhas utilizando o << (Heredocs), a palavra EOF vem dos primórdios da computação que significa End of file, que é uma palavra chave que indica o começo e fim da sua inserção de texto no Heredocs. <p>

<p> Agora vamos entender a funcionalidade desse comando, note que todo o input do "<<" é destinado para o comando cat que por sua vez é direcionado como uma saída padrão para o arquivo texto_heredocs. </p>

<p> Utilizando o comando cat texto_heredocs podemos ver que todo o texto foi inserido no arquivo de texto atráves desse fluxo </p>