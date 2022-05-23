# Creating REST Application with NestJS
- In this module we will create a REST API with NestJS
- You can use `postman`, `insomnia` (softwares) or `thunderclient` (vscode extension) for testing the endpoints/methods of the app
    - I have used thunderclient but any API tester will do the work.
## Running NestJS in Development Mode
- to run NestJS in development mode use following command
```
npm run start:dev
```
- This will recompile and start our application everytime we will save any project file
- This will save a lot of our development time

## Creating a Basic Controller
- click [here](https://docs.nestjs.com/controllers) to know more about controllers
- Controllers are one of the most important building block of our application as they handle requests

- use following command to create a controller
```
nest generate controller
```
- below is the shorthand form of above command to create controller
```
nest g co
```
- following is command to **NOT** generate test file for the controller 
```
nest g co --no-spec
```
- CLI will ask us to give name to our controller, name it `coffees`
- Nest will automatically create controller for us and will also update the AppModule
- The file(s) we just created will be created in the directory based on the name of the file we selected
    - you will find the file created at `/src/coffees/`
- If you want to generate something within a specific folder, type the director(y/ies) with slashes prior to the controller name.
- If you are not sure where generator will place the files you can dry run following command in the terminal
```
<filenameWithDirectory> --dry-run
```
- This won't actually create any file but will tell you the place where this command will create file if `--dry-run` was not included
- The newly created controller will look somethin like this
```
@Controller()
export class CoffeesController {

}
```
---
### How does application know which URL access which controller?
- in `@Controller()` decorator we can pass string which will act as an endpoint of the app
- This string then passes the metada needed for Nest to create a routing map
- Open any API tester and make a **GET** request to **http://localhost:3000/coffees**
    - You will see a 404 error because we have not specified any GET method corresponding to '/coffees' endpoint
---
### Let's mae a GET HTTP handler
-  Inside the `CoffeesController` class create a method called `findAll()` and annotate it with `@Get()` decorator, import it from `@nestjs/common`
```
@Get()
    findAll(){
        return "this returns all coffees";
}
```
- Now everytime '/coffees/ endpoint will hit `findAll()` method will execute
- Other HTTP verbs will be done in the same fashion
- To add nested routes or different GET routes in same controller can be added in similar we defined '/coffees' endpoint
```
@Get('coffees/flavor')
    findFlavor(){
        return "this endpoint returns all flavors available"
}
```

## Using Route Parameters
- We can define dynamic routes which behaves according to parameters passed with them
- for example if we define a dynamic route `/coffees/123` then it should return info about coffee having code 123
- to define a Get route with dynamic parameter do the following
```
@Get(':id')
    findOne(@Param('id') id: number){
        return `this action returns ${id} coffee`
}
```
- here first we have defined a parameter called with ':id' in @Get() decorator
- then we can access the parameter with its name through @Param decorator
- if we don't pass anything in @Param() decorator then we will get all the parameters and will be accessible through `params.id` fashion.