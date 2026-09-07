# 🌐 Laboratório de Infraestrutura de Rede Local e Análise de Protocolo ICMP

## 🎯 Objetivo do Projeto
Este projeto simula a montagem, endereçamento IP e validação de comunicação em uma infraestrutura de rede local (LAN) utilizando o **Cisco Packet Tracer**. O objetivo principal é demonstrar o ciclo de encapsulamento de dados no **Modelo OSI** e realizar a análise do tráfego do protocolo **ICMP** durante um teste de conectividade.

---

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer:** Simulação de topologia física e lógica de rede.
* **Modelo OSI e Pilha TCP/IP:** Análise das camadas L1 (Física), L2 (Enlace/Ethernet) e L3 (Rede/IP).
* **Protocolo ICMP:** Teste de conectividade e verificação de requisições de eco (`Echo Request` / `Echo Reply`).

---

## 📐 Topologia da Rede
A rede foi estruturada em um segmento local estático (`192.168.1.0/24`) com os seguintes hosts e endereçamentos:

| Dispositivo | Interface | Endereço IP | Máscara de Rede | Funções na Rede |
| :--- | :--- | :--- | :--- | :--- |
| **Router0** | GigabitEthernet0/0 | `192.168.1.1` | `255.255.255.0` | Gateway Padrão (Default Gateway) |
| **PC0** | FastEthernet0 | `192.168.1.10` | `255.255.255.0` | Host / Estação de Trabalho |
| **PC1** | FastEthernet0 | `192.168.1.20` | `255.255.255.0` | Host / Estação de Trabalho |
| **Switch0** | FastEthernet0/1 - 24 | *N/A (L2)* | *N/A* | Comutação de pacotes na camada 2 |

### Evolução do Cenário
<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 14 19 02" src="https://github.com/user-attachments/assets/4527590b-4a9e-46fc-95e7-2c3dbf30a7e0" />

*Figura 1: Ambiente limpo no Cisco Packet Tracer antes da montagem.*

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 14 36 28" src="https://github.com/user-attachments/assets/6bc766eb-dc1f-4c2d-97c2-6dcad05463b1" />

*Figura 2: Rede física e lógica totalmente configurada com link convergido.*

---

## 🔬 Testes Realizados e Análise de Tráfego

### 1. Teste de Conectividade End-to-End (`ping`)
Executou-se o diagnóstico de comunicação a partir da estação `PC0` direcionado ao Gateway Padrão `192.168.1.1`:
bash
ping 192.168.1.1
* **Resultado:** Comunicação estabelecida com sucesso, sem perda de pacotes.

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 14 38 14" src="https://github.com/user-attachments/assets/3808833b-14dc-44d8-ba17-61cad1a58ffb" />

*Figura 3: Simulação do envio e captura de pacotes ICMP no segmento de rede.*

### 2. Inspeção de Unidades de Dados de Protocolo (PDU) e Modelo OSI
Utilizando o modo de simulação do Cisco Packet Tracer, inspecionaram-se as informações trafegadas no envelope de dados durante a transmissão:

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 14 39 15" src="https://github.com/user-attachments/assets/b73e1036-0955-4e10-bad2-19cab1a272ce" />

*Figura 4: Análise detalhada das Camadas OSI (L1, L2 e L3).*

* **Camada 3 (Rede):** Origem `192.168.1.10` e Destino `192.168.1.1` via cabeçalho IP.
* **Camada 2 (Enlace):** Encapsulamento dos quadros Ethernet utilizando os endereços MAC de origem e destino.
* **Camada 1 (Física):** Conversão em sinais elétricos para transmissão pela interface `FastEthernet`.
