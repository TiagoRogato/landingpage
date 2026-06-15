# Diagnóstico e Correção de Sistemas Legados

## Laravel/PHP, Apache e Migração de Ambientes

### Visão Geral
Trabalho especializado de diagnóstico, correção e modernização de aplicações **Laravel/PHP legadas**, atuando em ambientes de produção e homologação com múltiplas versões de PHP, Apache FPM e bancos de dados variados (MySQL, MariaDB, Firebird).

### Tecnologias Utilizadas
- **Laravel 5.4 / Laravel 9.x** — frameworks legados
- **PHP 7.4 / PHP 8.5** — versões em produção e homologação
- **Apache 2.4**, mod_php → PHP-FPM
- **Composer**, namespaces PSR-4
- **MySQL / MariaDB / Firebird 4.0**

### Correções Realizadas
- Ajuste de namespaces de modelos (App → App\Models)
- Correção de métodos obsoletos (Input:: → request(), EncryptCookies)
- Configuração de Apache VirtualHost com PHP-FPM isolado
- Remediação de vulnerabilidades (npm audit fix — 137 vulnerabilidades)
- Correção de CSRF e sessão em ambientes de homologação
- Ajustes de SESSION_DOMAIN para suporte multi-domínio

### Resultados
- Ambientes de produção inalterados (risco zero)
- Homologação funcional com login e fluxos completos
- Documentação das alterações em MELHORIAS.md
- Roteiro claro para migração futura sem refatoração desnecessária
