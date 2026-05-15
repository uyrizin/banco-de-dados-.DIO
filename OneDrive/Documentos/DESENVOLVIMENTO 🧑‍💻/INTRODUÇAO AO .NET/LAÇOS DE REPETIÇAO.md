




### Entendendo if, else if e else (C#)

- if: executa um bloco quando a condição é verdadeira.

- else if: testa outra condição quando o if anterior foi falso.

- else: caso “padrão” quando todas as anteriores são falsas.

Exemplo clássico:

int nota = 72;

if (nota >= 90)

{

    Console.WriteLine("A");

}

else if (nota >= 80)

{

    Console.WriteLine("B");

}

else if (nota >= 70)

{

    Console.WriteLine("C");

}

else if (nota >= 60)

{

    Console.WriteLine("D");

}

else

{

    Console.WriteLine("F");

}

Boas práticas:

- Ordem decrescente nas faixas (evita lógica ambígua).

- Condições curtas e claras; extraia para métodos/variáveis se ficar grande.

- Use early return para reduzir aninhamento quando estiver dentro de funções.

- Se for apenas “valor → resultado”, prefira switch expression:
    
    string conceito = nota switch
    
    {
    
        >= 90 => "A",
    
        >= 80 => "B",
    
        >= 70 => "C",
    
        >= 60 => "D",
    
        _     => "F"
    
    };
    

Erros comuns:

- Sobrepor condições (ex.: >= 70 antes de >= 80).

- Esquecer o else final quando precisa de um caso padrão.

- Condições complexas sem parênteses, dificultando leitura.




### 🧠 Primeiro: o que acontece quando usamos `if`, `else if`, `else`?

Eles formam uma **cadeia de decisões**. O programa testa **cada condição na ordem** e **executa só o primeiro bloco que for verdadeiro**.

### 🔍 Exemplo simples com `if`, `else if`, `else`

csharp

```
int nota = 75;

if (nota >= 90)
{
    Console.WriteLine("Excelente");
}
else if (nota >= 70)
{
    Console.WriteLine("Bom");
}
else
{
    Console.WriteLine("Precisa melhorar");
}
```

👉 Aqui, só **um** desses blocos será executado. Como `nota >= 70` é verdadeiro, ele imprime **"Bom"** e ignora o resto.

### 🤔 Agora, e se eu usar outro `if` depois?

Se você escrever **um novo** `if` **fora da cadeia**, ele será **avaliado separadamente**. Olha só:

csharp

```
int nota = 75;
int faltas = 5;

if (nota >= 90)
{
    Console.WriteLine("Excelente");
}
else if (nota >= 70)
{
    Console.WriteLine("Bom");
}
else
{
    Console.WriteLine("Precisa melhorar");
}

// Novo if separado
if (faltas > 10)
{
    Console.WriteLine("Reprovado por faltas");
}
```

🧩 Aqui, o primeiro bloco avalia a **nota**, e o segundo `if` avalia **faltas** — são decisões **independentes**.





### O que é e como usar switch em C#

Use switch para escolher um caminho baseado em um valor, com código mais limpo que vários if/else if.

### Switch statement (tradicional)

int nota = 85;

switch (nota)

{

    case >= 90:

        Console.WriteLine("A");

        break;

    case >= 80:

        Console.WriteLine("B");

        break;

    case >= 70:

        Console.WriteLine("C");

        break;

    case >= 60:

        Console.WriteLine("D");

        break;

    default:

        Console.WriteLine("F");

        break;

}

- Não há “fallthrough” implícito; cada case precisa de break (ou return, etc.).

- Pode usar padrões relacionais (>=, <=) e default para o resto.

### Switch expression (mais moderno e enxuto)

int nota = 85;

string conceito = nota switch

{

    >= 90 => "A",

    >= 80 => "B",

    >= 70 => "C",

    >= 60 => "D",

    _     => "F"

};

Console.WriteLine(conceito);

- _ é o coringa (equivalente ao default).

- Útil para atribuições e retorno direto.

### Padrões com tipos e when (pattern matching)

object entrada = "123";

string tipo = entrada switch

{

    int n            => $"Inteiro: {n}",

    string s when s.Length > 0 => $"Texto: {s}",

    null             => "Nulo",

    _                => "Outro tipo"

};

Console.WriteLine(tipo);

### Com enum (caso clássico)

enum Operacao { Somar, Subtrair, Multiplicar, Dividir }

double Calcular(double a, double b, Operacao op) => op switch

{

    Operacao.Somar        => a + b,

    Operacao.Subtrair     => a - b,

    Operacao.Multiplicar  => a * b,

    Operacao.Dividir when b != 0 => a / b,

    Operacao.Dividir               => throw new DivideByZeroException(),

    _                               => throw new ArgumentOutOfRangeException(nameof(op))

};

### Dicas de boas práticas

- Prefira switch expression para mapear valor → resultado.

- Use padrões relacionais e when para regras claras.

- Sempre cubra o caso padrão (_/default) para robustez.

- Para lógica grande por case, extraia para métodos.





## 🔁 Estruturas de Repetição

### 1. `for` — Repetição com controle de contagem

**O que faz:** Executa um bloco de código um número determinado de vezes. Ideal quando você sabe quantas vezes quer repetir.

**Estrutura:**

csharp

```
for (início; condição; atualização)
{
    // Código repetido
}
```

**Exemplo:**

csharp

```
for (int i = 0; i < 5; i++)
{
    Console.WriteLine("i = " + i);
}
```

➡️ Imprime os números de 0 a 4.

### 2. `while` — Repetição com condição no início

**O que faz:** Repete o bloco **enquanto a condição for verdadeira**. A condição é verificada antes de cada execução.

**Exemplo:**

csharp

```
int i = 0;
while (i < 5)
{
    Console.WriteLine("i = " + i);
    i++;
}
```

➡️ Imprime os números de 0 a 4.

### 3. `do...while` — Repetição com condição no final

**O que faz:** Executa o bloco **pelo menos uma vez**, mesmo que a condição seja falsa.

**Exemplo:**

csharp

```
int i = 0;
do
{
    Console.WriteLine("i = " + i);
    i++;
} while (i < 5);
```

➡️ Imprime os números de 0 a 4.

### 4. `goto` — Salto para um rótulo

**O que faz:** Pula diretamente para um ponto específico do código. Deve ser usado com cuidado, pois pode deixar o código confuso.

**Exemplo:**

csharp

```
int x = 3;
if (x == 3)
{
    goto especial;
}
Console.WriteLine("Outro número");
return;

especial:
Console.WriteLine("Número especial!");
```

➡️ Imprime "Número especial!" se `x == 3`.

## 🧠 Estruturas Condicionais

### 5. `if` — Verifica uma condição

**O que faz:** Executa um bloco de código **se a condição for verdadeira**.

**Exemplo:**

csharp

```
int idade = 18;
if (idade >= 18)
{
    Console.WriteLine("Maior de idade");
}
```

### 6. `if...else` — Dois caminhos possíveis

**O que faz:** Executa um bloco **se a condição for verdadeira**, e outro **se for falsa**.

**Exemplo:**

csharp

```
int idade = 16;
if (idade >= 18)
{
    Console.WriteLine("Maior de idade");
}
else
{
    Console.WriteLine("Menor de idade");
}
```

### 7. `if...else if...else` — Vários caminhos

**O que faz:** Permite testar **várias condições diferentes** em sequência.

**Exemplo:**

csharp

```
int nota = 7;

if (nota >= 9)
{
    Console.WriteLine("Excelente");
}
else if (nota >= 7)
{
    Console.WriteLine("Aprovado");
}
else
{
    Console.WriteLine("Reprovado");
}
```

### 8. `switch...case` — Várias opções fixas

**O que faz:** Seleciona entre **várias opções pré-definidas** com base em um valor.

**Exemplo:**

csharp

```
int opcao = 2;

switch (opcao)
{
    case 1:
        Console.WriteLine("Opção 1");
        break;
    case 2:
        Console.WriteLine("Opção 2");
        break;
    default:
        Console.WriteLine("Opção inválida");
        break;
}
```

## 🧯 Comandos de Controle

### 9. `break` — Sai do loop imediatamente

**O que faz:** Interrompe o loop antes que ele termine naturalmente.

**Exemplo:**

csharp

```
for (int i = 0; i < 10; i++)
{
    if (i == 5)
        break;

    Console.WriteLine(i);
}
```

➡️ Imprime de 0 a 4 e sai do loop.

### 10. `continue` — Pula para a próxima repetição

**O que faz:** Ignora o restante da iteração atual e **vai direto para a próxima volta** do loop.

**Exemplo:**

csharp

```
for (int i = 0; i < 5; i++)
{
    if (i == 2)
        continue;

    Console.WriteLine(i);
}
```

➡️ Imprime 0, 1, 3, 4 (pula o 2).