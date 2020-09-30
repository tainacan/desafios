# Desafio de seleção

## configuração inicial:
para executar o ambiente do desafio, você precisa ter instalado em sua máquina o docker e o docker-compose:

1 - para instalar o docker: https://docs.docker.com/get-docker/

2 - para instalar o docker-compose: https://docs.docker.com/compose/install/


### estrutura de diretórios:
a estrutura de diretório do ambiente é descrita a seguir:
```
  data -> pasta que armazena o banco de dados do wordpress.
  volumes/html -> pasta com os arquivos da instalação do wordpress
  docker-compose.yml -> arquivo yml com a configuração do ambiente
  README.md -> arquivo com instruções
  run.sh -> script para auxiliar a subir e derrubar o ambiente (apenas ambiente linux)
```

### iniciando o ambiente:
para inicializar o ambiente de desenvolvimento, você pode na raiz do diretório, executar o seguinte comando:

* `./run.sh --start`: Vai inicializar os serviços, na primeira execução ele deve demorar um pouco pois irá baixar as imagens do repositório do docker.

* `./run.sh --start-bg`: Mesmo comportamento do `--start` porém roda o processo em segundo plano

> *observação*: o script `run.sh` foi testado somente em ambientes Linux, caso você utilize outro sistema operacional você pode utilizar os comandos padrões do docker-compose: [ `docker-compose up` ou `docker-compose up -d` ]

após inicializar o ambiente você pode acessar atraves de um navegado o endereço: [http://localhost:8012/](http://localhost:8012/) que uma instalação padrão do wordpress deve ser exibida.

para acessar a painel administrativo, você deve utilizar o endereço:
[http://localhost:8012/wp-admin](http://localhost:8012/wp-admin) com as credenciais:

```
user: dev
password: dev123
```

### desativando o ambiente:
* `./run.sh --stop`: Finaliza os serviços.

> *observação*: o script `run.sh` foi testado somente em ambientes Linux, caso você utilize outro sistema operacional você pode utilizar os comandos padrões do docker-compose: [ `docker-compose down` ]

## Teste:

Testes para o editor de blocos do WordPress
Estes testes devem cobrir o básico do novo editor de conteúdos do WordPress, também conhecido como Gutenberg. Não esperamos que você já tenha familiaridade com ele do zero, já que ele em si é relativamente recente, mas esperamos que com seus conhecimentos em PHP e React você possa se virar bem com a documentação (https://developer.wordpress.org/block-editor/developers/) e tutoriais (https://developer.wordpress.org/block-editor/tutorials/) existentes por aí. Dividimos o teste em três fases:
1. Um Hello Word! básico dos blocos;
2. Um simples bloco collapse;
3. Um bloco que busca dados dinamicamente da API usada nos testes anteriores;
Ao final da entrega, vamos bater um papo sobre como você fez o código.
1 - Hello Word!
Este teste deve servir para cobrir o básico de se registrar um bloco. O código de registro pode ser feito no próprio tema usado nos testes anteriores. Ao se inserir o seu bloco, um texto em negrito escrito "Hello World!" deve aparecer no editor de blocos. Você pode pesquisar, além da documentação do WordPress mencionada acima, outros tutoriais e ferramentas para te ajudar, só reforçamos que queremos que você explique o funcionamento do seu código.
2 - Criando um collapse interagível
Está na hora de criar algo com pouco mais de graça. Permita que os usuários definam qual conteúdo textual ele vai ter. Você pode fazer isso tanto modificando uma opção no InspectorControls (A barra lateral de configurações: https://developer.wordpress.org/block-editor/tutorials/block-tutorial/block-controls-toolbar-and-sidebar/) ou usando o componente RichText (https://developer.wordpress.org/block-editor/developers/richtext/).
Feito isto, permita que o conteúdo seja collapsável. Deve existir um botão dentro do bloco que fará com que o conteúdo todo se esconda ou reapareça. Fique atento que para isso você provavelmente precisará registrar scripts que rodam na versão publicada do seu post! 
3 - Obtendo dados da API
E se ao invés de deixar o usuário inserir dados você quiser buscar dados de uma API? Crie um bloco que liste itens da API criada anteriormente. Exiba título, descrição e imagens em um card com o layout que você preferir. ATENÇÃO: a consulta a API deve ocorrer não só do lado do editor mas também no post publicado. Isto significa que este bloco agora é dinâmico! Fica a dica: https://developer.wordpress.org/block-editor/tutorials/block-tutorial/creating-dynamic-blocks/



## endpoints da API REST:
* posts: http://localhost/wp-json/wp/v2/posts
* items: http://localhost/wp-json/wp/v2/Item