# Different kinds of logic
* Business Logic
* Application Logic
* User Interface Logic

# Patterns of Design
* MVC - Model View Controller
* MVP - Model View Presenter
* MVVM - Model View ViewModel

# MVC, Model View Controller
* Model - The data layer, Databases, SQL, CRUD, validation, etc.
* View - The presentation layer, HTML, CSS, EJS, Vue, JSON, etc.
* Controller - The business logic layer connecting the View and the Model, Parsing Requests, building responses, etc.

# Separation of concern
* Understand where the problem resides.
* Separate the problem into smaller, more manageable problems.
* Scalibility. 

# MVC in express - The Model
* Abstract all database logic into models.
* Create sequelize models for the tables 
* Fat model skinny controller

# Model - Ask, don't tell - Pattern
When Writing your queries, the model should be as delcarative as possible. 
```
const publishedPosts = await Post.findAll({
    where: { publishes: true }
})
```
Gets all the posts containing a column named publishes with a value of true.
Move this logic into the models.
```
class Post extends Model {
    getPublishedPosts() {
        return this.findAll({
            where: { publishes: true }
        })
    }
}
```
The caller then ASKS the model for the data:
```
const publishedPosts = await Post.getPublishedPosts()
```
The intent is to make the models as fat as possible while instilling all the potential business logic into the models. So that the controllers are as readable and skinny as possible.



# Tool - Sequelize CLI
* Sequelize CLI - A command line interface for Sequelize.
* A tool to help setup files and directory structure for Sequelize.
```
npm install --save-dev sequelize-cli sequelize
```
```
npx sequelize-cli --help
```
You can initialize a new project which configures a working directory
```
npx sequelize init
```
This will run 4 different commands: config, migrations, models, seeders.
