# Auditoria de segurança — Gympoint

## Correções aplicadas

- Atualizei o Express de `4.17.1` para `4.22.3` (mesma major) e atualizei `yarn.lock` e as dependências transitivas para versões corrigidas.
- A auditoria Yarn/NPM da árvore inicial reportou 8 vulnerabilidades: 1 crítica, 4 altas e 3 baixas. Após a atualização, `yarn audit` reportou 0 advisories.
- Removi `node_modules` do versionamento e adicionei regras para ignorar dependências instaladas e arquivos `.env`. O lockfile e o manifesto continuam sendo a fonte reproduzível; instale as dependências com `yarn install --frozen-lockfile`.

## Limitações da auditoria

O repositório não contém código de aplicação fora de `node_modules`, nem scripts de teste. O campo `main` aponta para `index.js`, mas esse arquivo não existe no estado auditado. Portanto, não foi possível auditar rotas, autenticação, autorização, validação de entradas, CORS ou comportamento de produção. A atualização de dependências não deve ser confundida com uma auditoria completa do serviço.

## Verificação

`yarn audit` após a atualização: 0 advisories. Não há comandos de build ou teste definidos em `package.json`; nenhuma aplicação executável pôde ser compilada ou exercitada neste repositório.
