# setup guide
Estes são os passos necessários para que seu computador esteja em ambiente de desenvolvimento.  
Busque o seu sistema operacional e siga o passo a passo dele.  

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
export PATH=\"~/.pyenv/bin:\$PATH\"
eval \"\$(pyenv init --path)\"
eval \"\$(pyenv virtualenv-init -)\"
" >> ~/.bashrc;
source ~/.bashrc
pyenv install --force 3.10.5;
echo "3.10.5" > ~/.python-version

# pdm
curl -sSL https://raw.githubusercontent.com/pdm-project/pdm/main/install-pdm.py | python3 -
$HOME/.local/bin/pdm completion bash | sudo tee /etc/bash_completion.d/pdm.bash-completion
```
