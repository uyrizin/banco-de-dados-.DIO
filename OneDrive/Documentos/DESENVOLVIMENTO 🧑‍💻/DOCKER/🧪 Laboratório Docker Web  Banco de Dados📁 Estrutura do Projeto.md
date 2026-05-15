




## 🧪 Laboratório Docker: Web + Banco de Dados

### 📁 Estrutura do Projeto



### Estrutura do Projeto

Crie uma pasta chamada `meu-lab-docker` com os seguintes arquivos:

Código

```
meu-lab-docker/
├── docker-compose.yml
└── index.html
```

### 1️⃣ `index.html` – Página simples para o Nginx

html

```
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
  <title>Meu Lab Docker</title>
</head>
<body>
  <h1>Olá, Uyrizin! 🚀</h1>
  <p>Essa página está rodando dentro de um container Nginx.</p>
</body>
</html>
```

### 2️⃣ `docker-compose.yml` – Orquestrando os containers

yaml

```
version: '3.8'

services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/usr/share/nginx/html/index.html
    networks:
      - meu-lab-net

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: labdb
      MYSQL_USER: uyrizin
      MYSQL_PASSWORD: senha123
    volumes:
      - dbdata:/var/lib/mysql
    networks:
      - meu-lab-net

volumes:
  dbdata:

networks:
  meu-lab-net:
```

### 3️⃣ Comandos para rodar o laboratório

Abra o terminal na pasta `meu-lab-docker` e execute:

bash

```
docker compose up -d
```

🔍 **Explicação:**

- `up -d`: sobe os containers em segundo plano.
    
- O Nginx vai servir o `index.html` na porta `8080`.
    
- O MySQL estará rodando com persistência de dados via volume `dbdata`.
    

### 4️⃣ Verificando os containers

bash

```
docker ps
```

Você verá algo como:

Código

```
CONTAINER ID   IMAGE     PORTS           NAMES
abc123         nginx     0.0.0.0:8080->80   meu-lab-docker-web-1
def456         mysql     3306/tcp           meu-lab-docker-db-1
```

### 5️⃣ Testando no navegador

Abra: http://localhost:8080 Você verá a página HTML com a saudação personalizada!

### 6️⃣ Explorando o banco de dados

Se quiser acessar o MySQL dentro do container:

bash

```
docker exec -it meu-lab-docker-db-1 mysql -u uyrizin -p
```

Digite a senha: `senha123`