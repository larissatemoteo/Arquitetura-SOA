# **Arquitetura SOA - Sistema de Reservas de Voos**
## **Visão Geral**
A arquitetura proposta para o sistema de reservas de voos é baseada em SOA (Service-Oriented Architecture), que promove modularidade, reutilização e integração com serviços externos. O sistema permite que clientes pesquisem voos, façam reservas e recebam confirmações, enquanto funcionários gerenciam voos e dados de clientes. A integração com APIs externas (ex.: Amadeus, Stripe, SendGrid) reduz custos de desenvolvimento e melhora a experiência do usuário.

## **Diagrama de Componentes**
O diagrama de componentes está disponível em ```diagrams/soa-components.mmd``` e ilustra os principais blocos do sistema e suas interações. Abaixo está uma visão textual do diagrama:

- **Interface do Usuário (Front-end)**: Interface web/mobile para clientes.
- **Interface de Administração (Front-end)**: Interface para funcionários.
- **API Gateway**: Ponto de entrada para requisições, gerencia autenticação e roteamento.
- **Enterprise Service Bus (ESB)**: Orquestra comunicação entre serviços internos e externos.
- **Serviços Internos**:
    - **Pesquisa de Voos**: Integra com APIs externas (Amadeus/Sabre).
    - **Reservas**: Gerencia reservas e validação de assentos.
    - **Pagamento**: Processa transações via Stripe/PayPal.
    - **Notificações**: Envia e-mails via SendGrid.
    - **Gerenciamento de Usuários**: Lida com cadastro e autenticação.
    - **Gerenciamento de Voos**: Permite atualizações de voos por administradores.

- **Serviços Externos**: APIs de voos, pagamento e e-mail.
- **Bancos de Dados**: Armazenam dados de voos, reservas e usuários.

## **Justificativa da Arquitetura**

1. **Interface do Usuário (Front-end):**
    - Separa a camada de apresentação da lógica de negócios, facilitando manutenção e atualizações. Tecnologias como React garantem responsividade.

2. **Interface de Administração (Front-end):**
    - Fornece controle seguro para funcionários, com autenticação específica.

3. **API Gateway:**
    - Centraliza requisições, melhora segurança (autenticação OAuth 2.0) e escalabilidade com balanceamento de carga.

    **1. Enterprise Service Bus (ESB):**
    - Facilita integração com APIs externas, transformando dados e gerenciando protocolos (REST/SOAP).

    **2. Serviços Internos:**
    - Modularidade permite desenvolvimento e escalabilidade independentes. Integração com APIs externas reduz complexidade.


    **3. Serviços Externos:**
    - APIs como Amadeus (voos), Stripe (pagamentos) e SendGrid (e-mails) oferecem funcionalidades robustas, diminuindo custos.

    **4. Bancos de Dados:**
    - Separação de dados (voos, reservas, usuários) garante isolamento e escalabilidade. Bancos relacionais (PostgreSQL) são ideais para dados estruturados.

Esta arquitetura atende às necessidades de modularidade, integração e escalabilidade do sistema de reservas de voos.