# Portfolio-redes
# Laboratório de Redes com Containerlab

Este laboratório prático demonstra a criação de uma topologia de rede virtualizada contendo **1 Switch e 2 Computadores** utilizando o Containerlab e Docker.

## 🛠️ Topologia da Rede

+-----------------------+
   |     Máquina Host      |
   |                       |
   |     +-----------+     |
   |     |  switch1  |     |
   |     +-----+-----+     |
   |           |           |
   |     +-----+-----+     |
   |     |     |     |     |
   |  eth1     |     eth2  |
   |   +-------+-------+   |
   |   |               |   |
+---+---+---+       +---+---+---+
|  node-a   |       |  node-b   |
| 10.0.0.1  |       | 10.0.0.2  |
+-----------+       +-----------+


* **node-a**: Máquina Linux (computador 1) - IP: `10.0.0.1/24`
* **node-b**: Máquina Linux (computador 2) - IP: `10.0.0.2/24`
* **switch1**: Switch central que interconecta os dois nós.

---

## 🚀 Como Executar o Laboratório

### Pré-requisitos
* Ambiente Linux ou WSL2.
* Docker e Containerlab instalados.

### 1. Clonar o Repositório
```bash
git clone [https://github.com/MÁRIO LÚCIO ROCHA CARDOSO/NOME-DO-SEU-REPOSITORIO.git](https://github.com/MÁRIO LÚCIO ROCHA CARDOSO/NOME-DO-SEU-REPOSITORIO.git)    
cd NOME-DO-SEU-REPOSITORIO
