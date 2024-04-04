# install
Este arquivo agrupa todas as instalações ou ações necessárias para que seu computador esteja em ambiente de desenvolvimento na organização.  
Se sinta livre para não instalar qualquer coisa que não seja necessária para você.  

Você é livre para usar outras ferramentas desde que não afetem a organização. Condições:  
- Sua ferramenta não gera nenhum arquivo extra no repositório do GitHub. 👍  
- Sua ferramenta não força adição de linhas nos arquivos para o funcionamento dela. 👍  
- Sua ferramenta não força outras pessoas a terem ela para executar o código. 👍  

(ferramentas novas são sempre negociáveis)

## macos
TODO

## ubuntu
```bash
# git
sudo apt install -y git

# curl
sudo apt install -y curl

# podman
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# zerotier
curl -s https://install.zerotier.com | sudo bash

# pdm
sudo apt install -y python3-venv;
curl -sSL https://pdm-project.org/install-pdm.py | python3 -;
echo "
# pdm
export PATH=~/.local/bin:\$PATH" | tee -a ~/.bash_profile ~/.bashrc;
source ~/.bashrc;
pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion;

# terraform
sudo apt-get install -y gnupg software-properties-common
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt-get install -y terraform

# github command line interface
sudo mkdir -p -m 755 /etc/apt/keyrings && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

## windows
TODO
