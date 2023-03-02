## Ordenar por data de criação
```
db.getCollection("NomeColecao")
    .find({}, {"campoDesejado" : 1, "_id" : 0})
    .sort({"createDate": -1});
```

## Count
`db.Colecao.countDocuments({});`

## Atualizar com replace no valor
```
db.Colecao.updateMany({}, [
  {
    $addFields:
      {
        data: { $replaceAll: { input: "$data", find: "campoAntigo", replacement: "campoNovo" } }
      }
  },
  {
    $addFields:
      {
        data: { $replaceAll: { input: "$data", find: "outroCampo", replacement: "outroNovoCampo" } }
      }
  }
]);
```
