# RPMS — Sistema de Controle de Produção Industrial

## Laravel 5.4, Multi-tenant, Indicadores e Relatórios

### Visão Geral
Sistema web para controle e rastreabilidade do processo produtivo de compensados/madeira. Desenvolvido em **Laravel 5.4** com suporte a múltiplas empresas (multi-tenant), geração de relatórios em PDF e Excel, e dashboards de indicadores industriais em tempo real.

### Tecnologias Utilizadas
- **Laravel 5.4 / PHP 7.4** — framework legado em produção
- **Laravel 9.x / PHP 8.5** — ambiente de homologação
- **MySQL / MariaDB** — banco de dados principal
- **Firebird 4.0** — banco de dados industrial legado
- **Apache 2.4 + PHP-FPM** — servidor web
- **Maatwebsite Excel v2.1** — exportação de planilhas
- **Snappy (wkhtmltopdf) / DomPDF** — geração de relatórios
- **Bootstrap 3 + jQuery** — frontend
- **Docker** — containerização do painel web

### Correções e Melhorias Realizadas

#### Namespace e Arquitetura
- Migração de **63 models** de `app/` para `app/Models/` com namespace `App\Models`
- Ajuste de PSR-4 no `composer.json` e classmap
- Atualização de todas as referências em ~50 controllers
- Backup de segurança em `_backup_models/`

#### Exportação Excel
- Correção de data/hora no PHPToExcel (`->startOfDay()` para serial numérico correto)
- Auditoria de 15 controllers — apenas Carregamento usava PHPToExcel
- Adição de `WithColumnFormatting::FORMAT_TEXT` em 6 classes Export (homologação)
- Correção de observações (exibia "Sim"/"Não" em vez do texto real)

#### Indicadores Industriais
- Farol NC (não conformidade) com bolinhas verde/vermelho clicáveis em **todos os módulos**
- Tabelas operacionais por módulo (Por Secador, Por Passadeira, Por Produto, Por Prensa, etc.)
- Gráficos de evolução (temperatura, velocidade, espessura, gramatura)
- Cabeçalhos coloridos por seção com badges de NC
- Tooltips customizados em todas as métricas

#### Paginação e Performance
- Paginação (`paginate(100)`) em 5 controllers principais
- Links de navegação nas views correspondentes
- Métodos de export mantidos com `->get()` (sem paginação)

#### Correções PHP 8
- Correção de sintaxe: ternários sem ramo falso, strings soltas sem aspas
- `number_format()` com separadores corretos
- `DATE_FORMAT()` com aspas no formato SQL
- `count(null)` → `json_decode()` corrigido para PHP 8
- `php -l` aprovado em todos os arquivos

#### Docker / Rede
- Rota persistente para evitar conflito `docker0` (172.17.0.0/16) com rede remota
- Configuração em `/etc/rc.local`

### Resultados
- Ambiente de produção inalterado durante todas as correções (risco zero)
- Homologação funcional com login e fluxos completos
- Documentação detalhada em MELHORIAS.md (624 linhas)
- Redução significativa no tempo de diagnóstico com Hermes Agent + OpenCode
- Preservação de todas as customizações existentes
