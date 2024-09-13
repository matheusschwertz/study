A ferramenta `ss` no Linux é utilizada para visualizar estatísticas de sockets (conexões de rede), substituindo o antigo comando `netstat`. Ela permite monitorar conexões de rede, portas abertas, estatísticas de tráfego, entre outras funcionalidades, com mais eficiência e desempenho que o `netstat`.

Aqui estão alguns pontos importantes sobre o `ss`:

### Principais funcionalidades:
1. **Listar conexões de rede ativas**: 
   O `ss` permite listar todas as conexões de rede ativas, tanto TCP quanto UDP, além de mostrar informações como IPs, portas, e o estado da conexão (estabelecida, em espera, etc.).
   
   Comando básico:
   ```bash
   ss
   ```

2. **Filtrar por protocolo**:
   Você pode filtrar as conexões por protocolo (TCP, UDP, Unix sockets, etc.).
   - Para conexões TCP:
     ```bash
     ss -t
     ```
   - Para conexões UDP:
     ```bash
     ss -u
     ```

3. **Exibir conexões com detalhes adicionais**:
   O `ss` pode mostrar informações mais detalhadas sobre cada conexão, como quantidade de dados enviados e recebidos, timers, estado da conexão e outros.
   ```bash
   ss -tuln
   ```
   - `-t` para TCP, `-u` para UDP, `-l` para sockets de escuta (listening), `-n` para não resolver nomes de hosts.

4. **Conexões ativas e processos associados**:
   É possível verificar quais processos estão usando determinadas conexões:
   ```bash
   ss -p
   ```

5. **Filtragem por porta**:
   Você pode exibir conexões em uma porta específica:
   ```bash
   ss -tuln 'sport = :80'
   ```

6. **Conexões estabelecidas**:
   Para listar apenas conexões TCP que estão estabelecidas:
   ```bash
   ss -t state established
   ```

### Vantagens do `ss` sobre `netstat`:
- **Desempenho**: O `ss` é mais rápido que o `netstat`, já que ele coleta dados diretamente do kernel, sem necessidade de parseamento.
- **Funcionalidade ampliada**: Ele oferece mais opções de filtragem e detalhes para análise de conexões de rede.
- **Substituição moderna**: Embora o `netstat` ainda funcione em muitas distribuições, ele foi descontinuado em várias, sendo o `ss` o seu sucessor.

Essa ferramenta é útil em troubleshooting de rede, verificação de portas abertas e conexões, e identificação de possíveis problemas em servidores ou aplicações conectadas à rede.

Comandos testes: (Portas Escutando)

$ ss -n

$ ss -l

$ ss -ln

$ ss -lnt -> somente sockets tcp

$ ss -lnu -> somente sockets udp

$ ss -lntp -> mostra o processo que está atrelado neste socket (socket que sai da nossa porta e se conecta com o serviço)

$ sudo ss -lntp -> mostra o processo que está atrelado neste socket (socket que sai da nossa porta e se conecta com o serviço) - LISTA TODOS OS SOCKETS (Inclusive os que não são do usuário corrente) - (Mostra o PID do processo)


