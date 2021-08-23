### 1.USE

![image](https://user-images.githubusercontent.com/50914198/130369164-55ea15f9-6502-47bb-b00d-40620292f3b5.png)

#### show dbs 
//para ver os bancos de dados disponíveis
#### use SistemaDeCompraDeIngressos    
//para usar o banco de dados SistemaDeCompraDeIngressos

# ------------------------------------------------------------------------

### 2.FIND

![image](https://user-images.githubusercontent.com/50914198/130369502-d2601ad0-cdfa-41c3-a6b0-ca1aa90caa52.png)

#### show collections
//para ver todas as collections do banco de dados que está sendo usado
#### db.pessoa.find().pretty()
//O Find mostra os documentos que há dentro de uma certa collection, nesse caso na collection pessoa. O pretty imprime o resultado formmatado
# ------------------------------------------------------------------------
### 3.SIZE

![image](https://user-images.githubusercontent.com/50914198/130532976-1626d6ac-7525-4abb-9502-8af00fcf6dfd.png)

### db.getCollection('sala').find( {tipo_sala: {$size: 2}})

![image](https://user-images.githubusercontent.com/50914198/130533439-c8319ed1-a7ed-41b1-9baf-4351e96ade69.png)


![image](https://user-images.githubusercontent.com/50914198/130533688-4676dee2-cdb2-4564-97ef-f41f565cbbdc.png)

//Perceba que a consulta só retornou um resultado em que a field= "tipo_sala" tem 2 elementos em seu vetor
# ------------------------------------------------------------------------
### 4. AGGREGATE
![image](https://user-images.githubusercontent.com/17653999/130370555-04eb0dfc-e2c0-41fa-9288-698ab1fb4fb0.png)
### db.alocar.aggegate()
// O Aggregate processa as operações e retorna os dados computados.
# ------------------------------------------------------------------------

### 5.MATCH
![image](https://user-images.githubusercontent.com/50914198/130373317-4c80ec13-9b8b-4313-b352-07931e65bf6d.png)
### db.sala.aggregate([ { $match: {"tipo_sala.nome_sala":"3D"}}, ]).pretty()
// Dá um Match no tipo_sala onde o nome_sala é igual a "3D"
# ------------------------------------------------------------------------
### 6. PROJECT

![image](https://user-images.githubusercontent.com/50914198/130372312-08bb8b55-0e76-4fe8-a23b-8978c7ade309.png)
### db.funcionario.aggregate([     {$project: {carteira_trabalho: 1, salario: 1, _id: 0}}])
// O aggregate usando apenas 1 estagio de pipeline, o Project, projetando apenas a carteira de trabalho e o salario, excluindo o ObjectId

#-------------------------------------------------------------------------
### 7. GTE

![image](https://user-images.githubusercontent.com/32939174/130409650-26ec2ba7-ecfa-4ab9-9d12-b2736d8c92fe.png)
### db.pessoa.find( { idade: { $gte: 20 } } )
// O GTE (ou greater or equal, >=) retorna os registros onde o valor é maior ou igual ao parâmetro passado. No exemplo, procuramos por pessoas com 20 ou mais anos.

# ------------------------------------------------------------------------
### 8.GROUP

![image](https://user-images.githubusercontent.com/17653999/130488524-14ba0d75-d4c3-4ba9-adec-84554c4e81fc.png)
### db.pessoa.aggregate ( { $group: { _id: "$nome",MaxIdade: { $max: "$idade" } } } ).pretty()
![image](https://user-images.githubusercontent.com/17653999/130488913-e62b0596-2824-429c-8004-f38d1d5c598c.png)
### db.pessoa.aggregate ( { $group: { _id: "$nome",cpf: { $max: "$cpf" } } } )
//Agrupa por meio da agregação cada _id distinto, gerando um um documento e sua saida contém o grupo exclusivo para cada valor.


# ------------------------------------------------------------------------
### 9.SUM

![image](https://user-images.githubusercontent.com/50914198/130372596-c7fe03c8-8b2d-449f-b708-39a05cfd69ac.png)
### db.funcionario.aggregate([ {$group: {_id: null, salario_total: {$sum: "$salario"} } } ])
//Somando o salario dos funcionarios usando como criterio de agregaçao o id=null, assim sendo agrupando tudo num único valor

# ------------------------------------------------------------------------
### 10.COUNT

![image](https://user-images.githubusercontent.com/50914198/130370156-c84b9554-33d7-47c3-8060-cda2a471f2e4.png)

#### db.pessoa.count()
//mostra a quantidade de pessoas cadastradas do nosso banco de dados <br /> <br />

![image](https://user-images.githubusercontent.com/50914198/130370743-8bea66a2-e7be-4180-8527-1462eca44835.png)

#### db.filme.find({$or: [{classificação_indicativa:"L"}, {classificação_indicativa:"12"}]} ).count()
//mostra a quantidade de filmes em que a classificação indicativa é "L" ou "12" (repare no operador *$or ) 

#-------------------------------------------------------------------------
### 11.MAX

![image](https://user-images.githubusercontent.com/32939174/130410986-dbf0d272-4100-4b8c-861e-e76594ae6e50.png)
### db.funcionario.aggregate ( { $group: { _id: "$funcionario",MaxSalario: { $max: "$salario" } } } )
// Max retorna o registro com o valor máximo da variável solicitada. No exemplo, foi buscado o funcionario com o maior salário.

#-------------------------------------------------------------------------
### 12.AVG

![image](https://user-images.githubusercontent.com/32939174/130411723-eb5fa7f4-5d18-4a57-825b-07d886c1b2cf.png)
### > db.sala.aggregate ( { $group: { _id: "$sala", AvgLugares: { $avg: "$num_lugares" } } } )
// AVG retorna a média entre os valores buscados. No exemplo, solicitamos a média de lugares nas salas de cinema.


# ------------------------------------------------------------------------
### 13.EXITS

![image](https://user-images.githubusercontent.com/50914198/130371142-f745371d-5bea-4a1c-8772-3da5cc1af4b7.png)

#### db.pessoa.find({idade: {$exists:true}}).pretty()
//Imprime as pessoas que tem o atributo idade
# ------------------------------------------------------------------------
### 14.SORT
![image](https://user-images.githubusercontent.com/17653999/130492218-6dbce2d7-0e71-4890-ac34-edee11518a35.png)
### db.pessoa.aggregate( {$sort: {name: 1 }} )
//O Sort ordena os elementos de uma matriz durante uma operação.

### 15.LIMIT
![image](https://user-images.githubusercontent.com/17653999/130493468-ea1de30a-a6e7-47d2-a666-a033aeacc4e9.png)
### db.funcionario.aggregate({$limit : 3 })
//Limita o número de documentos passado
# ------------------------------------------------------------------------
### 19.PRETTY

![image](https://user-images.githubusercontent.com/50914198/130370405-be4e10b6-3694-42db-b153-c77bb0862029.png)

#### db.endereco.find({estado:"Pernambuco"} ).pretty()
//printa de forma formatada (pretty,bonita) os documentos da collection endereco em que o estado seja igua a "Pernambuco"

# ------------------------------------------------------------------------
### 25.UPDATE

![image](https://user-images.githubusercontent.com/50914198/130374311-a229e5cb-5251-4452-b423-a2f13983dec7.png)

#### db.entrar_em_cartaz.update( {nome_filme: "Palm Springs"},{$set: {dia: "23/08/2021" }} )
//Usando UPDATE para alterar o dia de estreia do filme "Palm Springs", para o dia 23/08/2021, repare na imagem que antes o dia de estreia era "02/10/2021" e o objectId continua o mesmo

### 29.LOOKUP

![image](https://user-images.githubusercontent.com/50914198/130378725-424af0dd-3a15-41d2-96fe-08cb972dc82f.png)
#### db.filme.aggregate([{$lookup:from: "entrar_em_cartaz",localField: "titulo",foreignField: "nome_filme",as: "nome_titulo"}}])
/*A seguinte operação de agregação na coleção filme une os documentos 
de filme com os documentos da coleção entrar_em_cartaz usando os campos nome_filme da
coleção entrar_em_cartaz e o campo titulo da coleção filme.*/
# ------------------------------------------------------------------------
### 30.FindOne
![image](https://user-images.githubusercontent.com/17653999/130499724-5859f98d-11c4-4bf7-8483-5e06b7baf807.png)
### db.pessoa.findOne({"_id": ObjectId("6122ae04b95e8562ff73c217")})
//Retorna um único documento de uma coleção ou visualização . Se existir mais de um documentos satisfazendo a consulta, este método retornará o primeiro documento de acordo com a ordem de classificação ou ordem natural da consulta .




