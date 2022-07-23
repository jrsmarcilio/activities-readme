# Neo4J - Graph Database

### Consultas a serem resolvidas:

- Trazer os nomes dos filmes e os anos em que eles foram lançados ordenados pelo ano.

```sql
MATCH (n:Filme)
RETURN
    n.titulo AS Titulo, 
    n.ano AS Lançamento
ORDER BY n.ano
```
OUTPUT JSON:
```javascript
[
  {
    "Titulo": "Central do Brasil",
    "Lançamento": 1998
  },
  {
    "Titulo": "O Auto da Compadecida",
    "Lançamento": 2000
  },
  {
    "Titulo": "Cidade de Deus",
    "Lançamento": 2002
  },
  {
    "Titulo": "Carandiru: O Filme",
    "Lançamento": 2003
  },
  {
    "Titulo": "Tropa de Elite",
    "Lançamento": 2007
  }
]
```
- Quais os nomes dos filmes cujo sobrenome do diretor termina com S e o filme foi lançado no ano 2000? (utilizar o comando ENDS WITH)

- [ ] Apagar a informação de localização da filmagem do filme dirigido por Walter Salles.
- [ ] Quais os nomes dos filmes que foram adaptados de algum texto anterior ao roteiro?
- [ ] Quais os filmes lançados pela Globo Filmes?
- [ ] Incluir o elenco do filme 'Tropa de Elite' com os seguintes atores: Wagner Moura, André Ramiro, Maria Ribeiro. Lembre de obedecer o modelo dos demais nós e relacionamentos.
- [ ] De quantos filmes Fernanda Montenegro participou? (utilizar o comando COUNT)
- [ ] Quais os filmes que foram lançados por alguma produtora.