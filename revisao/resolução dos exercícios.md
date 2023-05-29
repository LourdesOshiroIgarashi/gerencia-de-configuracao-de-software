# Resolução dos exercícios de revisão - P2

## (Questão 1) 
Para cada uma das situações abaixo indique o conjunto de comandos git recomendado:

### A. Criar um branch e mover para um branch;
* git branch develop
* git checkout develop

### B. Atualizar o repositório local com a versão mais recente do repositório remoto, após isso modificar um arquivo, realizar um commit e mandar as alterações para o repositório remoto;
* git pull
* (modificar arquivo)
* git status
* git add .
* git commit -m “mensagem de commit”
* git status 
* git push

Observação: o git status antes e após a realização do commit é uma boa prática para conferir, anteriormente, os arquivos que foram alterados e, depois, para conferir que o commit foi realizado com sucesso.

### C. Você precisa mesclar ramos mas sem perder o histórico de evolução das versões;
* git checkout <ramificação-que-receberá-as-atualizações>
* git merge <ramificação-com-as-atualizações-desejadas>

### D. Quando estamos trabalhando na branch e sabemos que o repositório master foi
atualizado por outros desenvolvedores e precisamos ter nosso branch atualizado.
* git pull origin master

## (Questão 2) 
O que é ramificação? O que é um modelo de ramificação? (1,0)

R: Uma ramificação é uma linha de desenvolvimento separada que possui seu próprio histórico de commits, permitindo que os desenvolvedores trabalhem em paralelo em diferentes recursos, correções de bugs ou experimentos. A ramificação refere-se à criação de cópias independentes do repositório principal, permitindo que diferentes fluxos de trabalho ocorram simultaneamente sem afetar o ramo principal.
Um modelo de ramificação refere-se a um conjunto de práticas e estratégias para gerenciar as ramificações em um projeto. Existem vários modelos de ramificação populares, como o modelo Git Flow, GitHub Flow, One-Flow, Feature Branching, Release Branching, que fornecem diretrizes sobre como criar, mesclar e gerenciar ramificações em projetos de software.

## (Questão 3) 
Considere o cenário a seguir para indicar o motivo da escolha de um
branching model recomendado. Justifique sua decisão.
“Ash, Misty e Brock irão compor uma equipe distribuída (Japão, Brasil, Espanha, EUA) de
engenharia de jogos. O projeto se trata de um novo jogo de mundo aberto da série
Pokémon. Eles aproveitarão de mecanismos do jogo já existente. E, fora isso, uma
exigência da empresa é que os bugs indicados pelos jogadores sejam rapidamente
corrigidos, mas que isso não atrapalhe o desenvolvimento de novas funcionalidades. A
equipe tem uma composição de alta senioridade, exceto por Ash, Misty e Brock serem
plenos;”

O modelo Git Flow é uma escolha recomendada para uma equipe distribuída. Ele oferece um fluxo de trabalho estruturado que suporta o desenvolvimento contínuo de novas funcionalidades permitindo que eles trabalhem em paralelo, desenvolvendo novas funcionalidades sem afetar o ramo principal; a correção rápida de bugs(hotfix) para solucionar o problema imediatamente; e a manutenção de uma ramificação principal estável (master), representando a versão estável do jogo, isso é importante para garantir que apenas as funcionalidades testadas e revisadas sejam incorporadas à versão final. Além disso, a ramificação develop é usada como uma ramificação de integração, onde as novas funcionalidades são mescladas antes de serem lançadas. 
Essa estrutura clara e robusta ajuda a manter um fluxo de trabalho organizado e um histórico de versões confiável para o gerenciamento de ramificações, ideal para equipes com composição de alta senioridade.

## (Questão 4) 
Dadas as imagem abaixo descreva baseado no histórico de versão o que aconteceu com o projeto dentro do repositório. Por exemplo, quantos commits foram feitos em uma determinada branch, se houve criação de branch. Se foi feito merge...Recupere a maior quantidade de informações possíveis

### Imagem A
* O repositório remoto foi clonado para o repositório local 
* Foram feitos 2 commits localmente na branch master
* Foi criado a branch development
* A branch atual local foi alterada para a development
* A branch atual é a development

Observação: As alterações realizadas não foram enviadas para o repositório remoto

### Imagem B
* O repositório remoto foi clonado para o repositório local
* Foram feitos 2 commits localmente na branch master
* O repositório remoto foi atualizado com as alterações (os 2 commits)
* A branch atual é a master

### Imagem C
* O repositório remoto foi clonado para o repositório local
* Foram feitos 2 commits na branch master
* Foi criado a branch development
* A branch atual local foi alterada para a development
* Foram feitos 2 commits na branch development
* As alterações da branch development foram enviadas para a branch development remota (push)
* A branch atual local foi alterada para a master
* Foram feitos 2 commits na branch master
* As alterações da branch master foram enviadas para a branch master remota (push)
* A branch atual é a master 

* Todas as alterações estão atualizadas tanto remotamente como localmente nas 2 branches

Observação: os 2 commits realizados na branch master após a criação da branch development estão apenas na branch master, a branch development não possui esses commits. O mesmo ocorre com a branch development: os 2 commits realizados na branch development após a criação da branch development estão apenas na branch development, a branch master não possui esses commits.

### Imagem D
* O repositório remoto foi clonado para o repositório local
* Foram feitos 2 commits na branch master
* Foi criado a branch development
* A branch atual local foi alterada para a development
* Foram feitos 2 commits na branch development
* As alterações da branch development foram enviadas ao repositório remoto (push)
* A branch atual local foi alterada para a master
* Foram feitos 2 commits na branch master
* Foi feito o merge das alterações da branch development para a branch master
* As alterações da branch master foram enviadas ao repositório remoto (push)
* Foi realizado 1 commit na branch master
* A branch atual é a master 

Observação: O último commit está apenas no repositório local, não foi atualizado para o remoto.

## (Questão 5) Considerando a imagem de log abaixo responda ao que se pede:

### a) Se for realizado um commit. As ICs irão para qual ramificação?

R: Caso seja realizado um commit, as ICs vão para a ramificação develop.

### b) A ramificação “develop” existe no repositório remoto?

R: Sim, é possível fazer essa afirmação devido ao "remote/origin/develop".

### c) O que significa “origin” ?

R: "Origin" é um termo convencional usado para facilitar a referência ao repositório remoto original e identificar o repositório remoto padrão a partir do qual você clonou. Após clonar um repositório remoto para o seu ambiente local usando o comando git clone, o Git atribui automaticamente o nome "origin" a esse repositório remoto. Além disso, o "origin" também é usado para diferenciar as ramificações locais das ramificações remotas após o clone do repositório, o Git atualiza as referências das ramificações remotas no seu repositório local, prefixando-as com remotes/origin/. 
Por exemplo, a branch develop no repositório remoto é representada como remotes/origin/develop no seu repositório local.

### d) Quais são as ramificações do repositório local?

R: As ramificações do repositório local são a develop e a main.

### e) As ramificações locais também existem remotamente? Quais são?

R: Sim, ambas as ramificações locais, develop e main, existem remotamente.
