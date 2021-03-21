# GraphQL Node.js Example
This repository holds an example GraphQL server written in Node.js.
The code uses Apollo server with Knex, Objection.js and sqlite.

## Running Locally
- Clone the repository
- Install dependencies: `npm install` | `yarn install`
- Install knex globally for migrations: `npm install -g knex` | `yarn global add knex`
- Run `knex migrate:latest` and `knex seed:run` to create the database with sample data
- Execute `npm run dev` to start the development server on `localhost:4000`
- Use an app like [Insomnia](https://insomnia.rest/) / [Postman](The Collaboration Platform for API Development](https://www.postman.com/)) to send GraphQL queries to the server
  - POST http://localhost:4000/graphql
  - [Postman Collection](./Postman/Graphql-nodejs-example.postman_collection.json)
  - [Insomnia Collection](./Insomnia/Insomnia_2021-03-21.json)



## Example

### Query

- Get all Threads

```
{
  threads {
    id
    name
    description
    comments{
      id
      description
      user{
        id
        userName
        firstName
        lastName
   	 }
    }
  }
}
```

- get thread with id = 1

```
{
  thread(id: 1) {
    id
    name
    description
    comments{
      id
      description
      user{
        id
        userName
        firstName
        lastName
   	 }
    }
  }
}
```



### Mutation

- create Thread

```
mutation {
  createThread(
    name: "Thread 3",
  	description: "This is the third thread", 
  	userId: 1) {
      id
      name
      description
  }
}
```

- create Comment

```
mutation{
  createComment(userId: 1, threadId: 3, description: "This is a comment for Thread 3"){
    id
    description
    user{
      id
      userName
    }
  }
}
```



