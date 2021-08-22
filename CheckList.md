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
### 4. AGGREGATE
![image](https://user-images.githubusercontent.com/17653999/130370555-04eb0dfc-e2c0-41fa-9288-698ab1fb4fb0.png)
### db.alocar.aggegate()
// O Aggregate processa as operações e retorna os dados computados.

# ------------------------------------------------------------------------
### 6. PROJECT

![image](https://user-images.githubusercontent.com/50914198/130372312-08bb8b55-0e76-4fe8-a23b-8978c7ade309.png)
### db.funcionario.aggregate([     {$project: {carteira_trabalho: 1, salario: 1, _id: 0}}])
// O aggregate usando apenas 1 estagio de pipeline, o Project, projetando apenas a carteira de trabalho e o salario, excluindo o ObjectId

# ------------------------------------------------------------------------
### 10.COUNT

![image](https://user-images.githubusercontent.com/50914198/130370156-c84b9554-33d7-47c3-8060-cda2a471f2e4.png)

#### db.pessoa.count()
//mostra a quantidade de pessoas cadastradas do nosso banco de dados <br /> <br />

![image](https://user-images.githubusercontent.com/50914198/130370743-8bea66a2-e7be-4180-8527-1462eca44835.png)

#### db.filme.find({$or: [{classificação_indicativa:"L"}, {classificação_indicativa:"12"}]} ).count()
//mostra a quantidade de filmes em que a classificação indicativa é "L" ou "12" (repare no operador *$or ) 
# ------------------------------------------------------------------------
### 13.EXITS

![image](https://user-images.githubusercontent.com/50914198/130371142-f745371d-5bea-4a1c-8772-3da5cc1af4b7.png)

#### db.pessoa.find({idade: {$exists:true}}).pretty()
//Imprime as pessoas que tem o atributo idade


# ------------------------------------------------------------------------
### 19.PRETTY

![image](https://user-images.githubusercontent.com/50914198/130370405-be4e10b6-3694-42db-b153-c77bb0862029.png)

#### db.endereco.find({estado:"Pernambuco"} ).pretty()
//printa de forma formatada (pretty,bonita) os documentos da collection endereco em que o estado seja igua a "Pernambuco"

