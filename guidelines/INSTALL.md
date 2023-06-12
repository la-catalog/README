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

## fedora
```bash
# git
sudo dnf install -y git

# curl
sudo dnf install -y curl

# zero tier
curl -s https://install.zerotier.com | sudo bash

# pyenv
sudo dnf install make gcc zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel libuuid-devel gdbm-devel libnsl2-devel
sudo curl https://pyenv.run | bash
echo "
# pyenv
export PYENV_ROOT=\"\$HOME/.pyenv\"
command -v pyenv >/dev/null || export PATH=\"\$PYENV_ROOT/bin:\$PATH\"
eval \"\$(pyenv init -)\"
" | tee -a ~/.bash_profile ~/.bashrc
source ~/.bash_profile
pyenv install --force 3.11.0

# pdm
curl -sSL https://raw.githubusercontent.com/pdm-project/pdm/main/install-pdm.py | python3 -
echo "
# pdm
export PATH=/home/thiagola92/.local/bin:\$PATH
" | tee -a ~/.bash_profile ~/.bashrc
source ~/.bashrc
pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion
pdm plugin add pdm-version

# terraform
sudo dnf install -y dnf-plugins-core
sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/fedora/hashicorp.repo
sudo dnf -y install terraform

# github command line interface
sudo dnf install -y gh
```

## ubuntu
```bash
# git
sudo apt install -y git

# curl
sudo apt install -y curl

# docker + docker compose
sudo apt install -y ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo groupadd docker
sudo usermod -aG docker $USER

# zero tier
curl -s https://install.zerotier.com | sudo bash

# pyenv
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev git
sudo curl https://pyenv.run | bash
echo "
# pyenv
export PYENV_ROOT=\"\$HOME/.pyenv\"
command -v pyenv >/dev/null || export PATH=\"\$PYENV_ROOT/bin:\$PATH\"
eval \"\$(pyenv init -)\"
" | tee -a ~/.bash_profile ~/.bashrc
source ~/.bash_profile
pyenv install --force 3.11.0

# pdm
sudo apt install python3-venv -y
curl -sSL https://raw.githubusercontent.com/pdm-project/pdm/main/install-pdm.py | python3 -
echo "
# pdm
export PATH=/home/thiagola92/.local/bin:\$PATH
" | tee -a ~/.bash_profile ~/.bashrc
source ~/.bashrc
pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion
pdm --pep582 >> ~/.bash_profile
pdm config python.use_venv false
pdm plugin add pdm-version

# terraform
sudo apt-get install -y gnupg software-properties-common
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt-get install -y terraform

# github command line interface
type -p curl >/dev/null || sudo apt install curl -y
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

## windows
TODO
