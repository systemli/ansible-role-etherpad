# AGENTS.md

Ansible role that installs, configures and maintains Etherpad (3.x) on Debian and Ubuntu, with dirty, MySQL/MariaDB, Redis or PostgreSQL storage.

## Layout

- `defaults/main.yml`: all role variables with defaults; document them in the README
- `vars/main.yml`: internal variables
- `tasks/`: `main.yml` (entry), `preflight.yml` (checks), `mysql.yml` (database setup), `soffice.yml` (LibreOffice export)
- `templates/`: `settings.json.j2`, `APIKEY.txt.j2`, `schema.sql.j2` and files under `etc/`
- `handlers/`: service handlers; `meta/`: Galaxy metadata
- `molecule/default/`: integration test (Docker); `requirements.yml`: collections the role needs

## Checks

- `ansible-lint .` must pass with the default configuration (no `.ansible-lint`)
- `molecule test` runs the role in a container; CI runs it on Debian 12/13 and Ubuntu 22.04/24.04
- `ansible-lint` creates `.ansible/`; it is git ignored, never commit it

## Conventions

- Use fully qualified module names and quoted octal `mode` values
- Give every task a `name`
- New or changed role variables need an entry in `defaults/main.yml` and the README

## Commits and PRs

- Write in English, use conventional commit titles (`feat:`, `fix:`, `chore:`, `ci:`; `!` for breaking changes)
- The PR title sets the release-drafter label (`enhancement`, `bug`, `chore`, `breaking`); a breaking change bumps the major version
- Open PRs as draft and fill in `.github/pull_request_template.md`: what changed and why, plus a breaking changes section if needed
- Do not list changed files or claim test results in the description; CI covers that
