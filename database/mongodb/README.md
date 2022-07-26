# Fixação - MongoDB
[https://classroom.google.com/u/0/c/NDc5ODM5NjE1ODk4/a/NTM2MzEyMDI5NzA4/details](Classroom)

## Consultas a serem resolvidas:

### 1. Inserir os dados das tabelas no MongoDB seguindo os passos abaixo.
- [x] Criar uma nova collection;
- Transformar os dados das tabelas em documentos e inseri-los seguindo as seguintes regras:
  - [x] Colocar os filmes como item principal do documento;
  - [x] Os artistas participantes do elenco devem ser inserido como um array/lista;
  - [x] Os dados de lançamento devem ser criados como subobjetos;
  - [x] O uso do ID do filme como _id do documento é opcional.

```JSON
db.filme.insertMany([
  {
    "_id": ObjectId(32),
    "titulo": "Fica Comigo essa Noite",
    "diretor": "João Falcão",
    "roteiro": "Tatiana Maciel",
    "elenco": [
      "Aline Moraes",
      "Vladmir Brichta",
      "Clarice Falcão",
      "Milton Gonçalves"
    ],
    "lancamento": {
      "ano": 2006,
      "producao": "Diler Trindade",
      "observacao": ""
    }
  },
  {
    "_id": ObjectId(32),
    "titulo": "O Auto da Comparecida",
    "diretor": "Guel Arraes",
    "roteiro": "Ariano Suassuna",
    "elenco": [
      "Matheus Nachtergaele",
      "Selton Melo",
      "Virgínia Cavendish",
      "Denise Fraga"
    ],
    "lancamento": {
      "ano": 2000,
      "producao": "Globo Filmes",
      "observacao": "serie de tv adaptada"
    }
  },
  {
    "_id": ObjectId(32),
    "titulo": "Central do Brasil",
    "diretor": "Walter Salles",
    "roteiro": "João Emanuel Carneiro",
    "elenco": [
      "Fernanda Montenegro",
      "Vinícius de Oliveira",
      "Marília Pêra",
      "Fernanda Montenegro"
    ],
    "lancamento": {
      "ano": 1998,
      "producao": "Video Filmes",
      "observacao": "Filmado em: Rio de Janeiro"
    }
  }
]);
```
<hr>

### 2. Inserir o filme Tropa de Elite, que foi lançado em 2007 e produzido pela Globo Filmes, cujo diretor foi José Padilha.

```JSON
  db.filme.insertOne(
    {
      "_id": ObjectId(32),
      "titulo":"Tropa de Elite",
      "diretor":"José Padilha",
      "lancamento": {
        "ano": 2007,
        "producao":"Globo Filmes"
      }
    }
  );
```
<hr>

### 3. Apagar a informação de localização da filmagem do filme dirigido por Walter Salles.

```JSON
db.filme.deleteOne({ "diretor": "Walter Salles" });
```
<hr>

### 4. Trazer apenas os nomes dos filmes ordenados pelo ano de lançamento.

```JSON
db.filme.find({}, { "_id": 0, "titulo": 1 }).sort({ "lancamento": 1 });
```
<hr>

### 5. Quantos filmes que Fernanda Montenegro participou?

```JSON
  db.filme.find({ "elenco": { $elemMatch: { "$in": ["Fernanda Montenegro"] } } }).count();
```
<hr>

### 6. Quais os nomes dos filmes cujo sobrenome do diretor termina com S e o filme foi lançado nos anos 2000?

```JSON
  db.filme.find({ "diretor": { "$regex": / S/ }, "lancamento.ano" { "$eq": 2000 } });
```
<hr>

### 7. Quais os nomes e os anos de lançamentos dos filmes produzidos pela Globo Filmes?

```JSON
db.filme.find(
  {
    "lancamento.producao": "Globo Filmes"
  },
  {
    "_id": 0,
    "titulo": 1,
    "lancamento.ano": 1
  }
);
```
<hr>

### 8. Incluir o elenco do filme 'Tropa de Elite' com os seguintes atores: Wagner Moura, André Ramiro, Maria Ribeiro. Lembre-se de obedecer o modelo dos demais documentos.

```JSON
db.filme.updateOne(
  { 
    "titulo": "Tropa de Elite" 
  },
  {
    "$set": {
      "elenco": [ "Wagner Moura", "André Ramiro", "Maria Ribeiro" ]
    }
  }
);
```
<hr>
