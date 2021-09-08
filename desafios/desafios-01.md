## Os testes:

Estes testes devem cobrir o básico do novo editor de conteúdos do WordPress, também conhecido como [Gutenberg](https://wordpress.org/gutenberg/). Não esperamos que você já tenha familiaridade com ele do zero, já que ele em si é relativamente recente, mas esperamos que com seus conhecimentos em PHP e React você possa se virar bem com a [documentação](https://developer.wordpress.org/block-editor/developers/) e [tutoriais](https://developer.wordpress.org/block-editor/tutorials/) existentes por aí. Dividimos o teste em cinco fases:

1. Um Hello Word! básico dos blocos;
2. Um simples bloco collapse;
3. Um bloco que busca dados dinamicamente de uma API rest;
4. O mesmo bloco anterior, porém com opções de filtragem;
5. Blocos dentro de blocos!

Embora um código possa contribuir para o outro, sugerimos que você faça um bloco para cada, de preferência organizado em suas próprias pastas. Ao final da entrega, vamos bater um papo sobre como você fez o código.

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

Se você chegou até aqui, parabéns! Que tal melhorarmos um pouco o bloco de itens? Crie uma opção no InspectorControls para filtrar a busca pela taxonomia `typeItems`. Pode ser um select mostrando os Tipos de Itens existentes. Ao se escolher um deles, a busca pela API de itens deve ser filtrada via query. Vale uma pesquisada no Google para entender como APIs do WP realizam esta filtragem, caso você não saiba ;)

### 5 - Um bloco com blocos dentro dele!

Vamos dificultar um pouco mais: no bloco da lista de itens, você provavelmente usou suas próprias tags de imagem, parágrafo e cabeçalhos para mostrar o card de um item. E se estes caras também forem blocos? Faça com que seu bloco crie uma lista de cards, onde cada card na verdade é composto pelos blocos de Parágrafo e Imagem padrão do WordPress. Para entender como fazer isso você provavelmente vai ter que procurar por estes três conceitos: InnerBlocks, Block Templates e Child Blocks.

## Endpoints da API REST:

- Posts: `http://localhost:8012/wp-json/wp/v2/posts`
- Items: `http://localhost:8012/wp-json/wp/v2/items`
- Tipos de Itens: `http://localhost:8012/wp-json/wp/v2/typeItems`
