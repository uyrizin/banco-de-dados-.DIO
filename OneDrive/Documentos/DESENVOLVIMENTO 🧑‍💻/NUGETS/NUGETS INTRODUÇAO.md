


# oque é um nuget



## 🧩 O que é NuGet?

**NuGet** é o **gerenciador de pacotes oficial do .NET**. Ele permite que desenvolvedores compartilhem e reutilizem bibliotecas de código de forma simples e eficiente.

- Um **pacote NuGet** é um arquivo `.nupkg` (ZIP) que contém:
    
    - DLLs (código compilado)
        
    - Arquivos auxiliares
        
    - Um manifesto com metadados (versão, autor, descrição etc.)
        
- Você pode:
    
    - **Consumir** pacotes existentes (como Newtonsoft.Json, Dapper, etc.)
        
    - **Criar e publicar** seus próprios pacotes para uso interno ou público
        

🔗 Documentação oficial: O que é o NuGet e o que ele faz?

## 🚀 Como usar NuGet em projetos .NET

### ✅ Instalar um pacote NuGet

Se estiver usando o Visual Studio:

1. Clique com o botão direito no projeto > **Gerenciar Pacotes NuGet**
    
2. Busque o pacote desejado (ex: `Newtonsoft.Json`)
    
3. Clique em **Instalar**
    

Ou via terminal:

bash

```
dotnet add package Newtonsoft.Json
```

### ✅ Usar o pacote no código

csharp

```
using Newtonsoft.Json;

var pessoa = new { Nome = "Uyrizin", Idade = 25 };
string json = JsonConvert.SerializeObject(pessoa);
Console.WriteLine(json);
```

## 🛠️ Criar seu próprio pacote NuGet

### 1. Criar projeto de biblioteca

bash

```
dotnet new classlib -n MeuPacote
cd MeuPacote
```

### 2. Editar o `.csproj` com metadados

xml

```
<PropertyGroup>
  <TargetFramework>net6.0</TargetFramework>
  <PackageId>MeuPacote</PackageId>
  <Version>1.0.0</Version>
  <Authors>Uyrizin</Authors>
  <Description>Pacote de exemplo para estudos</Description>
</PropertyGroup>
```

### 3. Empacotar

bash

```
dotnet pack --configuration Release
```

Isso gera o `.nupkg` na pasta `bin/Release`.

### 4. Testar localmente

Crie uma pasta para pacotes locais:

bash

```
mkdir NuGetLocal
cp bin/Release/MeuPacote.1.0.0.nupkg NuGetLocal/
```

Adicione a fonte no terminal:

bash

```
dotnet nuget add source ./NuGetLocal --name LocalSource
```

Agora você pode instalar esse pacote em outro projeto:

bash

```
dotnet add package MeuPacote --source LocalSource
```

🔗 Tutorial completo: Seu Primeiro Pacote NuGet

## 📌 Resumo das partes mais importantes

| Tópico            | Essência                                                                   |
| ----------------- | -------------------------------------------------------------------------- |
| O que é NuGet     | Gerenciador de pacotes para .NET que facilita o compartilhamento de código |
| Como instalar     | Via Visual Studio ou terminal com `dotnet add package`                     |
| Como criar pacote | Criar projeto, editar `.csproj`, empacotar com `dotnet pack`               |
| Testar localmente | Criar pasta, copiar `.nupkg`, adicionar como fonte                         |
| Publicar pacote   | Criar conta no nuget.org, usar `dotnet nuget push                          |