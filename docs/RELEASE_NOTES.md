# Foxcron Desktop 1.27.1 — ECS e Foxcron Agent 1.0.2

- Verifica tarefas ECS no cluster integrador: acima de três horas em RUNNING gera alerta com início/duração e bloqueia o relatório de sucesso; leitura inconclusiva também bloqueia. Somente leitura, sem parar tarefas.
- Exige ecs:ListTasks e ecs:DescribeTasks na sessão AWS.
- O código atual inclui o Foxcron Agent 1.0.2 como componente opcional para macros e histórico de texto,
imagens e referências de arquivos/pastas, com instalação/ativação separadas.
- Administração pelo Foxcron; bandeja com nome Foxcron Agent e ícone original, janela
compacta com vidro/onda/relevo, menu lateral e ocultação ao clicar fora.
- Host confirma a pausa/proteção do Agent antes de AWS/Precify. Sem confirmação,
não inicia login. Componente ausente não interfere nas rotinas.
- Atualização/reversão do Agent preserva dados e preferências. Instalador/atualizador
existentes, login/MFA, cadastros, relatório e rotinas AWS/Precify preservados.
- Mantém caminhos/identificadores e schema anteriores; não migra cofre nem banco do
Desktop. A instalação padrão não habilita captura/expansão/autostart.
- Inicialização com Windows é opcional e desligada por padrão; a validação após novo login permanece pendente. Não se declara essa homologação concluída.

Veja [Foxcron Agent](OPTIONAL_TOOLS.md) para instalação, uso e limites.

## Últimas correções do Agent

- 1.0.1: confirma ativação e foco externo antes de ocultar por blur; várias aberturas de Win+V confirmadas pelo operador sem fechamento prematuro.
- 1.0.2: palavra-chave visível na lista compacta e nas informações da macro selecionada.

Pacote do Desktop 1.27.1 com Agent 1.0.2 opcional. Atualize pelo fluxo habitual do Foxcron; quem não habilitar o Agent continua usando AWS/Precify sem instalar o componente. A consulta ECS exige as permissões de leitura indicadas no [guia de acesso AWS](AWS_ACCESS_REQUEST.md).
