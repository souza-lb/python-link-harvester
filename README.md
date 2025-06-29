# 🚀 Python Link Harvester - Coletor de Links Python

**Um script inteligente para coletar e organizar links de código-fonte do Python diretamente do repositório oficial**  
`v1.0` · `Shell Script` · ⏱️ Atualizado em 29/06/2025

## 🌟 Visão Geral

O **Python Link Harvester** é um utilitário em shell script que automatiza a busca, filtragem e organização de links para códigos-fonte do Python diretamente do repositório oficial. Ideal para:

- Administradores de sistemas Python
- Desenvolvedores que precisam de versões específicas do Python
- Manutenção de ambientes com múltiplas versões do Python
- Automação de instalações em servidores remotos

## ⚙️ Parâmetros Configuráveis
| Variável         | Valor Padrão                               | Descrição                                  |
|------------------|--------------------------------------------|--------------------------------------------|
| `URL_BASE`       | `https://www.python.org/downloads/source/` | Repositório oficial do Python              |
| `EXTENSION`      | `tar.xz`                                   | Formato do arquivo de código-fonte         |
| `OUTPUT_FILE`    | `link-python.txt`                          | Arquivo de saída com links                 |

## 🛠️ Como Usar

### 📦 Execução Direta via URL
No terminal com sua conta de usuário comum execute:

```bash
wget -qO- https://raw.githubusercontent.com/souza-lb/python-link-harvester/main/get-link-python | bash
```

### 📥 Clonar e executar via Git
Para personalização e controle total:

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/python-link-harvester.git

# 2. Acesse o diretório
cd python-link-harvester

# 3. Dê permissão de execução
chmod +x get-link-python

# 4. Execute o script
./get-link-python

# (Opcional) Mova para seu PATH pessoal
mv get-link-python ~/.local/bin/
```

### ▶️ Execução Básica
```bash
./get-link-python
```

### 📝 Saída Esperada
```
🚀 Iniciando busca em: https://www.python.org/downloads/source/
🔍 Procurando por arquivos .tar.xz
⏳ Aguarde alguns instantes...
📁 Processando: https://www.python.org/downloads/source/

📋 Lista de links ordenados:
  ✅ https://www.python.org/ftp/python/3.12.0/Python-3.12.0.tar.xz
  ✅ https://www.python.org/ftp/python/3.11.6/Python-3.11.6.tar.xz
  ... [outros links]

✅ Busca concluída!
=================================
📦 Arquivos encontrados:    58
🔧 Após remover duplicatas: 55
💾 Links salvos em:         link-python.txt
=================================
```

### 🔄 Atualizando Parâmetros
Para buscar outras extensões (ex: `.tgz` para versões mais antigas):
```bash
# Edite o script e modifique:
EXTENSION="tgz"
```

## ⚠️ Dependências

### 📦 Instalação do Lynx
O script requer `lynx` para funcionar. Instale conforme seu sistema:

| Sistema Operacional      | Comando de Instalação       |
|--------------------------|-----------------------------|
| **Debian/Ubuntu**        | `sudo apt-get install lynx` |
| **RHEL/CentOS**          | `sudo yum install lynx`     |
| **Arch Linux**           | `sudo pacman -S lynx`       |
| **macOS (Homebrew)**     | `brew install lynx`         |

## 🧩 Detalhes Técnicos

### 🔍 Algoritmo de Filtragem
1. Coleta todos os links da página de downloads de código-fonte
2. Filtra links pela extensão especificada (ex: `.tar.xz`)
3. Extrai versões dos nomes de arquivo usando expressões regulares
4. Remove duplicatas mantendo a versão mais recente

### 📊 Ordenação Inteligente
As versões são processadas em 4 etapas:
```bash
# 1. Extração da versão do nome do arquivo:
"Python-3.12.0.tar.xz" → "3.12.0"

# 2. Conversão para formato ordenável (substitui pontos por espaços):
"3.12.0" → "3 12 0"

# 3. Ordenação numérica por partes (major, minor, patch):
sort -k1,1n -k2,2n -k3,3n -k4,4n

# 4. Remoção de duplicatas e reconstrução das URLs
```

### ⚡ Otimizações
- Uso de arquivos temporários para processamento eficiente
- Ordenação semântica de versões multi-nível
- Contagem precisa de arquivos válidos vs. duplicados
- Mensagens de status intuitivas com emojis visuais
- Tratamento de erros para dependência do lynx
- Suporte a diferentes formatos de release (alpha, beta, rc)

---

## ❤️ Apoie o Projeto

**Dúvidas, sugestões e contribuições?**  
Leonardo Bruno  
souzalb@proton.me  

**Gostou do projeto e quer realizar uma contribuição voluntária?**  
*(Pode ser o valor de uma xícara de café ou chá...) ☕ 🍵*  

Chave PIX:  
`8dcc7e3c-0c6a-4c6f-a4c0-26a5e62686db`  

Ou utilize o QR Code abaixo:  

<p align="center">
  <img src="images/qrcode-pix.png" alt="QR Code PIX" width="200">
</p>

**Você também pode utilizar o PayPal:**  

[![PayPal](https://img.shields.io/badge/Donate-PayPal-00457C?style=for-the-badge&logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=EQVW5QQ7GBGSY)

<p align="center">
  <img src="images/qrcode-paypal.png" alt="QR Code PayPal" width="200">
</p>

**A utilização deste projeto é livre para alterações e adaptações**  
*Desde que feita a devida referência ao repositório original e seu criador.*
