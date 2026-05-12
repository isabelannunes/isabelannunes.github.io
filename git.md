# Git e Github

## O que é Git?

O Git é um sistema de controle de versão. Podemos imaginá-lo como uma máquina do tempo do nosso projeto: ele permite salvar "fotografias" do estado atual do código em diferentes momentos. Cada uma dessas fotografias é chamada de commit. Assim, a cada etapa concluída do projeto, fazemos um commit para registrar as mudanças feitas. Isso nos permite rastrear, comparar e até reverter modificações ao longo do tempo.

link para um vídeo rápido que explica o que é Git/GitHub e como usar: [https://www.youtube.com/watch?v=-l4Aa8wef8s&t=112s](https://www.youtube.com/watch?v=-l4Aa8wef8s&t=112s)

---

## O que é o GitHub?

O GitHub, por sua vez, é uma plataforma online onde podemos hospedar e gerenciar nossos repositórios Git. 

Ele funciona como uma “nuvem” para os projetos versionados com Git — assim, o que está salvo localmente no seu computador pode ser sincronizado com o GitHub para ficar disponível em qualquer lugar e para outras pessoas.

Além do armazenamento, o GitHub oferece várias ferramentas que facilitam o trabalho em equipe e o desenvolvimento colaborativo, como:

- Pull requests: para propor e revisar alterações no código;
- Issues: para registrar tarefas, bugs ou ideias de melhorias;
- Wikis e Documentações;
- GitHub Actions, que permitem automatizar testes e implantações.

Existem outras plataformas parecidas, como o GitLab e o Bitbucket, mas o GitHub é, atualmente, a mais popular e amplamente utilizada na comunidade de desenvolvedores.

![1527503386626_319578f21381f9641cd8_512.png](1527503386626_319578f21381f9641cd8_512.png)

---

## Por que usar o Git e o GitHub?

- **Organização e histórico:** mantenha o registro completo de todas as alterações feitas no projeto, podendo voltar a qualquer versão anterior.
- **Reprodutibilidade:** garante que qualquer pessoa consiga reproduzir exatamente o estado de um projeto em um determinado momento.
- **Trabalho em equipe:** facilita o desenvolvimento colabor ativo, permitindo que várias pessoas contribuam ao mesmo tempo.
- **Experimentação segura:** permite criar **ramificações (branches)** para testar novas ideias sem comprometer a versão principal do projeto.

---

## Como instalar:

link para instalação do Git: 

[https://git-scm.com/downloads](https://git-scm.com/downloads)

- Windows
    
    No windows, depois de instalado o Git, temos que verificar o lance das variáveis de ambiente (Editar variáveis de ambiente do sistema). Na variável Path, temos que ver se está o caminho do Git e ver se está na localizacao certa.
    
- Dica extra
    
    Se você está em uma IDE ou no terminal, depois de instalado tente fechar e abrir novamente para assim usar o git normalmente.
    

terminal: 
`git --version` #Para confirmar se a instalação foi feita

---

## Configurações iniciais

As configurações a seguir serão feitas para conectar o nosso computador com a nossa conta do GitHub

```bash
git config --global user.email "you@email.com"
git config --global user.name "Your Name"
```

Além disso, precisamos gerar uma chave SSH e adicionar no GitHub para fazer esse link, para isso digitamos o seguinte comando no terminal

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

será criado uma pasta oculta chamada .ssh, ao entrar nela um dos arquivos conterá a chave pública SSH que precisamos.

[Gerando uma nova chave SSH e adicionando-a ao agente SSH - GitHub Docs](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

agora, temos que ir no nosso github → settings → SSH and GPG keys. clicar em “**New SSH key”,** e adicionar a chave SSH Pública que geramos com o comando acima.

[https://github.com/settings/keys](https://github.com/settings/keys)

---

## Criando um Repositório

Depois de criar sua conta no GitHub, clique em “New Repository” para criar um novo repositório.

Na página de criação, você pode definir:

- o nome do repositório,
- uma descrição opcional,
- se ele será público ou privado,
- e se deseja iniciar com um README.

Após criar o repositório, o GitHub exibirá uma página com um tutorial de comandos básicos — é ali que aprendemos como conectar o repositório local (no nosso computador) com o repositório remoto (no GitHub).

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin <url_do_repositorio>
git push -u origin main
```

Em seguida, abriremos o terminal dentro da pasta do projeto que queremos versionar e executaremos os comandos mostrados, prestando atenção às configurações iniciais.

---

## Inicializando o Git

Para inicializar o git, ou seja, para converter um diretório existente no computador em um repositório Git, usamos o seguinte comando:

```bash
git init
```

seguindo, para adicionar o arquivos da nossa pasta local para o git, usamos:

```bash
git add <nome_do_arquivo>
```

ou então, para adicionar todos os arquivos:

```bash
git add .
```

para registrar as nossas adições, usamos o comando abaixo, que vai indicar o nome do nosso registro

```bash
git commit -m "nome_do_commit"
```

O nome do commit deve trazer uma pequena descrição das alterações feitas no código. Existem boas práticas e convenções que ajudam a padronizar esses nomes, assim fica mais fácil visualizar o propósito de cada mudança no histórico do projeto. Em resumo, a mensagem do commit deve facilitar o entendimento e a navegação pelo histórico do Git. Ela ajuda, por exemplo, quando queremos voltar a um ponto específico do projeto, como antes de adicionar um filtro novo ou no momento em que integramos uma nova base de dados.

exemplos: 

- `feat: adiciona etapa de normalização log2 nas contagens`
- `fix: corrige valores ausentes substituindo por média da amostra`

---

## O que é uma branch?

Agora precisamos informar em qual branch — ou seja, em qual ramificação do projeto — queremos adicionar o nosso commit.        Para entender isso, vale lembrar como o sistema de versionamento do Git funciona.

Por padrão, todo repositório começa com uma branch principal, chamada `main`. Ela representa a versão estável do projeto — geralmente aquela que está funcionando corretamente e que será disponibilizada para os usuários.

Quando queremos fazer atualizações, corrigir erros ou testar novas funcionalidades sem correr o risco de quebrar o que já está funcionando, criamos novas branchs.

Essas branchs são cópias da main em que podemos trabalhar de forma isolada. Assim, todas as mudanças feitas ali não afetam o código principal até que estejam prontas e testadas.

Depois de revisar e testar tudo, podemos mesclar (merge) essa branch com a main, atualizando o projeto de forma segura.

![GitHub-Flow-1.png](GitHub-Flow-1.png)

- Comandos para criar e alterar branchs
    
    ```bash
    git branch #para ver quais branchs existem
    ```
    
    ```bash
    git branch <nome_da_nova_branch> #para criar uma nova branch
    ```
    
    ```bash
    git checkout <nome_da_branch> #para alterar para outra branch
    ```
    
    ou entao
    
    ```bash
    # para criar e ja mudar pra nova branch
    git switch -c <nova_branch>
    git checkout -b <nova_branch> 
    ```
    

```bash
git branch -M main
```

Agora, para conectar nosso repositório local com o nosso repositório online, usamos a chave https ou ssh com o comando:

```bash
	git remote add origin <ssh>
```

Depois de fazermos o link, podemos enviar para o github com o comando:

```bash
git push -u origin main
```

esse comando acima só é usado para a primeira vez que fazemos upload para esse repositório, nos próximos podemos usar apenas o git push

---

## Como trabalhar com outras pessoas

O primeiro passo para colaborar em um projeto de outra pessoa é clonar o repositório do GitHub para o seu computador. Para isso, abra uma pasta vazia, depois abra o terminal dentro dela e execute:

```bash
git clone <url_do_repositorio>
```

### 🔑 Permissões de colaboração

Além disso, o dono do repositório precisa te adicionar como **colaborador**. Para isso, ele deve ir até **Settings → Collaborators** e adicionar o seu nome de usuário do GitHub. Somente após essa etapa você poderá enviar alterações diretamente para o repositório. Depois de clonar, você pode trabalhar normalmente: editar arquivos, fazer commits e enviar suas alterações para o repositório remoto com:

```bash
git push origin main
```

### 🔄 Atualizando seu repositório local

Quando outros colaboradores fizerem mudanças e você quiser atualizar seu repositório local, basta executar:

```bash
git pull origin main
```

Dica: para evitar conflitos, é importante sempre dar um `git pull` antes de começar a trabalhar em novas alterações.

### 💡 Boa prática (opcional): Criar um ambiente virtual Python (também é possível com o R)

Ao trabalhar em projetos Python, é uma boa prática criar um ambiente virtual. Ele isola as dependências do projeto, evitando conflitos entre bibliotecas instaladas em outros projetos da sua máquina. Para criar e ativar um ambiente virtual, use:

```bash
python -m venv .venv
source .venv/bin/activate
```

Depois, instale as dependências listadas no arquivo `requirements.txt`:

```bash
pip install -r requirements.txt
```

---

## Resumo do uso no dia a dia

Levando em consideração que você já criou um repositório e quer apenas ir atualizando, aqui vai um resumo do uso no dia a dia

```bash
git status #para verificar as alteracoes feitas
git add . #para adicionar todas as alteracoes
git commit -m "nome_do_commit" #agrupando as alteracoes em um commit
git push #enviando o commit para o repositorio remoto
```

---

## Voltando no tempo

Para desfazer um commit, precisamos do ID dele, para isso executamos:

```bash
git log
```

em seguida

```bash
git revert <ID_do_commit>
```

para alterar o nome de um commit 

```bash
git commit --amend -m "nome_alterado"
```

para apagar de fato um commit

```bash
git reset --hard <id_do_commit_anterior>
```

## Mais recursos

### 📝 README.md

O **`README.md`** é um arquivo escrito em **Markdown** que serve para **apresentar o seu projeto**. Ele é uma forma de **documentação** que fica visível diretamente no repositório do GitHub. No `README.md`, costumamos incluir informações como:

- O que o projeto faz;
- Quais ferramentas e bibliotecas ele utiliza;
- Como está estruturado o código;
- Instruções para instalação e uso;
- Autores, licença e agradecimentos (opcional).

💡 *Dica:* um bom README é como o “cartão de visita” do seu projeto — ajuda outras pessoas (e você mesma no futuro!) a entenderem rapidamente do que se trata.

---

### 🚫 .gitignore

O **`.gitignore`** é o arquivo onde listamos **tudo o que não queremos que o Git rastreie**. Em outras palavras, ele define o que **não será enviado para o repositório remoto**. Isso é essencial para manter o repositório limpo e seguro, evitando enviar arquivos como:

- Dados **privados** (ex.: planilhas com informações sensíveis);
- Arquivos **temporários** do sistema;
- Ambientes virtuais (`.venv/`);
- Saídas geradas automaticamente (`__pycache__/`, arquivos `.log`, etc.).

Para criar, basta adicionar um arquivo chamado `.gitignore` na raiz do projeto e listar nele os arquivos ou pastas que o Git deve ignorar.

Exemplo:

```
# Ambiente virtual
.venv/

# Dados brutos
data/raw/

# Arquivos temporários
__pycache__/
*.log
```

---