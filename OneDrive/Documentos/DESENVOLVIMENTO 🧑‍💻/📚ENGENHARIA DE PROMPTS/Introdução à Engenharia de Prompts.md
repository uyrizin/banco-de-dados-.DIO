




# O que é um prompt

Um prompt é a instrução que você dá a um sistema (humano ou digital) para orientar a resposta. É a forma de “fazer a pergunta” ou “definir a tarefa” com clareza: o que você quer, para qual objetivo, com quais limites e em qual formato. Em IA generativa, o prompt é o texto que guia o modelo a produzir conteúdo (texto, código, imagem, áudio). Em essência, um bom prompt é a tradução do seu desejo em palavras específicas — quanto mais claro você estiver consigo mesmo, melhor a resposta.




# Onde o prompt aparece no dia a dia

- **IA conversacional:** Pedir um resumo, comparar opções, criar um texto, corrigir um email, gerar código.
    
- **Geração de imagens:** Descrever cena, estilo, iluminação, lente, humor, proporção.
    
- **Pesquisa e comandos:** Termos de busca, filtros, operadores; prompt de terminal ou SQL.
    
- **Design e marketing:** Briefings, criativos de anúncio, tom de voz, público, call to action.
    
- **UX/redação técnica:** Instruções, mensagens de erro, formulários que guiam o usuário.


# Elementos de um bom prompt

- **Objetivo:** O que exatamente você quer que aconteça.
    
- **Contexto:** Para quem é, qual cenário, restrições relevantes.
    
- **Critérios de qualidade:** Estilo, tom, nível de detalhe, fontes/formatos.
    
- **Exemplos:** Modelos de saída, few-shot (1–3 exemplos do que é “bom”).
    
- **Formato de entrega:** Tabela, lista com bullets, JSON, passos numerados.
    
- **Restrições:** Tamanho, idioma, regras de conteúdo, datas, limites.
    
- **Papel/perspectiva:** Quem “fala” (ex.: “atuando como redator técnico”).
    
- **Passo a passo:** Pedir raciocínio estruturado ou etapas claras do processo.# Exemplos práticos


# Exemplos práticos


Código

Copiar

```
Atue como redator técnico. Resuma o documento abaixo em até 120 palavras, em português claro, com 3 bullets de conclusões e 1 recomendação acionável. Público: gestores não técnicos. Mantenha termos-chave em negrito. Texto:
[cole aqui o texto]
```

#### Geração de imagens

Código

Copiar

```
Retrato ambiental de uma bióloga no Pantanal ao amanhecer, luz suave
```


#### Terminal/consulta

Código

```
Escreva uma consulta SQL que liste clientes com compras > 1000 nos últimos 30 dias, mostrando nome, total e última compra, ordenado por total descrescente. Assuma tabela orders(customer_id, amount, created_at) e customers(id, name).
```

#### Marketing

Código

```
Crie 2 variações de anúncio para Instagram, tom empático e direto, foco 
```




# Erros comuns e como corrigir

- **Pedido vago:** “Escreva sobre marketing.” — **Correção:** **Especificidade:** objetivo, público, tom, formato e limite de palavras.
    
- **Contexto insuficiente:** Não dizer para quem é. — **Correção:** **Persona:** nível de conhecimento, setor, situação.
    
- **Critérios soltos:** “Faça bonito.” — **Correção:** **Métricas e estilo:** exemplos, estrutura, restrições.
    
- **Um bloco só:** Muitas exigências misturadas. — **Correção:** **Listas e seções:** dividir em itens claros.
    
- **Esperar perfeição de 1 vez:** — **Correção:** **Iteração:** peça rascunho, dê feedback, refine.



# Dicas rápidas de “prompt engineering”

- **Role + Tarefa:** “Atue como [papel] e [faça X].”
    
- **Entrada estruturada:** Dê dados limpos e consistentes.
    
- **Exemplo de saída:** Mostre o formato desejado antes.
    
- **Restrições claras:** Tamanho, idioma, tom, estilo, fontes.
    
- **Verificação:** Peça uma checklist do que foi atendido no final.
    
- **Itere:** Avalie, peça ajustes, adicione exemplos.



## Exemplo: Prompt para Escrever E-mail para Cliente


Prompt vago:



```
Escreva um e-mail para um cliente.
```

Resposta do Modelo para o Prompt vago:



```
Assunto: Atualização sobre [Assunto Específico]

Prezado(a) [Nome do Cliente],

Espero que esteja bem.

Gostaria de informar que [descreva a situação, atualização ou pedido]. Estamos comprometidos em oferecer o melhor serviço e garantimos que [detalhe alguma ação que está sendo tomada ou alguma expectativa].

Se precisar de mais informações ou tiver alguma dúvida, não hesite em entrar em contato. Estou à disposição para ajudar.

Agradeço pela confiança em nossos serviços.

Atenciosamente,
[Seu Nome]
[Seu Cargo]
[Nome da Empresa]
[Telefone]
[Email]
```


A IA vai escrever um e-mail genérico. Ela não sabe o que você precisa: qual o objetivo do e-mail, qual o tom a ser utilizado, o que deve ser destacado ou qual a informação essencial.

Para que a IA escreva o e-mail ideal, você precisará ser específico. Um bom pedido poderia ser:

Prompt específico

Copiar

```
Escreva um e-mail formal para um cliente que está interessado em um notebook gamer chamado "Oblivion Core". Destaque as principais características do produto, como processador Intel Core i9, memória RAM 32GB, SSD 512GB, display de 16" com taxa de atualização de 240Hz, teclado RGB personalizável e refrigeração avançada. Além disso, ofereça um desconto especial de 10% e inclua um código promocional. O tom deve ser profissional, mas amigável.
```



Resposta do Modelo para o Prompt específico:

Copiar

```
Assunto: Apresentação do Notebook Gamer "Oblivion Core" e Oferta Exclusiva

Prezado(a) [Nome do Cliente],

Espero que esta mensagem o(a) encontre bem.

É com prazer que apresento o Oblivion Core, o notebook gamer que atende às mais altas expectativas dos entusiastas de tecnologia e performance. Este modelo foi desenvolvido para proporcionar uma experiência de jogo excepcional, combinando poder, agilidade e design inovador.

Aqui estão as principais características que fazem do Oblivion Core a escolha ideal:

Processador Intel Core i9: Desempenho de última geração para jogos e multitarefas.
Memória RAM 32GB: Capacidade ampliada para suportar os jogos mais exigentes e aplicações pesadas.
SSD de 512GB: Armazenamento rápido para inicialização quase instantânea e carregamento ágil dos jogos.
Display de 16" com Taxa de Atualização de 240Hz: Imagens ultra-fluídas para uma jogabilidade sem interrupções.
Teclado RGB Personalizável: Estilo e personalização para combinar com a sua vibe gamer.
Refrigeração Avançada: Sistema de resfriamento otimizado para garantir máximo desempenho sem sobreaquecimento.
Além disso, para tornar a sua experiência ainda mais vantajosa, oferecemos um desconto exclusivo de 10% na compra do Oblivion Core. Para aproveitar, basta utilizar o código promocional OBLIVION10 ao finalizar a compra em nosso site.

Se precisar de mais informações ou tiver alguma dúvida, estou à disposição para ajudá-lo(a).

Agradecemos o seu interesse e esperamos que aproveite esta oferta especial!

Atenciosamente,
[Seu Nome]
[Seu Cargo]
[Nome da Empresa]
[Telefone]
[E-mail]
```



### 

# Afinal, o que é Engenharia de Prompts?

Os modelos de linguagem precisam de instruções claras para fornecer respostas precisas. Em termos simples, um **prompt é a mensagem ou o comando que você dá ao modelo de IA**. A **Engenharia de Prompts,** que **é a habilidade de formular esses comandos de forma eficaz,** garante que você obtenha a resposta que realmente precisa.

