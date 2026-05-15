

De maneira geral, os modelos de linguagem não possuem **memória persistente** entre interações, ou seja, eles não "lembram" de conversas passadas depois que a interação termina. No entanto, dentro de uma única interação, o modelo consegue manter o contexto do que foi dito por meio da **janela de contexto**, que **é o limite de tokens que o modelo pode processar simultaneamente.

Cada modelo possui uma janela de contexto diferente, e quando o limite dela é atingido, os tokens mais antigos começam a ser descartados para dar espaço aos mais novos.



### 

# Analogia: Professor Escrevendo na Lousa

De forma análoga, imagine uma lousa em uma sala de aula. Ela tem um espaço limitado para escrever. À medida que o professor vai adicionando mais informações, ele precisa apagar o que escreveu primeiro para poder adicionar mais conteúdo.

O modelo funciona da mesma maneira: ele mantém as informações dentro do limite da janela de contexto, mas, quando esse limite é alcançado, as informações mais antigas são descartadas para que as novas possam ser processadas.


### 

# Exemplo: "O que é Aliança?"

Por exemplo, se você perguntar para o modelo "Em poucas palavras, o que é Aliança?". Ele vai retornar uma resposta genérica, pois depende do contexto.

Em seguida, se perguntarmos "O que é Azeroth?", ele vai responder que é um mundo fictício onde se passa a maior parte da história do universo de World of Warcraft. Agora, se perguntarmos para ele "O que é Aliança?" novamente, ele vai usar o contexto do nosso prompt anterior e vai trazer como resposta que a Aliança é uma das duas principais facções em World of Warcraft.


## **Exemplo de Prompt:**

```
Usuário: Em poucas palavras, o que é Aliança?
IA: Aliança é uma associação ou acordo entre partes para alcançar objetivos comuns, geralmente envolvendo cooperação e compromisso mútuo.

Usuário: O que é Azeroth?
IA: Azeroth é o nome do mundo fictício onde se passa a maior parte da história do universo de World of Warcraft, um popular jogo de RPG online. É um planeta cheio de diferentes raças, facções e seres, com uma rica mitologia e história.

Usuário: O que é Aliança?
IA: A Aliança é uma das duas principais facções em World of Warcraft, composta por várias raças como humanos, elfos, anões, gnomos, draenei e worgen. Ela busca a paz, a justiça e a proteção contra as ameaças do mundo, muitas vezes entrando em conflito com a Horda, a facção oposta.
```


Isso acontece, pois está dentro da janela de contexto dele, mas se a conversa continuar e ultrapassar o limite da janela, ele pode perder o início da conversa, necessitando que você reforce os pontos importantes caso queira que eles permaneçam no foco.



### 

# Personalização

No ChatGPT, por exemplo, é possível personalizar a experiência com funcionalidades como [memória](https://help.openai.com/en/articles/8590148-memory-faq) e [instruções](https://help.openai.com/en/articles/8096356-custom-instructions-for-chatgpt) [personalizadas](https://help.openai.com/en/articles/8096356-custom-instructions-for-chatgpt), que permitem ao modelo armazenar algumas informações entre os chats ou seguir diretrizes específicas dadas pelo usuário para melhorar as respostas.