# setup dev
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
" >> ~/.bashrc
source ~/.bashrc
pyenv install --force 3.10.5
echo "3.10.5" > ~/.python-version

# pdm
curl -sSL https://raw.githubusercontent.com/pdm-project/pdm/main/install-pdm.py | python3 -
$HOME/.local/bin/pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion
$HOME/.local/bin/pdm --pep582 >> ~/.bash_profile
$HOME/.local/bin/pdm config python.use_venv false
$HOME/.local/bin/pdm plugin add pdm-version

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

# directory structure

## macos

## ubuntu
```bash
# create directories
mkdir api
mkdir "cron job"
mkdir deployment
mkdir package
mkdir template
mkdir terraform
mkdir utility

# search repositories
gh search repos --owner la-catalog --topic api --json fullName > api.json
gh search repos --owner la-catalog --topic cronjob --json fullName > cron_job.json
gh search repos --owner la-catalog --topic deployment --json fullName > deployment.json
gh search repos --owner la-catalog --topic package --json fullName > package.json
gh search repos --owner la-catalog --topic template --json fullName > template.json
gh search repos --owner la-catalog --topic terraform --json fullName > terraform.json
gh search repos --owner la-catalog --topic utility --json fullName > utility.json

# remove templates from others topics
python -c "
import json
from pathlib import Path

template = json.loads(Path('template.json').read_text())

def remove_templates(path):
    content = json.loads(Path(path).read_text())
    content = [i for i in content if i not in template]
    Path(path).write_text(json.dumps(content))

remove_templates('api.json')
remove_templates('cron_job.json')
remove_templates('deployment.json')
remove_templates('package.json')
remove_templates('terraform.json')
remove_templates('utility.json')
"
```

## windows
