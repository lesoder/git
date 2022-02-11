# Adiciona os novos arquivos e modificados para o proximo commit
   $ git add .
# Registra o commint com todos os arquivos do gti add # -m "Adiciona uma mensagem"
   $ git commit -m "first commit"

# Status
   $ git status 
# para alterar o editor padrão do git
   $ git config --global core.editor

# Conf de usuário e email 
   $ git config --global user.name "lesoder"
   $ git config --global user.email "le.soder@gmail.com"
   $ git config --global init.defaultBranch main


# lista a conf 
   $ git config --list
      user.email=le.soder@gmail.com
      user.name=lesoder
      core.repositoryformatversion=0
      core.filemode=true
      core.bare=false
      core.logallrefupdates=true
      remote.origin.url=https://github.com/lesoder/azure.git
      remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
      branch.main.remote=origin
      branch.main.merge=refs/heads/main

# mostra os ultimos logs 
   $ git log 
   $ git log --oneline --decorate

# Lista os repositorios remotos 
   $ git remote -v 

# HEAD " Indica o direotiro " branch" de trabalho atual" 
   $ git log
commit 35b1e261067d00e843ef232f87ebcc1833649d9d (HEAD -> main, origin/main, origin/HEAD)
   $ git log --oneline --decorate --all --graph
# git checkout
  - Utlizado para trocar de branch
    $ git checkout feature1 
  - Para validar 
    $ cat .git/HEAD
    ref: refs/heads/feature1 
  - Permite ver como um arquivo ou todo o repositório estava em um determinado commit
  - Altera o repositorio para o estado daquele commit
  - Util para fazer testes antes e depois de alterações
    $ git checkout 97e24ef93720c936ea7806040b33af5807064afa
  - Para voltar o repositório no ultimo
    $ git checkout master
  - Para criar e já fazer checlout em uma branch
    $ git checkout -b feature1
    Switched to a new branch 'feature1'

# git checkout Desfazendo alterações
  - Irá desfazer todas as alterações que ão estajan no stage desde o ultimo commit 
    $ git checkout -- <path file>
  - Desfazer as alterações desde o ultimo commit incluido o stage
    $ git checkout HEAD -- <path file>

# Git merge
  - Aplicar os commits de uma branch na branch atual.
  - Encontra um commit comum(base) entre as branchs e aplica todos os commits que a  branch atual não possui
  - Caso existam commits na branch atual que não estão na outra, sera criado um commit de merge. 
  - Para Fazer merge da branch "main"  para branch  "feature1"
    $ git branch 
      * main
    $ git merge feature1 
    Already up to date.
    " fast-forward" é uma atualização da referência e só é possivel quando não existe digergências  entre os branches.
  - Para apagar a branch feature1, pois não é mais necessário 
     $ git branch -d  feature1 
  - Para merge com divergencia, o git gera um novo commit, colocar mensagem 
     $ git merge feature1 
# Git Stash
  - é possivel armazenar código, sem a necessidade de realizar um commit
  
# Git push 
  - é a acão de atualizar uma referẽncia remota a partir de uma referência local, enviando os objetos necessários para satisfazer as referências atualizadas. 
ssh -T git@github.com
git remote -v 
git config --global user.email "le.soder@gmail.com"
git config --global user.name "lesoder"
git remote add origin git@github.com:lesoder/docker.git
git remote -v 
git push -u origin main
git push -u origin main
git push -u origin main
git push origin master

git remote rm origin
git remote add origin git@github.com:lesoder/docker.git

# Estados dos arquivos
- não monnitorado (untracked)
- modificado (modified)
- Preparado (staged)
- Consolidado (commited)
 
# Comando git diff
- Exibir diferenças entre commits e branchs
 $git diff [path]
- diferença no diretorio  "HEAD~1 ponteiro para o ultimo commit na branch
  $git diff HEAD~1 
- Mostra que foi alterado no ultimo commit 

# git clone 
- baixa o repositorio remoto
- Outra forma de criar um repositorio local
- já vem com o remote configurado
 $git clone git@github.com:lesoder/docker.git

# git pull
- baixa as alterações do repositorio remoto
- Mantém o repositorio sincronizado com os ultimos  commits de uma branch
  git pull



# git revert
- Ira criar um  novo commit que defaz as alterações do commit especifico 
- Útil para desfazer um commit antigo
  $ git revert 38db70d430e124a76a4bd7bfbd855968165f40cf

# git diff
  $ git diff 38db70d4 d0074e8
  diff --git a/README.md b/README.md
  index 118e555..4fee6e4 100644
  --- a/README.md
  +++ b/README.md
  @@ -1,5 +1,3 @@
 
# git Reset
  - Resetar o repositorio para um determinado commit
  $ git reset <commit>
  - resetar e remover todas as alterações.
  -- Cuidado ao usar, Não usar se já estiver publicando
  - Util para desfazer ultimos commits
  $ git reset --hard <commint>

# Conflitos 
  - Conflitos podem acontecer ao unirmos alterações
  - Acontecem quando versões diferentes possuem as memas linhas nos mesmos arquivos editados diferentes
  - O git identifica os conflitos e fica aguardando a solução deles
  - Ao resolver os conflitos deve ser feito um commint

# Branch 
- é uma lista de commits
- Representa ramificações no repositório   
- Muito útil para trabalhos colaboraticos
- branchs de desenvolvimentos facilitam o controle 
- Branch master é a padrão
- cria uma nova branch
  $ git branch nova_branch
- Excluir uma Branch
  $ git branch -d <branch>
- Para mudar de branch 
  $ git checkout branch
- Seu repositório passa a ter os commits que a branch possui e novos commits serão   Adicionados a ela

# Exercício 4
- Criar uma nova branch no seu repositório
- Mude para está branch e faça pelo menos 2 commits
- Faca o push e veja nova branch no github
- Faça um commit na master que altere as mesmas linhas 


# Git rebase
- Semelhante ao Merge porém é diferente na ordem de aplicar os commits
- No rebase, os seus commits na frente da base são removidos temporariamente, e os commits de outra branch são aplicados 
na sua branch e por fim seus commits são apicados um a um.
- Pode ocorrer comflitos que serão resolvidos para cada commit.
