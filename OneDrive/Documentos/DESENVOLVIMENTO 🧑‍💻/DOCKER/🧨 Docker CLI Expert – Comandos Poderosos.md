




### 🔧 1. **Criar e rodar container com nome, volume e rede**

bash

```
docker run -d --name web-nginx \
  -p 8080:80 \
  -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
  --network minha-rede \
  nginx
```

- `-d`: modo detached
    
- `--name`: nome personalizado
    
- `-v`: monta volume local
    
- `--network`: conecta à rede personalizada
    

### 🧠 2. **Criar rede personalizada**

bash

```
docker network create minha-rede
```

- Ideal para conectar múltiplos containers isoladamente.
    

### 🧪 3. **Executar comando dentro do container**

bash

```
docker exec -it web-nginx bash
```

- Entra no terminal do container para inspeção ou ajustes.
    

### 📦 4. **Criar volume persistente**

bash

```
docker volume create dados-db
```

### 🐬 5. **Rodar MySQL com volume e variáveis**

bash

```
docker run -d --name meu-mysql \
  -e MYSQL_ROOT_PASSWORD=root123 \
  -e MYSQL_DATABASE=labdb \
  -e MYSQL_USER=uyrizin \
  -e MYSQL_PASSWORD=senha123 \
  -v dados-db:/var/lib/mysql \
  --network minha-rede \
  mysql:5.7
```

### 🔍 6. **Inspecionar container**

bash

```
docker inspect web-nginx
```

- Retorna JSON com todos os detalhes: IP, volumes, rede, etc.
    

### 📊 7. **Monitorar uso de recursos**

bash

```
docker stats
```

- CPU, memória, rede e disco em tempo real.
    

### 🧼 8. **Limpar tudo que não está em uso**

bash

```
docker system prune -a --volumes
```

- Remove containers parados, imagens não usadas e volumes órfãos.
    

### 🧬 9. **Build de imagem com Dockerfile**

bash

```
docker build -t minha-app .
```

- Cria imagem personalizada a partir do Dockerfile no diretório atual.
    

### ☁️ 10. **Login e push para Docker Hub**

bash

```
docker login
docker tag minha-app uyrizin/minha-app:latest
docker push uyrizin/minha-app:latest
```

- Publica sua imagem no Docker Hub.