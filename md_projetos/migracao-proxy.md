# Migração de Proxy/Squid (VPN)

## Modernização Completa da Infraestrutura de Proxy do Grupo Repinho

### Visão Geral
Migração completa do serviço de proxy Squid de um servidor legado **Debian 8 (Jessie)** para um moderno **Debian 13 (Trixie)**, incluindo swap de identidade de rede, relatórios visuais com GoAccess e SARG, painel de alertas de segurança e scripts de monitoramento.

### Tecnologias Utilizadas
- **Squid 6.13** — Proxy HTTP/HTTPS com ACLs e listas de controle
- **GoAccess** — Dashboard de relatórios em tempo real
- **SARG** — Relatórios históricos de acesso
- **Debian 8 → Debian 13** — Migração completa de sistema operacional
- **BIND9** — Serviço de DNS migrado
- **Zabbix** — Monitoramento de memória e serviço
- **Bareos** — Backup file daemon
- **Bash scripting** — Automação de rotinas

### Funcionalidades Implementadas

#### 1. Proxy (Squid 6.13)
- Migração completa de configuração e ACLs do Debian 8 para Debian 13
- Swap de identidade de rede (IP 172.16.0.1 mantido)
- Listas de controle: liberação/bloqueio por site, MAC, horário
- Bloqueio de TeamViewer por MAC address (whitelist/blacklist)
- Configuração de cache (20GB) e desempenho
- Suporte a interceptação (porta 3129)

#### 2. Dashboard de Relatórios (GoAccess)
- **http://172.16.0.1/proxy-dashboard/** — Tempo real com estatísticas de acesso
- Gráficos de sites mais acessados, horários, códigos HTTP
- Log format customizado para Squid 6.13 (epoch token)
- Atualização automática via cron

#### 3. Painel de Alertas de Segurança
- **http://172.16.0.1/proxy-alerts/** — Acessos indevidos e tentativas bloqueadas
- Filtro de HTTP 403 com relatório GoAccess dedicado
- Nav bar integrada entre dashboard principal e alertas
- Atualização a cada 2 minutos via cron

#### 4. Serviços Migrados
- **DNS (BIND9)** — Serviço de nomes configurado e funcional
- **Zabbix Agent + Proxy** — Monitoramento de memória, CPU e serviço Squid
- **Bareos** — File daemon de backup configurado
- **SARG** — Relatórios históricos semanais

#### 5. Scripts de Automação
- `atualiza-proxy.sh` — Geração do dashboard principal
- `atualiza-alerts.sh` — Geração do painel de alertas
- `check_mem_squid.sh` — Monitoramento de RAM
- `audit-acl.sh` — Limpeza e deduplicação de ACLs
- `backup-configs.sh` — Backup diário das configurações

### Resultados
- Servidor legado Debian 8 descontinuado com segurança
- Proxy moderno, estável e com suporte a segurança ativo
- Relatórios visuais de acesso em tempo real
- Painel de alertas para acessos indevidos (403)
- Monitoramento via Zabbix e Bareos
- Tudo executado sem downtime para os usuários
