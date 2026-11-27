# Instalação e atualização

## Instalar

1. Baixe o ZIP em [Versões do Foxcron Desktop](https://github.com/FoxStrife/FoxcronDesktop-Releases/releases/latest).
2. Extraia **todos** os arquivos.
3. Execute **Instalar Foxcron.cmd**. Aguarde a mensagem de conclusão.
4. Use o atalho **Foxcron** na Área de Trabalho e configure **Meu acesso**.

Use Windows x64 com interface gráfica e acesso à internet. O instalador continua aceitando Windows 10/11 x64. Para uma instalação limpa, a referência é Windows 11 x64, listado nos requisitos atuais do Playwright. As credenciais nominais AWS/Precify são necessárias somente quando o operador configurar suas rotinas. [Requisitos do Playwright](https://playwright.dev/python/docs/intro)

O instalador reaproveita um Python x64 compatível. Se não encontrar um, baixa o instalador oficial de `python.org`, confere seu SHA-256 e prepara o Python e o pip no perfil do usuário. O Python fornecido pelo Foxcron fica fora das pastas de versões. O fluxo dispensa WinGet e prepara também as bibliotecas do PyPI, o cliente Flet, o Chromium do Playwright e a CLI Bitwarden oficial. O preparo é local e não autentica no cofre ou na AWS.

As edições Windows N precisam do **Media Feature Pack** para carregar a interface do Flet. Se os arquivos do Media Foundation estiverem ausentes, o instalador interrompe a preparação com uma mensagem específica. O recurso faz parte do Windows e sua ativação depende das permissões do computador. [Media Feature Pack para Windows N](https://support.microsoft.com/pt-br/windows/experience/platform-variants/media-feature-pack-for-windows-n)

O diretório do programa é `%LOCALAPPDATA%\FoxcronDesktop`. O ZIP é pequeno porque não carrega Python, ambiente virtual, Chromium nem Bitwarden. O tamanho instalado é maior; a primeira instalação depende da internet e pode demorar.

Políticas de execução do Windows ou da empresa podem bloquear o script ou o cliente Flet. O instalador mantém essas políticas, o DNS e a VPN. [Smart App Control no Windows](https://learn.microsoft.com/en-us/windows/apps/develop/smart-app-control/overview)

Portal AWS, região SSO, servidor HTTPS do cofre e URL Precify já aparecem preenchidos na primeira configuração. Você pode alterar e salvar esses campos; valores personalizados existentes são preservados. E-mail, senhas e nome do item do cofre continuam sendo informados pelo operador. O caminho padrão do bw.exe é identificado na pasta do aplicativo; um caminho externo salvo pelo operador tem prioridade.

## Atualizar

Quando uma nova release estável é confirmada, aparece um aviso permanente com a versão e o botão **Atualizar**, além da opção **Operador → Atualizar para …**. Novas execuções ficam bloqueadas até atualizar; uma rotina em andamento pode terminar ou ser cancelada com segurança. A consulta pública é feita ao abrir e a cada 30 minutos, sem tokens GitHub e sem dados das suas contas. Se falhar ou estiver offline, nada é instalado.

A atualização começa ao clicar em **Atualizar**, com o app ocioso. Se a consulta não conseguir confirmar uma versão nova, o uso continua permitido; uma atualização já confirmada na sessão mantém o bloqueio mesmo se a rede falhar depois. Depois de conferir origem e SHA-256, o app abre o script de instalação e encerra com segurança. O script prepara uma nova versão, aguarda a anterior encerrar e só então troca o destino do atalho. Se uma etapa falhar, a versão ativa anterior permanece disponível; se o download falhar no aplicativo, o aviso permite tentar novamente. Ao concluir a instalação, a nova versão é aberta automaticamente.

O instalador mantém a versão anterior durante a preparação da atualização. Depois de validar e ativar a nova versão, tenta remover o runtime imediatamente anterior. Se a preparação falhar, a versão anterior continua disponível. Se a limpeza não puder ser feita com segurança, a pasta anterior é mantida. Os dados e o cache de downloads ficam fora dessa limpeza.

As atualizações correspondem a releases, não a qualquer commit da branch de desenvolvimento.

## Dados preservados

Cadastros, preferências e histórico ficam fora da instalação. Instalações novas usam `%USERPROFILE%\Foxcron`; versões anteriores preservam a pasta de dados existente. O cofre permanece no mesmo usuário Windows. Não apague essas pastas para reinstalar e não copie dados autenticados de outro operador.

## Instalação de desenvolvimento

Para quem tem acesso ao repositório privado:

```powershell
git clone https://github.com/FoxStrife/FoxcronDesktop.git
Set-Location .\FoxcronDesktop
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m playwright install --no-shell chromium
.\.venv\Scripts\python.exe app.py
```

O instalador cria uma instalação separada; não sobrescreve um checkout Git. Para testar telas sem contas: `.\.venv\Scripts\python.exe app.py --demo`.

Executar pelo checkout de desenvolvimento não altera esse checkout ao atualizar pelo aplicativo: o instalador prepara uma instalação gerenciada separada. Versões anteriores que só exibem a atualização no menu precisam ser atualizadas uma vez por esse caminho para receber o aviso permanente e o bloqueio.


## Foxcron Agent opcional

Macros e histórico de clipboard são administrados em **Operador → Ferramentas**.
A instalação não habilita captura, expansão ou autostart automaticamente.
Consulte [instalação, uso e limites do Foxcron Agent](OPTIONAL_TOOLS.md).
