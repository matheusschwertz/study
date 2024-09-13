A ferramenta `nc` (ou **Netcat**) no Linux é uma poderosa e versátil ferramenta de troubleshooting de rede. Ela é usada principalmente para ler e gravar dados em conexões de rede, tornando-se útil para diagnosticar problemas de conectividade, testes de portas, transferências de arquivos, e até mesmo para criar servidores simples.

Aqui estão os principais usos e características do **Netcat**:

### Principais Funcionalidades:
1. **Verificação de portas abertas (Port Scanning)**:
   O `nc` pode ser usado para verificar se uma porta específica em um servidor está aberta, ajudando a identificar serviços que estão em execução.

   Comando básico para verificar se a porta 80 está aberta:
   ```bash
   nc -zv 192.168.0.1 80
   ```
   - `-z`: Modo "zero I/O", útil para varreduras de portas.
   - `-v`: Saída detalhada (verbose).
   
   Para verificar um intervalo de portas:
   ```bash
   nc -zv 192.168.0.1 80-100
   ```

2. **Transferência de arquivos**:
   O `nc` pode ser usado para transferir arquivos entre dois sistemas conectados na rede.

   No **servidor** (máquina de destino), rode:
   ```bash
   nc -l -p 1234 > arquivo_recebido.txt
   ```
   No **cliente** (máquina de origem), rode:
   ```bash
   cat arquivo.txt | nc 192.168.0.1 1234
   ```
   Isso envia o conteúdo do `arquivo.txt` para o endereço IP e porta especificados, onde o `nc` em modo de escuta no servidor recebe o arquivo.

3. **Teste de conectividade TCP/UDP**:
   O `nc` pode se conectar a portas TCP ou UDP para verificar a conectividade. Por exemplo, você pode testar se um serviço está disponível em uma porta específica:

   Conectar-se a um servidor na porta 22 (SSH):
   ```bash
   nc 192.168.0.1 22
   ```

   Para testar conexões UDP, use a opção `-u`:
   ```bash
   nc -u 192.168.0.1 12345
   ```

4. **Criação de um servidor ou cliente simples**:
   O `nc` pode ser usado para criar servidores e clientes simples para diagnóstico. Você pode criar um **servidor TCP** que escuta em uma porta e retorna o que recebe.

   Servidor ouvindo na porta 8080:
   ```bash
   nc -l 8080
   ```

   Em outra máquina, você pode enviar dados para essa porta:
   ```bash
   echo "Hello, Server!" | nc 192.168.0.1 8080
   ```

5. **Modo de chat**:
   O `nc` pode ser usado para criar um chat simples entre duas máquinas na rede. Em uma das máquinas, inicie o servidor:
   ```bash
   nc -l 12345
   ```
   Na outra máquina, conecte-se ao servidor:
   ```bash
   nc 192.168.0.1 12345
   ```
   Agora, as duas máquinas podem trocar mensagens através dessa conexão.

6. **Forwarding de portas**:
   O Netcat também pode ser usado para realizar o redirecionamento de portas, o que é útil para tunelamento ou para criação de proxies simples.

   Exemplo de forwarding local:
   ```bash
   nc -l 1234 | nc 192.168.0.1 22
   ```

### Vantagens do **Netcat**:
- **Versatilidade**: Ele pode ser usado para uma ampla gama de tarefas de rede, desde simples pings de portas até transferências de arquivos.
- **Flexibilidade**: Compatível com muitos protocolos e formatos, oferecendo suporte tanto para TCP quanto para UDP.
- **Simples e leve**: É uma ferramenta mínima, sem muitas dependências, mas poderosa para debugging de problemas de rede.
  
### Exemplos comuns de uso:
- **Testar se uma porta está aberta**:
   ```bash
   nc -zv google.com 80
   ```

- **Enviar uma mensagem para uma máquina**:
   ```bash
   echo "Test message" | nc 192.168.0.10 8080
   ```

- **Transferir um arquivo**:
   ```bash
   nc -l 12345 > output_file.txt  # Servidor
   cat file.txt | nc 192.168.0.1 12345  # Cliente
   ```

O **Netcat** é uma ferramenta de troubleshooting de rede indispensável pela sua simplicidade e potência, sendo especialmente útil para sysadmins e engenheiros de redes que precisam de diagnósticos rápidos e eficientes.

Testar e abrir uma conexão com um Socket.

Comandos de teste:

Verificando

$ ss -ln | grep 5488