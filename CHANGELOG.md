# Changelog

Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/). Este projeto segue [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [Unreleased]

### Added
- Testes automatizados do CLI (`npm test`).
- GitHub Action que publica no npm automaticamente ao criar uma tag `v*`.
- Badges de versão, downloads e licença no README.

## [1.0.1] - 2026-08-21

### Fixed
- Caminho do binário no `package.json` (`bin/cli.js` em vez de `./bin/cli.js`).

### Changed
- README reescrito em tom profissional e objetivo, sem redundância entre seções.
- Adicionado arquivo `LICENSE` (MIT).

## [1.0.0] - 2026-08-21

### Added
- Primeira versão publicada no npm.
- CLI (`list`, `get <id>`, `get <id> --copy`) sem dependências externas.
- 7 prompts: `frontend`, `fullstack`, `backend`, `testes`, `auditoria-engenharia`, `auditoria-seguranca`, `revisao-copy`.
