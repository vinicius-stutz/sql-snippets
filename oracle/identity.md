# Identity
## GENERATED ALWAYS AS IDENTITY
Uma coluna IDENTITY criada com a cláusula ALWAYS sempre irá forçar a geração do valor sequencial. Caso algum valor seja informado na coluna IDENTITY, o erro ORA-32795 (ORA-32795: não é possível inserir em uma coluna de identidade sempre gerada) será emitido.
```
create table NOME_TABELA
(
  nu_seq NUMBER(15) generated always as identity,
  .
  .
  .
)
```

## GENERATED BY DEFAULT AS IDENTITY
Uma coluna IDENTITY criada com a cláusula BY DEFAULT não irá forçar a geração do valor sequencial, ou seja, caso algum valor seja informado na coluna IDENTITY, o mesmo será inserido ao invés do valor sequencial.
```
create table NOME_TABELA
(
  nu_seq NUMBER(15) generated by default as identity,
  .
  .
  .
)

```

## GENERATED BY DEFAULT ON NULL AS IDENTITY
Uma coluna IDENTITY criada com a cláusula BY DEFAULT ON NULL não irá forçar a geração do valor sequencial, ou seja, caso algum valor seja informado na coluna IDENTITY, o mesmo será inserido ao invés do valor sequencial. Caso NULL seja informado, então o valor sequencial será gerado para a coluna.
```
create table NOME_TABELA
(
  nu_seq NUMBER(15) generated by default on null as identity,
  .
  .
  .
)
```
