# Passo a passo no Ciclo de Vida

**GIT INIT** - Esse comando além de criar a pasta .git , ela também inicializa o conceito do git chamado repositório.

**Repositório:** lugar onde se guarda, arquiva, coleciona alguma coisa.
**Diretório:** Pasta, é uma estrutura utilizada para organizar arquivos em um computador ou um arquivo que contém referências a outros arquivos. Um diretório pode conter referências a arquivos e a outros diretórios, que podem também conter outras referências a arquivos e diretórios.

**Qual diferença entre Repositório e Diretório**: uma pasta no universo dos sistemas operacionais serve para armazenar arquivos, e diretório é um sinônimo de pasta, e repositório também é um local para armazenar arquivos, no final todos são sinônimos mesmo, porém a grande diferença é que no controle de versão (git ou outros) um repositório é um local onde os arquivos são armazenados e monitorados, já em uma pasta ou diretório qualquer da sua máquina isso não acontece a menos que você inicialize um no repositório.




#### **Tracked ou Untracked - Estágios dos Arquivos**

**Untracked:** São os arquivos que o Git não te ciência dele

**Tracked:** São os arquivos que o Git tem ciência dele.



<u> Tracked pode se dividir em 4 estágios diferentes, são eles:</u>

**Unmodified:** O arquivo que ainda não foi modificado
**modified:** E o arquivo Unmodified que sofreu alteração
**Staged:** E o conceito chave, e onde fica os arquivos se preparando para outro tipo de agrupamento
**Commit:** podem ser considerados versões "seguras" de um projeto, o Git nunca os altera, a menos que você peça a ele.

Ex Receita do Strogonoff

Quando criamos a pasta, incluímos a receita e salvamos, nesse momento o arquivo esta Untracked, porque o git ainda não sabia da existência dele.

Quando rodamos o segundo comando o **GIT ADD *** , ele móvel o arquivo de Untracked direto para Unmodified, ou seja, tirou o arquivo para uma área onde ele está esperando algo, alguma alteração.

Os arquivos Modified, ele altera automaticamente quando sofre uma alteração, como ele moda disso, o GIT vai comparar o SHA1 dos arquivos, e vai descobrir que o arquivo teve alteração.

Se agente rodar o GIT ADD * novamente neste arquivo ele vai para "STAGE" (STAGED), e uma área especial onde o GIT fica aguardando para entrar em ação, para executar uma outra ação ou entrar em outro grupo.

E se agente tiver um arquivo Unmodified que não sofreu alteração nenhuma e agente remove ele, ai ele volta para Untracked.

Quando o arquivo está no estado Staged ele está se preparando para fazer parte de um Commit. Commit e um objeto chave do Git, então quanto colocamos os arquivos no Staged, esperando ele entrar em ação, agente dá um commit neles, ou seja, agente envelopa todas essas informações com significância, agente escreve uma mensagem para nosso Commit, essa mensagem carrega um autor e uma data, integram de fato o Commit.

O Commit por sinal retorna os arquivos para Unmodified, antes guardando, "tirando uma foto" do código ou do arquivo naquele estágio, para recomeçar o ciclo, aguardando novas modificações,



#### O que os repositórios significam

Separação de dois ambientes _SERVIDOR_ e _AMBIENTE DE DESENVOLVIMENTO_.

**Ambiente de Desenvolvimento:** Representa tudo que está em nossa máquina.

**Servidor:** O Git e um sistema distribuído, vai ter uma versão no servidor que no caso é o GitHub, e tem a versão que está na nossa máquina. Ou seja, as alterações que você faz em sua máquina não repercutem imediatamente na versão que está repositório remoto que está guardado no servidor.



#### Servidor:

- Remoto Repository - Repositório Remoto

#### Ambiente de desenvolvimento:

- **Working Directory** - Repositório de Trabalho (E o que estamos utilizando no nosso livro-receitas)

- **Staging Area** - Área de stang - Os arquivos vão sempre se alternando entre o repositório de Trabalho e o Staging Área a medida que você vai adicionando novos arquivos neste trabalho, modificando enfim...
- **Local Repository** - Repositório Local - Quando você faz um Commit ele passar a integrar o seu repositório local, e seu repositório local pode ser empurrado para seu repositório remoto.

Seu Repositório local só vai ser composto por Commits, então tudo que está no seu repositório local tem que estar commitado, caso contrário você consegue enviar esse repositório local, para o repositório remoto.

Comando *git status*: Vai ajudar agente a monitorar os estagios dos arquivos, vai dizer para gente se o arquivo está Untracked ou Tracked (Unmodified, modified ou Staged). E um comando que vamos usar com muita freqüência.



#### Como alterar o nick do git

git config --global --unset "o que você deseja alterar"

**ex e-mail:**
git config --global --unset user.email



#### Como apontar nosso repositório local para o GitHub

_Qual o endereço desse repositório?_
E um URL simplesmente, e só copiar no quadro **"envie um repositório existente a partir da linha de comando"** 

O que vamos fazer agora e empurrar a versão do nosso repositório local, para o repositório remoto.

Primeiramente temos que adicionar a origem, para qual agente está enviando esses arquivos, o comando é:

**git remote add origin "link URL copiado do GITHUB"**

**git remote -v :** Listar as listas de repositórios remotos que tenho cadastrado;

O comando que vamos usar para levar o nosso código do repositório local para o repositório remoto, ele traduz do inglês diretamente empurrar push, segue comando abaixo:

**git push origin master**

Após apartar enter, vai aparecer uma caixa para incluir a senha, pode ser token, ou ssh.



#### Resolvendo conflitos

Conflito acontece quando o arquivo está no GitHub, e duas ou mais pessoas puxam o arquivo para o repositório local, em suas máquinas, ambos fazer alterações na mesma linha porem com diferentes caracteres no arquivo e sobem o arquivo novamente para GitHub, o primeiro arquivo vai subir normalmente, porém o segundo arquivo da outra pessoa não vai conseguir subir, vai aparecer uma mensagem de erro, falando que seu arquivo não está atualizado, Neste caso você tem que puxar o arquivo do GitHub, que a outra pessoa ja atualizou, e unificar manualmente as informações que foram alteradas na mesma linha.

Esse conflito chama conflito de Merge (mesclar)

**Obs:** Só da conflito neste caso se as alterações forem feitas na mesma linha.

condigo puxar, trazer o código do github para sua máquina.

**git pull origin master**

Após abrir o arquivo, verificar o conflito e só ajustar da maneira que convém, salva o arquivo, depois vai no git e dá um status, vai aparecer um both modified (erro)

Agora e ser vim com o comando **git add *** (adicionar tudo o arquivo), depois e só comitar usando o comando **git commit -m "resolve conflitos"**, agora e só empurrar esse arquivo atualizado para o repositório remoto GITHUB, usando o comando push, **git push origin master.**



#### Como baixar um código, baixar um repositório do GitHub para seu repositório local

Vá um repositório que você queira baixar, clique no botão verde de código. Você pode baixar pelo HTTPS , SSH ou CLI do GitHub.

Vamos utilizar o HTTPS, copiando o link.
No git bash vamos no diretório base, a pasta WORKSPACE
Vamos usar o comando **git clone + colar o link do GitHub**

Todo repositório tem uma pasta oculta **.git/**.
