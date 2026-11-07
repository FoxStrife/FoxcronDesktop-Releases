# Foxcron Desktop 1.26.3

- Relatório AWS com quadro de altura automática: a linha de performance do banco permanece visível, inclusive no layout compacto.
- Aviso permanente com versão e botão **Atualizar**, sem precisar abrir o menu Operador.
- Quando uma nova versão estável é confirmada, novas execuções ficam bloqueadas até atualizar. A rotina em andamento pode terminar ou ser cancelada com segurança; atualização começa com o aplicativo ocioso.
- Se a consulta não conseguir confirmar atualização, o uso continua permitido. Uma atualização já confirmada na sessão mantém o aviso após falhas de consulta ou download, com opção de tentar novamente.
- Instalação, SHA-256, reabertura após atualização, cadastros, histórico, login/MFA e rotinas AWS/Precify preservados. Sem novas dependências.

Quem utiliza uma versão anterior precisa abrir **Operador → Atualizar para 1.26.3** uma vez para receber o aviso permanente e o bloqueio de novas execuções quando houver atualização confirmada.

Validação com 339 testes simulados, dados temporários e capturas DEMO; nenhum acesso operacional real realizado.
