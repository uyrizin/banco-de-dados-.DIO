    


## 🧠 O que são classes genéricas?

Classes genéricas permitem que você defina **tipos parametrizados**, ou seja, você escreve uma única classe que pode trabalhar com qualquer tipo de dado — `int`, `string`, `bool`, ou até tipos personalizados.

csharp

```
public class Caixa<T>
{
    public T Conteudo { get; set; }

    public void Mostrar()
    {
        Console.WriteLine($"Conteúdo: {Conteudo}");
    }
}
```

Aqui, `T` é um **parâmetro de tipo**. Quando você cria uma instância, você define qual tipo será usado:

csharp

```
var caixaInt = new Caixa<int> { Conteudo = 42 };
var caixaTexto = new Caixa<string> { Conteudo = "Olá, Uyrizin!" };
```

## ✅ Vantagens dos genéricos

- **Reutilização de código**: uma única classe serve para múltiplos tipos.
    
- **Segurança de tipo**: evita conversões perigosas e erros em tempo de execução.
    
- **Performance**: evita boxing/unboxing de tipos de valor.
    
- **Flexibilidade**: você pode criar estruturas como listas, pilhas, filas, etc.
    

## 🔍 Exemplos práticos

### 1. Lista genérica personalizada

csharp

```
public class MinhaLista<T>
{
    private List<T> itens = new List<T>();

    public void Adicionar(T item) => itens.Add(item);
    public T Obter(int indice) => itens[indice];
}
```

### 2. Classe com múltiplos parâmetros de tipo

csharp

```
public class Par<K, V>
{
    public K Chave { get; set; }
    public V Valor { get; set; }
}
```

Uso:

csharp

```
var par = new Par<string, int> { Chave = "Idade", Valor = 30 };
```

## 🧩 Restrições de tipo (`where`)

Você pode limitar os tipos aceitos com `where`:

csharp

```
public class Repositorio<T> where T : IEntidade
{
    public void Salvar(T item) { /* ... */ }
}
```

Outras restrições possíveis:

|Restrição|Significado|
|---|---|
|`where T : class`|Apenas tipos de referência|
|`where T : struct`|Apenas tipos de valor|
|`where T : new()`|Deve ter construtor público sem parâmetros|
|`where T : BaseClass`|Deve herdar de `BaseClass`|
|`where T : Interface`|Deve implementar a interface|

## 🚀 Avançado: métodos genéricos

Você pode ter métodos genéricos dentro de classes comuns:

csharp

```
public class Util
{
    public static void Trocar<T>(ref T a, ref T b)
    {
        T temp = a;
        a = b;
        b = temp;
    }
}
```

## 📚 Recursos para aprofundar

- Documentação oficial da Microsoft sobre genéricos
    
- Explicação prática no Stack Overflow em Português
    
- Artigo completo com exemplos no Macoratti.Net