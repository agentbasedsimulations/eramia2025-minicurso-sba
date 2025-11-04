# Roteiro Minicurso NetLogo

## Introdução do NetLogo

### Primeiramente, o que é o NetLogo?

- NetLogo se trata de um software de modelagem de ambiente programável para simular fenômenos sociais e naturais, este software está sedo desenvolvido desde 1999 por Uri Wilensky.
- Ele foi desenvolvido com o objetivo em mente de ser necessário baixo conhecimento prévio sobre esse tipos de softwares mas que possui um grande leque de possibilidades para serem feitos na ferramenta (Low threshold, High ceiling), permitindo com que pessoas de diferentes níveis de conhecimento consigam utilizar a ferramenta, mas ainda permitindo que seja feito modelos avançados.

### Como ele funciona?

- Os desenvolvedores conseguem dar instruções para centenas ou milhares de “agentes” operando de forma independente. Isso torna possível a exploração de conexões entre indivíduos em nível microscópico e o padrão de suas interações em um nível macroscópico.
- A ferramenta permite que seja utilizado tanto modelos já criados, estes que ficam armazenados na biblioteca de modelos, quando criar o seu próprios modelos.

### Características Adicionais

- Open Source
- Totalmente Programável
- Pode ser usada com API’s

## Fundamentos do NetLogo

Para começar a aprender a utilizar a ferramenta NetLogo primeiro será necessário aprender alguns conceitos básicos e fundamentos da ferramenta. O mundo do NetLogo e habitado por Agentes, cujos esses são seres que conseguem seguir instruções.

Dentro do NetLogo há 4 tipos de Agentes;

1. Turtles
2. Patches
3. Links
4. Observer

### 1. Turtles

Se tratam dos objetos que irão se movimentar pelo mundo, podendo conter diversas “raças” com características e atributos diferentes.

### 2. Patches

Se trata de cada quadrado de “chão” da simulação, e por nela em que é habitado as Turtles. Patches são divididos uniformemente em uma “grade” 

### 3. Links

Se tratam de agentes com o intuito de conectar duas Turtles, não pode ser usado com Patches.

### 4. Observer

Se trata do comandante da simulação, ele não possui forma física na simulação, e é ele que envia as “ordens” para os outros agentes

### Interface do NetLogo

Dentro da ferramenta, encontramos três abas principais, sendo elas;

- Interface
    - Visualizar a simulação
    - Criar botões, deslizadores e outros itens
    - Interagir com os itens agregados ao modelo
    - Alterar no tipo de atualização e velocidade da simualção
- Informações
    - Servir como um ReadMe do modelo
    - Poder conter informações essências de como funciona a simulação, o que cada variável faz, entre outros
- Código
    - Onde é realizado de fato a programação da simulação

### Programação em NetLogo

A programação no NetLogo é bem simples para pessoas que já possuem algum tipo de conhecimento básico em programação. Para começar a explicar o básico da programação em NetLogo é necessário saber alguns conceitos

- Comandos
- Repórteres
- Procedimentos

### 1. Comandos

Se tratam das ações que você irá comandar para o programa fazer, eles possuem a função de mandar algum agente realizar alguma ação. 

<aside>
💡

Alguns comandos bem conhecidos são: create, die, hatch, foward, reset, entre outros.

ex:

`create-turtles 50`

`reset-ticks`

`forward 1`

</aside>

### 2. Repórteres

Similar aos comandos, ele possui a função de calcular e retornar algum tipo de valor/agente para ser realizado alguma ação/verificação

<aside>
💡

Alguns repórteres bem conhecidos são: random, patches, ticks, any?, with 

ex:

`ask patches`

`setxy random-xcor random-ycor`

`if any? turtles-here with [ color = green ]`

</aside>

### 3. Procedimentos

Os exemplos demonstrados agora se tratam de comandos e repórteres já criados pela ferramenta, por isso são chamados de comandos/repórteres primitivos. É possível também criar novos comandos e repórteres e modelar eles ao seu ver, esses são chamados de Procedimentos.

Um simples exemplo disso seria um procedimento de preparação de uma simulação (setup) e de partida (go), segue aqui um exemplo de procedimento criado por usuário.

Para começar um procedimento de comando é necessário começar com a palavra to e o nome do procedimento, e ao final do procedimento de comando escrever end

<aside>
💡

ex:

`to setup`

`clear-all`

`…`

`reset-ticks`

`end`

`to go`

`…`

`tick`

`end`

`clear-all`: Serve para limpar qualquer alteração feita em patches, turtles criadas, entre outros. Faz um reset na simulação

`reset-ticks`: Zera o contador de ticks.

`tick`: São uma medida de ‘tempo’ dentro da simulação, a cada tick que é avançado a simulação roda todos os seus comandos (dependendo do tipo de taxa de atualização só sendo de uma vez só ou continuamente)

</aside>

### 4. Documentação

A ferramenta do NetLogo possui uma documentação completa com todos os comandos, primitivas e reporters nativos da ferramenta. Caso desejem aprender novos comandos ou entender de forma mais aprofundada algum conhecimento basta entrar no site do NetLogo.

Link do Dicionário (Versão 6.3): [NetLogo 6.3.0 User Manual: NetLogo Dictionary](https://ccl.northwestern.edu/netlogo/6.3.0/docs/dictionary.html#S)

Guia de Programação para Iniciantes em NetLogo: [Welcome to Beginner's Interactive NetLogo Dictionary (BIND)](https://ccl.northwestern.edu/netlogo/bind/)

11 primitivas essências para novatos estudarem: [First 11 Netlogo Primitives To Learn | Beginner's Interactive NetLogo Dictionary](https://ccl.northwestern.edu/netlogo/bind/article/first-11-netlogo-primitives-to-learn.html)

## Iniciação de Programação em NetLogo

Agora que os conceitos básicos sobre NetLogo foram aprendidos, iremos utilizar esse conhecimentos na prática para desenvolver a nossa própria simulação dentro da ferramenta. 

Iremos criar uma simples simulação de ecossistema, onde será utilizado as Turtles que irão ter a função de “animais” da simulação tendo ações como andar, comer, reproduzir e morrer, possuindo um nível de energia que terá influência por parte de certas ações, e Patches, que irão ter a função do terreno da simulação.

Para isso é necessário abrir o software, ao abrir ele já deve abrir um modelo de simulação em branco para ser criado.

### Criação do Botão e Procedimento setup

Para começarmos a nossa criação vamos primeiro salvar o modelo clicando em Arquivo > Salvar, podem colocar o nome do modelo na sua escolha. Após fazer devemos selecionar o item “Botão” no seletor ao lado do botão “Adicionar”, após garantir que isso foi feito clique no botão “Adicionar” e clique em algum lugar da tela em que você deseja que o botão permaneça. Aqui entramos no pop-up de criação de Botão, nele vemos algumas opções, por exemplo o tipo de agente que irá realizar a ação do botão, se ele deve rodar para sempre, nome do botão, entre outros. Neste caso iremos criar o nosso botão de setup, botão esse que realizará a configuração inicial da nossa simulação, para isso será necessário apenas escrever na área “Comandos” a palavra setup, isso avisará ao modelo que estamos criando um novo Procedimento de nome “setup” que deve ser anexado ao botão que foi criado. Vou explicar brevemente as outras opções, os “Agentes” se refere a quais tipos de agentes vão ter acesso as ações do botão, “Para sempre” se refere se a ação do botão ficará se repetindo ou se deve rodar só uma vez, “Desabilitar até a execução” impede que o botão seja utilizável até a criação da simulação, “Comandos” seria o nome do procedimento que deve ser criado e anexado ao botão, “Nome para visualização” seria o nome que apareceria no botão em si, não afeta o nome do procedimento, e a “Tecla de ação” se refere a tecla a qual, ao clicada, irá acionar o botão.

1. Abra a ferramenta NetLogo
2. Clique em Arquivo > Novo
3. Selecione a opção “Botão” no seletor de itens
4. Clique em “Adicionar” e coloque o botão onde deseja na tela
5. Crie o botão da seguinte forma e clique em Ok
    1. Agentes → Observer
    2. Para sempre → Desabilitado
    3. Desabilitar até a execução → Desabilitado
    4. Comandos → setup
    5. Nome para visualização → 
    6. Tecla de ação → 

Ao criar esse botão, podemos perceber que ele está com sua fonte em vermelho, isso quer dizer que algum erro ocorreu e nesse caso seria pelo fato de que esse procedimento não foi implementado em nenhum momento no código. Seguindo por esse caminho, iremos criar o procedimento para esse botão, para isso devemos ir para a aba “Código” do software, e nisso devemos escrever o procedimento seguindo o padrão passado anteriormente, primeiro colocando a palavra `to` e depois o nome do procedimento, como esse procedimento já foi configurado pelo botão setup tendo como nome igual ao do botão, devemos manter o mesmo nome para o modelo reconhecer que se tratam do mesmo procedimento. 

Ao fazer isso iremos fazer algumas implementações simples para configurar o mundo da simulação e habitar o nosso mundo, vamos primeiro limpar a nossa simulação utilizando o comando `clear-all`, ao fazer isso podemos criar as novas turtles para habitar esse mundo, utilizando o comando `create-turtles 50 [ setxy random-xcor random-ycor ]`, após isso devemos zerar os ticks utilizando o comando `reset-ticks`, e por fim devemos colocar o comando para finalizar o procedimento, esse sendo o `end`. Esse procedimento que acabamos de criar tem a seguinte funcionalidade, ao rodar ele deverá configurar o modelo para uma nova simulação, garantido de que se foi criado uma simulação previamente tudo que tinha sido criado/afetado seja excluído,  impedindo de que elementos de uma simulação passada possa afetar os resultados da nova simulação. Após isso nós criamos os agentes que vão habitar o mundo, e que dentro dos colchetes definimos a suas posições iniciais, ou seja cada turtle haverá uma posição aleatória ao ser gerada pela simulação (outros atributos podem ser alterados dentro dos colchetes na hora da criação, como cor, tamanho, formato, entre outros). E por fim, resetamos o contador de ticks, isso é importante para evitar de bugs acontecerem dentro da nossa simulação.

1. Vá para a aba Código
2. Digite o seguinte procedimento
    
    ```lua
    to setup
      clear-all
      create-turtles 50 [ setxy random-xcor random-ycor ]
      reset-ticks
    end
    ```
    
3. Clique em Verificar
4. Teste o botão na aba Interface

### Criação do Botão go e Procedimento move-turtles

Testando esse botão podemos verificar que cada vez em que o mesmo é clicado, as 50 turtles aparecem em lugares diferentes, resultado dos comandos em que nós utilizamos. Entretanto o modelo até o momento está relativamente básico, apenas contendo um botão e um procedimento, vamos agora implementar um botão “go” para começar de fato a simulação e implementar um procedimento de movimentação para as turtles.

Para isso devemos criar o segundo botão do nosso modelo, iremos seguir passos parecidos com o que foi feito na criação do botão setup, apenas com as seguintes diferenças. Na parte de Comandos devemos colocar a palavra “go” e devemos marcar tanto a checkbox de “Para sempre” quanto a de “Desabilitar até a execução”. 

É necessário marcar ambas as checkbox pois desejamos que o procedimento “go” rode indefinidamente, sem ter que ficar acionando o botão toda hora para ele realizar a sua ação, e também desejamos em que esse comando só seja utilizável após a configuração da simulação, não seria viável rodar os comandos dentro desse procedimento se não temos uma simulação criada. 

Ao criar o botão notamos novamente que o botão ficou com sua fonte vermelha, mas também que ele  um símbolo de “replay” indicando que ele irá repetir a ação desse procedimento indefinidamente.

1. Selecione a opção “Botão” no seletor de itens
2. Clique em “Adicionar” e coloque o botão onde deseja na tela
3. Crie o botão da seguinte forma e clique em Ok
    1. Agentes → Observer
    2. Para sempre → Habilitado
    3. Desabilitar até a execução → Habilitado
    4. Comandos → go
    5. Nome para visualização → 
    6. Tecla de ação →

Após feito com sucesso a criação do botão go devemos fazer a sua implementação no código, para isso volte para a aba Código e vamos inicializar o procedimento escrevendo em uma área limpa do código o mesmo começo que foi usado para criar o procedimento setup, começando por escrevendo `to` e o nome do procedimento, que nesse caso seria go. 

Agora que temos o procedimento criado devemos implementar as suas funcionalidades, dentro desse procedimento vamos acionar outro procedimento para movimentar as turtles a cada tick rodado. 

Para isso será necessário que dentro do procedimento go escrevemos o nome do procedimento que queremos acionar, que nesse caso se chama `move-turtles`, esse procedimento que realizara a movimentação das nossas turtles que se encontram na simulação, por enquanto não iremos implementar mais nada no procedimento go, então antes de fecharmos ele devemos colocar a primitiva `tick` pois ela que vai sinalizar que um tick deve passar a cada vez que o procedimento go for acionado, essa primitiva deve sempre estar adicionada no seu botão go e de preferência estando no final, ao fazer isso basta finalizar o procedimento escrevendo `end`. Seu procedimento deve ficar da seguinte forma.

```lua
to go
  clear-all
  move-turtles
  reset-ticks
end
```

Entretanto ao fazer isso vamos receber o seguinte erro “Nada com MOVE-TURTLES foi definido anteriormente”, isso se dá poque esse procedimento em que chamamos não se refere a nenhuma primitiva ou procedimento que já foi criado pela própria ferramenta, para esses casos devemos realizar a criação do procedimento move-turtles também. 

Devemos primeiro atualizar a chamada do detro do procedimento go, após isso vamos programar a funcionalidade da movimentação das turtles. Vamos começar chamando todas as turtles utilizando a primitiva`ask` , primitiva essa fundamental para o aprendizado da ferramenta, pois ela permite que a gente interaja com os agentes da simulação “pedindo” para que eles realizem alguma ação. A primitiva `ask` pode ser usado por diferentes tipos de agentes, sendo eles conjuntos de agentes (Patches, Turtles, Links) ou algum agente em específico.

<aside>
💡

ex:

`ask turtles [ fd 1 ]`

`ask patch 0 0 [ set pcolor red ]`

</aside>

Dentro dos colchetes entrará os comandos que vamos mandar para todos os agentes chamados realizarem. 

Com os devidos agentes chamados e enviados para realizarem o procedimento, devemos criar um procedimento de mesmo nome começando digitando a palavra `to` e o nome do procedimento, após isso vamos programar a funcionalidade da movimentação das turtles. Nosso objetivo é que as turtles possam se direcionar para qualquer direção que desejar e após isso realizar um passo, para implementarmos isso precisamos escrever os comandos  `right random 180` , `left random 180` e `forward 1` , o primeiro e segundo comando informa para a turtle se direcionar em um angulo aleatório entre 0 e 180 graus, já o terceiro informa para a turtle dar um passo para frente ( esses comandos devem ficar dentro dos colchetes para funcionar corretamente ). Após ter sido implementado esses comandos no procedimento basta fechar ele utilizando a primitiva `end`.

1. Vá para a aba Código
2. Digite os seguintes procedimentos
    
    ```lua
    to go
    ask turtles[
      move-turtles
      ]
      tick
    end
    
    to move-turtles
      rt random 180 lf random 180 forward 1
    end
    ```
    
3. Clique em Verificar
4. Teste o botão na aba Interface

### Implementando variável de Energia e configurando Patches

Agora com esses procedimentos verificamos que as nossas turtles possuem a habilidade de se movimentar para qualquer direção. Vamos agora implementar alguns desafios para as turtles enfrentarem. Agora nas seguintes implementações iremos adicionar um sistema de energia para as turtles, que a cada passo dado deve ser gasto energia, e caso essa energia chegue a 0 a turtle deverá morrer. 

Juntamente com isso iremos adicionar comida para as turtles poderem se alimentar e continuarem vivas , implementação essa que será por meio dos patches que deverão funcionar como a grama para eles se alimentarem.

Tanto os patches mas principalmente as turtles possuem algumas variáveis padrões que são definidas ao criar um desses agentes, como por exemplo color (sendo pcolor para patches), shape, size. Elas funcionam de uma forma extremamente similar a um atributo de um objeto. Entretanto para o nosso modelo precisamos criar uma nova variável para as turtles, pois não existe nenhuma variável já criada que possamos atribuir a energia. 

Há dois tipos de variáveis a serem criadas, as persistentes e as temporárias, as persistentes sendo criadas fora de um procedimento e podendo ser chamada a qualquer momento, e a temporária sendo o contrário dela. No nosso modelo apenas utilizaremos as variáveis persistentes. Para criarmos uma variável persistente precisamos primeiro definir a qual tipo de agente deve se definir essa variável, esses podendo ser patches, turtles, links ou até mesmo uma variável global. 

Após definido o agente é necessário colocar um traço e a palavra `own` junto, para indicar que isso é um variável nova atribuída para esse tipo de agente, e por fim abrir colchetes, onde lá será definido o nome da variável.

<aside>
💡

ex:

`globals [ tempo-decorrido ]`

`patches-own [ recarga-grama  possui-grama? ]`

`turtles-own [ energia ]`

`links-own [ forca-ligacao ]`

</aside>

Para o nosso caso apenas desejamos criar uma variável nova para as turtles, essa sendo chamada energy, para isso devemos definir o agente em que vamos atribuir essa nova variável, esse agente sendo as turtles, escrever o comando `own` e dentro dos colchetes escrever a palavra energy. Ao fazer isso nós conseguimos atribuir com sucesso uma nova variável para todas as turtles, garanta que essa linha de código não esteja dentro de nenhum procedimento para garantir que funcione corretamente.

1. Vá para a aba Código
2. Digite o seguinte comando
    
    ```lua
    turtles-own [ energy ]
    ```
    
3. Clique em Verificar

Agora para começar a implementar essa nova funcionalidade devemos modificar um pouco como o nosso código estava estruturado.  Vamos primeiro voltar para o procedimento setup, dentro dele iremos aplicar um valor para a variável de energia e para fazermos isso devemos entrar dentro das chaves da linha create-turtles e devemos configurar um valor inicial de energia para as turtles, para se fazer isso devemos usar o comando `set energy random 50`, agora com esse comando adicionado cada turtle criada deverá ter um valor inicial de energia de 0 a 50 pontos. 

Podemos verificar se essa implementação funcionou clicando no botão verificar se não houve nenhum erro, caso o código foi implementado com sucesso devemos voltar para a aba de interface e é necessário clicar no setup, após isso basta clicar com o botão direito em cima de uma turtle e procurar a opção com o numero da turtle e selecionar inspect turtle. Ao fazer isso se deparamos com um menu de variáveis da turtles, podemos fazer essa inspeção tanto em turtles, patches e links. Dentro dela é possível ver todas as variáveis designadas para dito agente e seus respectivos valores.

Agora com os valores já definidos podemos implementar a lógica, no procedimento move-turtles, do gasto de energia e juntamente com isso também iremos criar um novo procedimento para verificar o valor de energia da turtle. Vamos começar com a lógica de movimento, para isso devemos voltar ao procedimento move-turtles e dentro dele basta adicionarmos um comando dentro das chaves para realizar a redução da energia, para isso devemos escrever `set energy energy - 1`,  esse comando garantirá que ele está realizando a redução com o seu próprio valor por menos 1. 

Agora com essa implementação em dia devemos criar um novo procedimento para verificar se a turtle possui energia, para isso devemos, fora de qualquer procedimento, começar o novo procedimento com `to` e o nome do procedimento que nesse caso será check-death, dentro dele iremos utilizar o operador if para verificar se o valor da energia está abaixo de 0, para fazer isso devemos fazer a verificação utilizando o seguinte comando `if energy <= 0 [ die ]`. Ao finalizar essa etapa basta fechar o procedimento utilizando a primitiva`end` e fazer a chamada desse procedimento dentro do procedimento go, apenas escrevendo o nome do procedimento check-death debaixo do procedimento move-turtles dentro dos colchetes.

1. Vá para a aba Código
2. Altere a linha create-turtles do procedimento go da seguinte forma
    
    ```lua
    create-turtles 50 [ setxy random-xcor random-ycor set energy random 50]
    ```
    
3. Altere o procedimento move-turtles da seguinte forma 
    
    ```lua
    to move-turtles
      rt random 360 fd 1 set energy energy - 1
    end
    ```
    
4. Digite o seguinte procedimento 
    
    ```lua
    to check-death
      if energy <= 0 [ die ]
    end
    ```
    
5. Clique em Verificar

Ao realizar essas alterações percebemos que, aos poucos, todas as nossas turtles vão morrendo por falta de energia, isso se dá pela implementação da nova lógica de movimentação que vai reduzindo gradativamente a energia das turtles a cada passo, entretanto elas não tem nenhuma chance de sobrevivência já que, até então, não há nenhuma forma de recuperar essa energia. Antes de seguirmos para a próxima parte, essa sendo da alimentação das turtles, verifique que se código esteja da seguinte forma.

```lua
turtles-own [ energy ]

to setup
  clear-all
  create-turtles 50 [ 
	  setxy random-xcor random-ycor 
	  set energy random 50
  ]
  reset-ticks
end

to go
 ask turtles[ 
    move-turtles
    check-death
  ]
  tick
end

to move-turtles
  lt random 180 
  rt random 180 
  forward 1 
  set energy energy - 1
end

to check-death
  if energy <= 0 [ die ]
end
```

Agora que garantimos que o código está correto, vamos prosseguir para a configuração dos Patches. Nosso objetivo com essa implementação é adicionar dois novos tipos de terreno, esses sendo grama e terra onde as turtles deverão se alimentar de terrenos que possuem grama e ignorar os que possuem terra, enquanto isso os terrenos que possuem terra deverão ter uma chance aleatória de crescer grama, assim permitindo que as Turtles possam se alimentar.

Para realizarmos a implementação dessa funcionalidade é necessário primeiramente criar um simples procedimento para realizar a configuração dos Patches iniciais, iremos nomear esse procedimento de setup-patches. Iremos solicitar agora para que todo o terreno possua a coloração verde, para indicar que todo o terreno no momento possui grama. Para isso devemos utilizar o comando `set pcolor green` que vai modificar a coloração de cada Patch para a cor verde, e por fim finalizar o procedimento utilizando a primtiva `end`. Ao criar esse procedimento devemos chamar ele dentro do procedimento setup e a chamada dos agentes, assim a cada criação de uma nova simulação ele realize a configuração dos Patches para a coloração correta.

1. Vá para a aba Código
2. Digite o seguinte procedimento
    
    ```lua
    to setup-patches
      set pcolor green
    end
    ```
    
3. Modifique o procedimento setup para ficar da seguinte forma
    
    ```lua
    to setup
      clear-all
      create-turtles 50 [ setxy random-xcor random-ycor set energy random 50]
      ask patches [ 
    	  setup-patches
      ]
      reset-ticks
    end
    ```
    
4. Clique em Verificar

### Configurando Procedimentos de Alimentação e Reprodução das Turtles

Com essa implementação adicionada podemos configurar agora o sistema de alimentação das Turtles, onde elas devem se alimentar de terrenos verdes (grama) e que ao se alimentar o terreno deve mudar a sua cor para marrom (terra). Primeiramente vamos implementar a funcionalidade de alimentação das Turtles, e para isso devemos criar um novo procedimento a qual vamos chamar de eat-grass, em uma parte limpa do código comece um novo procedimento escrevendo o comando `to` e o nome do procedimento.

Dentro do novo procedimento devemos chamar todas as turtles para verificar se o terreno a qual elas estão acima possuem grama, e para fazer isso devemos utilizar o comando `if pcolor = green [  ]`, esse vai ser o comando responsável pela verificação do tipo de terreno.

Dentro do par de colchetes vamos aplicar a lógica de troca de terreno para terra e de ganho de energia para a turtle que se alimentou. Devemos então adicionar respectivamente os comandos `set pcolor brown` e `set energy energy + 10`, com essa nova lógica aplicada a cada vez que uma turtle se alimentar de um terreno que possua grama (coloração verde) o terreno deverá se tornar do tipo terra (coloração marrom) e ele deve ganhar 10 pontos de energia. Para finalizar devemos, fora dos colchetes, adicionar a primitiva `end` e adicionar a sua chamada no procedimento go, com o intuito dele rodar esse procedimento a cada tick rodado dentro da simulação

1. Vá para a aba Código
2. Digite o seguinte procedimento
    
    ```lua
    to eat-grass
      if pcolor = green [ set pcolor brown set energy energy + 10 ]
    end
    ```
    
3. Modifique o procedimento go para ficar da seguinte forma 
    
    ```lua
    to go
    ask turtles[
      move-turtles
      eat-grass
      check-death
    ]
      tick
    end
    ```
    
4. Clique em Verificar

Percebemos agora ao rodar o código que as nossas Turtles consegue permanecer vivas por mais tempo graças a essa implementação, entretanto o nosso modelo ainda não está pronto. Vamos adicionar agora uma nova funcionalidade para realizar o crescimento da grama, adicionando uma espécie de cadeia alimentar no nosso ecossistema. Para começarmos a fazer essas alterações é necessário criar um novo procedimento que será responsável pela lógica de crescimento da terra, iremos chamar ele de regrow-grass.

Em uma parte limpa do código comece um novo procedimento utilizando o comando `to` e o nome do procedimento, esse sendo regrow-grass. Dentro dele é necessário chamar todos os pedaços de terra da simulação (patches com a cor marrom) e para isso utilizaremos um comando já utilizado, esse sendo o `ask patches`, em conjunto de um comando novo, esse sendo `with`.  Esse comando tem como função de extrair um conjunto de agentes dentro de um conjunto de agentes maior utilizando uma condicional como base para a filtragem. 

<aside>
💡

A primitiva `with` pode ser tanto usada dentro da primitiva `ask` quanto na primitiva `if`. Seu funcionamento é similar ao da primitiva `if`, entretanto ela pode causar algumas mudanças na lógica do seu código.

ex sem primitiva `with`:

`ask turtles [ if energy != 0 [ … ] ]` → deve chamar todas as turtles, fazer uma verificação se essa turtle possui energia maior que 0, e realizar uma ação

ex com primitiva **with**:

`ask turtles with [ energy != 0 ] [ … ]`  → deve chamar todas as turtles que possuem energia maior que 0 e realizar uma ação X

Na **primeira ela chama todas as turtles**, e **depois realiza o uso da condicional para filtrar as turtles,** isso pode ser bom caso você **deseja acessar o conjunto inteiro de agentes** e não deseja ser limitado para um conjunto já filtrado.

Na segunda ela chama diretamente as turtles com energia diferente de 0, isso pode ser bom em casos onde **não há importância validar agentes fora do conjunto solicitado**.

</aside>

No nosso caso desejamos que ele apenas chame os Patches com a cor marrom, então dentro do `with` devemos abrir colchetes e escrever `pcolor = brown`, isso garante em que estamos chamando apenas os terrenos em que não possui grama.

Após essa filtragem devemos abrir novamente colchetes para podermos dizer de fato o que desejamos que esses terrenos façam. Nesse modelo vamos configurar para que o crescimento do terreno seja feita de forma aleatória, sem ter necessariamente um tempo mínimo para crescer novamente a grama. Para ser feito isso devemos adicionar um operador condicional e e implementar a condição de aleatoriedade do crescimento utilizando o comando `if random 100 < 3 [  ]`, esse comando irá atribuir um numero aleatório de 0 a 100 e validar se o numero é maior que 3, caso isso for verdade o terreno deverá realizar com sucesso o crescimento da grama utilizando o seguinte comando dentro do colchete `set pcolor green`. Agora que a lógica de crescimento está aplicada podemos fechar o procedimento, utilizando o comando `end` fora dos colchetes e implementar uma chamada para esse procedimento dentro do procedimento go.

1. Vá para a aba Código
2. Digite o seguinte procedimento
    
    ```lua
    to regrow-grass
      ask patches with [ pcolor = brown ][ if random 100 < 3 [ set pcolor green ] ]
    end
    ```
    
3. Modifique o procedimento go para ficar da seguinte forma 
    
    ```lua
    to go
     ask turtles[ 
        move-turtles
        eat-grass
        check-death
      ]
      regrow-grass
      tick
    end
    ```
    
4. Clique em Verificar

Com esse novo procedimento implementado nosso ecossistema criado ganhou um novo nível de complexidade, tendo animais e alimento que habitam o mundo, esses animais podendo se alimentar, andar pelo mundo, e morrer. Para finalizar com o nosso modelo podemos adicionar uma última funcionalidade voltada para a reprodução das Turtles, dentro dela iremos adicionar uma lógica para caso uma Turtle atinge um numero x de energia, ela se reproduza e crie uma nova turtle, a custo de sua energia.

Para implementar essa funcionalidade basta criar um novo procedimento, que vamos chamar de reproduce, escrevendo `to` e o nome do procedimento. 

Agora precisamos adicionar uma condicional que realize a lógica de verificação da energia das turtles para determinar se elas possuem uma certa quantidade de energia, para isso será usado o comando `if energy > 100 [  ]`, esse comando deve verificar se a Turtle possui mais de 50 pontos de energia. Com a condicional realizando a verificação das Turtles devemos implementar o que desejamos caso essa condicional seja verdadeira, nosso objetivo é que caso uma Turtles chegue a ter 50 pontos ou mais de energia ela deve perder parcialmente essa energia e no lugar disso deve nascer um “filho” dessa Turtle. 

Com esse objetivo em mente devemos colocar, dentro dos colchetes, os seguintes comandos `set energy energy - 100`, cujo tem como objetivo realizar a perda de energia ao realizar a reprodução e uma nova primitiva chamada `hatch` , ela tem como objetivo de criar novas turtles com base nos atributos da Turtle Pai, ou seja tudo que a Turtle pai tinha foi passado para o filho.

Dentro desse comando podemos indicar quantos “filhos” devem vir dessa Turtle adicionando um numero ao lado do comando, e mais importante podemos também realizar certas alterações dentro desses “filhos” utilizando um colchete para escrever os comando ou variáveis que desejamos alterar. Para o nosso exemplo apenas desejamos que um “filho” nasça da Turtle e também que elas já possuam 50 pontos de energia para poder sobreviver. Para ser feita essa implementação basta adicionar a seguinte linha de código `hatch 1 [ set energy 50 ]`, fazendo isso garantimos que apenas nasça um “filho” possuindo um valor inicial configurado de energia, sem realizar nenhuma alteração extra no filho. 

Agora para finalizar esse procedimento basta adicionar a primitiva `end` fora dos colchetes, e realizar a chamada do procedimento dentro do procedimento go, para assim essa funcionalidade ser rodada de forma correta.

1. Vá para a aba Código
2. Digite o seguinte procedimento
    
    ```lua
    to reproduce
      if energy > 100 [ set energy energy - 100 hatch 1 [ set energy 50 ]  ] 
    end
    ```
    
3. Modifique o procedimento go para ficar da seguinte forma 
    
    ```lua
    to go
    ask turtles[
      move-turtles
      eat-grass
      reproduce
      check-death
    ]
      regrow-grass
      tick
    end
    ```
    
4. Clique em Verificar

Agora que realizamos todas essas implementações nós possuímos um modelo simples de ecossistema, onde possuímos uma cadeia alimentar entre o terreno, esse sendo terra e grama, e as Turtles. Nele também foi adicionado funcionalidades de crescimento de terra, alimentação, morte e reprodução de Turtles, entre outras. Agora que as funcionalidades principais da nossa simulação foram adicionadas, podemos implementar alguns elementos bônus para aprimorar o nosso modelo. Antes de realizarmos isso, confira se o seu código está da seguinte forma:

```lua
turtles-own [ energy ]

to setup
  clear-all
  create-turtles 50 [ 
    setxy random-xcor random-ycor 
    set energy random 50
  ]
  ask patches[
    setup-patches
  ]
  reset-ticks
end

to go
 ask turtles[ 
    move-turtles
    eat-grass
    reproduce
    check-death
  ]
  regrow-grass
  tick
end

to eat-grass
  if pcolor = green [ set pcolor brown set energy energy + 10 ]
end

to move-turtles
  lt random 180 
  rt random 180 
  forward 1 
  set energy energy - 1
end

to check-death
  if energy <= 0 [ die ]
end

to setup-patches
  set pcolor green
end

to regrow-grass
  ask patches with [ pcolor = brown ][ if random 100 < 3 [ set pcolor green ] ]
end

to reproduce
  if energy > 100 [ set energy energy - 100 hatch 1 [ set energy 50 ]  ] 
end
```

 

### Melhorias na lógica do código e adição de Gráficos, Monitores e Deslizadores

Agora que garantimos que o nosso código está correto, podemos realizar a implementação de itens novos na nossa interface, itens esse que podem nos ajudar a visualizar elementos em específicos da simulação, como por exemplo a quantidade de Turtles vivas, ou até mesmo interagir com variáveis do nosso código.

### Monitores

Tem como objetivo retornar, em valor numérico, algum dado solicitado da simulação. Para o nosso modelo podemos adicionar um monitor que retorne a quantidade de Turtles restantes dentro da simulação. 

Vamos primeiro ir para a aba interface, dentro dela iremos selecionar na lista de itens a opção “Monitor” e clicar no botão “Adicionar”. Ao fazer isso podemos escolher a posição onde desejamos que fique o monitor, após adicionar o monitor na tela o modelo deve abrir um pop-up de criação de Monitor, dentro dele podemos escrever o código em que vai ditar o que vai ser monitorado, isso fica na área de “Comando para mostrar no monitor”. Podemos também alterar o nome do monitor na área de “Nome do monitor”, e por fim podemos alterar as casas decimais em que pode ser retornada e o tamanho da fonte em que o monitor deve ter.

Na seção de “Comando para mostrar no monitor” desejamos que seja contado a quantidade de turtles presente na simulação, e para fazer isso é necessário o uso da primitiva `count`, sua funcionalidade é retornar o valor de quantidade de agentes dentro de um conjunto de agentes. Como desejamos apenas contar a quantidade total de Turtles, sem realizar algum tipo de filtragem, basta escrever o comando `count turtles`, com esse comando ele já vai realizar a contagem de todas as Turtles presentes na simulação. Na seção de “Nome do monitor”, vamos adicionar o nome de “turtles-vivas” para facilitar no entendimento da função do monitor, e por fim as ultimas duas seções não é necessário nenhum tipo de alteração. Ao finalizar a criação do monitor, basta clicar em ok para validar se a implementação foi feita corretamente. Caso houve algum erro na criação do monitor o mesmo vai apresentar o seu nome com a coloração vermelha.

1. Seleciona a aba Interface
2. Selecione a opção “Monitor” no seletor de itens
3. Clique em “Adicionar” e coloque o botão onde deseja na tela
4. Crie o botão da seguinte forma e clique em Ok
    1. Comando para mostrar no monitor → `count turtles`
    2. Nome do monitor → 
    3. Casas Decimais → 17
    4. Tamanho da Fonte → 11

Agora com esse novo monitor implementado, podemos observar facilmente a quantidade atual de Turtles dentro da simulação, assim facilitando a compreensão por parte do que está acontecendo durante a simulação no momento. Sinta-se a vontade de tentar implementar outros monitores para praticar o que foi aprendido, como por exemplo um que monitora a quantidade de gramas disponíveis, caso for necessário a filtragem dos conjuntos de agentes basta utilizar o comando `with` para realizar essa operação.

### Gráficos

Parecidos com os monitores, os gráficos tem como objetivo retornar um valor específico de um agente ou uma série de agentes, a principal diferença sendo o uso de elementos visuais para indicar esses resultados. Para o nosso caso iremos fazer um gráfico de Turtles x Gramas, dentro dele possuiremos dois elementos visuais, um deles sendo o número de Turtles vivas e o segundo sendo o numero de terrenos que possuem grama.

Para criarmos o gráfico devemos primeiro entrar na aba Interface, dentro dela é necessário selecionar a opção “Gráfico” na lista de itens e por fim clicar no botão “Adicionar”. Ao realizar a adição o modelo vai abrir um pop-up de criação do gráfico, é nele que realizaremos a configuração do nosso gráfico para atender o nosso objetivo. Dentro dessa tela iremos realizar as seguintes implementações, primeiro na seção “Nome” é onde devemos colocar o nome de exibição do nosso gráfico, que nesse caso será Turtles X Patches, após isso temos a seções  “Nome do Eixo X” e “Etiqueta do Eixo Y” que se refere ao nome atribuído para esses eixos dentro do gráfico,  em que vamos manter em branco, possuímos também a escala máxima e mínima tanto dos eixos X e Y onde podemos configurar a altura e comprimento máximo do nosso gráfico, não iremos configurar pois já temos a checkbox “Escala automática?” ativada que vai fazer a configuração do tamanho do gráfico de forma dinâmica conforme o tamanho do gráfico vai aumentando. 

Na parte principal do menu, há uma tabela em que possamos adicionar os elementos que desejamos representar no gráfico, e é dentro dessa seção que devemos adicionar os nossos elementos. Por padrão ao criar um gráfico um elemento “default” sempre é criado, vamos primeiramente editar esse elemento mudando o “Nome da Caneta” para “Turtle”, na seção de “Comandos de Atualização de Caneta” é onde vamos adicionar o comando para ele realizar a contagem e transformar isso em um elemento de um gráfico, dentro dessa seção vamos utilizar as primitivas `plot count`, sendo o `count` uma primitiva em que já utilizamos para realizar a contagem das turtles e a `plot` sendo uma primitiva com o intuito de representar esses dados dentro de um gráfico, com essas primitivas nós devemos realizar a contagem das turtles e para isso vamos utilizar o seguinte comando `plot count turtles`. 

Agora que temos o primeiro elemento adicionado no nosso gráfico vamos para o segundo, Ainda na tela de criação de gráfico há uma opção debaixo da tabela de canetas chamado “Adicionar Caneta”, que serve para adicionar novos elementos para dentro do gráfico, vamos clicar nesse botão para dar seguimento ao nosso elemento. Após fazer isso ele irá criar umo novo elemento em branco, cujo vamos fazer as seguintes alterações, na cor vamos mudar para verde, com o intuito de melhorar na visualização e compreensão do gráfico, Na coluna de “Nome da Caneta” vamos alterar para “Patches”. Por fim, dentro dos “Comandos de Atualização da Caneta” iremos utilizar mais uma vez as primitivas `plot count` mas dessa vez modificado para realizar a contagem das gramas, para isso vamos devemos usar o comando `plot count patches with [ pcolor = green ]`, que deve contar somente os Patches que possuem a coloração verde. Ao criar essas duas canetas basta clicar no botão Ok para validar as implementações.

1. Seleciona a aba Interface
2. Selecione a opção “Gráfico” no seletor de itens
3. Clique em “Adicionar” e coloque o botão onde deseja na tela
4. Crie o botão da seguinte forma e clique em Ok
    1. Nome → Turtles X Patches
    2. Nome dos eixos X e Y →
    3. Escala máxima e mínima dos eixos X e Y → 
    4. Escala Automática? → Habilitado
    5. Mostrar Legenda? → Habilitado (Opcional)
    6. Caneta 1
        1. Cor → Preto
        2. Nome da Caneta → Turtles
        3. Comandos de Atualização da Caneta → `plot count turtles`
    7. Caneta 2
        1. Cor → Verde
        2. Nome da Caneta → Patches
        3. Comando de Atualização da Caneta → `plot count patches with [ pcolor = green ]`

Agora com a implementação desse novo gráfico no nosso modelo podemos realizar uma avaliação, mais aprofundada, de como nossa simulação funciona, como os agentes interajam uns com os outros e as relações diretas e indiretas causadas entre agentes, diferentes valores de atributos, entre outros.

### Deslizadores

Os deslizadores é um dos diversos itens que podem ser adicionados dentro de um modelo, como por exemplo botões, monitores e gráficos, entretanto os deslizadores tem uma função tanto quanto única que nos ajuda a explorar uma simulação ao seu potencial máximo. Sua função é de criar e uma nova variável, cujo essa tem a possibilidade de editar em tempo real os valores da dita variável sem a necessidade de intervir a simulação para realizar mudanças no código. Isso pode ser essencial para quem deseja realizar testes de diferentes cenários de uma simulação, e ter essa praticidade de poder alterar os valores sem interferir com o código.

No nosso modelo iremos criar três deslizadores, cada um exercendo uma função distinta. O primeiro vai ser um deslizador para definir a energia inicial das Turtles, o segundo vai ser um deslizador para definir a quantidade de energia ganho por grama e o terceiro vai ser um deslizador que define o valor necessário para uma Turtle se reproduzir.

Antes disso precisamos saber como se cria um deslizador, e o primeiro passo para essa etapa é selecionando a opção “Deslizador” na lista de itens e clicar no botão “Adicionar”. Após adicionar o deslizador para dentro do modelo um pop-up de criação de deslizadores deve abrir, dentro dele podemos ver algumas ver algumas opções para customizarmos o nosso deslizador. A primeira dela sendo chamada de “Variável Global”, nela em que é definido o nome da nova variável global a qual vamos atribuir a esse deslizador, a segunda parte se refere aos valores máximos e mínimos permitidos no deslizador, a terceira seção chamada “Incremento” se refere ao valor referencia na incrementação do deslizador, seja para adicionar ou para reduzir (ex: Incremento de 1 deve aumentar e diminuir de 1 em 1), existe também uma seção chamada “Valor” que define o valor padrão selecionado pelo deslizador e por fim a seção “Unidades” que define qual vai ser o tipo de unidade definido pela variável, podendo ser números inteiros, porcentagem, entre outros.

<aside>
💡

Como esses deslizadores trabalham com variáveis, criando variáveis globais novas, as mesmas devem ser implementadas dentro do código para funcionarem corretamente. 

</aside>

Para o primeiro exemplo vamos criar um deslizador que tem a função de armazenar o valor de energia inicial para cada Turtle, para isso vamos criar um deslizador cujo possui uma variável global chamada “initial-energy” (o nome que é definido para variável é o mesmo que vai ser definido para o deslizador), para indicar de que se trata da energia inicial. Nas seções de “Mínimo” e “Máximo” vamos colocar respectivamente os valores 1 e 100, sendo escolhido o 1 ao invés de 0 para impedir de criar Turtles que já nasçam mortas. Dentro da seção de “Incremento”, desejamos implementar essa variável de 1 em um por isso, vamos atribuir o numero 1. Por fim vamos atribuir a seção “Valor” com 50 pontos, pois desejamos que o valor inicial de energia das Turtles, por padrão, seja de 50 pontos de energia. Por fim basta clicar no boão OK para criar o deslizador. 

Agora que temos o deslizador e a variável global criada, devemos realizar a implementação da mesma no código. No nosso caso devemos realizar a alteração da variável energia dentro da criação das Turtles, localizado no comando `create turtles [ … ]` dentro do procedimento setup. Na parte em que está sendo configurado a quantidade de energia devemos fazer a troca de `create-turtles 50 [ setxy random-xcor random-ycor set energy random 50]` para `create-turtles 50 [ setxy random-xcor random-ycor set energy initial-energy]`, nessa nova implementação retiramos o numero fixo de energia inicial, esse sendo 50, para adicionar a nossa variável global que está anexada ao deslizador. Agora toda vez em que for desejado alterar esse valor, basta selecionar o valor desejado no deslizador e clicar novamente no botão setup para reconfigurar a simulação. 

1. Seleciona a aba Interface
2. Selecione a opção “Deslizador” no seletor de itens
3. Clique em “Adicionar” e coloque o botão onde deseja na tela
4. Crie o botão da seguinte forma e clique em Ok
    1. Variável Global→ initial-energy
    2. Mínimo e Incremento → 1
    3. Máximo → 100
    4. Valor → 50
    5. Unidades → Pontos (Opcional)
5. Vá para a aba Código
6. Modifique os seguintes procedimentos

```lua
to setup
  clear-all
  create-turtles 50 [ 
    setxy random-xcor random-ycor 
    set energy initial-energy
  ]
  ask patches[
    setup-patches
  ]
  reset-ticks
end
```

Para o segundo, vamos desenvolver um deslizador que defina a quantidade de energia que uma Turtle ganha ao comer um pedaço de grama, para fazer isso devemos voltar para a aba Interface e criar um novo deslizador. Na criação do deslizador vamos manter as mesmas opções que usamos na criação do ultimo deslizador com exceção de duas, o nome da “Variável Global” deve ser energy-from-grass, para uma melhor representação da funcionalidade do deslizador, e no “Valor” vamos definir o valor padrão para 10, pois não queremos que, por padrão, as Turtles recebam uma quantidade alta de energia. 

Ao realizar isso devemos fazer a implementação dessa nova variável para dentro do nosso código, nesse caso sendo necessário modificar o procedimento “eat-grass”, dentro desse procedimento conseguimos encontrar a lógica por trás da funcionalidade de alimentação e os valores em que são atribuídos. Dentro desse procedimento devemos realizar a troca da lógica de atribuição de energia para as Turtles de `if pcolor = green [ set pcolor brown set energy energy + 1- ]` para `if pcolor = green [ set pcolor brown set energy energy + energy-from-grass ]`. Com essa nova implementação permitimos agora, dentro da própria interface, de poder alterar os valores de ganho de energia das Turtes. Tente experimentar com valores diferentes de ganho em conjunto com o deslizador de vida inicial.

1. Seleciona a aba Interface
2. Selecione a opção “Deslizador” no seletor de itens
3. Clique em “Adicionar” e coloque o botão onde deseja na tela
4. Crie o botão da seguinte forma e clique em Ok
    1. Variável Global→ energy-from-grass
    2. Mínimo e Incremento → 1
    3. Máximo → 100
    4. Valor → 10
    5. Unidades → Pontos (Opcional)
5. Vá para a aba Código
6. Modifique os seguintes procedimentos

```lua
to eat-grass
  if pcolor = green [ set pcolor brown set energy energy + energy-from-grass ]
end
```

Por fim, vamos adicionar o terceiro e ultimo deslizador, esse tendo a função de ditar qual é o valor necessário de energia para uma Turtle poder reproduzir, para a criação desse deslizador é necessário primeiro voltar para a aba “Interface” e adicionar um novo deslizador. Dentro desse novo deslizador vai ser mantido as opções do primeiro deslizador, com exceção da “Variável Global” que vamos nomear de “energy-cost-reproduce”.

Após criar esse novo deslizador devemos realizar a implementação do mesmo dentro do código, para começarmos a implementação devemos primeiramente voltar para a aba “Código”. Ao voltar dentro da aba, é necessário agora realizar a alteração do procedimento “reproduce”, esse que é responsável pela lógica de reprodução das Turtles, como e quanto é gasto de energia e como são criado as Turtles filhas. Dentro dela iremos alterar os seguintes atributos, primeiro sendo o valor necessário para a reprodução acontecer e segundo sendo o valor de energia atribuído para os recém nascidos. Dessa forma, vamos realizar a alteração da lógica do procedimento de `if energy > 50 [ set energy energy - 50 hatch 1 [ set energy 50 ] ]` para `if energy > energy-cost-reproduce [ set energy energy - energy-cost-reproduce hatch 1 [ set energy energy-cost-reproduce ] ]`, com essa troca de variáveis no código podemos utilizar com sucesso o nosso novo deslizador. Realize novos testes alterando os valores desse e dos outros deslizadores para ver os diferentes resultados que esses cenários trazem.

1. Seleciona a aba Interface
2. Selecione a opção “Deslizador” no seletor de itens
3. Clique em “Adicionar” e coloque o botão onde deseja na tela
4. Crie o botão da seguinte forma e clique em Ok
    1. Variável Global→ energy-cost-reproduce
    2. Mínimo e Incremento → 1
    3. Máximo → 100
    4. Valor → 50
    5. Unidades → Pontos (Opcional)
5. Vá para a aba Código
6. Modifique os seguintes procedimentos

```lua
to reproduce
  if energy > energy-cost-reproduce [ set energy energy - energy-cost-reproduce hatch 1 [ set energy energy-cost-reproduce ] ]
end
```

Após realizado as implementações dos monitores, gráficos e deslizadores, transformarmos o nosso simples modelo em um modelo mais complexo e interativo, que permite o usuário a fazer diferentes cenários utilizando deslizadores e receber dados vindo de monitores e gráficos para nos auxiliar na compreensão dos diferentes cenários criados. Nesse exemplo que foi criado foi ensinado e implementado os seguintes conceitos da ferramenta:

1. Agentes
    1. Turtles
    2. Patches
2. Primitivas
3. Procedimentos
4. Lógica de Programação no NetLogo
5. Botões
6. Monitores
7. Gráficos
8. Deslizadores

<aside>
💡

Caso tenha permanecido alguma dúvida referente a conceitos, primitivas, lógica de programação em NetLogo, o site da ferramenta apresenta um guia para iniciantes aprenderem os conceitos básicos da ferramenta, juntamente com um dicionário de primitivas, onde é explicado a função de cada uma e como implementar.

Para aprender mais basta voltar para o tópico Documentação dentro da parte de Fundamentos do NetLogo

</aside>

## Programação Avançada e Biblioteca de Modelos

Até então durante esse minicurso percorremos pelos fundamentos básicos e introdução a programação de modelos em NetLogo, já com esses conhecimentos adquiridos criamos o nosso próprio modelo de ecossistema, utilizando agentes, procedimentos, entre outros. Agora com esse conhecimentos básicos em mão, irei mostrar alguns modelos padrões da biblioteca do Netlogo que, por mais avançados que pareçam utilizam muito do conteúdo passado nesse minicurso.

### Biblioteca de Modelos

Dentro da ferramenta NetLogo é possível encontrar, na seção “Biblioteca de Modelos”, uma vasta coleção de modelos já criados e salvos dentro do software. Esses modelos criados podem ter como objetivo de demonstrar certas capacidades da ferramenta, quanto pode simular uma complexa rede de comunicações e muito mais. A Biblioteca de Modelos é uma parte fundamental para o aprendizado da ferramenta NetLogo, pois é nessas simulações que podemos ter uma base do que a ferramenta é capaz, além de ajudar no aprendizado de como fazer uma simulação e em boas práticas de programação dentro da ferramenta.

Nessa ultima seção vamos dar ênfase em dois modelos bem conhecidos da ferramenta, o primeiro chamado de “Virus”, que se trata de uma simulação de propagação de um vírus, e a segunda sendo chamada de “Wolf Sheep Predation”, que se trata de uma simulação de um ecossistema ambientado por lobos e ovelhas.

Para podermos visualizar essa biblioteca, precisamos primeiro ir para a aba “Arquivo” da ferramenta NetLogo e selecionar a opção “Biblioteca de Modelos”, ao entrar dentro dessa aba nos deparamos com uma vasta gama de modelos a disposição. Dentro da biblioteca temos algumas categorias de modelos disponíveis para o uso separadas em pastas, a pasta a qual vamos selecionar se refere a “Sample Models”, que possuem os modelos mais cuidadosamente avaliados, servindo de exemplo de como programar e manter boas práticas de documentação. Existe outras pastas bem informativas como por exemplo a “Code Examples” que possui modelos com o objetivo de apresentar breve ilustrações de funções em particular e técnicas de programação. 

### Modelo 1: Virus

Esse modelo tem como objetivo simular a transmissão gradual e contínua de um vírus dentro de uma população humana. Dentro desse modelo podemos criar diferentes cenários de epidemia, nos permitindo assim visualizar como diferentes tipos de vírus podem impactar dentro de um grupo de pessoas. É possível encontrar esse modelo dentro da subpasta “Biology” na pasta “Sample Models”.

Após algumas execuções da simulação, irei explicar de forma mais aprofundada sobre o modelo, como funciona e seu propósito. Começando pela interface do modelo, é possível ver que possui há alguns deslizadores, monitores e gráficos a nossa disposição. Na série de deslizadores encontramos o “**number-people**” que tem a função de configurar a quantidade inicial de pessoas dentro da simulação, há também o “**infectiousness**” que configura a taxa de infecção do respectivo vírus, “**chance-recovery**” que se trata na taxa de recuperação dos infectados em relação ao vírus e por fim temos também o “**duration**” que dita o tempo mínimo em que a doença fica presente no corpo. Dentro da interface também possuímos monitores que ditam a taxa de pessoas infectadas em relação a população total da simulação, a taxa de pessoas imunes em relação a população total e por fim temos também um gráfico que mostra, de uma forma visível,  o numero total de pessoas, pessoas saudáveis, pessoas imunes e pessoas doentes, ao decorrer do tempo.

Com base nessas informações, conseguimos tirar algumas conclusões de como o modelo pode funcionar, mas até então não realizamos nenhuma análise no código e por isso iremos realizar isso agora para ter um entendimento mais aprofundado de como o modelo funciona. Indo para a aba código, podemos nos deparar com toda a programação necessária para fazer esse modelo, junto comentários do criador para nos auxiliar no entendimento do código. Vamos entender agora como funcionar o modelo em sua ordem de execução;

1. Antes de mais nada, é criado dentro do modelo algumas variáveis específicas para as Turtles e algumas globais, essas sendo:
    1. Turtles:
        
        > “**sick?**” - variável booleana que registra se uma pessoa está doente ou não
        > 
        
        > “**remaining-immunity**” - tempo restante de imunidade de uma determinada pessoa
        > 
        
        > “**sick-time**” - tempo em que uma determinada pessoa está doente
        > 
        
        > “**age**” - idade de uma determinada pessoa
        > 
    2. Global
        
        > “**%infected**” - porcentagem de pessoas infectadas em relação a quantidade total de pessoas
        > 
        
        > “**%immune**” - porcentagem de pessoas imunes em relação a quantidade total de pessoas
        > 
        
        > “**lifespan**” - tempo máximo de vida de uma pessoa
        > 
        
        > ”**chance-reproduce**” - chance de uma pessoa se reproduzir a cada tick
        > 
        
        > ”**carrying-capacity**” - numero máximo de pessoas permitidas na simulação
        > 
        
        > ”**immunity-duration**” - tempo máximo de imunidade que se pode ter
        > 

Apenas com a descrição dessas variáveis, já foi possível ter um entendimento melhor sobre possíveis funcionalidades que o nosso modelo possui, como por exemplo a variável “**age**” e “**lifespan**” indicam que cada pessoa possui um valor de idade e que tem uma idade máxima a qual elas podem atingir, cujo chegando nela as mesmas irão morrer de idade avançada. Outros exemplos disso sendo a variável “**chance-reproduce**”, que implica na existência de uma funcionalidade de reprodução dentro dessa simulação, e também a variável “**remaining-immunity**”, que nos indica que todas as pessoas que possuem imunidade, em algum momento, devem perder essa imunidade.

Há outros exemplos a serem citados, mas vamos prosseguir com a análise do código do modelo. Vamos seguir agora para a parte dos procedimentos da simulação:

1. Procedimento **setup**
    1. Esse procedimento deve realizar a configuração do ambiente da simulação, o mesmo é divido em 4 procedimentos distintos:
        1. **setup-constanst**
            1. Realiza a inicialização das variáveis globais
                1. Configura para que as pessoas vivam no máximo 50 anos ( 50 vezes 52 semanas)
                2. Configura a população máxima da simulação para 300 pessoas
                3. Configura a chance de reprodução por tick igual a 1 
                4. Configura a duração de imunidade para um ano (52 semanas)
        2. **setup-turtles**
            1. Realiza a criação das pessoas da simulação, sendo a quantidade configurada pelo deslizador:
                1. Configura uma coordenada aleatória para cada pessoa
                2. Configura uma idade aleatória para cada pessoa (contanto que seja menor que 50)
                3. Realiza a chamada do procedimento “**get-healthy**”
            2. Após realizar a criação das pessoas, o procedimento chama 10 pessoas aleatória:
                1. Realiza a chamada do procedimento “**get-sick**”
        3. **update-global-variables**
            1. Realiza a configuração dos monitores “**%infected**” e “**%immune**” (no nosso exemplo, realizamos a programação dos monitores dentro do próprio item, porém pode ser realizado a configuração dentro da seção de código)
        4. **update-display**
            1. Realiza a configuração do formato das pessoas conforme o tipo de formato selecionado na interface (não visto no nosso modelo de exemplo, existe também um item chamado selecionador, a qual podemos adicionar um item que realiza a seleção entre elementos a qual desejamos adicionar). Além disso, realiza a alteração nas cores das pessoas, dependendo se elas estão saudáveis, doentes ou imunes.
2. Procedimentos a vulso citados nos procedimento **setup**
    1. Procedimento **get-healthy**
        1. A cada pessoa em que for chamado esse método, irá transformar ela em uma pessoa saudável
            1. Altera atributo **sick?** para false
            2. Altera o tempo restante de imunidade para 0
            3. Altera o tempo doente para 0
    2. Procedimento **get-sick**
        1. A cada pessoa em que for chamado esse método, irá transformar ela em uma pessoa doente
            1. Altera o atributo **sick?** para true
            2. Altera o tempo restante de imunidade para 0
3. Procedimento **go**
    1. Se refere o procedimento em que deve realizar a iniciação da simulação, ele começa o procedimento chamando todas as pessoas e realiza a chamada de alguns procedimentos
        1. **get-older**
            1. A cada pessoa em que for chamado o método, irá realizar o envelhecimento da pessoa
                1. Aumenta de 1 em 1 o atributo **age**
                2. Realiza uma validação se a idade atual (**age**) ultrapassa a idade máxima que uma pessoa pode ter (**lifespan**)
                    1. Se sim, então morre
                3. Realiza uma validação se a pessoa possui imunidade ativa (**immune?** = true)
                    1. Se sim, realiza o decréscimo do tempo restante de imunidade (**remaining-immunity**)
                4. Realiza uma validação se a pessoa está doente (**sick?** = true) 
                    1. Se sim, realiza o acréscimo no tempo doente da pessoa (**sick-time**)
        2. **move**
            1. A cada pessoa em que for chamado o método, irá realizar a movimentação da mesma
    2. Ainda verificando dentro de todas as pessoas, realiza uma validação se a pessoa está doente no momento (**sick?** = true)
        1. Se sim, deve realizar a chamada do procedimento **recover-or-die**
    3. É realizado uma segunda validação se a pessoa está doente
        1. Se sim, deve realizar a chamada do procedimento **infect**
        2. Senão, deve realizar a chamada do procedimento **reproduce**
    4. Após realizado as validações, realiza as atualizações dos monitores e gráficos por meio das chamadas dos procedimentos **update-global-variables** e **update-display**
4. Procedimentos a vulsos citados no procedimento **go**
    1. **recover-or-die**
        1. A cada pessoa que estiver doente e for realizada a chamada desse procedimento
            1. Realiza uma validação se o tempo doente, em que a pessoa passou, é maior do que a duração máxima da doença (**sick-time > duration**)
                1. Se sim, vai realizar uma nova validação. 
                2. Se um número aleatório de 0 a 99 for menor do que a taxa de recuperação (random-float < **chance-recovery)**
                    1. Se sim, realiza o chamado do procedimento **become-immune**
                        1. A cada pessoa em que for chamado esse método, irá transformar ela em uma pessoa imune
                            1. Altera atributo **sick?** para false
                            2. Altera o tempo restante de imunidade para um ano (52 semanas)
                            3. Altera o tempo doente para 0
                    2. Senão, a pessoa morre
    2. **infect**
        1. A cada pessoa doente a qual foi chamada este procedimento, deve realizar a infecção para outras pessoas saudáveis em sua proximidade
            1. Chama todas as pessoas que se situam próximas a uma pessoa doente e que estão saudáveis (other turtles-here with[ not **sick?** and not **immune?** ])
                1. Realiza uma validação se um numero aleatório do 0 a 99 é menor do que a taxa de infecção (random-float < **infectiousness**)
                    1. Se sim, realiza a chamada do procedimento **get-sick**
    3. **reproduce**
        1. A cada pessoa não doente a qual foi chamado este procedimento, deve realizar uma tentativa de reprodução
            1. Realiza uma validação se a quantidade de pessoas total da simulação é menor que a capacidade máxima de pessoas e se um numero aleatório de 0 a 99 é menor do que a chance de reprodução (count turtles < **carrying-capacity** and random-float 100 < **chance-reproduce)**
                1. Se sim, deve nascer uma nova pessoa com os seguintes valores
                    1. Configura o atributo idade para 1
                    2. Comanda para a pessoa dar um passo
                    3. Realiza a chamada do procedimento **get-healthy**

Agora que finalizamos a análise do código, podemos entender de forma mais aprofundada sobre como é o funcionamento dessa simulação. Entendemos melhor como funciona as lógicas de propagação de doenças e de sua recuperação, como as pessoas podem adquirir imunidade ao sobreviver a doença, entre outras funcionalidades escondidas por trás do código. Caso tenha restado alguma dúvida sobre o funcionamento do modelo, ou apenas deseja aprender de forma mais aprofundada, basta olhar a seção de informações, é lá onde o autor deixou um guia sobre suas ideias para criar o modelo, o propósito a qual ele pretende atingir com esse modelo e como ele funciona como um todo.

### Modelo 2: Wolf Sheep Predation

Esse modelo tem como objetivo explorar um ecossistema de presa-predador, explorando como ovelhas e lobos se comportam dentro de um ambiente fechado, analisando seus picos e declínios na população e como eles se mantem ao longo do tempo. Esse modelo é um dos mais conhecidos dentro da ferramenta NetLogo, contendo bons exemplos de boas práticas de programação, uso de comandos e primitivas, tanto iniciantes quanto intermediárias, na prática, e no geral sendo um modelo interessante de se estudar.

Agora que realizamos algumas execuções, irei começar com a explicação do modelo. Começando pela interface é possível notar diversos elementos a nossa disposição, possuímos alguns botões de configuração e inicialização da simulação (**setup** e **go**), podemos ver alguns monitores e gráficos, cujo possuem a função de contabilizar a quantidade de ovelhas, lobos e grama respectivamente, e por fim temos alguns deslizadores e um selecionador a qual vamos entrar em mais detalhes agora. Falando sobre os deslizadores, encontramos o “**initial-number-sheep**” e o “**initial-number-wolf**” que configuram a quantidade inicial de ovelhas e lobos respectivamente, possuímos também o “**grass-regrowth-time**” que dita quanto tempo leva para crescer grama em um pedaço de terra, há também o “**sheep-gain-from-food**” e o “**wolf-gain-from-food**” que definem a quantidade de energia ganha que uma ovelha e um lobo, respectivamente, recebem ao se alimentar, e por fim temos o “**sheep-reproduce**” e o “**wolf-reproduce**” que definem a probabilidade de reprodução de uma ovelha e um lobo a cada passo. Sobre o selecionador temos somente duas opções, uma delas sendo a “**sheep-wolves**” e a outra sendo “**sheep-wolves-grass**”.

Apenas com essa leitura dos elementos da interface, já é possível perceber algumas funcionalidades dentro do modelo, como por exemplo a funcionalidade de reprodução e de energia que ambos as ovelhas e lobos possuem, é possível ver que há duas versões diferentes do modelo, a primeiro sendo a “**sheep-wolves**” em que remove a grama como um fator do ecossistema, mantendo somente os lobos e as ovelhas, e a segunda sendo a “**sheep-wolves-grass**” que se trata do modelo padrão dessa simulação, contendo ovelhas, lobos e grama como fatores dentro do ecossistema. Entretanto esses conhecimentos não são o suficiente para entender de forma mais aprofundada o modelo em exibição, vamos agora realizar uma análise do código em ordem sua ordem de execução;

1. Para começar, é criado dentro do modelo algumas variáveis específicas para as Turtles, aos Patches e Globais, e é concebido as raças para as Turtles:
    1. Global:
        
        > “**max-sheep**” - variável que define a quantidade máxima de ovelhas na simulação
        > 
    2. Breed (Raças)
        
        > “**sheep**” - Define uma nova raça a qual as Turtles podem se associar, essa sendo as ovelhas
        > 
        
        > “**wolves**” - Define uma nova raça a qual as Turtles podem se associar, essa sendo os lobos
        > 
    3. Turtles
        
        > ”**energy**” - Quantidade de energia em que as Turtles, tanto ovelha quanto lobo, possuem
        > 
    4. Patches
        
        > ”**countdown**” - Contador que indica quanto tempo se passou, utilizado somente no modelo “**sheep-wolves-grass**”
        > 

<aside>
💡

Breeds são basicamente “classes” que você pode atribuir para a turtle, elas podem ser chamadas isoladamente e podem ter variáveis próprias a suas classes.

</aside>

Com essas informações adicionais, conseguimos descobrir algumas funcionalidades sobre o modelo que antes não era aparente, a mais relevante sendo a criação de duas raças de Turtles, as raças sendo as ovelhas e lobos, cujo essas vão possuir funcionalidades e características próprias. Vamos continuar com a análise dos procedimentos do modelo;

1. Procedimento **setup**
    1. Esse procedimento tem a função de inicializar com a simulação, inicializando variáveis, criando ovelhas e lobos, e por configurando o tipo de terreno conforme o modelo selecionado.
        1. Realiza uma validação se a versão selecionada é a “**sheep-wolves-grass**” (essa é a versão em que a grama é um elemento presente dentro do ecossistema)
            1. Se sim, então chama todo o terreno (patches) e:
                1. Configura sua coloração entre verde ou marrom
                2. Realiza uma validação se o terreno em que está sendo chamado possui a cor verde
                    1. Se sim, inicializa o contador para que receba o tempo de crescimento da grama
                    2. Se não, inicializa o contador para que receba um numero aleatório entre 0 e o tempo de crescimento da grama
            2. Se não, então chama todo o terreno (patches) e:
                1. Configura sua coloração para verde 
    2. Procedimento **go**
        1. É o procedimento responsável pela execução da simulação, dentro dele vai ser realizado as seguintes ações;
            1. Realiza uma validação se não há nenhuma Turtle ainda viva (tanto ovelhas quanto lobos)
                1. Se sim, então finaliza a simulação
            2. Realiza uma validação se não há mais nenhum lobo na simulação e se a quantidade total de ovelhas ultrapassa o valor limite de ovelhas
                1. Se sim, exibe uma mensagem para o usuário e finaliza a simulação
            3. Após isso, chama todas as ovelhas e
                1. Realiza a chamada do procedimento **move**
                2. Realiza uma validação se o modelo atual selecionado é o “**sheep-wolves-grass**”
                    1. Se sim, então
                        1. Efetua o decréscimo de energia da ovelha a cada tick que passa
                        2. Realiza o chamado do procedimento **eat-grass** 
                            1. A cada ovelha que for chamado esse procedimento, deve realizar uma validação se o pedaço de terra atual possui grama (pcolor = green)
                                1. Se sim, então altera a cor do Patch para marrom e realiza o aumento de energia, com base no deslizador de ganho de energia das ovelhas
                        3. Realiza a chamada do procedimento **death**
                3. Realiza o chamado do procedimento **reproduce-sheep**
                    1. A cada ovelha que for chamado esse procedimento, deve realizar uma validação se um numero aleatório sorteado de 0 a 99 é menor do que a taxa de reprodução das ovelhas ( random float 100 < sheep-reproduce )
                        1. Se sim, a turtle perde metade da energia atual que possui e cria um clone seu, mandando ele dar um passo para frente.
            4. Chama todos os lobos e 
                1. Realiza o chamado do procedimento **move**
                2. Efetua o decréscimo de energia do lobo a cada tick que passa
                3. Realiza o chamado do procedimento **eat-sheep**
                    1. A cada lobo em que esse procedimento for chamado, deve procurar por alguma ovelha que esteja em sua proximidade
                        1. Realiza uma validação se há alguma ovelha em sua proximidade
                            1. Se sim, a ovelha morre e o lobo recebe o seu ganho de energia de acordo com o deslizador de ganho de energia dos lobos
                        
                4. Realiza o chamado do procedimento **death**
                5. Realiza o chamado do procedimento **reproduce-wolves**
                6. A cada lobo que for chamado esse procedimento, deve realizar uma validação se um numero aleatório sorteado de 0 a 99 é menor do que a taxa de reprodução dos lobos ( random float 100 < wolf-reproduce )
                    1. Se sim, a turtle perde metade da energia atual que possui e cria um clone seu, mandando ele dar um passo para frente.