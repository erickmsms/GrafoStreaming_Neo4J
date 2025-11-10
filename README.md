# 🎬 Modelo de Grafo para Serviço de Streaming (Neo4j)

Este repositório contém um script Cypher inicial para modelar um pequeno serviço de streaming (como Netflix) usando o banco de dados de grafo Neo4j.

## 📈 O Modelo de Dados

O objetivo é criar um grafo de conhecimento que conecte usuários, mídias e artistas. O modelo é definido pelas seguintes entidades e conexões:

### Entidades (Nós)

  * `:User` (Usuário)
  * `:Movie` (Filme)
  * `:Series` (Série)
  * `:Genre` (Gênero)
  * `:Actor` (Ator)
  * `:Director` (Diretor)

### Conexões (Relacionamentos)

  * `(User)-[:WATCHED {rating: 5}]->(Movie)`
  * `(User)-[:WATCHED {rating: 4}]->(Series)`
  * `(Actor)-[:ACTED_IN]->(Movie)`
  * `(Director)-[:DIRECTED]->(Movie)`
  * `(Movie)-[:IN_GENRE]->(Genre)`
  * `(Series)-[:IN_GENRE]->(Genre)`

## 🔍 Consulta de Exemplo

Após popular o banco, você pode executar consultas. Por exemplo, para encontrar todos os filmes que um usuário chamado 'Alice' assistiu e deu nota 5:

```cypher
MATCH (u:User {name: 'Alice'})-[r:WATCHED]->(m:Movie)
WHERE r.rating = 5
RETURN m.title
```
