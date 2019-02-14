# Uma introdução ao JavaScript

Vamos ver o que há de tão especial em JavaScript, o que podemos conseguir com ele e quais outras tecnologias se conectam bem com ele.

## O que é JavaScript?

*JavaScript* foi criado inicialmente para *"tornar páginas da web vivas"*.

Os programas nessa linguagem são chamados *scripts*. Eles podem ser escritos diretamente no HTML de uma página e executados automaticamente à medida que a página carrega.

Scripts são providos e executados como texto simples. Eles não precisam de preparação especial ou compilação pra rodar.

Nesse aspecto, JavaScript é muito diferente de outra linguagem chamada [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Por que <u>Java</u>Script?"
JavaScript tinha outro nome quando foi criado: "LiveScript". Mas Java era bem popular na época, então foi decidido que colocar a linguagem como um "irmão mais novo" de Java poderia ajudar.

Mas a medida que evoluiu, JavaScript ficou totalmente independente com sua própria especificação chamada [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), e agora não tem mais nenhuma relação com Java.
```

Hoje, JavaScript pode executar não somente no navegador, mas também em servidor ou em qualquer dispositivo que tiver um programa especial chamado [engine de JavaScript](https://en.wikipedia.org/wiki/JavaScript_engine).

O navegador tem uma engine imbutida às vezes chamada de uma "máquina virtual de JavaScript".

Engines diferentes têm "codinomes" diferentes. Por exemplo:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- para Chrome e Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- para Firefox.
- ...Existem outros codinomes como "Trident" e "Chakra" pra versões diferentes do IE, "ChakraCore" pra Microsoft Edge, "Nitro" e "SquirrelFish" pra Safari, etc.

Os termos acima são bons para lembrar porque eles são usados em artigos de desenvolvedor na internet. Nós usaremos eles também. Por exemplo, se "um recurso X é suportado por V8", então ele provavelmente funciona em Chrome e Opera.

```smart header="Como engines funcionam?"

Engines são complicadas. Mas o básico é bem fácil.

1. A engine (imbutida se for um navegador) lê ("analisa") o script.
2. Então ela converte ("compila") o script pra linguagem de máquina.
3. E o código de máquina roda, bem rápido.

A engine executa otimizações em cada passo do processo. Ela até mesmo monitora o script compilado à medida que ele roda, analiza os dados que fluem através dele e aplica otimizações ao código de máquina baseado nesse conhecimento. Quando está feito, scripts rodam rapidamente.
```

## O que JavaScript do navegador pode fazer?

Javascript moderno é uma linguagem de programação "segura". Ela não provê acesso baixo nível à memória ou CPU, porque foi inicialmente criada pra navegadores, o que torna isso desnecessário.

As capacidades de JavaScript dependem do ambiente no qual o script está rodando. Por exemplo, [Node.JS](https://wikipedia.org/wiki/Node.js) suporta funções que permitem JavaScript ler/escrever arquivos arbitrários, realizar solicitações de rede, etc.

JavaScript no navegador pode fazer tudo ligado à manipulação de páginas, interação com usuário e com o servidor web.

Por exemplo, o JavaScript no navegador é capaz de:

- Adicionar novo HTML à página, alterar o conteúdo existente, modificar estilos.
- Reagir às ações do usuário, executar cliques do mouse, movimentos de ponteiro, teclas pressionadas.
- Envie solicitações pela rede para servidores remotos, baixar e enviar arquivos (chamados tecnologias [AJAX](https://en.wikipedia.org/wiki/Ajax_ (programação)) e [COMET](https: // en. wikipedia.org/wiki/Comet_(programming))).
- Obter e definir cookies, fazer perguntas para o visitante, mostrar mensagens.
- Lembrar-se dos dados no lado do cliente ("armazenamento local").

## O que o JavaScript do navegador NÃO consegue fazer?

As habilidades do JavaScript no navegador são limitadas em prol da segurança do usuário. O objetivo é evitar que uma página maléfica acesse informações privadas ou prejudique os dados do usuário.

Exemplos de tais restrições incluem:

- JavaScript em uma página da web pode não ler/gravar arquivos arbitrários no disco rígido, copiá-los ou executar programas. Ele não tem acesso direto às funções do sistema operacional.

    Os navegadores modernos permitem que ele trabalhe com arquivos, mas o acesso é limitado e fornecido apenas se o usuário fizer determinadas ações, como "soltar" um arquivo em uma janela do navegador ou selecioná-lo por meio de uma tag `<input>`.

    Existem maneiras de interagir com a câmera / microfone e outros dispositivos, mas eles exigem permissão explícita do usuário. Assim, uma página com JavaScript habilitado pode não habilitar uma câmera web sorrateiramente, observar os arredores e enviar as informações para a [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Diferentes guias/janelas geralmente não se conhecem. Às vezes elas conhecem, por exemplo, quando uma janela usa JavaScript para abrir a outra. Mas, mesmo neste caso, o JavaScript de uma página não pode acessar o outro se eles vierem de sites diferentes (de um domínio, protocolo ou porta diferente).

    Isso é chamado de "Política da mesma origem". Para contornar isso, *ambas as páginas* devem conter um código JavaScript especial que manipule a troca de dados.

    Essa limitação é, novamente, para a segurança do usuário. Uma página de `http://anysite.com` que um usuário abriu não deve conseguir acessar outra guia do navegador com o URL `http://gmail.com` e roubar informações de lá.
- JavaScript pode se comunicar facilmente pela rede com o servidor de onde a página atual veio. Mas sua capacidade de receber dados de outros sites/domínios é prejudicada. Embora possível, requer acordo explícito (expresso em cabeçalhos HTTP) do lado remoto. Mais uma vez, isso é uma limitação de segurança.

![](limitations.png)

Tais limitações não existem se o JavaScript for usado fora do navegador (em um servidor por exemplo). Os navegadores modernos também permitem plugins/extensões que podem solicitar permissões estendidas.

## O que torna o JavaScript único?

Há pelo menos *três* coisas ótimas sobre JavaScript:

```compare
+ Integração total com HTML/CSS.
+ Coisas simples são feitas de forma simples.
+ Suportada por todos os principais navegadores e ativada por padrão.
```
Javascript é a única tecnologia de navegador que combina essas três coisas.

Isso é o que torna JavaScript único. É por isso que esta é a ferramenta mais difundida para criar interfaces de navegador.

Enquanto planeja aprender uma nova tecnologia, é benéfico verificar suas perspectivas. Então, vamos seguir para as tendências modernas que a afetam, incluindo novas linguagens e habilidades de navegador.


## Linguagens "acima" de JavaScript

A sintaxe do JavaScript não atende às necessidades de todos. Pessoas diferentes querem recursos diferentes.

Isso é esperado, porque os projetos e requisitos são diferentes para todos.

Então, surgiu recentemente uma infinidade de novas linguagens, as quais são *transpiladas* (convertidas) para JavaScript antes de rodarem no navegador.

Ferramentas modernas tornam a transpilação muito rápida e transparente, permitindo que os desenvolvedores programem em outra linguagem e convertendo o código automaticamente "por baixo dos panos".

Exemplos de tais linguagens:

- [CoffeeScript](http://coffeescript.org/) é um "açúcar sintático" para JavaScript. Introduz uma sintaxe mais curta, permitindo escrever código mais claro e preciso. Normalmente, o Ruby é como ele.
- [TypeScript](http://www.typescriptlang.org/) se concentra em adicionar "digitação estrita de dados" para simplificar o desenvolvimento e suporte de sistemas complexos. É desenvolvido pela Microsoft.
- [Dart](https://www.dartlang.org/) é uma linguagem autônoma que possui seu próprio mecanismo que é executado em ambientes sem navegador (como aplicativos móveis). Ele foi inicialmente oferecido pelo Google como um substituto para o JavaScript, mas, a partir de agora, os navegadores exigem que ele seja transferido para o JavaScript como os acima.

Existem muitas outras. Mesmo usando uma dessas linguagens, é claro que devemos também conhecer JavaScript para entender o que estamos realmente fazendo.

## Resumo

- Inicialmente, JavaScript foi criada somente para navegador, mas agora é usada em muitos outros ambientes.
- Hoje, JavaScript tem uma posição única como a linguagem de navegador mais adotada, com total integração com HTML/CSS.
- Existem muitos idiomas que são "transpilados" para JavaScript e fornecem certos recursos. Recomenda-se dar uma olhada neles, pelo menos brevemente, depois de dominar o JavaScript.
