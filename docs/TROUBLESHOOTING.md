# Solução de problemas

Comece pelo resultado da rotina e pelas últimas etapas em **Atividade**. Um valor ausente ou inconclusivo não deve ser tratado como zero ou OK.

| Sintoma | O que conferir |
| --- | --- |
| O aplicativo não abre | Execute os comandos do guia de instalação na pasta correta; confira Python, `.venv` e dependências. Registre a mensagem do terminal sem compartilhar dados sensíveis. |
| Chromium indisponível | Feche o app e execute `.\.venv\Scripts\python.exe -m playwright install chromium` na pasta do projeto. |
| CLI do cofre não encontrada | Em Meu acesso, confira o caminho completo do `bw.exe` oficial e se o arquivo ainda existe. |
| Cofre não conecta | Confira servidor HTTPS, e-mail, senha mestra e conectividade. O login automático não trata desafios adicionais do próprio cofre. |
| Item AWS não encontrado/duplicado | Use o nome exato de um item único, com usuário, senha e TOTP. |
| Cópia local ausente | Conecte o cofre, importe em Cópia local protegida e escolha Local protegido no seletor. |
| MFA local rejeitado | Confira o relógio do Windows e se senha/autenticador mudaram. Importe o item novamente após atualizar os dados no cofre. |
| SSO recusado ou expirado | Confira portal e região SSO. Se persistir, use Esquecer sessão SSO e execute novamente; se houver recusa de política/permissão, contate o responsável pela conta. |
| Autorização sem avanço | Registre a última etapa de Atividade. Desafios desconhecidos não são aprovados automaticamente; não altere repetidamente os cadastros para tentar contornar a tela. |
| Acesso negado a Logs/CPU/SQS | A sessão pode estar válida sem permissão para esse recurso. Solicite revisão de acesso com o guia de permissões; não é necessário reinstalar o app. |
| Stream do dia inexistente | A automação do dia pode ainda não ter executado. Confira o horário operacional UTC−03:00 e execute novamente depois; não utilize o stream de ontem. |
| CPU sem amostra válida | Aguarde e repita. Uma amostra antiga ou ausente não é CPU zero; o app não a apresenta como atual. |
| Fila com mensagens disponíveis | É alerta operacional, não falha do aplicativo. Siga o procedimento do NOC; o Foxcron não consome nem apaga mensagens. |
| Precify não entra | Confira URL e cadastro Precify, conta nominal e disponibilidade do site. Um novo desafio do site pode exigir suporte técnico. |
| Relatório desabilitado | Execute AWS até concluir sem alertas nesta sessão. Precify não desbloqueia o relatório. |
| Histórico não salva | Confira espaço e acesso à pasta de dados do Foxcron; em instalações anteriores, o local legado é mantido. Preserve o banco existente; não o exclua para tentar corrigir. |
| Configuração local não carrega | Preserve a pasta de dados e procure suporte. Não apague preferências/cofre/banco sem avaliar a causa. |
| Conteúdo não cabe na tela | Maximize a janela, use a rolagem e confira a escala do Windows. O layout foi conferido a 100% em 1280 × 720 e 1900 × 1080. |

## Informações úteis para suporte

Informe a versão exibida no título, resolução/escala do Windows, rotina afetada, origem de login escolhida e o trecho final do log sanitizado. Se possível, descreva o último passo concluído e se o problema se repete.

Antes de enviar um print ou trecho de log, revise o conteúdo. Não inclua senhas, semente TOTP, códigos MFA, tokens SSO, sessão CLI, arquivos do cofre ou banco de dados. Não cole comandos que imprimam credenciais para investigar.

## Tela de login SSO sem campos

Na versão 1.24.2, um documento vazio recebe espera limitada para renderização e pode ser recarregado uma única vez antes do envio de usuário, senha ou MFA. O prazo total continua limitado; tela desconhecida, domínio externo ou desafio não são aprovados automaticamente.

Se persistir, envie o trecho sanitizado com `SSO renderização:` e `SSO recursos:`, além da última ação. Os contadores distinguem ausência de conteúdo/campos de falhas observadas em scripts, estilos e chamadas da página. HTTP 200 do documento principal, sozinho, não confirma que o login foi renderizado. Não é necessário apagar cadastros, TOTP ou histórico para investigar.

## Reiniciar somente a sessão SSO

Em **Meu acesso → AWS → Sessão SSO deste computador → Esquecer sessão SSO**, remova os tokens locais do aplicativo e execute AWS novamente. Cadastros, TOTP e histórico permanecem. Isso não revoga sessões remotas nem resolve uma permissão negada pela organização.
