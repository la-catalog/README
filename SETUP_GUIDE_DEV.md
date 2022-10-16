# setup guide
Este arquivo agrupa todas as instalações ou ações necessárias para que seu computador esteja em ambiente de desenvolvimento no *la catalog*.  
Se sinta livre para não instalar qualquer coisa que não seja necessária para você.  

Você é livre para usar outras ferramentas desde que não afetem a organização. Condições:  
- Sua ferramenta não gera nenhum arquivo extra no repositório. 👍  
- Sua ferramenta não força adição de linhas nos arquivos para o funcionamento dela. 👍  
- Sua ferramenta não força outras pessoas a terem ela para executar o código. 👍  

(ferramentas novas são sempre negociáveis)

## windows
TODO

## macos
TODO

## ubuntu

```bash
# git
sudo apt install -y git;

# curl
sudo apt install -y curl;

# docker + docker compose
sudo apt install -y ca-certificates curl gnupg lsb-release;
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg;
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null;
sudo apt update;
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin;
sudo groupadd docker;
sudo usermod -aG docker $USER;

# zero tier
curl -s https://install.zerotier.com | sudo bash;

# pyenv
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev git;
sudo curl https://pyenv.run | bash;
echo "
# pyenv
export PYENV_ROOT=\"\$HOME/.pyenv\"
command -v pyenv >/dev/null || export PATH=\"\$PYENV_ROOT/bin:\$PATH\"
eval \"\$(pyenv init -)\"
" >> ~/.bashrc;
source ~/.bashrc
pyenv install --force 3.10.5;
echo "3.10.5" > ~/.python-version

# pdm
curl -sSL https://raw.githubusercontent.com/pdm-project/pdm/main/install-pdm.py | python3 -
$HOME/.local/bin/pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion
$HOME/.local/bin/pdm --pep582 >> ~/.bash_profile
$HOME/.local/bin/pdm config python.use_venv false
$HOME/.local/bin/pdm config repository.la-catalog.url ${PYPI_URL}
$HOME/.local/bin/pdm config repository.la-catalog.username ${PYPI_USER}
$HOME/.local/bin/pdm config repository.la-catalog.password ${PYPI_PASS}
$HOME/.local/bin/pdm plugin add pdm-version
```
