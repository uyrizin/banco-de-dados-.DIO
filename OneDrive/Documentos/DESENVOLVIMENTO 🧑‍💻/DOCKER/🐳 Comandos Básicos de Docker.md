



## **Básicos de Docker**

### 1. `docker --version`

- **Função:** Exibe a versão instalada do Docker.
    
- **Uso:** Útil para verificar se o Docker está instalado corretamente e qual versão está em uso.
    

### 2. `docker pull <imagem>`

- **Exemplo:** `docker pull nginx`
    
- **Função:** Baixa uma imagem do Docker Hub (ou outro repositório).
    
- **Explicação:** Se você quiser usar o servidor web Nginx, esse comando baixa a imagem oficial para seu ambiente local.
    

### 3. `docker images`

- **Função:** Lista todas as imagens disponíveis localmente.
    
- **Explicação:** Ajuda a visualizar quais imagens você já tem e pode usar para criar containers.
    

## 🚀 **Trabalhando com Containers**

### 4. `docker run <opções> <imagem>`

- **Exemplo:** `docker run -d -p 8080:80 nginx`
    
- **Função:** Cria e inicia um container.
    
- **Explicação:**
    
    - `-d`: executa em segundo plano (detached mode).
        
    - `-p 8080:80`: mapeia a porta 80 do container para a 8080 do host.
        
    - Isso significa que você pode acessar o Nginx via `localhost:8080`.
        

### 5. `docker ps`

- **Função:** Lista os containers em execução.
    
- **Explicação:** Mostra ID, imagem, status e portas expostas dos containers ativos.
    

### 6. `docker ps -a`

- **Função:** Lista todos os containers, inclusive os que já foram parados.
    
- **Explicação:** Útil para ver o histórico de containers criados.
    

### 7. `docker stop <container_id ou nome>`

- **Função:** Para um container em execução.
    
- **Exemplo:** `docker stop my-nginx`
    

### 8. `docker rm <container_id ou nome>`

- **Função:** Remove um container parado.
    
- **Dica:** Use `docker rm -f <id>` para forçar a remoção de um container em execução.
    

## 🛠️ **Gerenciando Imagens e Containers**

### 9. `docker rmi <imagem>`

- **Função:** Remove uma imagem local.
    
- **Exemplo:** `docker rmi nginx`
    
- **Cuidado:** Só funciona se nenhum container estiver usando essa imagem.
    

### 10. `docker exec -it <container> <comando>`

- **Exemplo:** `docker exec -it my-nginx bash`
    
- **Função:** Executa um comando dentro de um container.
    
- **Explicação:** Com `-it`, você entra interativamente no terminal do container.
    

### 11. `docker build -t <nome_da_imagem> .`

- **Função:** Cria uma imagem a partir de um `Dockerfile`.
    
- **Exemplo:** `docker build -t minha-app .`
    
- **Explicação:** O `.` indica que o Dockerfile está no diretório atual.
    

## 📦 **Volumes e Persistência de Dados**

### 12. `docker volume create <nome>`

- **Função:** Cria um volume para persistência de dados.
    
- **Exemplo:** `docker volume create dados-db`
    

### 13. `docker run -v <volume>:/caminho <imagem>`

- **Exemplo:** `docker run -v dados-db:/var/lib/mysql mysql`
    
- **Explicação:** Monta o volume no caminho especificado dentro do container