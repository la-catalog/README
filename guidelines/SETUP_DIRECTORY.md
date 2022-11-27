# setup directory
Este guia te ajuda a ter um diretório da organização com todos os repositórios organizados.  

- Crie um diretório onde você pretende armazenar todos os repositórios da organização
- Execute o script abaixo dentro do diretório criado

```python
import json
import subprocess
from pathlib import Path

org = "la-catalog"
templates = []
topics = ["api", "cronjob", "deployment", "package", "terraform", "utility"]


def setup_topic(topic):
    path = f"{topic}.json"

    subprocess.run(f"mkdir {topic}", shell=True)
    subprocess.run(
        f"gh search repos --owner {org} --topic {topic} --json fullName > {path}",
        shell=True,
    )

    repositories = json.loads(Path(path).read_text())
    repositories = [i for i in repositories if i not in templates]

    for repo in repositories:
        subprocess.run(f"cd {topic}; gh repo clone {repo['fullName']}", shell=True)

    subprocess.run(f"rm {path}", shell=True)

    return repositories


templates = setup_topic("template")

for topic in topics:
    setup_topic(topic)
```
