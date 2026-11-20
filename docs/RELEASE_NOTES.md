# Foxcron Desktop 1.27.7 — correção da limpeza após atualização

- Corrige a reabertura do Desktop após a atualização para que a nova sessão possa iniciar sem manter a pasta anterior em uso.
- Ao limpar a versão imediatamente anterior, o instalador move a pasta antes de excluir seus arquivos. Se a pasta estiver bloqueada, ela fica intacta. A limpeza também reconhece pastas vazias ou ausentes e trata o ponteiro `previous.txt` correspondente.
- O Foxcron Agent opcional permanece na versão 1.0.3. Cadastros, macros, histórico e preferências ficam fora da limpeza.

Atualize pelo fluxo habitual do Foxcron. Consulte o [guia de uso](USER_GUIDE.md) e o [guia de instalação](INSTALLATION.md).
