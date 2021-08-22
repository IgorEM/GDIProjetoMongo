### 1.USE

![image](https://user-images.githubusercontent.com/50914198/130369164-55ea15f9-6502-47bb-b00d-40620292f3b5.png)

#### show dbs 
//para ver os bancos de dados disponíveis
#### use SistemaDeCompraDeIngressos    
//para usar o banco de dados SistemaDeCompraDeIngressos

### 2.FIND

![image](https://user-images.githubusercontent.com/50914198/130369502-d2601ad0-cdfa-41c3-a6b0-ca1aa90caa52.png)

#### show collections
//para ver todas as collections do banco de dados que está sendo usado
#### db.pessoa.find().pretty()
//O Find mostra os documentos que há dentro de uma certa collection, nesse caso na collection pessoa. O pretty imprime o resultado formmatado

### 10.COUNT

![image](https://user-images.githubusercontent.com/50914198/130370156-c84b9554-33d7-47c3-8060-cda2a471f2e4.png)

#### db.pessoa.count()
//mostra a quantidade de pessoas cadastradas do nosso banco de dados


### 19.PRETTY

![image](https://user-images.githubusercontent.com/50914198/130370405-be4e10b6-3694-42db-b153-c77bb0862029.png)

#### db.endereco.find({estado:"Pernambuco"} ).pretty()
//printa de forma formatada (pretty,bonita) os documentos da collection endereco em que o estado seja igua a "Pernambuco"

