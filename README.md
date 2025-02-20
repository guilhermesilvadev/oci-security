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

## <a name="Tarefa 1: Deploy do ambiente básico">Tarefa 1: Deploy do ambiente básico</a>

[![Deploy_To_OCI](images/DeployToOCI.svg)](https://cloud.oracle.com/resourcemanager/stacks/create?zipUrl=https://github.com/guilhermesilvadev/oci-security/blob/c1b720536dad773f5718ed56b96412a8e3f707b9/stack/stack/main.zip)<br>
*If you are logged into your OCI tenancy in the Commercial Realm (OC1), the button will take you directly to OCI Resource Manager where you can proceed to deploy. If you are not logged, the button takes you to Oracle Cloud initial page where you must enter your tenancy name and login to OCI.*
<br>

## <a name="Laboratório 6: Web Application Firewall (WAF)  ">Laboratório 6: Web Application Firewall (WAF) </a>


O WAF é um serviço de segurança global compatível com PCI (Payment Card Industry) que protege aplicativos de tráfego malicioso e indesejado na internet.
Objetivos
- Configurar um WAF com o Load Balancer do exercício anterior
- Trabalhar com regra de Controle de Acesso
- Configurar Rate Limiting
- Testar

### <a name="Tarefa 1: Criar o WAF">Tarefa 1: Criando o WAF</a>
1. Acesse o menu **Identity and Security**

2. Clique na opção **Policies**, primeira opção abaixo da sessão “Web Application Firewall”
   ![](./images/lab_waf01.png)

3. Clique na opção **Create WAF Policy**
   ![Criação police](./images/lab_waf02.png)

4. Preencha o campo Name com o valor **waf-policie-dataprev** e clique no botão **next** que está no final da página
   ![](./images/lab_waf03.png)

5. Marque a opção **Enable access control** e clique no botão **Add access rules**
   ![](./images/lab_waf04.png)

6. Adicione uma regra com as configurações abaixo
      - name: block-USA
      - conditions type: Contry/Region
      - operator: In List
      - Contries: United States
      - Sessão Rule Action
          - Action name: Create new Action
            - Name: block-USA
            - Type: Return HTTP response
            - Response page body:  
              ``` 
              <!DOCTYPE html>
              <html>
              <head>
              <title>Região não permitida!</title>
              </head>
              <body>
              <h1 id="Welcome">Região não permitida!</h1>
              <p>Esta página não tem compatibilidade com sua região</p>
              </body>
              </html>
              ```
        - Clicar no botão *** Add action ***
   ![](./images/lab_waf05.png)
   ![](./images/lab_waf06.png)
   ![](./images/lab_waf07.png)
   ![](./images/lab_waf08.png)
7. Clique em next para ***Rate Limmit** 
8. Clique em next para ***Protections** 
9. Na opção ***Select enforcement point** selecione o load balance criado no workshop anterior
   ![](./images/lab_waf09.png)
10. Cliente en next para a opção ***Review and create** em seguida clique em ***Create WAF policy**
   ![](./images/lab_waf10.png)
