# Data Plane

## Kubelet
O **Kubelet** é o componente responsável por gerenciar os nós de um cluster Kubernetes. Ele atua como o "capitão do navio", comunicando-se diretamente com o API Server. Suas principais responsabilidades incluem:

- **Criação e gerenciamento de Pods**: O Kubelet recebe as solicitações do API Server para criar e gerenciar Pods, que são as unidades básicas de execução no Kubernetes.
- **Monitoramento de Containers**: Ele realiza verificações de saúde (health checks) para garantir que as aplicações dentro dos containers estejam funcionando corretamente.
- **Relato de Estado**: O Kubelet envia informações sobre o estado dos Pods de volta ao API Server, permitindo que o Kubernetes mantenha um controle efetivo sobre a saúde do cluster.

## Kube-Proxy
O **Kube-Proxy** é responsável por gerenciar as regras de rede dentro do cluster Kubernetes. Suas principais funções incluem:

- **Gerenciamento de Regras de IPTables**: O Kube-Proxy manipula as regras de IPTables para assegurar que o tráfego de rede seja direcionado corretamente para os serviços (services) definidos no cluster.
- **Serviços de Rede**: Ele permite a comunicação entre os Pods e os serviços, garantindo que as solicitações sejam roteadas para os Pods corretos, mesmo que eles mudem ao longo do tempo.

## Conclusão
Tanto o Kubelet quanto o Kube-Proxy desempenham papéis cruciais no funcionamento do plano de dados no Kubernetes, garantindo a criação, gerenciamento e comunicação eficaz entre os containers em execução no cluster.
