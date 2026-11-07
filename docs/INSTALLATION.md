# Instalação e atualização

## Instalar

1. Baixe o ZIP em [Versões do Foxcron Desktop](https://github.com/FoxStrife/FoxcronDesktop-Releases/releases/latest).
2. Extraia **todos** os arquivos.
3. Execute **Instalar Foxcron.cmd**. Aguarde a mensagem de conclusão.
4. Use o atalho **Foxcron** na Área de Trabalho e configure **Meu acesso**.

Requisitos: Windows 10/11 x64, internet e credenciais nominais AWS/Precify. O script usa Python x64 instalado ou tenta instalar Python 3.12 pelo winget oficial, sem privilégios de administrador. Se o Windows não tiver winget, instale Python x64 de python.org com pip e launcher. Ele não altera a política permanente do PowerShell, DNS ou VPN.

Os downloads vêm de Python/winget, PyPI, Playwright/Flet e GitHub oficial do Bitwarden. A CLI Bitwarden tem versão e SHA-256 fixados. Nenhum login no cofre ou na AWS ocorre durante a instalação.

O diretório do programa é `%LOCALAPPDATA%\FoxcronDesktop`. O ZIP é pequeno porque não carrega Python, ambiente virtual, Chromium nem Bitwarden. O tamanho instalado é maior; a primeira instalação depende da internet e pode demorar.

Se houver bloqueio por política de segurança, consulte a administração do computador. Um script sem certificado não garante aceitação por todos os controles do Windows.

Portal AWS, região SSO, servidor HTTPS do cofre e URL Precify já aparecem preenchidos na primeira configuração. Você pode alterar e salvar esses campos; valores personalizados existentes são preservados. E-mail, senhas e nome do item do cofre continuam sendo informados pelo operador. O caminho padrão do bw.exe é identificado na pasta do aplicativo; um caminho externo salvo pelo operador tem prioridade.

## Atualizar

Quando uma nova release estável é confirmada, aparece um aviso permanente com a versão e o botão **Atualizar**, além da opção **Operador → Atualizar para …**. Novas execuções ficam bloqueadas até atualizar; uma rotina em andamento pode terminar ou ser cancelada com segurança. A consulta pública é feita ao abrir e a cada 30 minutos, sem tokens GitHub e sem dados das suas contas. Se falhar ou estiver offline, nada é instalado.

A atualização começa ao clicar em **Atualizar**, com o app ocioso. Se a consulta não conseguir confirmar uma versão nova, o uso continua permitido; uma atualização já confirmada na sessão mantém o bloqueio mesmo se a rede falhar depois. Depois de conferir origem e SHA-256, o app abre o script de instalação e encerra com segurança. O script prepara uma nova versão, aguarda a anterior encerrar e só então troca o destino do atalho. Se uma etapa falhar, a versão ativa anterior permanece disponível; se o download falhar no aplicativo, o aviso permite tentar novamente. Ao concluir a instalação, a nova versão é aberta automaticamente.

Versões antigas ficam em `%LOCALAPPDATA%\FoxcronDesktop\versions` para recuperação; não são removidas automaticamente. Se necessário, peça orientação antes de excluir pastas. Para recuperar manualmente, feche o app e execute o `app.py` da pasta anterior com o respectivo `.venv\Scripts\python.exe`.

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
.\.venv\Scripts\python.exe -m playwright install chromium
.\.venv\Scripts\python.exe app.py
```

O instalador cria uma instalação separada; não sobrescreve um checkout Git. Para testar telas sem contas: `.\.venv\Scripts\python.exe app.py --demo`.

Executar pelo checkout de desenvolvimento não altera esse checkout ao atualizar pelo aplicativo: o instalador prepara uma instalação gerenciada separada. Versões anteriores que só exibem a atualização no menu precisam ser atualizadas uma vez por esse caminho para receber o aviso permanente e o bloqueio.
