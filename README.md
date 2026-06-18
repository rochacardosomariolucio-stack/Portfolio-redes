# Relatório de Aula Prática - Redes de Computadores
Ambiente: Containerlab (Docker) | Disciplina: Infraestrutura de Redes
 
## 1.	Configuração do Laboratório
O laboratório subiu usando dois containers interconectados de forma direta. O primeiro nó foi configurado como `node-a (IP 10.0.0.1/24)` e o segundo como `node-b (IP 10.0.0.2/24)`. O objetivo foi testar ferramentas de monitoramento, largura de banda e simular problemas comuns de rotas. 

## 2.	Captura de Tráfego com tcpdump
Para começar o monitoramento, foi rodado o sniffer de pacotes na placa eth1 do node-a. Na primeira tentativa de salvar, aconteceu um erro de digitação normal no terminal escrevendo "/tpm/" ao invés de "/ tmp/", mas logo depois o comando foi corrigido para o diretório certo. 

`tcpdump -i eth1 -n -w /tmp/ping_captura.pcap`

<img width="1064" height="611" alt="image" src="https://github.com/user-attachments/assets/3bd40b0a-3eeb-40b6-b92f-a86f5a56092b" />

Para ler o arquivo gravado e analisar os cabeçalhos das requisições e respostas do ping (ICMP) e também as tabelas de endereços físicos (ARP), o comando de leitura verbosa foi executado: 

`tcpdump -r /tmp/ping_captura.pcap -v`

<img width="1064" height="772" alt="image" src="https://github.com/user-attachments/assets/c7818976-6ba1-4d42-86aa-fbb3dae2b1c4" />
<img width="1064" height="759" alt="image" src="https://github.com/user-attachments/assets/7216f31a-b83e-46a4-8bbf-a0df89b9e4d2" />

## 3.	Teste de Banda com iperf3
Em seguida, rodamos o iperf3 para ver o limite de transmissão de dados entre as duas máquinas virtuais. Deixando o node-b como servidor, o teste do cliente acusou uma taxa média de transferência bem alta, alcançando a marca estável de 11.9 Gbps. 

`iperf3 -c 10.0.0.2`

<img width="1064" height="521" alt="image" src="https://github.com/user-attachments/assets/cd14de4b-9b27-44a0-b721-4d2516eb4e0a" />

## 4.	Teste de Aplicação TCP com Netcat (nc)
Fizemos um teste rápido abrindo uma porta manual (porta TCP 8080) usando o Netcat no node-b. Pelo node-a, enviamos uma linha de texto direto pelo socket para validar a comunicação na camada de aplicação. A mensagem chegou intacta do outro lado. 

`node-b:~# nc -l -p 8080`

<img width="835" height="609" alt="image" src="https://github.com/user-attachments/assets/dc8d7c2a-61a8-4326-bf5f-3a046d4ad2ce" />

## 5.	Simulação de Falhas e Testes de Sub-rede
O primeiro teste de conectividade normal foi feito dando ping do node-a para o node-b, onde todas as respostas voltaram normais e com tempo mínimo por estarem no mesmo host. 

`ping -c 3 10.0.0.2`

<img width="1064" height="273" alt="image" src="https://github.com/user-attachments/assets/c3693420-bdae-41ef-800d-cda5876db4db" />

Depois, simulamos um cenário de problema de máscara de rede. Mudamos a máscara do node-b e do node-a para o escopo /30, alterando o IP do node-a para 10.0.0.5. Ao tentar deletar e trocar os IPs no terminal, algumas mensagens de endereço já associado apareceram, o que é comum quando já existe configuração rodando na placa, mas conseguimos forçar a mudança usando o parâmetro change. 

`ip addr change 10.0.0.5/30 dev eth1`

`ping -c 3 10.0.0.2`

O resultado foi 100% de perda de pacotes. Isso ocorreu porque o IP 10.0.0.2 ficou fora do novo intervalo delimitado pela máscara /30 do node-a, fazendo com que o sistema operacional descartasse os pacotes internamente sem nem chamar o protocolo ARP. 

<img width="1064" height="364" alt="image" src="https://github.com/user-attachments/assets/011f92e0-013f-486d-87c8-1f870e438596" />
<img width="1064" height="180" alt="image" src="https://github.com/user-attachments/assets/f6707dc6-6eaf-4abd-accf-7f1cf89b8c75" />

## 6.	Conclusão
Os testes práticos mostraram o funcionamento real dos protocolos de rede da pilha TCP/IP. Conseguimos ver a importância das máscaras de sub-rede na comunicação direta entre dispositivos e como usar os comandos básicos de terminal para identificar problemas de conectividade e analisar o tráfego de dados. 

