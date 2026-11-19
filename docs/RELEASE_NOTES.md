# Foxcron Desktop 1.27.3

- Corrige a atualização pelo aplicativo que podia fechar a janela sem instalar a nova versão. A versão 1.27.1 pode atualizar diretamente para a 1.27.3.
- Precify e login AWS usam o mesmo Chromium nos modos visível e em segundo plano. O instalador deixa de baixar o Chromium Headless Shell.
- Ao atualizar, o instalador pode reutilizar a CLI Bitwarden da versão ativa se o SHA-256 corresponder à versão esperada. Quando não puder reutilizar o arquivo, instala uma cópia verificada.
- O Foxcron Agent opcional permanece na versão 1.0.2. Preferências, credenciais e dados continuam nos locais existentes.
- As versões anteriores e o cache instalado anteriormente permanecem disponíveis. O instalador não faz limpeza automática.

Atualize pelo fluxo habitual do Foxcron. Consulte o [guia de instalação](INSTALLATION.md) e o [guia do Foxcron Agent](OPTIONAL_TOOLS.md).
