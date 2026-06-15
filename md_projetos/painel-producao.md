# Painel de Produção — Indicadores Industriais

## Evolução de Painéis com n8n, Firebird e Power BI

### Visão Geral
Projeto contínuo de evolução dos painéis de indicadores industriais para uma indústria madeireira, integrando dados de produção via **Firebird 4.0**, automações em **n8n**, visualização em **Power BI** e dashboard web customizado com **HTML/CSS/JavaScript** puro.

### Tecnologias Utilizadas
- **Firebird 4.0** — banco de dados relacional industrial
- **n8n** — automação de workflows e integrações
- **Power BI** — dashboards estratégicos com DAX
- **Docker** — containerização do painel web
- **PHP/Laravel 5.4** — backend do sistema legado
- **JavaScript** customizado (~1293 linhas) — frontend do painel

### Funcionalidades Principais
- Painel com métricas em tempo real de produção por máquina
- Correção de período padrão e calendário nos filtros de data
- Visualização de eficiência por equipamento e turno
- Tooltips customizados para melhor experiência do usuário
- Sistema de retry em falhas de atualização do banco
- Backups automáticos de scripts customizados antes de alterações

### Diferenciais Técnicos
- Arquitetura híbrida (Docker + servidor físico) para resiliência
- Roteamento personalizado para evitar conflitos de rede Docker
- Integração com banco legado via consultas otimizadas
- Customizações preservadas em atualizações (nunca sobrescritas)
