# Foxcron Desktop 1.27.14 — progresso da atualização do Desktop

27/11/2026

- **Atualizando Foxcron.** Após o download, uma janela com barra animada mostra as etapas de preparação, instalação, verificação e reabertura. A janela continua visível depois que o Desktop fecha.
- **Conclusão e recuperação.** A janela fecha quando o Foxcron confirma a abertura. Se houver falha, o instalador mostra o aviso correspondente, incluindo a recuperação da versão anterior quando ela ocorrer.
- **Foxcron Agent.** O pacote inclui o Agent opcional 1.0.4.

## Foxcron Desktop 1.27.13 — atalhos do Menu Iniciar sem terminal

27/11/2026

- **Menu Iniciar.** O instalador atualiza os atalhos existentes do Foxcron para abrir sem terminal. Se o atalho público estiver protegido contra gravação, instala um atalho no perfil do usuário. O Menu Iniciar pode continuar exibindo a entrada pública antiga.
- **Foxcron Agent.** O pacote inclui o Agent opcional 1.0.4.

## Foxcron Desktop 1.27.12 — abertura e atualização sem terminal

27/11/2026

- **Abertura e atualização.** O atalho do Windows abre o Foxcron sem terminal. A reabertura após a instalação e as atualizações iniciadas pela 1.27.12 também rodam sem terminal. Ao atualizar a partir da 1.27.11, o console do atualizador antigo ainda pode aparecer.
- **Avisos de falha e recuperação.** O lançador deixa de pedir Enter. Caixas de diálogo informam falhas de abertura ou de atualização e indicam quando a versão anterior foi recuperada.
- **Foxcron Agent.** O pacote inclui o Agent opcional 1.0.4. Quem já usa essa versão pode continuar usando o Agent instalado.

## Foxcron Desktop 1.27.11 — recuperação do Foxcron Agent e preparação da instalação

27/11/2026

- **Recuperação do Agent.** O Desktop consegue retomar uma atualização pendente quando o Agent ainda aponta para um ambiente virtual removido do Desktop e o Python base continua válido. Os novos ambientes do Agent usam o Python base. O processo preserva macros, histórico e preferências. O pacote inclui o Foxcron Agent opcional 1.0.4.
- **Preparação da instalação.** Se o Windows já tiver um Python x64 compatível, o instalador o reutiliza. Caso contrário, baixa o instalador oficial do Python, verifica seu SHA-256 e prepara o Python no perfil do usuário sem depender do WinGet. O instalador prepara o cliente nativo do Flet antes de ativar o Desktop.

## Foxcron Desktop 1.27.10 — busca manual e atualização do Foxcron Agent

27/11/2026

- **Buscar atualização do Desktop.** Em **Operador → Buscar atualização**, consulte na hora se há uma versão mais nova. O download só começa quando você seleciona **Atualizar** no aviso ou escolhe atualizar pelo próprio menu. A busca automática continua a cada 30 minutos.
- **Aviso de atualização do Agent.** Se o Agent estiver instalado e o pacote local do Desktop contiver uma versão mais nova, válida e compatível, o aviso mostra a versão e oferece **Abrir Ferramentas**. A oferta do Agent vem do pacote incluído no Desktop, que contém o Foxcron Agent 1.0.4.
- **Progresso da atualização do Agent.** Ao selecionar **Atualizar módulo**, acompanhe a preparação do pacote e das dependências, o encerramento da versão atual, a cópia de segurança dos dados, a ativação e a verificação do funcionamento. A mensagem final distingue atualização concluída, recuperação concluída e falha. Quando a recuperação for concluída, confira a versão instalada.

## Foxcron Desktop 1.27.9 — recuperação de atualização, diagnóstico e Foxcron Agent 1.0.4

26/11/2026

- **Recuperação de atualização.** A versão anterior fica disponível até a nova abrir e confirmar a inicialização. Se a abertura falhar, o Foxcron informa o motivo e restaura a anterior, que ainda pode exigir uma atualização. Se o lançador não conseguir confirmar o encerramento da nova versão, bloqueia a abertura em paralelo.
- **Diagnóstico na Administração.** Use **Copiar diagnóstico** para revisar a prévia e depois **Copiar** para levar o texto à área de transferência. O texto se limita às versões, ao estado do Agent, ao registro de início com o Windows, ao resultado da última atualização do Desktop e à memória residente do Desktop, do Agent e da janela rápida.
- **Foxcron Agent 1.0.4.** O **Modo de baixo consumo da janela rápida** é opcional e vale a partir da próxima vez que o Agent iniciar. A janela carrega no primeiro uso, o que pode tornar a primeira abertura mais lenta. O pré-carregamento continua como padrão. Macros e captura de histórico seguem as preferências. Se você já usa o Agent, selecione **Atualizar módulo** na **Administração** depois de atualizar o Desktop para ter acesso à opção.

Atualize pelo fluxo habitual do Foxcron. Consulte o [guia de uso](USER_GUIDE.md) e o [guia de instalação](INSTALLATION.md).
