-



# Seu Primeiro Pacote NuGet: Um Passo a Passo Prático

[#csharp](https://dev.to/t/csharp)[#nuget](https://dev.to/t/nuget)[#dotnet](https://dev.to/t/dotnet)[#tutorial](https://dev.to/t/tutorial)

Quando você trabalha em diferentes aplicações, é comum se deparar com os mesmos problemas e as mesmas soluções aparecendo de novo e de novo. Isso faz parte do dia a dia de um desenvolvedor, mas pode ser meio cansativo. Agora, imagine se você pudesse pegar esse código repetido, organizar direitinho e usar facilmente em outros projetos. Legal, né? Neste artigo, vamos explorar como fazer isso com o NuGet.

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#vis%C3%A3o-geral)Visão geral:

O NuGet é o gerenciador de pacotes oficial do .NET e ajuda você a empacotar, compartilhar e usar funcionalidades reutilizáveis de forma simples. Com ele, dá para organizar seu código em pacotes, reaproveitá-los em outros projetos e até colaborar de maneira mais prática com outros desenvolvedores.

> **_"Um pacote NuGet é um arquivo ZIP com a extensão .nupkg que contém código compilado (DLLs), arquivos relacionados e um manifesto descritivo com informações como o número da versão. Desenvolvedores criam e publicam pacotes, enquanto consumidores obtêm e utilizam suas funcionalidades. O NuGet gerencia os detalhes intermediários."_**

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#criando-um-projeto)Criando um projeto

Antes de começar, crie uma conta no [NuGet.org](https://www.nuget.org/). Isso será necessário para publicar seu pacote.

Crie um projeto do tipo **Class Library**. No terminal, execute:  

```
dotnet new classlib --name ExamplePackage
```

Em seguida, abra o projeto em seu editor de preferência. Vamos criar um exemplo simples que converte um objeto em uma string JSON.

[![Código do pacote](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F7y48cfl467arr7olqu5b.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F7y48cfl467arr7olqu5b.png)

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#definindo-os-metadados)Definindo os Metadados

Para criar um pacote, é necessário configurar informações importantes diretamente no arquivo .**csproj** do projeto. Esse arquivo define os metadados essenciais que identificarão seu pacote no NuGet.

### [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#metadados-obrigat%C3%B3rios)**Metadados Obrigatórios:**

- **TargetFramework**: Define a versão do .NET que seu projeto utilizará.
- **PackageId**: Um identificador único para seu pacote.
- **Version**: Versão do pacote no formato Major.Minor.Patch ([SemVer](https://semver.org/)).
    - **Major**: Alterações que quebram compatibilidade.
    - **Minor**: Novas funcionalidades.
    - **Patch**: Correções de bugs.

### [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#metadados-opcionais-n%C3%A3o-obrigat%C3%B3rios-mas-fortemente-recomendados)**Metadados opcionais (não obrigatórios mas fortemente recomendados):**

- **Authors** Nome do autor ou autores do pacote.
- **Description**: Uma breve descrição do propósito do pacote.
- **PackageLicenseExpression**: Especifica a licença sob a qual o pacote é distribuído.

Atualize o arquivo .**csproj** para incluir essas informações:

[![Arquivo .csproj](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F89870cwcsdoy3k0jydm2.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F89870cwcsdoy3k0jydm2.png)

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#compilando-o-pacote)Compilando o pacote

Com os metadados configurados, é hora de compilar o pacote. No terminal, execute:  

```
dotnet pack --configuration Release
```

Esse comando criará um arquivo .**nupkg** na pasta bin/Release.

[![Localização do pacote compilado](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F0hqb023yysu4xs6z90ov.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F0hqb023yysu4xs6z90ov.png)

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#testando-localmente)Testando localmente

### [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#configurando-a-fonte-local)**Configurando a Fonte Local:**

Dentro do projeto, crie uma pasta para os pacotes locais:  

```
mkdir NuGetLocal
```

Copie o arquivo .**nupkg** gerado para essa pasta:  

```
cp bin/Release/examplePackage.Convert.1.0.0.nupkg NuGetLocal
```

Adicione a pasta como uma fonte NuGet:  

```
dotnet nuget add source /caminho/completo/para/NuGetLocal --name NuGetLocal
```

### [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#consumindo-o-pacote-no-projeto)**Consumindo o Pacote no Projeto:**

Você pode criar um projeto console para testes:  

```
dotnet new console --name ExamplePackageTest
cd ExamplePackageTest
```

Use o comando dotnet add package para instalar o pacote:  

```
dotnet add package examplePackage.Convert --version 1.0.0
```

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#testando-o-pacote)Testando o Pacote

Abra o arquivo **Program.cs** do projeto de teste e use o pacote:

[![Importando pacote da fonte local](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Friirfv6wsay6rkoz3tdq.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Friirfv6wsay6rkoz3tdq.png)

[![Utilizando pacote da fonte local](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fd123n0bvkc5mmi2jmw01.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fd123n0bvkc5mmi2jmw01.png)

## [](https://dev.to/devgabrielb/seu-primeiro-pacote-nuget-um-passo-a-passo-pratico-1o4n#publica%C3%A7%C3%A3o)Publicação

Após validar seu pacote, é hora de publicá-lo. Acesse sua conta em [NuGet.org](https://www.nuget.org/), vá até o seu perfil e crie uma nova chave.

[![Gerando chave para publicação de pacotes](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fpvjfb3ozoz75bqijmmrd.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fpvjfb3ozoz75bqijmmrd.png)

No terminal, use o comando abaixo para publicar seu pacote no NuGet:  

```
dotnet nuget push bin\Release\examplePackage.Convert.1.0.0.nupkg --api-key SuaAPIkEY --source https://api.nuget.org/v3/index.json
```

Pronto, se tudo estiver correto após alguns minutos, o pacote estará disponível no [NuGet.org](http://nuget.org/).

[![Pacote publicado](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F2ptnm395so7h1w2g567d.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F2ptnm395so7h1w2g567d.png)

