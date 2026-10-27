# Security and Repository Handling

## Intended visibility

This project is intended to be maintained in a **private Git repository**. The documentation pack does not include the AI-QSIS implementation.

## Before committing

- Confirm the GitHub repository visibility is set to **Private**.
- Review `git status` and `git diff --cached --name-only` before every commit.
- Do not commit source notebooks, `.py` files, generated reports, downloaded market data, credentials, access tokens, or local configuration.
- Keep private implementation files in a separate local folder/repository from this documentation-only pack.
- Treat `.gitignore` as a safety net, not as an access-control boundary.

## If sensitive material was exposed

Changing a repository to private does not guarantee that previously exposed material has disappeared from clones, forks, caches, or downloaded copies. Remove the material from repository history as appropriate, rotate any exposed credentials, and assess the scope of exposure.

## Reporting

Do not place confidential details or credentials in a public issue. Use a private channel controlled by the repository owner.
