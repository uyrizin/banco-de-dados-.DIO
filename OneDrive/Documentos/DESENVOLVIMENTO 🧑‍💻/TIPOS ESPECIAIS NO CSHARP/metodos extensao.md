



## 🧠 O que são métodos de extensão?

São métodos **estáticos** definidos em uma **classe estática**, mas que podem ser chamados como se fossem métodos de instância do tipo que estão estendendo.

csharp

```
public static class MinhasExtensoes
{
    public static int Dobrar(this int numero)
    {
        return numero * 2;
    }
}
```

Uso:

csharp

```
int valor = 5;
Console.WriteLine(valor.Dobrar()); // Saída: 10
```

## ✅ Regras para criar métodos de extensão

1. Devem estar em uma **classe estática**
    
2. O método deve ser **estático**
    
3. O primeiro parâmetro deve ter o modificador `this` e indicar o tipo que será estendido
    
4. O namespace da classe deve estar **importado com** `using` para o método ficar disponível
    

## 🔍 Exemplos úteis

### 1. Extensão para `string`

csharp

```
public static class StringExtensions
{
    public static bool TemConteudo(this string texto)
    {
        return !string.IsNullOrWhiteSpace(texto);
    }
}
```

Uso:

csharp

```
string nome = "Uyrizin";
Console.WriteLine(nome.TemConteudo()); // True
```

### 2. Extensão para `DateTime`

csharp

```
public static class DateTimeExtensions
{
    public static int DiasAteHoje(this DateTime data)
    {
        return (DateTime.Today - data).Days;
    }
}
```

Uso:

csharp

```
DateTime nascimento = new DateTime(2000, 1, 1);
Console.WriteLine(nascimento.DiasAteHoje());
```

## 🚀 Avançado: LINQ e métodos de extensão

Os métodos de extensão são a base do LINQ. Por exemplo:

csharp

```
int[] numeros = { 1, 2, 3, 4, 5 };
var pares = numeros.Where(n => n % 2 == 0);
```

Aqui, `Where` é um método de extensão para `IEnumerable<T>` definido em `System.Linq`.

## 🛠️ Boas práticas

- ✅ Use para adicionar comportamento sem quebrar encapsulamento
    
- ✅ Mantenha os métodos em namespaces intuitivos
    
- ❌ Evite métodos que alteram estado — prefira métodos puros
    
- ✅ Documente bem os métodos para facilitar o uso por outros devs
    

## 📚 Fontes para aprofundar

- Guia oficial da Microsoft sobre métodos de extensão
    
- Artigo prático com exemplos no Macoratti.Net