# Guia Completo para Certificações AWS

Este documento cobre os tópicos mais recorrentes em certificações AWS, como **Solutions Architect Associate**, **Developer Associate**, e **SysOps Administrator**. Aqui estão os conceitos, serviços e benefícios que você deve conhecer para passar nas certificações AWS.

---

## 1. **Serviços Essenciais da AWS**

### 1.1 **Amazon EC2 (Elastic Compute Cloud)**
- **Conceito**: Serviço que permite criar e gerenciar instâncias de servidores virtuais.
- **Tipos de Instância**: T2/T3 (Uso geral), M5 (Uso balanceado), C5 (Otimizado para computação), R5 (Otimizado para memória).
- **Pricing**:
  - **On-Demand**: Paga pelo uso por hora ou segundo.
  - **Reserved Instances**: Desconto em troca de um compromisso de uso de 1 ou 3 anos.
  - **Spot Instances**: Até 90% de desconto para capacidade não utilizada.
- **Auto Scaling**: Escala automaticamente a quantidade de instâncias com base na demanda.

### 1.2 **Amazon S3 (Simple Storage Service)**
- **Conceito**: Armazenamento de objetos escalável e altamente durável.
- **Classes de Armazenamento**: 
  - **S3 Standard**: Para dados acessados com frequência.
  - **S3 Intelligent-Tiering**: Alterna entre classes com base nos padrões de acesso.
  - **S3 Glacier**: Arquivamento de dados de longo prazo.
- **Versionamento**: Mantém múltiplas versões de objetos.
- **S3 Lifecycle Policies**: Regras para mover automaticamente dados entre classes de armazenamento.
- **Segurança**: Controla o acesso usando **Bucket Policies** e **IAM Roles**.

### 1.3 **Amazon RDS (Relational Database Service)**
- **Suporte**: MySQL, PostgreSQL, Oracle, SQL Server, MariaDB e Amazon Aurora.
- **Multi-AZ Deployment**: Alta disponibilidade com failover automático.
- **Read Replicas**: Escalabilidade de leitura para replicação de dados.

### 1.4 **Amazon VPC (Virtual Private Cloud)**
- **Subnets**: Redes segmentadas dentro de uma VPC (públicas e privadas).
- **Route Tables**: Definem regras de roteamento entre subnets e a Internet.
- **Security Groups**: Controle de tráfego em nível de instância.
- **Network ACLs (NACLs)**: Controle de tráfego em nível de subnet.
- **Peering de VPCs**: Conexão entre VPCs para comunicação entre redes.

---

## 2. **Conceitos de Segurança na AWS**

### 2.1 **Identity and Access Management (IAM)**
- **Usuários e Grupos**: Gerenciamento de permissões.
- **Roles**: Atribui permissões temporárias a instâncias de EC2 ou outros serviços AWS.
- **Policies**: JSON-based, define permissões específicas para usuários, grupos e roles.
- **Principle of Least Privilege**: Forneça o mínimo de permissões necessárias.

### 2.2 **AWS KMS (Key Management Service)**
- **Gerenciamento de Chaves**: Criação e gerenciamento de chaves de criptografia.
- **Integração**: Utilizado com S3, EBS, RDS, etc., para criptografar dados em repouso.

### 2.3 **AWS Shield e AWS WAF**
- **AWS Shield**: Proteção contra ataques DDoS.
- **AWS WAF (Web Application Firewall)**: Protege aplicações contra ataques baseados na Web (SQL Injection, XSS).

---

## 3. **Redes e Conectividade**

### 3.1 **Elastic Load Balancing (ELB)**
- **Tipos de Load Balancers**:
  - **Classic Load Balancer (CLB)**: Camada 4 e 7.
  - **Application Load Balancer (ALB)**: Camada 7 (HTTP/HTTPS).
  - **Network Load Balancer (NLB)**: Camada 4, para alta performance.
  
### 3.2 **AWS Direct Connect**
- **Conceito**: Conexão dedicada de alta velocidade entre sua rede on-premises e a AWS.

### 3.3 **Route 53**
- **DNS Gerenciado**: Resolve nomes de domínio para endereços IP.
- **Tipos de Routing**: Simple, Weighted, Latency-based, Failover e Geolocation.

---

## 4. **Alta Disponibilidade e Recuperação de Desastres**

### 4.1 **Amazon CloudWatch**
- **Conceito**: Monitora métricas de desempenho de serviços da AWS e configura alarmes.
- **Logs**: Armazena e monitora logs de aplicativos e recursos.
- **Custom Metrics**: Define métricas personalizadas para monitoramento.

### 4.2 **Amazon CloudTrail**
- **Conceito**: Registra todas as chamadas de API dentro da conta AWS.
- **Auditoria**: Rastreia alterações de configuração, atividade de usuários e acesso a recursos.

### 4.3 **Elastic Load Balancer (ELB) com Auto Scaling**
- **Alta Disponibilidade**: Escalabilidade horizontal automática de instâncias EC2 com balanceamento de carga.

### 4.4 **Backup e Recuperação**
- **AWS Backup**: Serviço centralizado para gerenciamento de backups para S3, RDS, DynamoDB, EFS, etc.
- **Cross-Region Replication**: Replica buckets do S3 entre regiões para recuperação de desastres.

---

## 5. **Serviços Sem Servidor (Serverless)**

### 5.1 **AWS Lambda**
- **Conceito**: Executa código sem necessidade de gerenciar servidores.
- **Eventos**: Pode ser acionado por eventos do S3, DynamoDB, API Gateway, etc.
- **Pay-as-you-go**: Paga apenas pelo tempo de execução do código.

### 5.2 **Amazon API Gateway**
- **Conceito**: Serviço para criar e gerenciar APIs RESTful ou WebSocket.
- **Integração**: Com AWS Lambda para criar APIs sem servidor.

### 5.3 **Amazon DynamoDB**
- **Banco de Dados NoSQL**: Totalmente gerenciado, com baixa latência e escalabilidade automática.
- **DynamoDB Streams**: Captura alterações em tempo real para replicação ou processamento com Lambda.

---

## 6. **Ferramentas de DevOps**

### 6.1 **AWS CloudFormation**
- **Infraestrutura como Código**: Define a infraestrutura em arquivos de template YAML/JSON.
- **Stack Updates**: Atualiza recursos de maneira controlada.

### 6.2 **AWS CodePipeline**
- **Integração Contínua/Entrega Contínua (CI/CD)**: Automatiza pipelines de entrega de software.
- **Integração**: Funciona com CodeBuild, CodeDeploy, GitHub, Jenkins, etc.

### 6.3 **Amazon Elastic Container Service (ECS) & Elastic Kubernetes Service (EKS)**
- **ECS**: Serviço de orquestração de containers com suporte para Docker.
- **EKS**: Gerencia clusters Kubernetes na AWS.

---

## 7. **Modelos de Custo**

### 7.1 **Pay-as-you-go**
- Pague apenas pelos recursos que
