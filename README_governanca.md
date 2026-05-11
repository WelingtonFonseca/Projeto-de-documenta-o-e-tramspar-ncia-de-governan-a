# 📊 Gestão de Vendas Dados — Repositório de Governança

> Repositório privado de dados e documentos do projeto **Gestão de Vendas Dados**.
> Mantido conforme as diretrizes de Governança de Dados da FIAP — Turma 1TSCF/1TSCPW-2026.

---

## 📁 Estrutura de Pastas

```
gestao-vendas-dados/
├── /documentacao       # Políticas, contratos, manuais e registros de auditoria
├── /dados              # Bases de dados, datasets e arquivos de entrada/saída
└── /fontes             # Scripts SQL, Python e demais fontes de processamento
```

---

## 🔐 1. Controle de Acesso

| Perfil           | Permissão          | Descrição                                              |
|------------------|--------------------|--------------------------------------------------------|
| `owner`          | Admin              | Proprietário do repositório. Aprova merges e configurações. |
| `maintainer`     | Write              | Desenvolvedores autorizados. Podem criar branches e PRs. |
| `collaborator`   | Read               | Stakeholders e auditores externos. Somente leitura.    |
| `ci-bot`         | Write (automação)  | Conta de serviço para pipelines automatizados.         |

**Regras:**
- Nenhum colaborador tem acesso direto à branch `main` — toda alteração passa por Pull Request.
- Credenciais e dados sensíveis **nunca** devem ser commitados. Utilizar variáveis de ambiente ou `.env` (listado em `.gitignore`).
- Revisão de acessos: trimestral, registrada em `/documentacao/auditoria/`.

---

## 🔄 2. Controle de Versão

### Estratégia de Branching

```
main               → produção / versão estável
develop            → integração contínua
feature/<nome>     → novas funcionalidades ou documentos
hotfix/<nome>      → correções urgentes em produção
release/<versão>   → preparação de entrega formal
```

### Convenção de Commits (Conventional Commits)

```
feat:     nova funcionalidade ou documento
fix:      correção de dado ou script
docs:     atualização de documentação
chore:    tarefas de manutenção
audit:    registros relacionados a auditorias
```

**Exemplo:**
```
feat: adiciona relatório de vendas Q1 2026
audit: atualiza log de acesso - abril/2026
```

### Tags de Versão

- Seguir padrão **SemVer**: `v1.0.0`, `v1.1.0`, `v2.0.0`
- Toda entrega formal deve ser tagueada e vinculada a uma Release no GitHub.

---

## 🔍 3. Processo de Auditoria

### Trilha de Auditoria (Audit Trail)

Toda alteração relevante é rastreável via:

1. **Git log** — histórico completo de commits com autor, data e hash.
2. **Pull Requests** — cada PR documenta o que foi alterado, por quem e quando.
3. **Issues vinculadas** — mudanças estruturais devem referenciar uma issue aberta.
4. **Registro manual** — alterações de dados críticos devem ser documentadas em `/documentacao/auditoria/log_AAAA-MM.md`.

### Procedimento de Auditoria Periódica

| Frequência | Atividade                                          |
|------------|----------------------------------------------------|
| Semanal    | Revisão de PRs abertos e issues pendentes          |
| Mensal     | Revisão de acessos e permissões                    |
| Trimestral | Auditoria completa: dados, scripts e documentação  |
| Anual      | Revisão da política de governança                  |

### Aprovação de Pull Requests

- Mínimo de **1 reviewer** obrigatório para branches `feature/*`
- Mínimo de **2 reviewers** para merges em `main`
- PRs sem aprovação não podem ser merged (branch protection ativado)

---

## 📋 4. Política de Backup

- Dados críticos em `/dados` devem ser exportados mensalmente para armazenamento externo seguro.
- Scripts em `/fontes` são versionados pelo próprio Git (histórico = backup).
- Documentos em `/documentacao` devem ter cópia em repositório ou drive corporativo.

---

## 📚 Referências

- DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge*. 2ª ed., 2017.
- ISO/IEC 38505-1:2017 — *Information technology — Governance of IT — Governance of data*.
- Lei Geral de Proteção de Dados (LGPD) — Lei nº 13.709/2018.
- GitHub Docs. *About protected branches*. Disponível em: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches

---

*Documento mantido por: Jonatas Menezes da Silva — RM 569091 | Turma 1TSCF/1TSCPW-2026 | FIAP*
