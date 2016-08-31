# Installation

Install it via npm

    npm install --save neo4-js

# Usage

Use it via models

    var Neo4js = require('Neo4js');

    const neo4js = new Neo4js('neo4j', 'neo4j');
    const User = neo4js.define('User', {
      guid: {
        index: true,
        defaultValue: Neo4js.uuid4,
      },
      name: {
        unique: true,
        exists: true,
      },
      email: {
        unqiue: true,
      },
    });

    User.create({ name: 'John', email: 'john@example.com' })
      .then((createdUser) => {
        console.log(createdUser);
      })
      .catch((err) => {
        console.log(err);
      });

Use it via queries

    var Neo4js = require('Neo4js');

    const neo4js = new Neo4js('neo4j', 'neo4j');
    const query = neo4js.Query();

    query
      .match('n', ['User'], { name: 'John' })
      .ret('n')
      .limit(1)
      .execute()
      .then((rawResult) => {
        console.log(rawResult);
      })
      .catch((err) => {
        console.log(err);
      });

# Docs

[Rudimentary docs](https://janpeter.github.io/neo4js/)
