# Creating a simple node server
Notes for creating a simple node server


1. npm init

2. npm install express

3. create index.js
# setup server using express
    const express = require('express')
    const app = express()
    const PORT = 3033

    ## REQUEST HANDLER
        ## app.httpMethod('url', callback function)

    app.get('/', (req,res) => {
        res.json({text : 'Welcome to the website'})
    })

    app.listen(PORT, () => {
        console.log('Listening to port', PORT)
    })

4. Establish database connection
    * - npm install mongoose
    * - const mongoose = require('mongoose')
    * - 
    # DB Configuration
    
        mongoose.connect('mongodb://localhost:27017/oct-weekend-notes-app', { useNewUrlParser: true, useUnifiedTopology: true }) 
    
        .then(() => {
            console.log('Connected to db')
        })
        .catch((err) => {
            console.log(err)
        })

5. Creating Schema
    # Creating Schema
        const Schema = mongoose.Schema
        const noteSchema = new Schema({
            title: {
                type: String,
                required: true
            },
            body: {
                type: String
            },
            createdAt: {
                type: String,
                required: true,
                default: Date.now()
            }
        })

6. Create note model

    # Creating note Model
        const Note = mongoose.model('Note',noteSchema )     ## The model name should be singular and first letter should be capital 
        const note = new Note()
        console.log(note)

7. ODM - Object Document Model
    * map a model to a collection
    * map an object to a document
    * map a property to a document's field
