# 🌐 Roteamento de Redes Multi-Classe no Cisco Packet Tracer

> **Apresentação no Canva:** [Visualizar Slides do Projeto](https://canva.link/g3ogatq0hpk2prh)
> 
> <img width="1920" height="1080" alt="ROTEAMENTO INTER-REDES" src="https://github.com/user-attachments/assets/5b61be14-36a2-4284-95ee-e757554c6e45" />
 


---

## 👤 Sobre Mim

Olá! Sou **Anaya Felix**, graduanda em Ciência e Tecnologia com foco de especialização em Ciência da Computação na **Universidade Federal do ABC (UFABC)**. 

Atualmente, estou me capacitando no **Programa Mulher Digital** uma iniciativa apoiada pela **Cisco** e pela **JA Brasil** , onde desenvolvo competências práticas em infraestrutura de redes, cibersegurança e arquitetura de sistemas, com foco na preparação para a certificação **Cisco Certified Support Technician (CCST) Cybersecurity**.

---

## 📌 Visão Geral do Projeto

Este projeto consiste na simulação e implementação de uma infraestrutura corporativa dividida em três sub-redes lógicas independentes (Classes A, B e C). O objetivo central foi estabelecer a comunicação inter-redes completa através de um roteador central Cisco 2911, aplicando conceitos de endereçamento IPv4, gateways padrão e comutação via switches Catalyst 2960.

### 🛠️ Tecnologias e Ferramentas
* **Simulador:** Cisco Packet Tracer
* **Equipamento de Camada 3:** 1x Roteador Cisco 2911
* **Equipamentos de Camada 2:** 3x Switches Cisco Catalyst 2960-24TT
* **Dispositivos Finais:** 6x PCs
* **Protocolos e Conceitos:** IPv4, ICMP, Subnetting, Gateways Padrão, Cisco IOS CLI

---

## 📊 Topologia e Tabela de Endereçamento

[Topologia do Projeto]

<img width="1920" height="1080" alt="ROTEAMENTO INTER-REDES (1)" src="https://github.com/user-attachments/assets/1a91f137-2e2b-4896-b9ec-4bfb54f00200" />



| Dispositivo | Interface | Endereço IP | Máscara de Sub-rede | Gateway Padrão | Pertence à Rede |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Roteador** | `GigabitEthernet0/0` | `10.0.0.1` | `255.0.0.0` | N/A | Classe A (Gateway) |
| **Roteador** | `GigabitEthernet0/1` | `172.16.0.1` | `255.255.0.0` | N/A | Classe B (Gateway) |
| **Roteador** | `GigabitEthernet0/2` | `192.168.1.1` | `255.255.255.0` | N/A | Classe C (Gateway) |
| **PC A1** | `FastEthernet0` | `10.0.0.2` | `255.0.0.0` | `10.0.0.1` | Rede Classe A |
| **PC A2** | `FastEthernet0` | `10.0.0.3` | `255.0.0.0` | `10.0.0.1` | Rede Classe A |
| **PC B1** | `FastEthernet0` | `172.16.0.2` | `255.255.0.0` | `172.16.0.1` | Rede Classe B |
| **PC B2** | `FastEthernet0` | `172.16.0.3` | `255.255.0.0` | `172.16.0.1` | Rede Classe B |
| **PC C1** | `FastEthernet0` | `192.168.1.2` | `255.255.255.0` | `192.168.1.1` | Rede Classe C |
| **PC C2** | `FastEthernet0` | `192.168.1.3` | `255.255.255.0` | `192.168.1.1` | Rede Classe C |

---

## ⚙️ Configuração dos Equipamentos (Cisco IOS / CLI)

Configuração das três interfaces GigabitEthernet do Roteador Cisco 2911 para servir como gateways das respectivas sub-redes:

```cisco
Router> enable
Router# configure terminal
Router(config)# hostname Roteador

! Interface Gi0/0 - Gateway da Rede Classe A
Roteador(config)# interface GigabitEthernet0/0
Roteador(config-if)# ip address 10.0.0.1 255.0.0.0
Roteador(config-if)# no shutdown
Roteador(config-if)# exit

! Interface Gi0/1 - Gateway da Rede Classe B
Roteador(config)# interface GigabitEthernet0/1
Roteador(config-if)# ip address 172.16.0.1 255.255.0.0
Roteador(config-if)# no shutdown
Roteador(config-if)# exit

! Interface Gi0/2 - Gateway da Rede Classe C
Roteador(config)# interface GigabitEthernet0/2
Roteador(config-if)# ip address 192.168.1.1 255.255.255.0
Roteador(config-if)# no shutdown
Roteador(config-if)# exit
