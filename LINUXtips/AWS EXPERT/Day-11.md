# Resumo dos Conceitos

## ELB (Elastic Load Balancer)

### Parte 01 - Introdução
- **Elastic Load Balancer (ELB)** distribui automaticamente o tráfego de entrada entre múltiplas instâncias EC2, melhorando a disponibilidade e tolerância a falhas.
- Três tipos principais:
  - **Application Load Balancer (ALB)**: Opera na camada 7 (HTTP/HTTPS) e suporta roteamento baseado em conteúdo.
  - **Network Load Balancer (NLB)**: Opera na camada 4 (TCP/UDP), oferece baixa latência e é ideal para cargas de trabalho intensas.
  - **Classic Load Balancer (CLB)**: Suporta tanto camada 7 quanto camada 4, mas é a versão mais antiga e menos recomendada.

### Parte 02 - Application Load Balancer (ALB)
- Balanceia cargas a nível de aplicação, permitindo roteamento com base em:
  - URL
  - Headers
  - Dados de requisição
- Suporta HTTP/2 e WebSockets. É ideal para microsserviços e aplicações distribuídas.

### Parte 03 - Application Load Balancer (ALB)
- Integra com **Auto Scaling** e **ECS (Elastic Container Service)**.
- Permite gerenciar aplicações distribuídas de forma eficiente, com foco em performance e escalabilidade.

### Parte 04 - Network Load Balancer (NLB)
- Projetado para cargas intensas e baixa latência.
- Gerencia milhões de conexões simultâneas, ideal para aplicações em tempo real.
- Suporte para endereços IP estáticos e balanceamento de cargas TCP e UDP.

### Parte 05 - Network Load Balancer (NLB)
- Foco em conexões rápidas e confiáveis, ideal para bancos de dados ou sistemas de mensagens.
- Configuração simples, porém eficiente para lidar com tráfego em grande escala.

## AWS Auto Scaling

### Parte 01 - Launch Templates
- **Launch Templates** armazenam as configurações necessárias para lançar instâncias EC2:
  - Tipo de instância
  - Segurança
  - Configurações de rede
- Eles são reutilizáveis e permitem versionamento, o que facilita a gestão de diferentes configurações.

### Parte 02 - Launch Configuration
- **Launch Configurations** são semelhantes, mas não suportam versionamento.
- Definem parâmetros de instâncias EC2 usados pelo Auto Scaling, mas têm menos flexibilidade que os Launch Templates.

### Parte 03 - Auto Scaling
- **AWS Auto Scaling** ajusta automaticamente a capacidade computacional com base em regras de monitoramento.
- Permite aumentar ou diminuir instâncias EC2 com base na demanda de tráfego.
- Ideal para otimizar custos e garantir alta disponibilidade de recursos.

---

# Configuração dos Serviços na AWS

## Configurar Elastic Load Balancer (ELB)

### Application Load Balancer (ALB)
1. **Acessar o Console da AWS**: Ir para o serviço **EC2** e selecionar **Load Balancers**.
2. **Criar Load Balancer**:
   - Selecione **Application Load Balancer**.
   - Defina o **Scheme** como Internet-facing (externo) ou Internal (interno).
   - Escolha as **Zonas de Disponibilidade** que o ALB cobrirá.
3. **Definir Listeners**: Configure listeners para HTTP ou HTTPS (caso tenha certificados SSL/TLS).
4. **Configurar Grupos-Alvo (Target Groups)**:
   - Crie um grupo-alvo para registrar instâncias EC2 ou containers.
   - Selecione o tipo de verificação de integridade (health check).
5. **Atribuir Instâncias EC2**: Adicione as instâncias que receberão o tráfego balanceado.

### Network Load Balancer (NLB)
1. **Criar Load Balancer**:
   - Selecione **Network Load Balancer**.
   - Escolha entre TCP ou UDP para o protocolo de transporte.
   - Defina o **Scheme** e as **Zonas de Disponibilidade**.
2. **Configurar Grupos-Alvo**:
   - Selecione instâncias EC2 ou endereços IP para o balanceamento de carga.
   - Configure a verificação de integridade baseada em portas TCP/UDP.

## Configurar Auto Scaling com Launch Templates

### Criar Launch Template
1. **Acessar o Console da AWS** e navegar até **EC2**.
2. Na seção **Launch Templates**, clique em **Create Launch Template**.
3. Preencha os campos:
   - **Nome e descrição**.
   - Escolha o **AMI** (Imagem de Máquina Amazon).
   - Selecione o **Tipo de Instância** (ex: t2.micro).
   - Configure as permissões de **Segurança** e as configurações de **Rede** (VPC, Subnet, etc.).
   - (Opcional) Adicione volume de armazenamento adicional ou configurações avançadas.
4. **Salvar o Template**.

### Criar um Auto Scaling Group
1. **Ir para EC2** e selecionar **Auto Scaling Groups**.
2. **Criar Auto Scaling Group**:
   - Escolha o **Launch Template** previamente criado.
   - Defina as **Zonas de Disponibilidade**.
   - Configure o **Número Mínimo, Máximo e Inicial de Instâncias**.
3. **Definir Políticas de Escalabilidade**:
   - Defina políticas com base em métricas do **CloudWatch** (ex: CPU Usage, Network In/Out).
   - Configure regras para escalar horizontalmente ou verticalmente, dependendo da demanda.
4. **Verificação de Saúde**: Habilite a verificação de integridade para substituir instâncias com falhas.
5. **Finalizar a Criação**.

---

Seguindo esses passos, você conseguirá configurar os serviços de ELB e Auto Scaling na AWS para garantir escalabilidade e alta disponibilidade da sua aplicação.
