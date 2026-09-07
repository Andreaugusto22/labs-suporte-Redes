# Configuração de Serviços de Rede: DHCP e DNS no Cisco Packet Tracer

## 📌 Visão Geral do Projeto
Este laboratório demonstra a implementação e integração de serviços essenciais de infraestrutura de rede (DHCP e DNS) em um ambiente corporativo simulado. O objetivo é automatizar o endereçamento IP dos hosts e permitir a resolução de nomes de domínio internos.

---

## 📐 Topologia da Rede
A rede foi estruturada em uma topologia estrela conectando clientes, servidor de nomes e roteador gateway.

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 16 11 08" src="https://github.com/user-attachments/assets/5e5b07fe-db2b-48c1-85f6-789d3e774bfe" />


### Endereçamento e Parâmetros
* **Sub-rede:** `192.168.10.0/24`
* **Gateway Padrão (Roteador):** `192.168.10.1`
* **Servidor DNS:** `192.168.10.2`
* **Escopo DHCP:** `192.168.10.3` até `192.168.10.254`
* **Domínio Local:** `empresa.local`

---

## 🛠️ Configurações Aplicadas

### 1. Configuração do Servidor DHCP (Cisco IOS)
As configurações de entrega dinâmica de IP foram aplicadas diretamente na interface do roteador via CLI:

```text
Router> enable
Router# configure terminal
Router(config)# ip dhcp pool REDE_LOCAL
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 192.168.10.2
Router(dhcp-config)# exit
```

### 2. Configuração do Servidor DNS
* **IP Estático:** `192.168.10.2/24`
* **Serviço DNS:** Ativo (ON)
* **Registro A:** `empresa.local` -> `192.168.10.2`

---

## 🧪 Validação e Testes

### Teste 1: Obtenção de Endereço IP via DHCP
Validação do recebimento das configurações automáticas no cliente (IP, Subnet, Gateway e DNS Server).

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 16 11 51" src="https://github.com/user-attachments/assets/c3f943f6-7c3a-4d6b-bbd7-431bff7deb52" />


---

### Teste 2: Resolução de Nomes de Domínio (DNS)
Teste de conectividade e resolução de nomes utilizando o domínio `empresa.local` via `ping` no terminal do PC0.

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 16 13 10" src="https://github.com/user-attachments/assets/27b369d3-63b7-4c70-af2c-f055f5ef84e3" />


---

### Teste 3: Inspeção de Pacotes no Modo Simulação
Análise do fluxo de pacotes DNS e ICMP cruzando o switch até o servidor de nomes.

<img width="1470" height="956" alt="Captura de Tela 2026-09-07 às 16 28 28" src="https://github.com/user-attachments/assets/476a9ab0-435b-4f98-b202-bca70519b0ec" />


---

## 🚀 Conclusão
O projeto demonstrou com sucesso a automação da distribuição de IPs e a resolução de nomes na rede LAN, reduzindo erros manuais de configuração e garantindo conectividade end-to-end.

