# Docker e Orquestração de Containers

## Visão Geral do Docker

Docker foi inicialmente desenvolvido como uma maneira de simplificar o processo de deploy de aplicações. Foi criado por Solomon Hykes como parte de um projeto dentro da dotCloud em 2013. O Docker permitiu que os desenvolvedores empacotassem aplicações em containers, incluindo todas as suas dependências, para rodarem uniformemente e de maneira consistente em diferentes ambientes.

Os containers fornecem uma maneira leve, portátil e escalável de implantar e executar aplicações. O Docker engine ajuda a construir e rodar containers, abstraindo as complexidades da virtualização de sistemas operacionais.

### Por que o Docker foi Desenvolvido?
O Docker resolveu vários problemas chave:
- **Gerenciamento de Dependências**: Ele empacota a aplicação junto com suas dependências, bibliotecas e configurações.
- **Consistência**: Os containers podem ser executados de maneira uniforme em múltiplos ambientes — desenvolvimento, testes e produção.
- **Eficiência de Recursos**: Os containers são leves, consumindo menos recursos do que máquinas virtuais.

## Evolução da Orquestração de Containers

Embora o Docker forneça uma boa base para a conteinerização de aplicações, gerenciar containers em um ambiente de produção requer uma solução de orquestração mais robusta. O Docker Swarm foi uma ferramenta inicial de orquestração que permitiu a criação de clusters de containers Docker, mas as limitações em termos de escalabilidade, tolerância a falhas e o gerenciamento de cargas de trabalho complexas levaram a indústria a adotar o Kubernetes.

### Por que Kubernetes ao invés de Docker Swarm?
O Kubernetes oferece:
- **Escalabilidade Automática**: Ele permite que as aplicações escalem automaticamente com base na demanda.
- **Auto-recuperação**: Se uma aplicação ou container falha, o Kubernetes pode reiniciar ou substituir a instância com falhas.
- **Descoberta de serviços e balanceamento de carga**: O Kubernetes ajuda a gerenciar a distribuição de tráfego entre múltiplos containers ou serviços.
- **Aplicações multi-serviços**: O Kubernetes gerencia aplicações complexas compostas por muitos serviços interdependentes.

## Orquestradores de Containers (Além do Docker Swarm)
1. **Kubernetes** - A plataforma de orquestração de containers mais popular e open-source.
2. **Mesos** - Oferece capacidades de orquestração de containers em larga escala.
3. **Nomad** - Uma plataforma de orquestração mais simples e leve da HashiCorp.
4. **OpenShift** - A plataforma de containers da Red Hat baseada no Kubernetes.

---

## Visão Geral do Kubernetes

Kubernetes (frequentemente abreviado como K8s) foi desenvolvido pelo Google e lançado como um projeto open-source em 2014. Ele teve origem na experiência do Google com o Borg, seu sistema interno de orquestração de containers.

O Kubernetes fornece uma plataforma poderosa para gerenciar cargas de trabalho e serviços conteinerizados. Ele automatiza muitos dos processos manuais envolvidos no deploy, gerenciamento e escalonamento de aplicações em containers.

### Principais Benefícios do Kubernetes:
- **Escalabilidade**: O Kubernetes pode escalar automaticamente as aplicações com base no uso de recursos ou padrões de tráfego.
- **Alta Disponibilidade**: Garante que a aplicação permaneça operacional, distribuindo as cargas de trabalho entre nós e zonas.
- **Tolerância a Falhas**: Se um pod (a menor unidade de deploy no Kubernetes) falha, o Kubernetes o substitui para manter o estado desejado.

---

## E se a Aplicação Falhar?

O Kubernetes reinicia automaticamente containers falhos, substituindo-os para atender o estado desejado da aplicação. Se um pod falhar, o Kubernetes pode:
- **Reiniciar o pod**: Os containers dentro do pod são reiniciados sem afetar o sistema inteiro.
- **Relocar o pod**: Se um nó falhar, o Kubernetes agenda o pod para outro nó.

## E se a Aplicação Precisar Escalar?

O Kubernetes pode escalar horizontalmente uma aplicação aumentando ou diminuindo o número de réplicas de pods com base no consumo de recursos (CPU, memória, etc.) ou no tráfego.

## E se Houver Múltiplos Serviços?

O Kubernetes suporta nativamente o deploy e gerenciamento de aplicações multi-serviço através de:
- **Namespaces**: Partições lógicas para gerenciar serviços relacionados separadamente.
- **Service Mesh**: Ferramentas como o Istio podem ser usadas para gerenciar microsserviços, fornecendo recursos como roteamento de tráfego, balanceamento de carga e aplicação de políticas.

## Balanceamento de Carga no Kubernetes

O Kubernetes distribui automaticamente o tráfego entre múltiplos pods usando mecanismos internos de descoberta de serviços e balanceamento de carga. Serviços como `LoadBalancer`, `Ingress`, e `ClusterIP` ajudam a rotear o tráfego de maneira eficiente.

## E se Houver Dados Sensíveis?

O Kubernetes fornece maneiras seguras de gerenciar informações sensíveis:
- **Secrets**: O Kubernetes permite armazenar informações sensíveis como senhas, tokens ou chaves como Secrets.
- **RBAC (Controle de Acesso Baseado em Funções)**: Ajuda a controlar quem pode acessar e gerenciar recursos.
- **Políticas de Rede**: Permitem definir regras para comunicação entre serviços, adicionando uma camada de segurança.

---

![alt text](<Screenshot from 2024-09-24 21-41-56.png>)

### Conclusão

Docker revolucionou a maneira como aplicações são empacotadas e implantadas, mas o Kubernetes leva a orquestração de containers a um novo nível, permitindo que as aplicações escalem, se recuperem e sejam gerenciadas de forma eficiente em produção. Kubernetes é uma ferramenta versátil e poderosa para rodar aplicações conteinerizadas em ambientes complexos.

---