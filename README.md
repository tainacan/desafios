# Desafio de seleção

## Configuração inicial:

Para executar o ambiente do desafio, você precisa ter instalado em sua máquina o docker e o docker-compose:

1 - Para instalar o docker: https://docs.docker.com/get-docker/

2 - Para instalar o docker-compose: https://docs.docker.com/compose/install/

### Estrutura de diretórios:

A estrutura de diretório do ambiente é descrita a seguir:

```
  volumes/html -> pasta com os arquivos da instalação do wordpress

  volumes/data -> diretório que armazena o banco de dados do wordpress.

  volumes/init.d -> script de inicialização da base.

  docker-compose.yml -> arquivo yml com a configuração do ambiente
  
  README.md -> arquivo com instruções

  run.sh -> script para auxiliar a subir e derrubar o ambiente (apenas ambiente linux)
```

Durante o desafio, você provavelmente irá trabalhar mais com a pasta do tema `/volumes/html/wp-content/themes/twentyseventeen`.

### Iniciando o ambiente:

Para inicializar o ambiente de desenvolvimento, você pode na raiz do diretório, executar o seguinte comando:

- `./run.sh --start`: Vai inicializar os serviços, na primeira execução ele deve demorar um pouco pois irá baixar as imagens do repositório do docker.

- `./run.sh --start-bg`: Mesmo comportamento do `--start` porém roda o processo em segundo plano

> _observação_: o script `run.sh` foi testado somente em ambientes Linux, caso você utilize outro sistema operacional você pode utilizar os comandos padrões do docker-compose: [ `docker-compose up` ou `docker-compose up -d` ]

Após inicializar o ambiente você pode acessar atraves de um navegado o endereço: [http://localhost:8012/](http://localhost:8012/) que uma instalação padrão do wordpress deve ser exibida.

Para acessar a painel administrativo, você deve utilizar o endereço:
[http://localhost:8012/wp-admin](http://localhost:8012/wp-admin) com as credenciais:

```
user: dev
password: dev123
```

### Desativando o ambiente:

- `./run.sh --stop`: Finaliza os serviços.

> _observação_: o script `run.sh` foi testado somente em ambientes Linux, caso você utilize outro sistema operacional você pode utilizar os comandos padrões do docker-compose: [ `docker-compose down` ]


#### problemas comuns:

```
ERROR: Couldn't connect to Docker daemon at http+docker://localhost - is it running?
```
verifique se o docker foi inicializado corretamente, `docker ps` deve mostrar a lista de containers que está rodando. Pode ser um problema com permissão também, tente usar o __sudo__

---

```
Error starting userland proxy: listen tcp 0.0.0.0:8012: bind: address already in use
```
Algum outro serviço está sendo executado na porta 8012, você deve finalizar esse serviço para que o servidor possa inicializar corretamente.


## Os testes:

Estes testes devem cobrir o básico do novo editor de conteúdos do WordPress, também conhecido como [Gutenberg](https://wordpress.org/gutenberg/). Não esperamos que você já tenha familiaridade com ele do zero, já que ele em si é relativamente recente, mas esperamos que com seus conhecimentos em PHP e React você possa se virar bem com a [documentação](https://developer.wordpress.org/block-editor/developers/) e [tutoriais](https://developer.wordpress.org/block-editor/tutorials/) existentes por aí. Dividimos o teste em quatro fases:

1. Um Hello Word! básico dos blocos;
2. Um simples bloco collapse;
3. Um bloco que busca dados dinamicamente de uma API rest;
4. EXTRA - o mesmo bloco anterior, porém com opções de filtragem.

Ao final da entrega, vamos bater um papo sobre como você fez o código.

### 1 - Hello Word!

Este teste deve servir para cobrir o básico de se registrar um bloco. O código de registro pode ser feito no próprio tema TwentySeventeen. Ao se inserir o seu bloco, um texto em negrito escrito "Hello World!" deve aparecer no editor de blocos.

> Você pode pesquisar, além da documentação do WordPress mencionada acima, outros tutoriais e ferramentas para te ajudar, só **reforçamos que queremos que você explique o funcionamento do seu código.**

### 2 - Criando um collapse interagível

Está na hora de criar algo com pouco mais de graça. Desta vez, permita que os usuários definam qual conteúdo textual seu bloco vai ter. Você pode fazer isso tanto modificando uma opção no InspectorControls (A [barra lateral de configurações](https://developer.wordpress.org/block-editor/tutorials/block-tutorial/block-controls-toolbar-and-sidebar/)) ou usando o componente [RichText](https://developer.wordpress.org/block-editor/developers/richtext/).
Feito isto, permita que o conteúdo seja collapsável. Deve existir um botão dentro do bloco que fará com que o conteúdo todo se esconda ou reapareça. Fique atento que para isso você provavelmente precisará registrar scripts que rodam na versão publicada do seu post!

### 3 - Obtendo dados da API

E se ao invés de deixar o usuário inserir dados você quiser buscar dados de uma API? Crie um bloco que liste itens da API de itens. Exiba título, descrição e imagens em um card com o layout que você preferir.

> ATENÇÃO: a consulta a API deve ocorrer não só do lado do editor mas também no post publicado. Isto significa que este bloco agora é dinâmico! [Fica a dica!](https://developer.wordpress.org/block-editor/tutorials/block-tutorial/creating-dynamic-blocks/)

### 4 - Criando opções de filtragem

Se você cehgou até aqui, parabéns! Que tal melhorarmos um pouco o bloco de itens? Crie uma opção no InspectorControls para filtrar a busca pela taxonomia `typeItems`. Pode ser um select mostrando os Tipos de Itens existentes. Ao se escolher um deles, a busca pela API de itens deve ser filtrada via query. Vale uma pesquisada no Google para entender como APIs do WP realizam esta filtragem, caso você não saiba ;)

## Endpoints da API REST:

- Posts: `http://localhost:8012/wp-json/wp/v2/posts`
- Items: `http://localhost:8012/wp-json/wp/v2/items`
- Tipos de Itens: `http://localhost:8012/wp-json/wp/v2/typeItems`
