# graphQL from scratch

# Steps to follow:

1) Set up express application
Import express into your application
Get the app from the express method
Make the express app to listen on 5000 port
Define script for running the node.js server
2) Bring graphql into your express app
Import express graphql 
Define the route for the app,
Pass express graphql as a parameter to app.use method
Set graphiql to true in order to be able to use it for making requests
3) Create a const schema with new graphql schema object type
Pass the query as a parameter and define it with new graphql object type
Pass the name as a parameter  to new graphql object type with the value “HelloWorld”
Define fields method and pass to it message field with graphql string type (import graphql string type from graphql library) and resolve it in a simple method which will return static string: “Hello World”
Call this newly created schema within express graphql
4) Paste authors and books data into your application
5) Remove the test sample related to Hello world
6) Create a root query type which is going to be new  graphql object type
Pass the name as a parameter with the value “Query”
Pass the description as a parameter with the value of “Root Query”
Define a books filed which will return list of books type(import graphql list type from graphql library) it also will have a description with the value: “List of all Books”
7) Create book type as a new graphql object type
Give a name as a Book
Give a description “Single book written by author”
Define the field id as a graphql int type and make it non nullable
Define the field name as a graphql string type and make it non nullable
Define the field author id as a graphql int type and make it non nullable
8) Since we have Root query defined and the type for it (Book type) create a schema as a new graphql schema, it will receive as parameter a query which is going to be root query type
9) Define the author information  on book type , for that add the new field to the to book type named as author, which will be a new type of Author
10) Since the author information is not defined on represented book data , add the custom resolver to it, which would return ->  search for authors and find a author with id from the book, the book will be parameter for the resolver (as a parent parameter, since the author is inside the book type)
11) Do a check if the author id is same as book author id
12) Create the author type with same way as book type with its corresponding fields: id as an graphql int type and a name as a graphql string type
13) Create an author's query with the same way as books query
14) Add  the books field for the authors which will be type of list of book type 
Resolve the books field with custom resolver, search for books filter the book and compare if the book author id is equal to author id(author is a parameter for resolver as a parent)
15) Define a query to get one single book and author(query definitions will be similar to books and authors queries)
For instance for a single book the type would be Book type instead of list of book types, and we would get it based on the argument that we pass to resolve method(resolve method receives two parameters: parents and args)
In order to define what args are valid identify the args object, with id property which will have graphql int type 
Use that id parameter in order to find books, compare if the book id equals to args id 
16) Define a query to get a single author with the same way as for authors
17)Pass the schema mutation as a parameter with a type of root mutation type
18) Create a root mutation type similarly to query mutation type
Define the root mutation type which is going to be graphql object type
Pass to it name as a parameter
Give the value to the name as a ‘’Mutation”
Pass the description as a parameter with the following value: ‘’Add the Book’’
Pass the fields object named as add book (it’s a mutation name)with the type of book type and with the description of “Add a book”
Define args object since we need to add to the server in order to add new book
Args object will have the following fields: name with graphql string type and it always required(use non nullable) authorId with graphql int type which is always required as well(use non nullable)
Define the custom resolver with parent and args parameters
Create a book constant inside the resolver and define fields for it
It will have field id , which type would be books.lengt+1 (in the case of database relation it would be generated automatically) name: which would be type of args.name,
And author id as args.authorId
Add that newly created book into books array with push operation and return that book
19) Create new mutation for adding the author similar to adding the book

# Data that will be used for Book and Author representation :

const authors = [
	{ id: 1, name: 'E. Hemingway' },
	{ id: 2, name: ' R. Branson' },
	{ id: 3, name: 'C. Discens' }
]

const books = [
	{ id: 1, name: 'The Torrents of Spring ', authorId: 1 },
	{ id: 2, name: 'The Sun Also Rises', authorId: 1 },
	{ id: 3, name: 'A Farewell to Arms', authorId: 1 },
	{ id: 4, name: 'Finding My VIrginity ', authorId: 2 },
	{ id: 5, name: 'Losing My VIrginity', authorId: 2 },
	{ id: 6, name: 'Globalisation Laid Bare', authorId: 2 },
	{ id: 7, name: 'Oliver Twist', authorId: 3 },
	{ id: 8, name: 'A tale of two cities', authorId: 3 }
]

