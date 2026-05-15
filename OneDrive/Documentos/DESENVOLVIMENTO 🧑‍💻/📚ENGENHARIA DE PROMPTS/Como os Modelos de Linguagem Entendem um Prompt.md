

Os **Modelos de Linguagem de Grande Escala** (LLMs) são treinados com grandes volumes de dados textuais para compreender e gerar linguagem natural. Em vez de "entender" o texto como um ser humano, o modelo calcula probabilidades com base nos padrões aprendidos durante o treinamento. Esses modelos são fundamentados principalmente na arquitetura **Transformer**, apresentada no artigo "Attention Is All You Need" (Vaswani et al., 2017).


A arquitetura **Transformer usa mecanismos de atenção para processar palavras em sequência, considerando o contexto de cada palavra em relação a todas as outras no texto**, e não de forma linear, como em modelos anteriores. Isso permite que os LLMs compreendam o contexto de um prompt de maneira mais eficaz, gerando respostas mais coerentes e contextualmente relevantes.

Para simplificar ainda mais esse conceito, vamos fazer uma analogia com um editor experiente revisando um texto.

 

Analogia: Editor Experiente Revisando um Texto

Imagine que o editor está analisando uma frase como "Ana pegou o livro porque achou interessante". Para entender completamente, ele não lê apenas palavra por palavra na ordem, mas consulta outras partes do texto, como quem é "Ana" ou por que o livro seria "interessante".



![[Pasted image 20250828083342.png]]


De maneira simplista, esse processo de buscar conexões em diferentes partes do texto, sem seguir uma ordem rígida, é como o mecanismo de atenção do Transformer, que destaca automaticamente os trechos mais relevantes para o contexto, facilitando uma análise mais precisa e rápida.


### 

# Como os Modelos Processam os Prompts?

Quando você fornece um prompt a um modelo de linguagem, ele transforma o texto em uma sequência de **tokens — unidades básicas que podem ser palavras, partes de palavras ou até caracteres**. Essa sequência é processada pelas camadas de atenção e por outras transformações até gerar a resposta.


# Exemplo: Tokenização


## ****utilizando o app da openIA

O [Tokenizer](https://platform.openai.com/tokenizer)

A DIO é a primeira plataforma Open Education brasileira dedicada a tornar o conhecimento em tecnologias exponenciais acessível a todos.

![[Pasted image 20250828084911.png]]
Após a tokenização, os tokens são convertidos em embeddings, que são representações vetoriais que capturam seu significado. Esses embeddings passam por camadas de redes neurais com transformadores, onde o modelo aplica operações de atenção para entender o contexto. O modelo então gera uma distribuição de probabilidade para prever o próximo token, repetindo o processo até gerar a sequência desejada.