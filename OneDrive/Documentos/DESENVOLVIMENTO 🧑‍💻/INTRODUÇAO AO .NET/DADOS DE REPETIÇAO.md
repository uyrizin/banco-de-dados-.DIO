


## COMO FUNCIONA 

### como funciona uma classe 

  Boa pergunta, Uyrizin! Em C#, uma **classe** é como um molde ou modelo que define um tipo de objeto. Ela agrupa **dados** (variáveis, chamadas de campos ou propriedades) e **comportamentos** (métodos ou funções) que representam algo do mundo real ou lógico.



### 🧱 Definição básica de classe

csharp

```
public class Pessoa
{
    // Propriedades (dados)
    public string Nome;
    public int Idade;

    // Método (comportamento)
    public void Apresentar()
    {
        Console.WriteLine($"Olá, meu nome é {Nome} e tenho {Idade} anos.");
    }
}
```


Essa classe `Pessoa` define que toda pessoa tem um nome, uma idade e pode se apresentar.



### 🧪 Como usar essa classe

csharp

```
class Programa
{
    static void Main()
    {
        Pessoa p1 = new Pessoa(); // Criando um objeto da classe Pessoa
        p1.Nome = "Uyrizin";
        p1.Idade = 25;
        p1.Apresentar(); // Chama o método da classe
    }
}
```

🟢 Saída:

Código

```
Olá, meu nome é Uyrizin e tenho 25 anos.
```



### 🧠 Por que usar classes?

- Organiza o código em **blocos reutilizáveis**
    
- Facilita a **manutenção** e o **reuso**
    
- Permite aplicar conceitos de **Programação Orientada a Objetos** (POO), como herança, encapsulamento e polimorfismo


