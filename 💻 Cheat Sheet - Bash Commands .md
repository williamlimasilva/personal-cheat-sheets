# 💻 Cheat Sheet - Bash Commands 

<style>
:root {
    --bg-primary: #1E1E1E;
    --bg-secondary: #252526;
    --bg-tertiary: #2D2D2D;
    --text-primary: #D4D4D4;
    --text-accent: #569CD6;
    --keyword: #C586C0;
    --string: #CE9178;
    --comment: #6A9955;
    --operator: #D4D4D4;
    --border: #404040;
}

body {
    background-color: var(--bg-primary);
    color: var(--text-primary);
    font-family: 'Consolas', monospace;
    line-height: 1.6;
    margin: 20px;
    max-width: 1920px;
}

.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(600px, 1fr));
    gap: 20px;
    margin: 0 auto;
}

.section {
    background: var(--bg-secondary);
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 20px;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin: 10px 0;
    background-color: var(--bg-tertiary);
    border-radius: 4px;
}

th, td {
    padding: 12px;
    text-align: left;
    border-bottom: 1px solid var(--border);
}

td:nth-child(3) {
    font-family: 'Consolas', monospace;
    color: var(--string);
}

td:nth-child(4) {
    color: var(--comment);
    font-style: italic;
}

code {
    color: var(--string);
    background-color: var(--bg-tertiary);
    padding: 2px 4px;
    border-radius: 3px;
}

h2 {
    color: var(--text-accent);
    border-bottom: 1px solid var(--text-accent);
    padding-bottom: 5px;
}

h3 {
    color: var(--keyword);
}

.example {
    background-color: var(--bg-tertiary);
    padding: 8px;
    border-radius: 4px;
    margin-top: 4px;
    font-size: 0.9em;
}
</style>

## 📜 Bash Scripting Basics

<div class="container">
<div class="section">

### 🔰 Elementos Fundamentais

| Elemento | Descrição | Exemplo | Resultado |
|----------|-----------|---------|-----------|
| 📌 Shebang | Define o interpretador | `#!/bin/bash` | Define bash como interpretador |
| 🔤 Variáveis | Armazenamento de valores | `nome="João"` | Variável 'nome' contém "João" |
| 📥 Input | Entrada do usuário | `read -p "Nome: " nome` | Aguarda input do usuário |
| ⚡ Execução | Permissão de execução | `chmod +x script.sh` | Torna script executável |

### 🗂️ Navegação e Arquivos
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 📍 `pwd` | Mostra diretório atual | `pwd` | `/home/usuario` |
| 📁 `cd` | Muda diretório | `cd ~/Documentos` | Vai para Documentos |
| 📋 `ls` | Lista conteúdo | `ls -la` | Mostra arquivos ocultos e detalhes |
| 📝 `touch` | Cria arquivo vazio | `touch projeto.txt` | Cria arquivo 'projeto.txt' |
| 📂 `mkdir` | Cria diretório | `mkdir -p proj/src` | Cria diretórios aninhados |
| ✂️ `cp` | Copia arquivos | `cp -r pasta1 pasta2` | Copia recursivamente |
| 📦 `mv` | Move/renomeia | `mv old.txt new.txt` | Renomeia arquivo |
| 🗑️ `rm` | Remove arquivo | `rm -rf pasta/` | Remove pasta e conteúdo |

### 🔍 Busca e Filtros
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔎 `find` | Busca arquivos | `find . -name "*.log"` | Lista todos arquivos .log |
| 📝 `grep` | Busca texto | `grep -r "erro" .` | Busca "erro" recursivamente |
| 📊 `wc` | Conta linhas/palavras | `wc -l arquivo.txt` | Número de linhas |
| 👀 `less` | Visualiza arquivo | `less +F log.txt` | Monitora arquivo em tempo real |
| 📄 `cat` | Mostra conteúdo | `cat -n script.sh` | Mostra com números de linha |
| 🔍 `locate` | Busca rápida | `locate -i arquivo` | Busca case-insensitive |

### 💻 Processos e Sistema
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 📊 `ps` | Lista processos | `ps aux \| grep nginx` | Mostra processos nginx |
| 🔝 `top` | Monitor de processos | `top -u usuario` | Mostra processos do usuário |
| ⚡ `kill` | Termina processo | `kill -9 1234` | Força término do PID 1234 |
| 💾 `df` | Espaço em disco | `df -h /home` | Espaço em formato legível |
| 🧮 `free` | Memória livre | `free -m` | Memória em megabytes |
| ⏰ `date` | Data e hora | `date "+%d/%m/%Y"` | Data formatada |

### 🌐 Rede e Conectividade
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🌍 `ping` | Testa conexão | `ping -c 4 google.com` | 4 pings para google.com |
| 📡 `wget` | Baixa arquivos | `wget -c arquivo.zip` | Download com continuação |
| 🔌 `netstat` | Status da rede | `netstat -tulpn` | Portas TCP/UDP abertas |
| 🔒 `ssh` | Conexão segura | `ssh -p 2222 user@host` | SSH na porta 2222 |
| 📤 `scp` | Copia via SSH | `scp -P 2222 arq.txt srv:~` | Copia usando porta 2222 |
| 🌐 `curl` | Transfere dados | `curl -o file.txt url` | Salva output em file.txt |

### 🔐 Permissões e Usuários
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 👤 `chmod` | Muda permissões | `chmod 755 script.sh` | rwxr-xr-x |
| 👥 `chown` | Muda proprietário | `chown -R user:group .` | Muda recursivamente |
| 🔑 `sudo` | Executa como root | `sudo !!` | Repete último comando como root |
| 👥 `useradd` | Cria usuário | `useradd -m -s /bin/bash user` | Cria com home e bash |
| 🔒 `passwd` | Muda senha | `passwd -l usuario` | Bloqueia conta |

### 📦 Compressão e Arquivos
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 📦 `tar` | Arquiva/Comprime | `tar -czf backup.tgz ./` | Comprime diretório atual |
| 🗜️ `zip` | Comprime ZIP | `zip -r backup.zip ./` | ZIP recursivo |
| 📤 `unzip` | Extrai ZIP | `unzip -l arquivo.zip` | Lista conteúdo do ZIP |
| 🗜️ `gzip` | Comprime GZIP | `gzip -9 arquivo.txt` | Máxima compressão |

### 🔄 Redirecionamento e Pipes
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| `>` | Redireciona saída | `ls > lista.txt` | Salva lista em arquivo |
| `>>` | Anexa saída | `echo "log" >> app.log` | Anexa ao final do arquivo |
| `\|` | Pipe | `ps aux \| grep php` | Filtra saída do ps |
| `2>` | Redireciona erro | `cmd 2> erro.log` | Salva erros em arquivo |
| `&>` | Redireciona tudo | `cmd &> tudo.log` | Salva saída e erros |

### 📊 Monitoramento e Diagnóstico
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 📈 `htop` | Monitor avançado | `htop -u user` | Monitor interativo por usuário |
| 🔍 `lsof` | Lista arquivos abertos | `lsof -i :80` | Mostra processos usando porta 80 |
| 📊 `vmstat` | Estatísticas virtuais | `vmstat 1` | Stats a cada 1 segundo |
| 🌡️ `sensors` | Temperatura hardware | `sensors` | Mostra temp. do sistema |
| 📉 `iostat` | Estatísticas I/O | `iostat -x 1` | Stats de disco detalhadas |
| 🔎 `strace` | Trace chamadas sistema | `strace -p 1234` | Debug processo 1234 |
| 📊 `dmesg` | Mensagens kernel | `dmesg -T` | Logs com timestamp |
| 💻 `uname` | Info do sistema | `uname -a` | Todas as infos do sistema |

### ⚙️ Configuração do Sistema
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔧 `modprobe` | Gerencia módulos | `modprobe -r modulo` | Remove módulo do kernel |
| ⚡ `systemctl` | Controle systemd | `systemctl status ssh` | Status do serviço SSH |
| 🔄 `update-rc.d` | Gerencia init.d | `update-rc.d ssh defaults` | Habilita SSH no boot |
| 🔧 `alternatives` | Gerencia alternativas | `alternatives --config java` | Configura versão Java |
| 📝 `hostnamectl` | Config hostname | `hostnamectl set-hostname novo` | Muda nome do host |
| 🕒 `timedatectl` | Config datetime | `timedatectl set-timezone UTC` | Define timezone |
| 🌐 `localectl` | Config locale | `localectl set-locale LANG=pt_BR.UTF-8` | Define locale |

### 🗄️ Gerenciamento de Pacotes
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 📦 `apt` | Gerenciador Debian | `apt update && apt upgrade` | Atualiza sistema |
| 🔍 `apt-cache` | Info de pacotes | `apt-cache search nginx` | Busca pacote nginx |
| 📥 `dpkg` | Pacotes Debian | `dpkg -i pacote.deb` | Instala pacote .deb |
| 🔄 `yum` | Gerenciador RHEL | `yum install httpd` | Instala Apache |
| 📦 `rpm` | Pacotes RPM | `rpm -qa` | Lista todos pacotes |
| 🔍 `snap` | Pacotes Snap | `snap list` | Lista snaps instalados |
| 📥 `flatpak` | Pacotes Flatpak | `flatpak install app` | Instala aplicativo |

### 🛠️ Ferramentas de Desenvolvimento
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔍 `gdb` | Debugger GNU | `gdb ./programa` | Inicia debug do programa |
| 📊 `valgrind` | Análise memória | `valgrind ./app` | Detecta memory leaks |
| 🏗️ `make` | Build automação | `make install` | Compila e instala |
| 📝 `diff` | Compara arquivos | `diff -u file1 file2` | Mostra diferenças |
| 🔄 `patch` | Aplica patches | `patch < fix.patch` | Aplica correção |
| 🔍 `nm` | Lista símbolos | `nm -D lib.so` | Símbolos da biblioteca |
| 🔬 `objdump` | Analisa binários | `objdump -d prog` | Mostra assembly |

### 🌐 Análise de Rede
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔍 `nmap` | Scanner de rede | `nmap -sS 192.168.1.0/24` | Scan stealth da rede |
| 📊 `tcpdump` | Captura pacotes | `tcpdump -i eth0` | Monitora interface eth0 |
| 🌐 `dig` | Consulta DNS | `dig +short google.com` | IPs do google.com |
| 🔍 `whois` | Info domínios | `whois domain.com` | Info do domínio |
| 📡 `iftop` | Monitor de rede | `iftop -i eth0` | Uso de banda por conexão |
| 🌍 `traceroute` | Trace rota | `traceroute -n site.com` | Mostra hops até destino |
| 🔌 `ss` | Status sockets | `ss -tuln` | Lista portas abertas |
| 📊 `iptraf` | Monitor tráfego | `iptraf-ng -i eth0` | Stats de rede em tempo real |

### 🔒 Segurança e Criptografia
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔑 `ssh-keygen` | Gera chaves SSH | `ssh-keygen -t ed25519` | Cria chave ED25519 |
| 🔒 `openssl` | Ferramentas SSL | `openssl enc -aes-256-cbc` | Encripta com AES |
| 🔐 `gpg` | GNU Privacy Guard | `gpg -c arquivo` | Encripta arquivo |
| 🔑 `keyctl` | Gerencia chaves | `keyctl list @u` | Lista chaves do usuário |
| 🛡️ `fail2ban-client` | Proteção brute force | `fail2ban-client status` | Status das proteções |
| 📝 `logwatch` | Analisa logs | `logwatch --detail high` | Relatório detalhado |
| 🔒 `chage` | Política de senhas | `chage -l usuario` | Info de senha do usuário |

### 📱 Dispositivos e Hardware
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 💽 `fdisk` | Gerencia partições | `fdisk -l` | Lista partições |
| 💾 `mount` | Monta sistemas | `mount /dev/sdb1 /mnt` | Monta partição |
| 🔍 `lsblk` | Lista block devices | `lsblk -f` | Mostra filesystems |
| 🖥️ `lshw` | Lista hardware | `lshw -short` | Resume hardware |
| 🎮 `lspci` | Lista PCI | `lspci -v` | Devices PCI detalhado |
| 🔌 `lsusb` | Lista USB | `lsusb -t` | Árvore de devices USB |
| 🖨️ `lpstat` | Status impressora | `lpstat -p -d` | Lista impressoras |
| 💿 `dd` | Copia bit-a-bit | `dd if=/dev/sda of=backup.img` | Backup de disco |

### 🗃️ Manipulação de Texto Avançada
| Comando | Descrição | Exemplo | Resultado |
|---------|-----------|---------|-----------|
| 🔄 `sed` | Editor de streams | `sed 's/old/new/g' file` | Substitui texto |
| 📊 `awk` | Processamento texto | `awk '{print $1}' file` | Extrai primeira coluna |
| 🔤 `sort` | Ordena linhas | `sort -k2 -n file` | Ordena pela coluna 2 |
| 🎯 `uniq` | Remove duplicados | `sort file \| uniq -c` | Conta ocorrências |
| ✂️ `cut` | Extrai campos | `cut -d: -f1 /etc/passwd` | Extrai usernames |
| 🔍 `tr` | Traduz caracteres | `tr '[:lower:]' '[:upper:]'` | Converte para maiúsculas |
| 📏 `column` | Formata colunas | `column -t file` | Alinha em colunas |
| 🔄 `join` | Une arquivos | `join file1 file2` | Combina por chave |

### 📝 Exemplo Prático: Script Básico
```bash
#!/bin/bash                          # -----------------------> Shebang Line

# Variáveis
nome="João"                          # -----------------------> Variables
idade=25

# Input do Usuário
read -p "Digite seu nome: " usuario  # -----------------------> User Input
echo "Olá, $usuario!"

# Verificação de Root
if [ "$EUID" -ne 0 ]; then          # -----------------------> Conditional if
    echo "Execute como root"
else
    echo "Você é root"
fi

# Loop Exemplo
for i in {1..5}; do                 # -----------------------> For Loop
    echo "Contagem: $i"
done

# Função de Saudação
function saudar() {                 # -----------------------> Functions
    echo "Olá, $1!"
}
saudar "Alice"

# Menu de Opções
echo "Escolha uma opção (1-3):"     # -----------------------> Case Statement
read opcao
case $opcao in
    1) echo "Opção Um";;
    2) echo "Opção Dois";;
    *) echo "Opção Inválida";;
esac
```

### 🔧 Exemplo Prático: Manipulação de Arquivos
```bash
#!/bin/bash

# Verificação de Arquivo
arquivo="config.txt"                 # -----------------------> File Operations
if [ -e "$arquivo" ]; then
    echo "Arquivo existe"
else
    echo "Arquivo não existe"
fi

# Argumentos da Linha de Comando
echo "Primeiro arg: $1"             # -----------------------> Command Line Arguments
echo "Segundo arg: $2"

# Status de Saída
ls arquivo_inexistente 2> /dev/null # -----------------------> Exit Status
echo "Status: $?"

# Arrays
frutas=("Maçã" "Laranja" "Banana")  # -----------------------> Indexed Arrays
echo "Primeira fruta: ${frutas[0]}"

# Arrays Associativos
declare -A capitais                 # -----------------------> Associative Arrays
capitais[Brasil]="Brasília"
echo "Capital: ${capitais[Brasil]}"

# Substituição de Comando
hoje=$(date +%Y-%m-%d)              # -----------------------> Command Substitution
echo "Data: $hoje"

# Redirecionamento
echo "Log entry" > log.txt          # -----------------------> Redirections
find / -name "*.txt" &> /dev/null

# Operações Aritméticas
resultado=$((5 + 3))                # -----------------------> Arithmetic
echo "5 + 3 = $resultado"

# Expansão de Parâmetros
DIR="/usr/local/bin"                # -----------------------> Parameter Expansion
echo ${DIR##*/}
```

### 🌐 Exemplo Prático: Rede e Sistema
```bash
#!/bin/bash

# Monitoramento de Sistema
echo "🔍 Verificando Sistema..."
echo "CPU: $(top -bn1 | grep "Cpu(s)" | awk '{print $2}')%"
echo "Memória: $(free -h | awk '/^Mem:/ {print $3 "/" $2}')"
df -h / | awk 'NR==2 {print "Disco: " $5 " usado"}'

# Verificação de Rede
echo "🌐 Testando Conectividade..."
if ping -c 1 google.com &> /dev/null; then
    echo "Internet: Conectado"
else
    echo "Internet: Desconectado"
fi

# Portas Abertas
echo "🔌 Portas TCP Abertas:"
netstat -tuln | grep LISTEN

# Processos
echo "📊 Top 5 Processos por CPU:"
ps aux --sort=-%cpu | head -n 6
```

### 🔒 Exemplo Prático: Segurança e Backup
```bash
#!/bin/bash

# Backup de Diretório
backup_dir="backup_$(date +%Y%m%d)"
echo "📦 Criando backup em $backup_dir..."
mkdir -p "$backup_dir"
tar -czf "$backup_dir/files.tar.gz" /path/to/files

# Verificação de Permissões
echo "🔐 Verificando permissões..."
find . -type f -perm /111 -ls

# Log de Acesso
echo "📝 Últimos 5 logins:"
last | head -n 5

# Monitoramento de Arquivos
echo "👀 Arquivos modificados nas últimas 24h:"
find /home -mtime -1 -type f -ls
```

### 🔧 Exemplo Prático: Manutenção
```bash
#!/bin/bash

# Limpeza de Sistema
echo "🧹 Iniciando limpeza..."
find /tmp -type f -atime +7 -delete
find /var/log -type f -name "*.log" -size +100M

# Verificação de Serviços
echo "⚙️ Status dos serviços críticos:"
services=("ssh" "nginx" "mysql")
for service in "${services[@]}"; do
    systemctl is-active "$service" &> /dev/null
    if [ $? -eq 0 ]; then
        echo "✅ $service: Ativo"
    else
        echo "❌ $service: Inativo"
    fi
done

# Relatório de Saúde
echo "📊 Gerando relatório de saúde..."
echo "Uptime: $(uptime)"
echo "Carga do Sistema: $(cat /proc/loadavg)"
echo "Espaço em Disco: $(df -h /)"
```

{{ ... }}
