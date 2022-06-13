# Entenda Como o GIT Funciona por     Baixo dos Panos



###  Git e um sistema distribuído e seguro



- Objetos fundamentais
- Sistema distribuído
- Segurança



#### **_SHA1_**

A sigla SHA significa Secure Hash Algorithm (Algoritmo de Hash Seguro), é um conjunto de funções hash criptográficas projetas pela NSA (Agência de Segurança Nacional dos EUA).

SHA gera algoritmos criptografados, a encriptação gera um conjunto de caracteres identificador de 40 dígitos.

SHA1 e uma forma curta de representar o arquivo.




#### _Git Bash_

O Git Bash é o aplicativo para ambientes do Microsoft Windows que oferece a camada de emulação para a experiência de linha de comando.

Quando você clica com o botão direto dentro da área de trabalho e seleciona a opção Git Bash Here, ele vai lançar o arquivo dentro da pasta onde estou, neste caso a desktop.

Para passar o arquivo para o algoritmo de crepitação utilizando o SHA1, digite no Git Bash openssl sha1 + o nome do arquivo ficando no meu caso:

_openssl sha1 Rascunho HTML.txt_

 _**Obs:**_ O arquivo tem que estar no mesmo diretório da pasta do Git Bash ou seja, neste caso ambos têm que estar dentro da área de trabalho.

Gerou uma chave criptografada com 40 caracteres

Se eu mudar qualquer coisa no arquivo, pode ser um letra ou um ponto, qualquer coisa, depois salvar e chamar novamente no Git Bash ele vai gerar uma nova chave criptografada com 40 caracteres

Alterei um caractere salvei o arquivo e me gerou uma nova chave de acesso


### Os 3 tipos básicos de objetos do Git responsáveis por direcionamento do nosso código



- BLOBS

- TREES

- COMMITS

  

**_Blobs (bolhas)_**

O blob (Binary Large Object - grande objeto binário) é um campo criado para o armazenamento de qualquer tipo de informações em formato binário, dentro de uma tabela de um banco de dados.

Git vai guarda esses arquivos fazendo o SHA dele, e também armazena meta dados nesses objetos, o primeiro objeto que conhecemos o BLOBS armazena meta dados do Git, que são o tipo do objeto, o tamanho do arquivo dentro outros.

O blob guarda a chave criptografado do arquivo.



**_TREE (Árvores)_**

Tree (árvore em português) é comando do MS-DOS que exibe graficamente a árvore de diretórios e arquivos. a partir do diretório-raiz para que o usuário tenha a organização hierárquica do seu disco.

A árvores armazenam as blobs, e contém também meta dados ela aponta para um blob, a arvores guarda o nome do arquivo, responsável por montar toda estrutura de onde estão localizados os arquivos, as arvores pode apontar para um blob ou para outras arvores. por que isso, porque um diretório pode ter outros diretórios dentro dele.

A árvores também tem um Sha1 do meta dado, então veja bem os blobs tem o Sha1 do arquivo, as arvores apontam para esses blobs e tem um sha criptografado com meta dados da arvores, se mudar uma virgula de um arquivo no qual essa arvores esta apontado, quando ela for gerar o SHA1 , o sha da bolha em si vai ter mudado e vai refletir a sha da arvore.


**_COMMIT_**

Em ciência da computação e gerenciamento de dados, um commit é a realização de um conjunto de mudanças provisórias permanentes, marcando o fim de uma transação e proporcionando durabilidade às transações ACID.

E o objeto que vai juntar tudo, que vai dar sentido a para alteração que você está fazendo, vai apontar para uma árvore, aponta para um parente, ou seja, o ultimo commit antes dele, ele aponta para um altor e aponta para uma mensagem também.

Um arquivo e representado pelo blobs, dentro das pastas representadas pelas tree, querem dizer? Essas significam uma alteração, então você pode escrever uma mensagem neste objeto chamado commit que vai estar explicando, dando significado para esse monte de arquivo, dentro de um monte de pasta, e o autor também neste caso eu, ou a pessoa que está fazendo o commit.

Este objeto também leva a data e a hora certinha de quando ele foi criado.

Os COMMIT também possui SHA1, ou seja criptação, significa que se você alterar um dado dentro do arquivo, ele vai gerar um sha1 daquela blob, a blob por sua vez tem uma árvore apontando para ela, então vai alterar também o meta dado daquela árvore, gerando um no sha1 da árvore, por sua vez o commit aponta para uma árvore que por sua vez pode estar apontando para outra árvore, dentro de outras árvores, então se você mudar qualquer coisa em um arquivo, que seja uma vírgula, isso mudar o blob, que vai refletir na árvore, que por sua vez vai refletir no commit, por isso o GIT e tão confiável.

Você consegue montar uma linha do tempo de quais commits foram realizados, e uma forma segura de demonstrar que aquele commit representa exatamente o que você quis dizer com o código, que não teve interferência de ninguém, não tem como uma pessoa agir maliciosamente, tentando alterar o código de um respectivo commit ou arquivo, sem que isso fique muito claro dentro de um histórico de coomits. Por que uma vez que você altera o arquivo você altera toda a estrutura daquele commit, por isso o commit e único para cada autor, da pessoa que está codificando.
