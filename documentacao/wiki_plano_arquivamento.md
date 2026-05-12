# Plano de Arquivamento — Wiki

**Projeto:** Gestão de Vendas Dados
**Versão:** 1.0
**Data:** Maio/2026
**Responsável:** Jonatas Menezes da Silva — RM 569091

---

## 1. Objetivo

Este plano define as diretrizes para organização, retenção, arquivamento e descarte de documentos e dados no repositório **Gestão de Vendas Dados**, assegurando rastreabilidade, conformidade e transparência no ciclo de vida das informações.

---

## 2. Escopo

Aplica-se a todos os artefatos armazenados nas pastas:

| Pasta            | Tipo de Conteúdo                                 |
|------------------|--------------------------------------------------|
| `/documentacao`  | Políticas, contratos, atas, logs de auditoria    |
| `/dados`         | Datasets, exports, relatórios de vendas          |
| `/fontes`        | Scripts SQL, Python, arquivos de configuração    |

---

## 3. Classificação dos Documentos

| Classificação   | Descrição                                          | Exemplo                          |
|-----------------|----------------------------------------------------|----------------------------------|
| **Público**     | Pode ser compartilhado externamente                | README, documentação técnica     |
| **Interno**     | Uso restrito à equipe do projeto                   | Scripts de processamento         |
| **Confidencial**| Acesso limitado a perfis autorizados               | Dados de vendas, PII de clientes |
| **Restrito**    | Somente owner/maintainer                           | Credenciais, chaves de API       |

---

## 4. Ciclo de Vida dos Documentos

```
Criação → Revisão → Aprovação (PR) → Publicação (merge) → Manutenção → Arquivamento → Descarte
```

### Prazos de Retenção

| Tipo de Documento         | Retenção Ativa | Arquivamento | Descarte         |
|---------------------------|----------------|--------------|------------------|
| Dados de vendas           | 2 anos         | 3 anos       | Após 5 anos      |
| Logs de auditoria         | 1 ano          | 4 anos       | Após 5 anos      |
| Scripts e fontes          | Indefinido     | —            | Apenas se obsoleto|
| Contratos e políticas     | Vigência +1 ano| 4 anos       | Após 5 anos      |
| Relatórios gerenciais     | 1 ano          | 2 anos       | Após 3 anos      |

---

## 5. Procedimento de Arquivamento

### 5.1 Arquivamento de Documentos

1. Identificar o documento a ser arquivado.
2. Mover para subpasta `/documentacao/arquivo/AAAA/`.
3. Renomear seguindo o padrão: `AAAA-MM-DD_nome-do-documento_v1.0.ext`.
4. Registrar no log: `/documentacao/auditoria/log_AAAA-MM.md`.
5. Criar commit com mensagem: `chore: arquiva [nome do documento] - [motivo]`.

### 5.2 Arquivamento de Dados

1. Exportar dataset em formato `.parquet` ou `.csv.gz` para compressão.
2. Mover para `/dados/arquivo/AAAA/`.
3. Gerar hash SHA-256 do arquivo e registrar no log de auditoria.
4. Documentar: data de arquivamento, responsável, período coberto.

### 5.3 Descarte Seguro

- Dados confidenciais: remoção via `git filter-repo` + notificação ao owner.
- Dados em storage externo: exclusão documentada com evidência (screenshot ou log).
- **Nunca usar `git rm` simples para dados sensíveis** — o histórico persiste.

---

## 6. Nomenclatura de Arquivos

```
Padrão: AAAA-MM-DD_descricao-resumida_vX.Y.extensao

Exemplos:
  2026-05-08_relatorio-vendas-abril_v1.0.xlsx
  2026-05-08_politica-acesso-dados_v2.1.md
  2026-05-08_script-etl-vendas_v1.3.sql
```

---

## 7. Responsabilidades

| Responsável       | Atribuição                                              |
|-------------------|---------------------------------------------------------|
| Owner             | Aprovação de políticas e descarte de dados restritos    |
| Maintainer        | Execução do arquivamento e manutenção dos logs          |
| Collaborator      | Sinalização de documentos desatualizados via issue      |

---

## 8. Referências

- DAMA-DMBOK, Cap. 9 — Gestão de Documentos e Conteúdo.
- NBR ISO 15489-1:2018 — Informação e documentação — Gestão de documentos de arquivo.
- LGPD — Art. 15 e 16 (término do tratamento e conservação de dados).

---

*Última atualização: Maio/2026 | Branch: `feature/docs`*
