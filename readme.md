# MERN: Book Search Engine
# Table of Contents
  * [Description](#description)
  * [Installation](#installation)
  * [Usage](#usage)
  * [License](#license)
  * [Contributions](#contributions)
  * [Tests](#tests) (not available in this project)
  * [Questions](#questions)
  
  ## Description  
  A book search app that allows users to search for books and create an account that can be logged back into at a later point. Logged in users are able to save books to a favorites list that can be viewed seperately. 

![snapshot1](https://raw.githubusercontent.com/TylerBYeager/book-search-engine/main/images/snapshot1.png)
  ## Code Snippets
  Here are some code snippets and what they accomplished. This first snippet is found within server.js within the server directory. This bit of code is what set the app to use ApolloServer and its associated typeDefs, resolvers, and middleware on the front end. 
  ```
    const app = express();
    const PORT = process.env.PORT || 3001;
    const server = new ApolloServer({
    typeDefs,
    resolvers,
    context: authMiddleware,
    });

    server.applyMiddleware({ app });
  ```

  This second snippet is found within the schemas directory on the server side. Specifically this is from typeDefs.js. This code is what sets the GraphQL argument strings/the description of the data that the client side can request. 
  ```
    const { gql } = require("apollo-server-express");

    const typeDefs = gql`

    type Query {
        me: User  
    }

    type Mutation {
        login(email: String!, password: String!): Auth
        addUser(username: String!, email: String!, password: String!): Auth
        saveBook(input: savedBook!): User
        removeBook(bookId: ID!): User
    }

    type Book {
        _id: ID!
        bookId: String
        authors: [String]
        # authors: String
        description: String
        title: String
        image: String
        link: String
    }
  ```

  The third snippet is found within the utils directory on the client side. Specifically mutations.js. This code is used on the client side to modify the back end data that is received. In this case, this is what saves books to a user's list or removes the book from the list. 
  ```
    export const SAVE_BOOK = gql`
    mutation saveBook($input: savedBook!) {
        saveBook(input: $input)
        {
            _id
            username
            email
            bookCount
            savedBooks {
                # _id
                bookId
                authors
                description
                title
                image
                link
            }
        }
    }
    `;

    export const REMOVE_BOOK = gql`
    mutation removeBook($bookId: ID!) {
        removeBook(bookId: $bookId) {
            _id
            username
            email
            bookCount
            savedBooks {
                # _id
                bookId
                authors
                description
                title
                image
                link
            }
        }
    }
    `;
  ```

  ## Installation
  To install:
  ```
  Once you have a working SSH key added to your Github account, go to the book-search-engine repository. Click the green "code" button on the top right and clonecopy the @github.com link with the SSH key option to your clipboard. 
  ```

  Next, 
  ```
  Open Gitbash or Terminal and navigate to a directory that you would like to add the cloned repository. Once in your desired directory type in "git clone 'right click to paste'" and press enter. This will clone the repository onto your personal machine.
  ```

  Lastly, 
  ```
  Type 'ls' into your Gitbash or Terminal to see a list of items within the directory. If you have done the previous steps correctly then you should see a respository titled "book-search-engine". Simply type in "code ." to open it in your code editor of choice. Lastly, check the package.json file to see the dependencies needed to run this. WIthin your terminal run an npm install.
  ```

  ## Usage
  This app can be used by user's to search a plethora of books, read a brief plot synopsis of the book, and save their favorites to a list that can be viewed later. 
  
  ![snapshot1](https://raw.githubusercontent.com/TylerBYeager/book-search-engine/main/images/snapshot2.png)
  
  ## Built With
  * [JAVASCRIPT](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  * [NODE.JS](https://nodejs.org/en/)
  * [EXPRESS.JS](https://expressjs.com/)
  * [CSS](https://www.w3schools.com/css/)
  * [HTML](https://www.w3schools.com/html/)
  * [MONGODB](https://www.mongodb.com/)
  * [MONGOOSE](https://mongoosejs.com/) 
  * [REACT.JS](https://reactjs.org/)
  * [APOLLO/GRAPHQL](https://www.apollographql.com/docs/apollo-server/integrations/middleware/)
  * [WEB-MANIFESTS](https://developer.mozilla.org/en-US/docs/Web/Manifest)
  * [SERVICE-WORKERS](https://developers.google.com/web/fundamentals/primers/service-workers)

  ## Deployed Link
* [See the Live Site!](https://book-search-engine1024.herokuapp.com/) 

## Authors

* **Tyler Brian Yeager**

- [Link to Repo Site](https://github.com/TylerBYeager/book-search-engine)
- [Link to My Github](https://github.com/TylerBYeager)
- [Link to My LinkedIn](https://www.linkedin.com/in/tyler-yeager-611926213/)

## Contributions

- UC Berkeley Coding Bootcamp & its Instructor and TA's
- BCS learning assistants & tutors
- Google 

## License
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Questions
- wow_d2@hotmail.com 
