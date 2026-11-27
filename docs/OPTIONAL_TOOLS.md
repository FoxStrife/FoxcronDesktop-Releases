# Foxcron Agent — macros e histórico de clipboard

Foxcron Agent 1.0.4 é o componente opcional incluído no Foxcron Desktop 1.27.9.
Disponível para Windows 10/11 x64, com instalação e ativação separadas.

## Instalar e habilitar

1. Atualize primeiro o Foxcron Desktop para uma versão que ofereça Operador → Ferramentas.
2. Abra essa administração e clique em Instalar módulo. O componente possui runtime próprio;
a instalação pode baixar as dependências fixadas e não habilita captura/expansão automaticamente.
3. Habilite o módulo e ative somente as funções desejadas em Preferências:
Capturar histórico, Expandir macros e, opcionalmente, Iniciar com o Windows.
4. O ícone original do Foxcron aparece na bandeja ao lado do relógio, com a identificação
Foxcron Agent. O Windows pode colocá-lo nos ícones ocultos; abra a seta da bandeja.

Não é necessário instalar o Agent para executar AWS ou Precify. Quem não o habilitar
continua usando o Foxcron normalmente. Instalações antigas do Desktop sem esta
administração não possuem o contrato de proteção e devem receber o host novo primeiro.

## Macros

Cadastre, edite, duplique ou exclua macros pela administração. Informe nome,
palavra-chave e texto simples. Exemplos de palavra-chave: teste, .teste, ;teste e ##teste.
Use de 2 a 64 letras/números/símbolos, sem espaços, acentos ou emojis no gatilho. O texto
pode conter Unicode, emojis e quebras de linha. Conflitos de gatilho são informados
antes de salvar. A expansão ocorre imediatamente ao terminar o gatilho, sem Enter.
Gatilhos sem prefixo também podem expandir ao final de uma palavra maior; escolha
combinações que não coincidam com a digitação normal.

A expansão insere o texto em uma operação e procura preservar o clipboard anterior.
Aplicativos protegidos/elevados, controles próprios e IME podem exigir exclusões e
homologação específica; não existe garantia de funcionamento em qualquer aplicativo.

## Janela rápida e cópia

Em **Preferências** na aba **Administração**, ative **Modo de baixo consumo da janela rápida**. A partir do próximo início do Agent, a janela carrega no primeiro uso. A primeira abertura pode demorar mais. O pré-carregamento continua como padrão, e macros e captura de histórico seguem suas preferências. Se o Agent já estiver instalado, atualize o Desktop e use **Atualizar módulo** para ter acesso à opção.

- Win+V abre o histórico; Ctrl+Alt+Espaço abre a busca de macros.
- A janela tem tamanho fixo; mova-a pela faixa superior ou pelos seis pontinhos.
- Busca e filtros Todos/Texto/Imagem/Arquivos ajudam a localizar itens. A prévia fica
acima dos metadados. Referências de arquivos/pastas guardam caminhos, não os arquivos.
Se o original for movido/removido, a referência pode deixar de funcionar.
- Clique direito seleciona a linha e abre ações à direita. Outro clique direito troca
item, prévia e ações no mesmo clique. Copiar e Copiar como texto simples ocultam a
janela após sucesso. Copiar e manter a janela aberta permite continuar escolhendo.
- Ctrl+Enter copia o item; Enter sozinho não cola. Cole manualmente no aplicativo desejado.
Esc oculta; clicar fora também oculta, mesmo quando a janela abriu sem ter recebido foco.
O serviço continua ativo. Não há opção Copiar como… no menu.
- Fixar mantém o item nas limpezas normais, respeitando o limite de armazenamento.
Excluir/Limpar pedem confirmação e não alteram o conteúdo original dos arquivos.

Se Raycast, histórico do Windows ou outro programa usar o mesmo atalho, ajuste o conflito
nas configurações desse programa. O Foxcron não altera nem desinstala o Raycast e não
muda silenciosamente as preferências do Windows.

## Privacidade, retenção e proteção das rotinas

Os dados ficam separados em %LOCALAPPDATA%/FoxcronTools/data, em SQLite próprio,
com payloads protegidos por DPAPI do usuário Windows. Não se migram os cadastros,
cofre ou preferências do Foxcron Desktop. Pastas, chave de autostart FoxcronTools e
identificadores internos anteriores são mantidos por compatibilidade; o nome público é
Foxcron Agent. Não copie o banco para outro usuário supondo portabilidade do DPAPI.

Padrões: 500 itens, 7 dias e 250 MiB. Texto por item até 1 MiB; imagem até 32 MiB / 32 megapixels.
A administração permite mudar limites e aplicativos excluídos. Capture somente o que
você deseja manter. Origem desconhecida é recusada; detecção de campos sensíveis é
parcial e não garante identificar todas as senhas ou controles próprios de aplicativos.
Exportar macros para JSON produz texto legível por solicitação expressa do operador.

Antes de AWS/Precify, o host confirma a proteção da árvore de processos e a pausa da
expansão/injeção. A captura em outros aplicativos continua conforme preferências;
as janelas da rotina ficam excluídas. Se o Agent habilitado não confirmar a pausa, a
rotina não inicia login. Cancelamento/encerramento mantêm o fluxo seguro. Após falha,
recuperação de pausa exige confirmar que automações e janelas de autenticação terminaram;
a pausa não é liberada apenas por timeout.

## Atualizar, desativar e remover

O Desktop entrega o pacote opcional e seu SHA256. Na administração, Atualizar módulo
verifica compatibilidade, prepara a candidata e preserva macros, histórico, preferências
e o estado habilitado. Falha de saúde inicia reversão para versão/dados anteriores.
Depois de confirmar a atualização, o gerenciador tenta remover somente o runtime
imediatamente anterior.
Aguarde qualquer rotina terminar; atualização e habilitação são bloqueadas durante
automação/manutenção. Não há canal de atualização independente silenciosa do Agent.

Desabilitar encerra o serviço sem apagar dados e desativa autostart. Desinstalar remove
o componente, preservando a pasta de dados para reinstalação; não apaga automaticamente
macros/histórico. Se existir recuperação pendente, siga a mensagem do estado antes de
excluir qualquer pasta. Não remova manualmente banco, instalação ou backups em uso.

## Inicialização com Windows

A opção é desligada por padrão. Quando ligada, registra o launcher no usuário Windows
atual; ele inicia apenas se o módulo continuar habilitado e não houver atualização
pendente. Fechar o Desktop não equivale a desabilitar o Agent. Use Desabilitar na
administração para interromper as funções e a inicialização automática.

## Escopo e suporte

Esta entrega é para Windows. A interface e a lógica permanecem Python/Flet; adaptadores
Linux/Wayland ainda não fazem parte do produto. Não use elevação de privilégios como
solução genérica para incompatibilidade. Para diagnóstico, informe versão do Desktop e
do Agent e o comportamento observado, evitando enviar senhas ou seu histórico pessoal.

[Voltar à ajuda](README.md)

### Correções locais 1.0.1 e 1.0.2

O fechamento por perda de foco exige ativação confirmada, abertura atual e foco nativo externo; clicar fora continua fechando normalmente. O operador confirmou várias aberturas de Win+V sem fechamento prematuro. A lista de macros mostra a palavra-chave ao lado do nome, e as informações da seleção mostram o gatilho completo.

Consulte as [notas da versão](RELEASE_NOTES.md). A inicialização com Windows permanece opcional; o teste após novo login ainda está pendente, embora o comando de inicialização e as condições de habilitação tenham sido validados.
