



### 🔍 1. `docker inspect <container ou imagem>`

- **Exemplo:** `docker inspect meu-lab-docker-web-1`
    
- **Função:** Retorna um JSON completo com todos os detalhes do container ou imagem.
    
- **Uso avançado:** Pode extrair IP interno, volumes montados, variáveis de ambiente, etc.
    
- **Dica:** Combine com `jq` para filtrar:
    
    bash
    
    ```
    docker inspect meu-lab-docker-web-1 | jq '.[0].NetworkSettings.IPAddress'
    ```
    

### 🧱 2. `docker commit <container> <nova-imagem>`

- **Exemplo:** `docker commit meu-lab-docker-web-1 uyrizin/nginx-custom`
    
- **Função:** Cria uma nova imagem a partir de um container modificado.
    
- **Uso avançado:** Ideal para salvar alterações feitas manualmente dentro de um container.
    

### 🧰 3. `docker diff <container>`

- **Função:** Mostra as mudanças feitas no sistema de arquivos do container.
    
- **Exemplo:** `docker diff meu-lab-docker-web-1`
    
- **Dica:** Excelente para auditoria e debugging.
    

### 🧠 4. `docker stats`

- **Função:** Exibe uso de CPU, memória, rede e disco em tempo real dos containers.
    
- **Uso avançado:** Monitoramento leve sem precisar de ferramentas externas.
    

### 🧭 5. `docker network ls` + `docker network inspect`

- **Função:** Lista e inspeciona redes Docker.
    
- **Exemplo:**
    
    bash
    
    ```
    docker network inspect meu-lab-net
    ```
    
- **Dica:** Ajuda a entender como os containers se comunicam entre si.
    

### 🧼 6. `docker system prune`

- **Função:** Remove tudo que não está sendo usado: containers parados, imagens não referenciadas, volumes órfãos.
    
- **Cuidado:** Use com atenção!
    
    bash
    
    ```
    docker system prune -a --volumes
    ```
    
- **Dica:** Excelente para liberar espaço em disco.
    

### 🔒 7. `docker scan <imagem>`

- **Função:** Verifica vulnerabilidades conhecidas na imagem.
    
- **Exemplo:** `docker scan nginx`
    
- **Uso avançado:** Segurança em ambientes de produção.
    

### 🧪 8. `docker build --no-cache`

- **Função:** Força o build da imagem sem usar cache.
    
- **Exemplo:** `docker build --no-cache -t minha-app .`
    
- **Dica:** Útil quando você quer garantir que tudo seja reconstruído do zero.
    

### 🧬 9. `docker tag <imagem> <novo-nome>`

- **Exemplo:** `docker tag nginx uyrizin/nginx:dev`
    
- **Função:** Cria uma nova tag para uma imagem existente.
    
- **Uso avançado:** Preparar para push em repositórios como Docker Hub.
    

### ☁️ 10. `docker push <imagem>`

- **Exemplo:** `docker push uyrizin/nginx:dev`
    
- **Função:** Envia sua imagem para o Docker Hub ou outro registry.
    
- **Pré-requisito:** Estar logado com `docker login`.
    

