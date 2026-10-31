# Compatibilidade de dados e nomes anteriores

Foxcron é o nome público e o nome usado em novos clientes SSO. Alguns valores antigos são endereços de dados e segredos, não marcas ativas. Eles permanecem literais em `legacy_compat.py` e nos testes que garantem continuidade.

## Pasta de dados

A seleção é somente por existência de diretório, sem ler contas durante importação e sem mover arquivos:

1. `%USERPROFILE%\ZabbixCapture`, se existir;
2. `%USERPROFILE%\Nexo`, se existir;
3. `%USERPROFILE%\Foxcron`, para instalações novas.

Pastas anteriores têm prioridade, inclusive se uma pasta Foxcron vazia já existir. Não renomeie a pasta de dados para mudar a marca: a CLI e os cadastros podem conter referências ao caminho. O conteúdo SQLite e as referências de cofre não são migrados nesta atualização.

## Cofre e preferências

O prefixo `@precify-vault:`, serviços `PrecifyMonitor/`, namespaces usados para calcular referências, a raiz de registro `Software\PrecifyMonitor\Desktop` e outros identificadores de compatibilidade permanecem. Trocá-los sem uma migração específica tornaria dados existentes inacessíveis. Eles não são usados como nome público.

## SSO

Novos registros usam **Foxcron**. As telas de consentimento também reconhecem os nomes exatos **Nexo** e **Precify Monitor Desktop** para sessões anteriores. Isso não dispensa origem autorizada nem vínculo ao código de dispositivo atual. Nomes semelhantes continuam sendo recusados.

## Variável temporária da CLI

O processo filho recebe a senha sob `FOXCRON_VAULT_PASSWORD` apenas quando necessário. Variáveis herdadas com nomes antigos são removidas junto da atual antes de preparar o ambiente isolado. A senha não é escrita em argumentos, logs ou Git.

## Código, instalação e histórico

O módulo atual é foxcron_ui.py; recursos e licenças estão em assets/foxcron. O repositório privado e a pasta de desenvolvimento usam FoxcronDesktop. O repositório público FoxcronDesktop-Releases fornece instalação e atualizações. Essas mudanças não alteram os identificadores persistidos nem os dados dos operadores.
