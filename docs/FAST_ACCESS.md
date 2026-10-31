# Modo rápido: login e MFA locais protegidos

O modo **Local protegido — modo rápido** usa uma cópia do usuário AWS, senha e configuração TOTP no cofre nativo do Windows. A sessão SSO continua sujeita às regras da AWS; a cópia local apenas evita consultar/desbloquear a CLI para obter o MFA durante a rotina.

## Ativar

1. Configure o portal/região AWS e conecte seu cofre seguindo [Configurar Vaultwarden / Bitwarden](BITWARDEN_SETUP.md).
2. Em **Meu acesso → AWS**, expanda **Cópia local protegida**.
3. Clique em **Importar / atualizar** e aguarde a confirmação. Essa ação lê o item selecionado e protege uma cópia local do login e da semente TOTP; não altera o item remoto.
4. Use **Conferir cópia local** para verificar a disponibilidade do cadastro protegido. Essa conferência não faz login AWS nem comprova que a senha continua aceita pelo portal.
5. Selecione **Local protegido — modo rápido** em **Login e MFA AWS** e clique em **Salvar configuração AWS**.
6. Na **Visão geral**, clique em **Executar AWS**.

Não é preciso preencher uma sessão CLI nem um código de seis dígitos no uso normal. O aplicativo gera o TOTP no desafio, com o relógio do computador sincronizado.

## Quando atualizar

Se alterar a senha ou o autenticador AWS no cofre, repita **Importar / atualizar**. A cópia não é sincronizada silenciosamente. Mudar portal/região também exige conferir o vínculo da cópia local. Falha ao validar uma importação não substitui a cópia anterior por dados não confirmados.

Para voltar ao uso direto do cofre, escolha **Vaultwarden / Bitwarden** e salve. O aplicativo não troca automaticamente de origem quando uma delas falha.

## Testar uma autenticação nova

Em **Meu acesso → AWS → Sessão SSO deste computador**, clique em **Esquecer sessão SSO**. Execute AWS novamente: o aplicativo precisará obter uma nova autorização usando a origem de login/MFA configurada.

Essa ação remove os tokens locais do aplicativo. Não apaga login/TOTP, cadastro Precify ou histórico; não encerra outros navegadores nem revoga sessões remotas.

## Proteção

A configuração TOTP permite gerar códigos futuros e deve receber o mesmo cuidado da senha. Login e TOTP ficam acessíveis ao usuário Windows que executa o aplicativo, sem uma senha adicional do Foxcron. Cada operador deve usar sua própria conta Windows e seu próprio item de cofre.

O ganho de tempo depende da sessão SSO, rede, portal e serviços. O modo rápido não garante duração fixa nem elimina as políticas de MFA/consentimento da organização.
