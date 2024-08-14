# Conceitos Chave para Containers: chroot, Namespaces e cgroups

Containers são uma forma eficiente e escalável de empacotar, distribuir e executar aplicações. Três conceitos fundamentais para a criação e gerenciamento de containers são `chroot`, namespaces e cgroups. Vamos explorar cada um deles a seguir.

## 1. chroot

O `chroot` (change root) é uma funcionalidade do sistema operacional que permite alterar o diretório raiz (`/`) para um processo específico e seus filhos. Isso cria um ambiente isolado, chamado de "chroot jail", onde o processo pode operar como se fosse a raiz do sistema de arquivos.

### Características do chroot:
- **Isolamento de Sistema de Arquivos**: O `chroot` isola o processo de outros arquivos do sistema, restringindo o acesso ao diretório especificado.
- **Segurança Limitada**: Embora ofereça algum nível de isolamento, o `chroot` não fornece um isolamento robusto. Processos dentro do `chroot jail` ainda podem acessar o sistema operacional host de várias maneiras, como através de chamadas de sistema ou exploits de segurança.

### Uso Típico:
- **Ambientes de Desenvolvimento**: O `chroot` pode ser usado para criar ambientes de desenvolvimento isolados.
- **Serviços Seguros**: Pode ajudar a proteger serviços críticos ao limitar o acesso ao sistema de arquivos.

## 2. Namespaces

Os namespaces são uma característica do kernel do Linux que permite criar ambientes isolados para processos. Eles fornecem isolamento para diferentes aspectos do sistema, permitindo que diferentes processos vejam diferentes "visões" do sistema operacional.

### Tipos de Namespaces:
- **Mount Namespace**: Isola o sistema de arquivos montado, permitindo que diferentes processos vejam diferentes pontos de montagem.
- **PID Namespace**: Isola o espaço de IDs de processos, permitindo que processos em namespaces diferentes tenham IDs de processos idênticos sem conflitos.
- **Network Namespace**: Isola a pilha de rede, permitindo que diferentes processos tenham suas próprias interfaces de rede e rotas.
- **UTS Namespace**: Isola o nome do host e o domínio do sistema, permitindo que processos em namespaces diferentes tenham diferentes nomes de host.
- **IPC Namespace**: Isola os recursos de comunicação entre processos, como semáforos e filas de mensagens.
- **User Namespace**: Isola IDs de usuários e grupos, permitindo que processos vejam IDs de usuários diferentes dos IDs de usuários reais.

### Características dos Namespaces:
- **Isolamento Completo**: Fornece isolamento completo entre diferentes processos e recursos do sistema.
- **Flexibilidade**: Permite a criação de ambientes independentes e seguros para execução de processos.

### Uso Típico:
- **Containers**: Namespaces são fundamentais para a criação de containers, permitindo que cada container tenha seu próprio ambiente isolado.

## 3. cgroups

Cgroups (control groups) é uma funcionalidade do kernel Linux que permite limitar, contabilizar e isolar o uso de recursos de sistema (CPU, memória, disco, etc.) por grupos de processos.

### Características dos cgroups:
- **Limitação de Recursos**: Permite definir limites máximos de recursos que um grupo de processos pode consumir, ajudando a evitar que um processo monopolize todos os recursos.
- **Contabilização de Recursos**: Fornece informações detalhadas sobre o uso de recursos por diferentes grupos de processos.
- **Isolamento de Recursos**: Permite criar ambientes isolados onde os recursos do sistema são gerenciados de forma independente.

### Uso Típico:
- **Gerenciamento de Containers**: cgroups são usados para garantir que containers não consumam mais recursos do que o permitido e para monitorar o uso de recursos.
- **Desempenho e Escalabilidade**: Ajuda a otimizar o desempenho e a escalabilidade do sistema ao gerenciar eficientemente os recursos.

## Conclusão

O `chroot`, namespaces e cgroups são funcionalidades essenciais para o gerenciamento de containers. Eles fornecem diferentes tipos de isolamento e controle que permitem a criação de ambientes seguros e eficientes para a execução de aplicações. Combinados, esses conceitos ajudam a criar e gerenciar containers de maneira eficaz, garantindo segurança e desempenho para aplicações.

# Exemplo explicativo: 

## 1. chroot

* Todas as bibliotecas que o bash utiliza para poder funcionar 

```bash
ldd /bin/bash
```
- Copiar as bibliotécas e o binário do bash para esse diretório isolado

### Criar a mesma estrutura de diretório /bin, /lib e /lib64

```bash
mkdir /bin
mkdir /lib
mkdir /lib64
```

- O bash precisa para rodar dentro do diretório 
- Realizar a cópia das libs
```bash
sudo cp /lib/x86_64-linux-gnu/libtinfo.so.6 lib/
sudo cp /lib/x86_64-linux-gnu/libc.so.6 lib/
sudo cp /lib64/ld-linux-x86-64.so.2 lib64/
sudo cp /bin/bash bin/
```

Para visualizar: 
```bash
ls **
```

Para testar: 
```bash
sudo chroot chroot bash
```

Para vizualizar a estrtura de árvore do diretório:
```bash
pstree
```

Buscar o ps 
```bash
wich ps 
```


Visualizar

```bash
ldd /usr/bin/ps | cut -d " " -f 3
```
Automatizar a cópia de todas as libs

```bash
for i in $(ldd /usr/bin/ps | cut -d " " -f 3); do sudo cp $i lib/; done
```

### Premissa da criação de um contâiner "Montar um container apenas com o que iremos usar, binários e libs" 

- Chroot então serviria para Isolar um diretório

## 2. Namespaces

### Comando nativo "unshare"

Faz um fork para executar o Chroot dentro do unshare

```bash
sudo unshare -p -f --mount-proc chroot .
```

Precisamos desmontar o diretório proc criado na anteriormente

```bash
sudo umount proc
```

Valdiar se não tem nada 

```bash
ls proc
```

Executamos o comando unshare novamente

```bash
sudo unshare -p -f --mount-proc chroot .
```
E agora sim montamos um /proc zerado (genérico), um proc dentro do container, fora de minha userland

```bash
mount -t proc proc /proc
```
Ele consegue ver apenas os processos isolados dentro do container, assim temos quase um container pronto. Temos um processo isolado e um diretório isolado de minha máquina host.
é isso que o docker faz, juntar essas funcionalidades.

## 3. cgroups

Onde iremos passar limites para os contâiners (processos, para que não ocupem todo o processamento), por trás dos panos o docker usa o cgrups.

Caminho para localizar o Cgroups

```bash
cd /sys
cd fs
cd cgroup
```
Dentro dele temos os limites que podemos colocar basicamente ou cpu ou memória.

Realizar um teste dentro de:

```bash
cd /sys/fs/cgroup/cpu
```

Criar outro cgroup

```bash
mkdir demo
cd demo
ls
```

Teste de processamento:

```bash
dd if=/dev/zero of=/dev/null bs=1M &
```
Iniciar mais de um processo - cada um consumindo uma Vcpu repartindo o processamento entre essas 2 Vcpus = 200% de processamento.

Executar um:

```bash
top
```

Jogar os 2 primeiros processos criados para o meu Cgroup 

```bash
echo <pid> >> tasks
```

Os dois processos que estão no mesmo Cgroup irão dividir o processamento

Sobreescrever o arquivo e jogar dois processos genéricos para dentro:

```bash
echo "" > tasks
```
Adicionar os dois procesos:

```bash
echo <pid> >> tasks
```
