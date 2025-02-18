# OCI Security Lab

## <a name="overview">Introdução</a>
Neste guia, trabalharemos na disseminação e criação de diversos conceitos de segurança voltados à Oracle Cloud, seguindo diferentes processos e boas técnicas de implementação.

Exploraremos diversos recursos de segurança disponíveis na Oracle Cloud. É importante que o usuário possua um conhecimento prévio de OCI, e de preferência tenha participado de nosso workshop inicial (OCI Fast Track).

Por meio deste guia, trabalharemos com:

- Security Zones
- Bastion e Network Security Group
- Vulnerability Scanning
- Cloud Guard
- Load Balancer
- Web Application Firewall

Nosso objetivo é que, ao final deste workshop, os participantes possam ter o conhecimento na prática para implementar e manter seus ambientes na nuvem seguros.

## <a name="Tarefa 1: Compartimentos, Security Zones e VCN">Tarefa 1: Compartimentos, Security Zones e VCN</a>

Objetivos:
- Criar um compartimento
- Criar uma Security Zone
- Realizar testes na Security Zone
- Criar uma VCN

Nesta seção, você aprenderá mais sobre os serviços listados acima.

### <a name="Tarefa 1.1: Criando um Compartimento">Tarefa 1.1: Criando um Compartimento</a>
1. No menu principal( hamburger), clique em “Identity”, e escolha a opção “Compartments”
![](./images/image01.png)

2. Clique em “Create Compartment” e preencha com as informações abaixo:

- **Name:** workshop-security
- **Description:** Compartimento para o workshop de segurança
- **Parent Compartment:** root
