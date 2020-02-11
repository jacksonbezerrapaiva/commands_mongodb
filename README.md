# Commands MongoDB
Comandos Mongo  

#MongoDB

**Instalar **

	Linux Ubuntu 16.04
	echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
	sudo apt-get update
	sudo apt-get install -y mongodb-org

	Windows
	https://www.mongodb.com/download-center?_ga=2.64603375.1741256980.1533504188-618048179.1533504187&_gac=1.194667231.1533515354.CjwKCAjwwJrbBRAoEiwAGA1B_ZWN2eFazQDp6PU3rgxc8965FoUptAud7dtiqQj5hRZwhgMLOMn2gBoCz8QQAvD_BwE#atlas

	Mac
	brew install mongodb
	mkdir -p /data/db
	mongod

**Conjunto de collections é um database.**  
Não temos tables temos collections.
Limite de 16megas por documentos

**Mostrar todos os bancos de dados**   
show dbs

**Insert**  
db.mongoDb.insert({"name":"Jackson", "age": 27})

**Update múltiplos registros**  
db.mongoDb.update({'title':'Jackson '},{$set:{'title':'Jackson Paiva'}},{multi:true})

**Select**  
db.mongoDb.findOne({"name": "Jackson Paiva"})

**Apagar banco de dados**  
db.dropDatabase()

**Deletar a coleção**  
db.mongoDb.drop()

**Dropar**  
db.mongoDb.drop();

**Remover múltiplos registros**  
db.mongoDb.remove({'title':'Jackson Paiva'})

**Remover todos os registros**  
db.mongoDb.remove({});

**Busca Maior que 26**  
db.mongoDb.find({age : {$gt : 26}})

**Buscar apenas 1 registro menos o id**  
db.mongoDb.find({},{"title":1,_id:0}).limit(1)

**-1 é decrescente e 1 é crescente**  
db.mongoDb.find({},{"title":1,_id:0}).sort({"likes":-1})

**Count**  
db.mongoDb.count()

**Criar um dump do mongo**  
mongodump -h dbhost -d dbname -o dbdirectory

**Monitorar**  
mongostat

**Semelhante ao comando top do linux com os processos do mongo.**  
mongotop

**Criar um array de índice**  
db.users.ensureIndex({"name":1,"age":1})

**Atualizar uma chave**
{ $set : { field : value } }

**Remover uma chave**  
{ $unset : { field : 1} }

**Incrementar uma chave**  
{ $inc : { field : value } }

**Empurrar uma matriz**  
{ $push : { field : value } }

**Empurrar uma matriz**  
{ $pushAll : { field : value_array } }

**Excluir uma matriz**  
{ $pull : { field : _value } }

**Remover o último registro**  
{ $pop : { field : 1 } }

**Renomear**  
{ $rename : { old_name : new_name } }

**Bit**  
{$bit : { field : {and : 5}}}

**Buscar coordenadas geográficas**  
{ $near : [ <coordenada>,<coordenada>], $maxDistance: <distancia> } }

**Json Formatado**   
db.mongoDb.findOne({"name": "Jackson Paiva"}).pretty();

**Criar um índice**  
db.mongoDb.ensureIndex({"title":1})

**Listar todos os índice**  
db.mongoDb.getIndexes()

**Remover índice**  
db.mongoDb.dropIndex("name");

**Adicionar índice em background**  
db.mongoDb.ensureIndex( { "name": 1},{background: true} );

**Operações executadas**  
db.currentOp()

**Criar um ObjectId**  
obj = ObjectId()

**Retornar a data da criação**  
ObjectId("5b678c6aadd09fe00bba01c0").getTimestamp()

**Manutenção se ocorreu algum erro**  
db.repairDatabase();

**Select com limit**  
db.mongoDb.find({},{_id:0,name:1}).limit(1);

**Select com ordernação descrescente**  
db.mongoDb.find({},{_id:0,name:1}).sort({nome:-1});

**Select com ordernação Crescente**  
db.mongoDb.find({},{_id:0,name:1}).sort({nome:1});

**Distinct**  
db.mongoDb.distinct("name")

**Exemplos de like**  
db.mongoDb.find({"name":{$regex:'Jackson'}}).count()

**Exemplos de like**  
db.mongoDb.find({"name":/Jackson/}).count();

**Exemplos de like não importando**  
db.mongoDb.find({ "name": /jackson/i},{"nome":1,"_id":0});

**Importar csv**  
mongoimport -c abcd -type csv --headerline abcd.csv
