



## 🧠 Como funciona o `Nullable<T>` em C#

- A sintaxe `T?` é um atalho para `Nullable<T>`, onde `T` é um tipo de valor.
    
- Exemplo: `int? idade = null;` permite que `idade` seja um número ou `null`.
    

## ✅ Exemplos básicos

csharp

```
int? idade = null;
double? salario = 3500.50;
bool? aprovado = null;

if (idade.HasValue)
    Console.WriteLine("Idade: " + idade.Value);
else
    Console.WriteLine("Idade não informada");
```

### Alternativa com comparação direta:

csharp

```
if (salario != null)
    Console.WriteLine("Salário: " + salario);
else
    Console.WriteLine("Salário não disponível");
```

## 🔍 Propriedades úteis

|Propriedade / Método|Descrição|
|---|---|
|`HasValue`|Retorna `true` se há um valor|
|`Value`|Retorna o valor (lança exceção se for `null`)|
|`GetValueOrDefault()`|Retorna o valor ou o padrão do tipo (`0`, `false`, etc.)|
|`??` (operador coalescência)|Retorna valor alternativo se for `null`|

### Exemplo com `??`:

csharp

```
int? idade = null;
int idadeFinal = idade ?? 18; // Se idade for null, assume 18
Console.WriteLine("Idade final: " + idadeFinal);
```

## 🧪 Uso avançado com padrões e `is`

csharp

```
int? nota = 85;

if (nota is int valorNota)
    Console.WriteLine($"Nota registrada: {valorNota}");
else
    Console.WriteLine("Nota ausente");
```

## 🚀 Dicas para melhor proveito

- Use `nullable` em modelos de dados que refletem campos opcionais (ex: APIs, banco de dados).
    
- Combine com `??`, `?.`, e `is` para evitar exceções e tornar o código mais limpo.
    
- Use `Nullable<T>.GetValueOrDefault()` quando quiser evitar `null` sem lançar exceção.
    
- Em C# 8+, você pode ativar **nullable reference types** com `#nullable enable` para que o compilador te avise sobre possíveis `NullReferenceException`.




## 🧠 O que são tipos anuláveis?

Em C#, tipos de valor como `int`, `double`, `bool` normalmente **não aceitam** `null`. Para permitir isso, usamos `Nullable<T>` ou a sintaxe simplificada `T?`.

csharp

```
int? idade = null; // Válido
int idade2 = null; // Erro de compilação
```

Isso é útil quando você precisa representar a ausência de valor — como um campo opcional em um formulário ou banco de dados.

## 🔍 Propriedades e métodos úteis

|Recurso|Descrição|
|---|---|
|`HasValue`|Retorna `true` se o valor não é nulo|
|`Value`|Retorna o valor (lança exceção se for `null`)|
|`GetValueOrDefault()`|Retorna o valor ou o padrão do tipo (`0`, `false`, etc.)|
|`??` (coalescência nula)|Retorna valor alternativo se for `null`|
|`?.` (acesso condicional)|Evita exceção ao acessar membros de objetos possivelmente nulos|
|`!` (null-forgiving)|Diz ao compilador: “confia em mim, isso não é nulo”|

## ✅ Exemplos práticos

### 1. Cálculo com valor opcional

csharp

```
double? bonus = null;
double salarioBase = 3000;

double salarioFinal = salarioBase + (bonus ?? 0);
Console.WriteLine($"Salário final: R${salarioFinal}");
```

### 2. Validação com `HasValue`

csharp

```
int? idade = null;

if (idade.HasValue)
    Console.WriteLine("Idade: " + idade.Value);
else
    Console.WriteLine("Idade não informada");
```

### 3. Uso com `GetValueOrDefault()`

csharp

```
int? votos = null;
Console.WriteLine("Votos: " + votos.GetValueOrDefault()); // Saída: 0
```

## 🚀 Avançado: Tipos de referência anuláveis (`string?`, `object?`)

A partir do **C# 8.0**, você pode ativar o recurso de **nullable reference types**, que permite ao compilador te alertar sobre possíveis `NullReferenceException`.

### Ativando no código:

csharp

```
#nullable enable

string? nome = null; // permitido
string sobrenome = null; // alerta do compilador
```

### Operador de perdão (`!`):

csharp

```
string? nome = null;
Console.WriteLine(nome!); // Diz ao compilador: “confia, não é nulo”
```

> ⚠️ Use com cautela! O operador `!` ignora a verificação de nulidade e pode causar exceções se usado indevidamente.

## 🧩 Padrões modernos com `is` e `switch`

csharp

```
object? dado = 42;

if (dado is int numero)
    Console.WriteLine($"Número: {numero}");
```

Ou com `switch`:

csharp

```
object? valor = null;

switch (valor)
{
    case int n:
        Console.WriteLine($"Inteiro: {n}");
        break;
    case null:
        Console.WriteLine("Valor nulo");
        break;
}
```

## 🛠️ Boas práticas

- ✅ Use `T?` para campos opcionais em modelos de dados
    
- ✅ Combine com `??`, `?.`, `is`, `switch` para lógica segura
    
- ✅ Ative `#nullable enable` para receber alertas úteis do compilador
    
- ❌ Evite usar `!` sem certeza absoluta de que o valor não é nulo
    
- ✅ Documente bem os campos que podem ser nulos para evitar bugs
    

## 📚 Fontes para estudo aprofundado

- Tipos de referência anuláveis – Microsoft Learn
    
- Guia completo sobre Nullable em C# – Macoratti.Net
    
- Manipulação de valores com Nullable Types – DevMedia






Um _tipo de valor anulável_`T?` representa todos os valores do [tipo de valor](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/value-types)`T` subjacente e um valor [null](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/keywords/null) adicional. Por exemplo, você pode atribuir qualquer um dos seguintes três valores a uma variável `bool?`: `true`, `false` ou `null`. Um tipo de valor `T` subjacente não pode ser um tipo de valor anulável em si.

Qualquer tipo de valor anulável é uma instância da estrutura genérica [System.Nullable<T>](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1). Você pode se referir a um tipo de valor anulável com um tipo subjacente `T` em qualquer um dos seguintes formulários intercambiáveis: `Nullable<T>` ou `T?`.

Normalmente, você usa um tipo de valor anulável quando precisa representar o valor indefinido de um tipo de valor subjacente. Por exemplo, uma variável booliana ou `bool`, só pode ser `true` ou `false`. No entanto, em alguns aplicativos, um valor variável pode estar indefinido ou ausente. Por exemplo, um campo de dados pode conter `true` ou `false`, ou pode não conter nenhum valor, ou seja, `NULL`. Você pode usar o tipo `bool?` nesse cenário.

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#declaration-and-assignment)

## Declaração e atribuição

Como um tipo de valor é implicitamente conversível para o tipo de valor anulável correspondente, você pode atribuir um valor a uma variável de um tipo de valor anulável, como faria com o tipo de valor subjacente. Você também pode atribuir o valor `null`. Por exemplo:

C#Copiar

```
double? pi = 3.14;
char? letter = 'a';

int m2 = 10;
int? m = m2;

bool? flag = null;

// An array of a nullable value type:
int?[] arr = new int?[10];
```

O valor padrão de um tipo de valor anulável representa `null`, ou seja, é uma instância cuja propriedade [Nullable<T>.HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) retorna `false`.

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#examination-of-an-instance-of-a-nullable-value-type)

## Exame de uma instância de um tipo de valor anulável

Você pode usar o [operador `is` com um padrão de tipo](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/type-testing-and-cast#type-testing-with-pattern-matching) para examinar uma instância de um tipo de valor anulável para `null` e recuperar um valor de um tipo subjacente:

C#Copiar

Executar

```
int? a = 42;
if (a is int valueOfA)
{
    Console.WriteLine($"a is {valueOfA}");
}
else
{
    Console.WriteLine("a does not have a value");
}
// Output:
// a is 42
```

Você sempre pode usar as seguintes propriedades somente leitura para examinar e obter um valor de uma variável de tipo de valor anulável:

- [Nullable<T>.HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) indica se uma instância de um tipo de valor anulável tem um valor do tipo subjacente dela.
    
- [Nullable<T>.Value](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.value) obtém o valor de um tipo subjacente quando [HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) é `true`. Quando [HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) é `false`, a propriedade [Value](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.value) gera uma [InvalidOperationException](https://learn.microsoft.com/pt-br/dotnet/api/system.invalidoperationexception).
    

O seguinte exemplo usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:

C#Copiar

Executar

```
int? b = 10;
if (b.HasValue)
{
    Console.WriteLine($"b is {b.Value}");
}
else
{
    Console.WriteLine("b does not have a value");
}
// Output:
// b is 10
```

Você também pode comparar uma variável de um tipo de valor anulável com `null` em vez de usar a propriedade `HasValue`, como mostra o seguinte exemplo:

C#Copiar

Executar

```
int? c = 7;
if (c != null)
{
    Console.WriteLine($"c is {c.Value}");
}
else
{
    Console.WriteLine("c does not have a value");
}
// Output:
// c is 7
```

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#conversion-from-a-nullable-value-type-to-an-underlying-type)

## Conversão de um tipo de valor anulável para um tipo subjacente

Se você quiser atribuir um valor de um tipo de valor anulável a uma variável de tipo de valor não anulável, talvez seja necessário especificar o valor a ser atribuído no lugar de `null`. Use o [operador de avaliação de nulo `??`](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/null-coalescing-operator) para fazer isso (você também pode usar o método [Nullable<T>.GetValueOrDefault(T)](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.getvalueordefault#system-nullable-1-getvalueordefault\(-0\)) para a mesma finalidade):

C#Copiar

Executar

```
int? a = 28;
int b = a ?? -1;
Console.WriteLine($"b is {b}");  // output: b is 28

int? c = null;
int d = c ?? -1;
Console.WriteLine($"d is {d}");  // output: d is -1
```

Se quiser usar o valor [padrão](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/default-values) do tipo de valor subjacente no lugar de `null`, use o método [Nullable<T>.GetValueOrDefault()](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.getvalueordefault#system-nullable-1-getvalueordefault).

Você também pode converter explicitamente um tipo de valor anulável em um tipo não anulável, como mostra o seguinte exemplo:

C#Copiar

```
int? n = null;

//int m1 = n;    // Doesn't compile
int n2 = (int)n; // Compiles, but throws an exception if n is null
```

Em tempo de execução, se o valor de um tipo de valor anulável for `null`, a conversão explícita vai gerar uma [InvalidOperationException](https://learn.microsoft.com/pt-br/dotnet/api/system.invalidoperationexception).

Um tipo de valor não anulável `T` é implicitamente conversível para o tipo de valor anulável correspondente `T?`.

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#lifted-operators)

## Operadores suspensos

Os [operadores](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/) unários e binários predefinidos ou quaisquer operadores sobrecarregados com suporte por um tipo de valor `T` também têm suporte pelo tipo de valor anulável correspondente `T?`. Esses operadores, também conhecidos como _operadores suspensos_, vão gerar `null` se um ou ambos os operadores forem `null`; caso contrário, o operador usará os valores contidos dos operadores dele para calcular o resultado. Por exemplo:

C#Copiar

```
int? a = 10;
int? b = null;
int? c = 10;

a++;        // a is 11
a = a * c;  // a is 110
a = a + b;  // a is null
```

 Observação

Para o tipo `bool?`, os operadores predefinidos `&` e `|` não seguirão as regras descritas nessa seção: o resultado de uma avaliação do operador poderá ser não nulo, mesmo quando um dos operandos for `null`. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/boolean-logical-operators#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/boolean-logical-operators).

Para os [operadores de comparação](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/comparison-operators)`<`, `>`, `<=` e `>=`, se um ou ambos os operandos forem `null`, o resultado será `false`; caso contrário, os valores contidos de operandos serão comparados. Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`. O exemplo a seguir mostra que 10

- nem maior ou igual a `null`
- nem menor que `null`

C#Copiar

Executar

```
int? a = 10;
Console.WriteLine($"{a} >= null is {a >= null}");
Console.WriteLine($"{a} < null is {a < null}");
Console.WriteLine($"{a} == null is {a == null}");
// Output:
// 10 >= null is False
// 10 < null is False
// 10 == null is False

int? b = null;
int? c = null;
Console.WriteLine($"null >= null is {b >= c}");
Console.WriteLine($"null == null is {b == c}");
// Output:
// null >= null is False
// null == null is True
```

Para o [operador de igualdade](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/equality-operators#equality-operator-)`==`, se ambos os operandos forem `null`, o resultado será `true`, se apenas um dos operandos for `null`, o resultado será `false`; caso contrário, os valores contidos dos operandos serão comparados.

Para o [operador de desigualdade](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/equality-operators#inequality-operator-)`!=`, se ambos os operandos forem `null`, o resultado será `false`, se apenas um dos operandos for `null`, o resultado será `true`; caso contrário, os valores contidos dos operandos serão comparados.

Se houver uma [conversão definida pelo usuário](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/user-defined-conversion-operators) entre dois tipos de valor, a mesma conversão também poderá ser usada entre os tipos de valor anuláveis correspondentes.

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#boxing-and-unboxing)

## Conversão boxing e unboxing

Uma instância de um tipo de valor anulável `T?` é [demarcada](https://learn.microsoft.com/pt-br/dotnet/csharp/programming-guide/types/boxing-and-unboxing) da seguinte maneira:

- Se [HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) retorna `false`, a referência nula é produzida.
- Se [HasValue](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1.hasvalue) retornar `true`, o valor correspondente do tipo de valor subjacente `T` será demarcado, não a instância de [Nullable<T>](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1).

Você pode desfazer um valor demarcado de um tipo de valor `T` para o tipo de valor anulável correspondente `T?`, como mostra o seguinte exemplo:

C#Copiar

Executar

```
int a = 41;
object aBoxed = a;
int? aNullable = (int?)aBoxed;
Console.WriteLine($"Value of aNullable: {aNullable}");

object aNullableBoxed = aNullable;
if (aNullableBoxed is int valueOfA)
{
    Console.WriteLine($"aNullableBoxed is boxed int: {valueOfA}");
}
// Output:
// Value of aNullable: 41
// aNullableBoxed is boxed int: 41
```

[](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#how-to-identify-a-nullable-value-type)

## Como identificar um tipo de valor anulável

O seguinte exemplo mostra como determinar se uma instância [System.Type](https://learn.microsoft.com/pt-br/dotnet/api/system.type) representa um tipo de valor anulável construído, ou seja, o tipo [System.Nullable<T>](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable-1) com um parâmetro de tipo especificado `T`:

C#Copiar

Executar

```
Console.WriteLine($"int? is {(IsNullable(typeof(int?)) ? "nullable" : "non nullable")} value type");
Console.WriteLine($"int is {(IsNullable(typeof(int)) ? "nullable" : "non-nullable")} value type");

bool IsNullable(Type type) => Nullable.GetUnderlyingType(type) != null;

// Output:
// int? is nullable value type
// int is non-nullable value type
```

Como mostra o exemplo, você usa o operador [typeof](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/type-testing-and-cast#the-typeof-operator) para criar uma instância [System.Type](https://learn.microsoft.com/pt-br/dotnet/api/system.type).

Se você quiser determinar se uma instância é de um tipo de valor anulado, não use o método [Object.GetType](https://learn.microsoft.com/pt-br/dotnet/api/system.object.gettype) para fazer com que uma instância [Type](https://learn.microsoft.com/pt-br/dotnet/api/system.type) seja testada com o código anterior. Quando você chama o método [Object.GetType](https://learn.microsoft.com/pt-br/dotnet/api/system.object.gettype) em uma instância de um tipo de valor anulável, a instância é [demarcada](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/builtin-types/nullable-value-types#boxing-and-unboxing) para [Object](https://learn.microsoft.com/pt-br/dotnet/api/system.object). Como a conversão boxing de uma instância não nula de um tipo de valor anulável é equivalente à conversão boxing de um valor do tipo subjacente, [GetType](https://learn.microsoft.com/pt-br/dotnet/api/system.object.gettype) retorna uma instância [Type](https://learn.microsoft.com/pt-br/dotnet/api/system.type) que representa o tipo subjacente de um tipo de valor anulável:

C#Copiar

Executar

```
int? a = 17;
Type typeOfA = a.GetType();
Console.WriteLine(typeOfA.FullName);
// Output:
// System.Int32
```

Além disso, não use o operador [is](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/type-testing-and-cast#the-is-operator) para determinar se uma instância é de um tipo de valor anulável. Como mostra o seguinte exemplo, não é possível distinguir tipos de uma instância de tipo de valor anulável e a instância de tipo subjacente dela com o operador `is`:

C#Copiar

Executar

```
int? a = 14;
if (a is int)
{
    Console.WriteLine("int? instance is compatible with int");
}

int b = 17;
if (b is int?)
{
    Console.WriteLine("int instance is compatible with int?");
}
// Output:
// int? instance is compatible with int
// int instance is compatible with int?
```

Em vez disso, use o operador [Nullable.GetUnderlyingType](https://learn.microsoft.com/pt-br/dotnet/api/system.nullable.getunderlyingtype) do primeiro exemplo e o operador [typeof](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/type-testing-and-cast#the-typeof-operator) para verificar se uma instância é de um tipo de valor anulável.

 Observação