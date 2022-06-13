# Autenticação: CHAVES SSH E TOKENS



### <u>Chaves SSH</u>



Chaves SSH são uma forma segura de identificar usuários conhecidos, substituindo o tradicional "usuário e senha". Sua vantagem está na quantidade de caracteres em relação à uma senha tradicional, fazendo com que ataques bruteforce sejam inviabilizados devido ao tempo absurdo necessário para se "encontrar" a chave secreta através de tentativa e erro.

E uma de estabelecer uma conexão segura e encriptada entre duas maquinas. Nós vamos nos conectar no servidor do GIT HAB, e vamos configurar nossa máquina local como uma máquina confiável para o GIT HAB, estabelecendo esta conexão com duas chaves, vai ter sempre uma chave pública e uma chave privada. Nós vamos pegar essa chave pública e vamos lá no Git Hub colocar ele lá, e a partir do momento que agente fizer isso, o Git Hub vai conhecer nossa máquina. Então todos os repositórios que tiver na nossa máquina por esse processo SSH, agente for enviar condigos para lá, o Git Hub já vai conhecer a assinatura da nossa máquina, já vai ter uma conexão prévia estabelecida ali, e agente vai ser capaz de mandar codigos sem a necessidade de mandar senha.



#### Comando para criar chaves criptografadas para o Git hab

sequêncida de comandos

_ssh-keygen -t ed25519 -C  + e-mail_

Chaves criadas agora vão acessar elas, digite:

_cd / c/Users/willi/.ssh/_

Apos entrar digite ls para listar os arquivos da pasta, assim vai aparecer as chaves públicas e privadas.

id_ed25519 privada

id_ed25519.pub publica

Usar o comando **cat id_ed25519.pub** para visualizar o conteúdo destas chaves para colocar no GIT HUB

Acessamos a chave pública para colocar no Git Hub, segue abaixo:

ssh-ed25519 

No GitHub clicar no canto direito superior, em sua foto, depois clicar em DEFINIÇÕES, depois clicar em CHAVES SSH e GPS, depois clicar em NOVA CHAVE SSH, colocar o título MINHA MAQUINA WINDOWS, depois colar a chave pública.

Fazer mais um processo no Git Bash para validar a chave.

Digite **pwd** para mostrar o caminho completo do arquivo. Agora vamos inicializar o SSHagent

O comando que vamos rodar agora é **eval $(ssh-agent -s)**, este comando vai nos trazer um seqüência de numero no caso para mim foi Agent pid 2026, este e o numero que ele esta estartando um projeto, estando o sshagent.

Liste somente o arquivo com o comando **ls**, vai aparecer nossos arquivos contendo as chaves públicas e privadas.

Agora vamos passar nossa chave privada para o sshagent, quer dizer que sempre que chegar uma criptografia com esta chave, ele vai utilizar nossa chave privada para discriptografar nossa essa mensagem, então o agente vai ficar encarregue de perceber esse tipo de coisa, vamos utilizar o comando:

_ssh-add id_ed25519_

Após digitar a senha que voce colocou para sua chave, logo depois aparece a mensagem de senha adicionada ou IDENTITY ADDED.



#### Agora precisamos validar tudo

Vá no seu Github, vá na seta **"+"** no canto direto superior da tela, clica em **novo repositório**, digitar o **nome do projeto**, depois marcar a opção **INITIALIZE THIS REPOSITORY WITH A README,**
Depois clicar em criar repositório. Parabéns você acaba de criar seu novo repositório no GITHUB porém ele está vazio, ele está sem códigos,

Agora precisamos fazer clonar o código, clicar na botar código, dentro de uma caixa verde, depois copiar o link SSH.

Agora no terminal do Git, digitar o comando git clone e colar o link ssh.

Vai aparecer uma mensagem de confirmação, para salvar esta assinatura digital, só escrever yes.

Agora e só dar um **ls** e você vai ver que o repositorio ja foi criado.

Agora sim a chave está configurada e funcionando aqui no windows, porque não pediu a senha e já baixou direto.



### <u>Token de Acesso Pessoal</u>


No GitHub clicar no canto direito superior, em sua foto, depois clicar em  **DEFINIÇÕES**, na ultima opção da lista no canto esquerdo, clicar na opção **CONFIGURAÇÕES DO DESENVOLVEDOR**, depois clicar na opção **TOKENS DE ACESSO PESSOAL**, após clicar em **GERAR NOVO TOKEN**.

Escrever no nome da chave no campo em branco escrito **OBSERVAÇÃO**.
Você pode configurar o tempo que expira esta chave.
Deixe sempre marcado a opção **REPOSITÓRIO**, dentro do campo **SELECIONAR ESCOPOS**.

Você copiar esse Token e salvar em algum lugar seguro da sua máquina.
Muito importante você copiar este token porque na própria página do Github ele avisa que você não verá mais esse token.



#### Agora vamos testar ele, vamos usar ele no Git Bash.

Primeiramente vamos acessar novamente nosso repositorio criado no GitHub e quando for copiar o codigo, vamos ter que usar outro link de acesso, pois a chave SSH ele já está configurado na nossa máquina, ou seja, não vai pedir o token para acesso, neste caso vamos copiar o link HTTPS,.

Agora no terminal do Git, digitar o comando git clone e colar o link HTTPS:

Depois disso vai pedir para você logar no github ou colar a chave token de acesso.

Feito o repositório foi baixado usando um token de acesso.
