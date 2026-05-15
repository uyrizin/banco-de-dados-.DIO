

## 🧠 O que são tipos anônimos?

São objetos criados com `new { ... }` que encapsulam propriedades **somente leitura**. O compilador gera o tipo automaticamente, e você não precisa nomeá-lo.

csharp

```
var produto = new { Nome = "Mouse", Preco = 89.90 };
Console.WriteLine($"Produto: {produto.Nome}, Preço: R${produto.Preco}");
```

- O tipo de `produto` é gerado pelo compilador.
    
- As propriedades são inferidas: `Nome` é `string`, `Preco` é `double`.
    

## 🔍 Características principais

|Característica|Detalhes|
|---|---|
|Somente leitura|As propriedades não podem ser alteradas após a criação|
|Sem nome de tipo|O tipo é gerado automaticamente e não pode ser referenciado diretamente|
|Inferência de tipo|O compilador deduz os tipos das propriedades|
|Sem métodos ou eventos|Apenas propriedades públicas|
|Usado com LINQ|Ideal para projeções em consultas LINQ|

## ✅ Exemplos práticos

### 1. Criando um tipo anônimo simples

csharp

```
var pessoa = new { Nome = "Aline", Idade = 28 };
Console.WriteLine($"{pessoa.Nome} tem {pessoa.Idade} anos");
```

### 2. Usando com LINQ

csharp

```
var produtos = new[]
{
    new { Nome = "Teclado", Preco = 120 },
    new { Nome = "Monitor", Preco = 950 }
};

var consulta = from p in produtos
               where p.Preco > 200
               select new { p.Nome };

foreach (var item in consulta)
{
    Console.WriteLine(item.Nome);
}
```

## 🧩 Inicializadores de projeção

Você pode usar variáveis locais diretamente:

csharp

```
string nome = "Carlos";
int idade = 35;

var cliente = new { nome, idade }; // Propriedades serão nome e idade
```

## 🚀 Avançado: Comparação e agrupamento

Tipos anônimos implementam `Equals()` e `GetHashCode()` com base nos valores das propriedades:

csharp

```
var a = new { Nome = "Ana", Idade = 30 };
var b = new { Nome = "Ana", Idade = 30 };

Console.WriteLine(a.Equals(b)); // True
```

> Mas atenção: se os tipos forem criados em contextos diferentes, mesmo com mesmas propriedades, podem não ser considerados iguais em compilação.

## 🛠️ Boas práticas

- ✅ Use para dados temporários ou projeções
    
- ✅ Combine com LINQ para consultas enxutas
    
- ❌ Evite usar em retornos de métodos públicos (sem nome de tipo, difícil reutilizar)
    
- ✅ Prefira tipos nomeados (classes) para estruturas persistentes ou complexas
    

## 📚 Fontes para estudo

- Tipos Anônimos na documentação oficial da Microsoft
    
- Tutorial completo no Macoratti.Net com exemplos reais