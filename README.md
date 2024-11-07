# Exercise: Video Games Library with Mongoose

## Learning Goals

Upon completing this exercise, you will be able to:

- Connect to MongoDB using Mongoose
- Import existing data using `mongoimport`
- Create and implement Mongoose Schemas and Models
- Perform CRUD operations on a MongoDB database
- Execute advanced queries using Mongoose
- Handle asynchronous database operations



## Introduction

You've been hired by a video game retailer to build their inventory management system using MongoDB and Mongoose. They need a robust system to track their extensive collection of video games across different platforms, manage inventory, and analyze gaming trends.

Your task is to build the backend system using MongoDB and Mongoose that will power their operations!

## Getting Started

Follow the instructions below to get started:

1. Fork this Repository
2. Clone the repository to your computer
3. Open the repository in VS Code
4. Install mongoose dependency
5. Follow instructions

## Setup

1. After forking and cloning the repository, install mongoose as a dependencies:

```bash
npm install mongoose
```

1. Navigate to the `data` directory and import the initial video games dataset:

```bash
cd data
mongoimport --db videogames --collection games --jsonArray --file games.json
```

The `games.json` file contains a collection of 75 popular video games with details like title, platform, genre, release date, price, and stock information.


## Instructions

### Task 1: Database Connection

Create the initial connection to MongoDB in `app.js`:

- Establish a connection to the MongoDB database
- Implement proper error handling for the connection
- Log successful connection to the console

Keep in mind that establishing a database connection is an asynchronous operation, so implement it using appropriate asynchronous patterns. 

### Task 2: Schema Creation

In `models/Game.js`, create a mongoose schema for video games with the following fields:

- `title` (String, required)
- `platform` (String, required)
- `genre` (String, required)
- `releaseDate` (Date)
- `publisher` (String)
- `price` (Number, required)
- `rating` (Number, min: 0, max: 10)
- `inStock` (Boolean, default: true)
- `stockQuantity` (Number, min: 0)
- `tags` (Array of Strings)

Create a `Game` model that uses this schema. 

Export the `Game` model and import it into your `app.js` file.

### **Task 3: Basic CRUD Operations**

Implement the following functions in `app.js`:

1. Create a new game entry
2. Find a game by title
3. Update a game’s price
4. Remove a game from the database

Implement each function asynchronously and test them thoroughly. Handle potential errors and log successful results to the console.

### **Task 4: Advanced Queries**

Implement functions to:

1. Find all games from the "PS5" platform
2. Find all games released in 2023
3. Find all games priced between $20 and $40
4. Find all games in the "RPG" genre
5. Find all games with stock quantity less than 5 units

All these queries should return multiple results, so you'll need to use the `find()` method which returns an array of documents. Make sure to handle the case where no results are found by checking if the returned array is empty and log an appropriate message to the console.

Remember to call or invoke each function to verify that it works as expected.

### **Task 5: Update Operations**

Each of these operations modifies existing data. Make sure to use the specified update method for each task.

1. Using `findOneAndUpdate()`, update the price of "Minecraft" to $19.99
2. Using `updateOne()`, set "The Last Guardian" stock quantity to 0 and inStock to false
3. Using `updateMany()`, add "Sale" to the tags array for all games under $20
4. Using `findByIdAndUpdate()`, update a game's rating by its ID
5. Using `findOneAndUpdate()`, increase the stock quantity by 10 for "Spider-Man 2"

### **Bonus Challenges**

1. Implement a search function that can search across multiple fields: title, genre, publisher *(hint, you could pass in one search parameter and use the `$or` operator to search across multiple fields)*


## Submission

When you've completed the exercise:

```jsx
git add .
git commit -m "Completed Video Games Library in Mongoose"
git push origin main
```

Create a Pull Request and provide the link so that we can review it.


## Frequently Asked Questions (FAQs)    

<details>
<summary>Why isn’t my `mongoimport` command working?</summary>
If you're encountering issues with the mongoimport command, here are some common solutions:

• Check that MongoDB is running on your system
• Verify you're in the correct directory containing the JSON file
• Ensure the JSON file is properly formatted
• Double-check that you're using the correct database and collection names in the command

If you're still having trouble, try running the command with the --verbose flag for more detailed error messages.
</details>

<details>
<summary>How do I handle asynchronous operations with Mongoose?</summary>
  You can use async/await syntax for asynchronous operations and wrap database operations in try/catch blocks.  
  You could also use the promise-based approach with `.then()` and `.catch()` as each database operations returns a Promise.
</details>

<details>
<summary>What's the difference between updateOne() and findOneAndUpdate()?</summary>
  `updateOne()` only updates the document, but doesn't return it. 
    `findOneAndUpdate()` ****updates and returns the document.
</details>

<details>
<summary>How do I test my queries?</summary>
  To effectively test your queries:
  1. Use `console.log()` to print query results and examine the output
  2. Compare the returned data with what you expect based on your database content
  3. Utilize MongoDB Compass to visually inspect your data and run test queries
</details>
