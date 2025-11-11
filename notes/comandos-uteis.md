# 🧰 Comandos Úteis – Linux e Docker

Lista de comandos práticos e comentados para administração do Linux e manuseio do Docker.  
Ideal para estudos, testes e configuração de ambientes no servidor Ubuntu (T430) e via VS Code remoto.

---

## 🐧 Comandos Linux básicos

### 🔹 Navegação e manipulação de arquivos
```bash
pwd                          # Mostra o diretório atual
ls -lh                       # Lista arquivos com detalhes e tamanhos legíveis
cd /caminho/                 # Acessa um diretório
mkdir nome_pasta             # Cria um novo diretório
rm -rf nome_pasta            # Remove pasta e conteúdo (⚠️ cuidado!)
cp arquivo1 arquivo2         # Copia arquivo
mv origem destino            # Move ou renomeia arquivo
cat arquivo.txt              # Exibe conteúdo de um arquivo
less arquivo.txt             # Exibe arquivo paginado (setas ↑ ↓)
```
### 🔹 Sistema e informações
```bash
hostnamectl                  # Exibe informações do sistema
uname -a                     # Mostra kernel e arquitetura
lsb_release -a               # Mostra versão da distribuição
uptime                       # Tempo ligado e carga média
df -h                        # Espaço em disco
free -h                      # Memória usada e livre
top ou htop                  # Monitora uso de CPU e RAM
ps aux | grep processo        # Lista processos em execução
kill -9 PID                  # Mata um processo travado
```
### 🔹 Rede e conectividade
```bash
ip a                         # Mostra interfaces de rede e IPs
ping google.com              # Testa conectividade com a internet
curl ifconfig.me             # Mostra IP público
netstat -tuln                # Lista portas abertas
ss -tunlp                    # Mostra conexões ativas e processos
systemctl status ssh         # Verifica status do serviço SSH
```
### 🔹 Permissões e usuários
```bash
sudo useradd nomeusuario     # Cria novo usuário
sudo passwd nomeusuario      # Define senha
sudo usermod -aG sudo nomeusuario   # Adiciona ao grupo sudo
groups nomeusuario           # Mostra grupos do usuário
chmod 755 arquivo.sh         # Permissão leitura/execução (rwxr-xr-x)
chown willian:willian arquivo.txt  # Muda dono e grupo de um arquivo
```
### 🔹 Gerenciamento de pacotes (Ubuntu)
```bash
sudo apt update              # Atualiza lista de pacotes
sudo apt upgrade -y          # Atualiza todos os pacotes instalados
sudo apt install nome        # Instala um pacote
sudo apt remove nome         # Remove pacote
sudo apt autoremove          # Remove dependências não usadas
dpkg -l | grep nome          # Lista pacotes instalados com nome específico
```
### 🔹 Serviços e logs
```bash
sudo systemctl start nome    # Inicia um serviço
sudo systemctl stop nome     # Para um serviço
sudo systemctl restart nome  # Reinicia um serviço
sudo systemctl enable nome   # Habilita na inicialização
sudo systemctl disable nome  # Desativa na inicialização
sudo journalctl -u nome -f   # Acompanha log em tempo real
```
## 🧠 Git – Versionamento rápido
```bash
git init                     # Cria repositório Git local
git clone URL                # Clona repositório existente
git add .                    # Adiciona alterações
git commit -m "mensagem"     # Confirma alterações
git push origin main         # Envia para o GitHub
git pull                     # Atualiza com últimas alterações
git branch -a                # Lista branches
git checkout -b nova-branch  # Cria e muda de branch
```
## 🐳 Docker – Comandos essenciais

### 🔹 Verificar instalação e status
```bash
docker --version             # Mostra versão instalada
sudo systemctl status docker # Verifica status do serviço
sudo systemctl start docker  # Inicia o daemon
sudo systemctl enable docker # Habilita na inicialização
```
### 🔹 Imagens
```bash
docker pull ubuntu:22.04     # Baixa imagem
docker images                # Lista imagens locais
docker rmi nome_imagem       # Remove imagem
```
### 🔹 Containers
```bash
docker ps                    # Lista containers ativos
docker ps -a                 # Lista todos (ativos e parados)
docker run hello-world       # Teste do Docker
docker run -it ubuntu bash   # Abre shell interativo no Ubuntu
docker run -d app            # Evita que o terminal trave
docker run -P app            # Atribui uma porta aleatoria para o container
docker run -p 3000:80 app    # Atribui uma porta especifica para o container
docker start ID              # Inicia container existente
docker stop ID               # Para container
docker rm ID                 # Remove container
docker logs ID               # Mostra logs
docker exec -it ID bash      # Acessa container já em execução
```
### 🔹 Volumes e persistência
```bash
docker volume ls             # Lista volumes
docker volume create nome    # Cria volume
docker run -v meuvolume:/dados ubuntu   # Monta volume
docker volume inspect nome   # Detalhes de um volume
docker volume rm nome        # Remove volume
```
### 🔹 Rede
```bash
docker network ls            # Lista redes Docker
docker network create minha_rede
docker run --network minha_rede nginx
docker inspect nome_container | grep IPAddress   # Ver IP do container
```
### 🔹 Limpeza de ambiente
```bash
docker system prune -af      # Remove tudo que não está sendo usado
docker rm -f $(docker ps -aq)     # Remove todos containers
docker rmi -f $(docker images -q) # Remove todas imagens
```
## 🧩 Docker Compose

### 🔹 Comandos principais
```bash
docker compose up -d         # Sobe os serviços em segundo plano
docker compose down          # Para e remove containers
docker compose ps            # Lista serviços ativos
docker compose logs -f       # Mostra logs em tempo real
docker compose build         # Reconstrói imagens
docker compose exec app bash # Acessa container nomeado "app"
```
## ⚙️ Troubleshooting (resolução de problemas)
```bash
docker run hello-world               # Testar o Docker rodando um container de teste
sudo usermod -aG docker $USER        # Adiciona usuário ao grupo docker
sudo systemctl restart docker        # Reinicia daemon
sudo journalctl -fu docker.service   # Ver logs do Docker
docker inspect nome_container        # Detalhes técnicos de um container
docker-compose config                # Valida arquivo docker-compose.yml
```
## 🧾 Dicas gerais

# Use TAB para autocompletar comandos.
#Use CTRL + R para buscar comandos anteriores.
#clear limpa o terminal.
#exit sai do shell atual (ou container).
#Use --help após qualquer comando para ver opções:
```bash
docker run --help 
```
