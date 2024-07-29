# Configurações e Comandos

Neste módulo, você irá trabalhar nas seguintes configurações e comandos:

## 1. Comando para Rearm - Windows

- **Comando:** `slmgr -rearm`
- **Descrição:** Remove a mensagem de que o Windows está expirado. É possível rodar o rearm até 2 vezes, permitindo um total de 180 dias de licença trial.

## 2. Baixar ISO Windows 10 – Windows

- **Descrição:** Baixe a ISO do Windows 10 diretamente do site oficial da Microsoft ou de uma fonte confiável.

## 3. Criar Máquina Hyper-V - Hyper-V

- **Descrição:** Realize a criação das partições de forma correta ao configurar uma nova máquina virtual no Hyper-V.

## 4. Adicionar Máquina no Domínio – AD

- **Descrição:** Inclua a máquina criada no domínio Active Directory.

## 5. Validar Lease – DHCP

- **Descrição:** Verifique as concessões de IP no servidor DHCP para garantir que os endereços IP estejam sendo distribuídos corretamente.

## 6. Criar Reserva – DHCP

- **Descrição:** Configure uma reserva no servidor DHCP para garantir que um endereço IP específico seja sempre atribuído a um dispositivo específico.

## 7. Criar Regra de Bloqueio – DHCP

- **Descrição:** Crie regras para bloquear determinados endereços IP ou dispositivos no servidor DHCP.

## 8. Criar Range de Exclusão – DHCP

- **Descrição:** Defina um intervalo de IPs que não serão atribuídos pelo servidor DHCP.

## 9. `ipconfig /release` – DHCP

- **Descrição:** Libera o endereço IP atualmente atribuído ao adaptador de rede pelo servidor DHCP. Isso "desconecta" o IP atual, tornando-o disponível para outros dispositivos.

## 10. `ipconfig /renew` – DHCP

- **Descrição:** Solicita um novo endereço IP ao servidor DHCP após usar o comando `/release`. Renova a concessão do IP para o adaptador de rede.

## 11. `ipconfig /flushdns` – DNS

- **Descrição:** Limpa o cache do resolvedor DNS. Apaga as informações de cache, forçando uma nova resolução DNS para os próximos nomes de domínio acessados.

## 12. `ipconfig /registerdns` – DNS

- **Descrição:** Solicita ao cliente de DNS que registre ou atualize o nome do computador e o endereço IP atual com o servidor DNS. Ajuda a resolver problemas de resolução de nomes.

## 13. Criar um Registro de DNS Alternativo – DNS

- **Descrição:** Configure registros DNS alternativos para garantir que o nome do computador possa ser resolvido corretamente por diferentes servidores DNS.

## 14. Arquivo Hosts - Windows/DNS

- **Descrição:** Edite o arquivo `hosts` no Windows para mapear endereços IP a nomes de domínio localmente.

## 15. Logon Hours – AD

- **Descrição:** Configure as horas em que os usuários podem fazer logon no Active Directory.

## 16. Logon Computer – AD

- **Descrição:** Configure as máquinas específicas nas quais os usuários podem fazer logon no Active Directory.

---

Esses comandos e configurações são frequentemente usados para solucionar problemas de rede e DNS em sistemas Windows.
