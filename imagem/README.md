# 📸 Galeria de Evidências do Laboratório

Este diretório contém todas as capturas de ecrã (prints) obtidas durante a execução da aula prática no ambiente Containerlab. As imagens servem como comprovação dos testes de conectividade, vazão de banda e simulação de falhas.

## 🛠️ 1. Inicialização e Monitoramento (tcpdump)
Imagens referentes à verificação das interfaces dos containers e captura dos primeiros pacotes ICMP (ping).

* **Interface eth1 ativa e testes iniciais:** `<img width="1064" height="611" alt="image" src="https://github.com/user-attachments/assets/e2baa33b-cedf-4a38-8110-8ec8f9c5aa60" />`

* **Análise de pacotes ICMP e ARP:** `<img width="1064" height="772" alt="image" src="https://github.com/user-attachments/assets/0a7468b5-3046-4d21-92e9-1f3264477e60" />` e `<img width="1064" height="759" alt="image" src="https://github.com/user-attachments/assets/e74ec38e-5126-49e7-ab3f-7e6776742e30" />`

---

## 🚀 2. Testes de Performance (iperf3)
Evidências do teste de largura de banda bidirecional entre o `node-a` e o `node-b`.

* **Vazão de 11.9 Gbps:** `<img width="1064" height="521" alt="image" src="https://github.com/user-attachments/assets/58184c3a-0b68-4378-b166-adce2c499736" />`

---

## 💬 3. Camada de Aplicação (Netcat)
Validação da comunicação via socket TCP na porta 8080.

* **Mensagem recebida com sucesso:** `<img width="835" height="609" alt="image" src="https://github.com/user-attachments/assets/8190cb57-bf52-4fe0-b841-fc156304ac36" />`

---

## ⚠️ 4. Testes de Sub-rede e Falhas
Evidências das alterações de máscara de rede (/30) e comportamento do ping antes e depois do isolamento.

* **Ping com 0% de perda (Mesma rede):** `<img width="1064" height="273" alt="image" src="https://github.com/user-attachments/assets/1f7461c6-7cb8-401b-8b73-7a292d4f05ae" />`
* **Alteração para IP 10.0.0.5/30:*** **Ping com 100% de perda (Isolamento):** `<img width="1064" height="364" alt="image" src="https://github.com/user-attachments/assets/8fd11a66-cb38-4157-8013-9585a6baf2cf" />` e `<img width="1064" height="180" alt="image" src="https://github.com/user-attachments/assets/5c13bafa-0b74-455c-be0c-f760219eaf41" />`

  
