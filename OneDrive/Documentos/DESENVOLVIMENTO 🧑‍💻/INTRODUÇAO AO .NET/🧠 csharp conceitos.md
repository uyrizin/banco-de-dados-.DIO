



## 🧠 **1. Conversão de Tipos (Type Casting)**

### 🔹 Quando usar:

- Quando você precisa **converter dados entre tipos diferentes**, como de `string` para `int`, ou de `double` para `int`.
    
- Muito comum ao **ler dados do usuário**, **trabalhar com APIs**, ou **fazer cálculos**.
    

### 🔸 Exemplos:

csharp

```
// Conversão explícita (casting)
double preco = 19.99;
int inteiro = (int)preco; // perde a parte decimal → 19

// Conversão segura com TryParse
string entrada = "123a";
if (int.TryParse(entrada, out int resultado)) {
    Console.WriteLine($"Número: {resultado}");
} else {
    Console.WriteLine("Valor inválido");
}
```

### ✅ Use TryParse quando:

- O valor pode vir de fora (usuário, arquivo, API)
    
- Você quer evitar exceções
    

## 🔡 **2. ToString() e formatação**

### 🔹 Quando usar:

- Para **exibir dados** no console, em logs, ou em interfaces gráficas.
    
- Para **formatar datas, moedas e números**.
    

### 🔸 Exemplos:

csharp

```
double valor = 1234.567;
Console.WriteLine(valor.ToString("C2")); // R$1.234,57

DateTime hoje = DateTime.Now;
Console.WriteLine(hoje.ToString("dddd, dd MMMM yyyy")); // Segunda-feira, 03 novembro 2025
```

### ✅ Use quando:

- Precisa exibir dados com clareza e estilo
    
- Está gerando relatórios, mensagens ou arquivos de saída
    

## 🧱 **3. Constantes (**`const`**) e** `readonly`

### 🔹 Quando usar:

- `const`: quando o valor **nunca muda** e é conhecido em tempo de compilação.
    
- `readonly`: quando o valor é fixo **após o construtor**, mas pode depender de lógica.
    

### 🔸 Exemplo:

csharp

```
const double PI = 3.14159;

readonly DateTime dataCriacao;

public MinhaClasse() {
    dataCriacao = DateTime.Now; // permitido com readonly
}
```

### ✅ Use `const` para:

- Tamanhos fixos, limites, mensagens padrão
    

✅ Use `readonly` para:

- Datas de criação, configurações carregadas no início
    

## ➕ **4. Operadores Aritméticos**

### 🔹 Quando usar:

- Em **cálculos matemáticos**, **pontuação**, **controle de tempo**, etc.
    

### 🔸 Exemplo:

csharp

```
int pontos = 10;
pontos += 5; // soma e atribui
pontos *= 2; // dobra os pontos
```

### ✅ Use quando:

- Precisa atualizar valores com base em regras de negócio
    

## 🔁 **5. Operadores de Atribuição Composta**

|Operador|Uso típico|
|---|---|
|`+=`|Acumular valores|
|`-=`|Reduzir contadores|
|`*=`|Dobrar, escalar|
|`/=`|Reduzir proporcionalmente|
|`%=`|Verificar ciclos, alternância|

## 🔼🔽 **6. Incremento e Decremento (**`++`**,** `--`**)**

### 🔹 Quando usar:

- Em **laços de repetição**, **contadores**, **navegação de índices**
    

### 🔸 Exemplo:

csharp

```
for (int i = 0; i < 10; i++) {
    Console.WriteLine($"Item {i}");
}
```

## 🔍 **7. Operadores Relacionais**

### 🔹 Quando usar:

- Em **condições**, **validações**, **filtros**
    

### 🔸 Exemplo:

csharp

```
if (idade >= 18 && idade <= 60) {
    Console.WriteLine("Adulto em idade ativa");
}
```

## 🔗 **8. Operadores Lógicos**

|Operador|Uso|
|---|---|
|`&&`|Ambas as condições devem ser verdadeiras|
|`||`|Pelo menos uma deve ser verdadeira|
|`!`|Inverte o valor lógico|

### 🔸 Exemplo:

csharp

```
if (!string.IsNullOrEmpty(nome) && nome.Length > 3) {
    Console.WriteLine("Nome válido");
}
```

## 🔣 **9. Precedência e Associatividade**

### 🔹 Quando usar:

- Ao escrever **expressões complexas**, para evitar erros de lógica
    

### 🔸 Exemplo:

csharp

```
int resultado = 2 + 3 * 4; // resultado = 14
int certo = (2 + 3) * 4;   // resultado = 20
```

✅ Use parênteses para **deixar claro o que você quer fazer**

## ❓ **10. Operador Ternário**

### 🔹 Quando usar:

- Para **condições simples** que retornam um valor
    

### 🔸 Exemplo:

csharp

```
string status = idade >= 18 ? "Maior" : "Menor";
```

## 🧠 **11. Inferência de Tipos (**`var`**)**

### 🔹 Quando usar:

- Quando o tipo é **óbvio** ou **muito longo**
    

### 🔸 Exemplo:

csharp

```
var lista = new Dictionary<string, List<int>>();
```

✅ Evite usar `var` quando o tipo **não for claro** para quem lê o código

## ❓ **12. Nullable Reference Types**

### 🔹 Quando usar:

- Para **evitar erros de null** em tipos de referência
    

### 🔸 Exemplo:

csharp

```
#nullable enable

string? nome = null;

if (nome != null)
```