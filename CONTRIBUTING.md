# Como contribuir

Toda mudança entra por **Pull Request**, revisado por um(a) professor(a) do time `professores`.

## 1. Crie uma branch com nome no padrão

| Prefixo | Quando usar | Exemplo |
| --- | --- | --- |
| `feat/` | nova funcionalidade | `feat/tela-de-login` |
| `fix/` | correção de bug | `fix/validacao-email` |
| `ci/` | automação, workflows, build | `ci/cache-dependencias` |
| `doc/` | documentação | `doc/como-rodar-local` |
| `teste/` | testes automatizados ou experimentos | `teste/api-usuarios` |

Use **minúsculas, números e hífens**. Branches fora do padrão **não abrem PR automático e não podem ser mescladas**.

```bash
git switch -c feat/tela-de-login
```

## 2. Faça commits pequenos e descritivos

```bash
git commit -m "feat: formulário de login com validação"
```

## 3. Faça o push — o PR abre sozinho

```bash
git push -u origin feat/tela-de-login
```

O workflow **Abrir PR automaticamente** cria o PR para a `main` com a lista de commits.
Na primeira vez, um(a) professor(a) clica em *Approve and run workflows* no PR.

## 4. CI e revisão

- **`branch-name`** valida o nome da branch.
- **`build`** detecta a stack (Node, Java/Maven/Gradle, Flutter, Python ou `scripts/ci.sh`) e roda build e testes.
- O merge exige os dois checks verdes **e** a aprovação de alguém do time `professores`.
- Novo push depois da aprovação? A aprovação é descartada e precisa ser refeita.

## Outra stack?

Crie `scripts/ci.sh` com os comandos de build/teste do seu projeto — o CI executa automaticamente:

```bash
#!/usr/bin/env bash
set -euo pipefail
go build ./... && go test ./...
```

## Regras

- Nunca faça commit de senhas, tokens, chaves ou arquivos `.env`.
- Só publique nomes, fotos ou dados de pessoas com autorização.
- Mudanças em `.github/` (workflows, CODEOWNERS) recebem um alerta no PR e revisão redobrada.
