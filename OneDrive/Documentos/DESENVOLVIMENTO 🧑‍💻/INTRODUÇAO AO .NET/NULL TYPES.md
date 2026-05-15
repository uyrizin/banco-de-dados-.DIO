

 ### 🧩 O que são Nullable Types?

Em linguagens como C#, _nullable types_ permitem que tipos de valor (como `int`, `double`, `bool`) aceitem o valor `null`. Isso é útil quando você precisa indicar que uma variável pode não ter um valor definido — algo comum em bancos de dados ou em lógica condicional.

A sintaxe é simples: basta adicionar um `?` ao tipo. Exemplo: `int? idade = null;`



### 🛠️ Quando usar Nullable Types

Você deve considerar usar _nullable types_ nas seguintes situações:

- **Integração com banco de dados**: quando um campo pode conter `null`, como uma data de nascimento opcional (`DateTime?`).
    
- **Representação de estados indefinidos**: por exemplo, um `bool?` pode representar `true`, `false` ou "não informado".
    
- **Evitar valores padrão ambíguos**: `0` pode ser um valor válido, então usar `null` ajuda a distinguir entre "zero" e "sem valor".
    
- **Formulários e entrada de dados**: quando o usuário pode deixar um campo em branco.
    
- **Lógica de negócios condicional**: quando o valor de uma variável depende de uma condição que pode não ser satisfeita.
    

### 🔍 Como verificar e usar

Você pode verificar se um _nullable type_ tem valor com `.HasValue` ou usando o operador `== null`.

csharp

```
int? idade = null;

if (idade.HasValue)
    Console.WriteLine($"Idade: {idade.Value}");
else
    Console.WriteLine("Idade não informada.");
```

Ou de forma mais concisa:

csharp

```
Console.WriteLine(idade ?? -1); // Usa -1 como valor padrão se for null
```

### 🧠 Dica

Evite abusar de _nullable types_ em situações onde o valor sempre será obrigatório. Use-os apenas quando o `null` realmente representa um estado significativo na lógica da aplicação.