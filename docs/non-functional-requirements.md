# **Requisitos Não Funcionais - Sistema de Reservas de Voos**
Abaixo estão cinco requisitos não funcionais do sistema, com justificativas e sua relação com a arquitetura SOA.

1. **Escalabilidade**
- **Descrição**: O sistema deve suportar picos de tráfego (ex.: promoções), escalando para milhares de usuários simultâneos.
- **Justificativa**: Picos de uso são comuns em sistemas de reservas, e a escalabilidade evita falhas.
- **Relação com SOA**: Serviços independentes (ex.: Pesquisa de Voos) podem ser escalados horizontalmente com contêineres (Docker/Kubernetes). O API Gateway balanceia carga.


2. **Disponibilidade**
- **Descrição**: Garantir 99,9% de disponibilidade para reservas a qualquer momento.
- **Justificativa**: Indisponibilidade resulta em perda de receita e insatisfação.
- **Relação com SOA**: Serviços redundantes e o ESB redirecionam requisições para instâncias disponíveis.


3. **Segurança**

- **Descrição**: Proteger dados sensíveis com criptografia (TLS) e conformidade com PCI-DSS.
- **Justificativa**: A confiança do cliente depende da segurança contra vazamentos e fraudes.
- **Relação com SOA**: O API Gateway gerencia autenticação (OAuth 2.0), e o ESB assegura comunicação segura.


4. **Desempenho**

- **Descrição**: Pesquisas de voos em < 2 segundos, reservas em < 5 segundos.
- **Justificativa**: Latência alta prejudica a experiência do usuário.
- **Relação com SOA**: Cache (Redis) no Serviço de Pesquisa e integração eficiente via ESB otimizam resposta.


5. **Interoperabilidade**

- **Descrição**: Integrar com APIs externas (Amadeus, Stripe, SendGrid) via REST/SOAP.
- **Justificativa**: APIs externas reduzem custos e exigem compatibilidade com protocolos variados.
- **Relação com SOA**: O ESB transforma mensagens, garantindo interoperabilidade.



