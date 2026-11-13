# Foxcron Desktop 1.26.5

- Corrige a rejeição do endereço regional `{região}.signin.aws` na autorização SSO, alinhando a validação à etapa do navegador.
- Preserva HTTPS, região configurada e restrições de segurança do endereço.
- Login/MFA automáticos, cadastros, rotinas AWS/Precify, instalação e atualização com SHA-256 mantidos. Sem novas dependências.
- O módulo experimental de macros/clipboard não faz parte desta distribuição.

Validação com 343 testes usando mocks, páginas sintéticas e dados temporários; nenhum acesso operacional real realizado.
