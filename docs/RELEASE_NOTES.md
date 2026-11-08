# Foxcron Desktop 1.26.4

- Corrige o histórico Precify: quando a tela carregou e o botão **Lotes em processamento** não aparece, o resultado é **0 processamentos na fila**.
- A ausência válida não torna a execução incompleta; o resumo informa **SEM PROCESSAMENTOS**, e a métrica mostra zero.
- Tela vazia, login, carregamento visível, falha de navegação ou número ilegível continuam sendo tratados como leitura não confirmada.
- Preserva formatos Precify, AWS, cadastros, histórico, login/MFA, instalação por script e atualização com SHA-256. Sem novas dependências.

Validação com 341 testes simulados, HTML sintético e dados temporários; nenhum acesso operacional real realizado.
