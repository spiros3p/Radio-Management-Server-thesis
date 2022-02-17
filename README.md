# Radio-Management-Server-thesis
## Summary

## Initialization
* Download/clone the repository on your local system using the flag --recursive (*to download the content of both submodules*)     
`git clone --recursive https://github.com/spiros3p/Radio-Management-Server-thesis.git`

### Prerequisites
* Have **Node.js** and **NPM** [installed](https://nodejs.org/en/download/) on your system.
* Have **Angular (12.2.7)** [installed](https://angular.io/guide/setup-local) on your system: `npm install -g @angular/cli@12.2.7`
* (*Optional*) Have **Docker** [installed](https://www.docker.com/get-started) on your system.

### Manual Setup
#### Angular app - Frontend
1. Navigate to ***./frontend*** directory
2. RUN `npm install`
3. Edit file ***./frontend/src/app/app-routing.module.ts***  
by commenting out the desired block of code that defines the `const appRoutes`     
`canActivate: [AuthGuard]` protects the routes using an ***authAPI*** server that exists in ***./backend*** directory in this present project.
4. (*Optional*) RUN `npm run server` on ***./frontend*** directory     
**Starts** a local [JSON-SERVER](https://github.com/typicode/json-server) (fake RestAPI) at port 5000 that serves your [TMF639](https://www.tmforum.org/resources/specification/tmf639-resource-inventory-management-api-rest-specification-r17-0-1/) Resources.     
   - Edit ***./frontend/package.json - line 10*** to change port or uninstall the module.
   - ***./frontend/json-server/db.json*** file contains the dummy Resources that are being served.
5. Edit files 
   - For **Development** build ***./frontend/src/environments/environment.ts*** 
   - For **Production** build ***./frontend/src/environments/environment.prod.ts***    
     - **Define** the following variables according to your own servers and ports that RUN the restAPI for the Resources (*here JSON-SERVER port 5000*) and the restAPI for the user Authorization (*here the nodejs server in the ./backend directory at port 3000*)     
![image](https://user-images.githubusercontent.com/16209859/154480699-a9356aaa-e0b8-4ebf-886b-d76d257e908e.png)
6. Start the Angular application on the ***./frontend*** directory  
   - For **Development** RUN `ng serve` 
   - For **Production** RUN `ng build` ([compiles](https://angular.io/cli/build) the angular app)
7. Angular app is ready and running at [http://localhost:4200/](http://localhost:4200/)
   - if you chose to use the `canActivate: [AuthGuard]` routes, at step  **3.**, you landed at a login page and you have to move to step **8.** to continue setup.     
![image](https://user-images.githubusercontent.com/16209859/154483016-cf7180bb-2f24-4a16-a5c0-c8dbe3774333.png)
   - if you chose to **NOT** use the `canActivate: [AuthGuard]` routes you are **DONE**     
![image](https://user-images.githubusercontent.com/16209859/154483481-a650e98a-286d-4982-bebd-b65f1756774d.png)
#### Nodejs app (authorization/user restAPI) - Backend 
8. Navigate to ***./backend*** directory
9. RUN `npm install` (*you may need to RUN `npm install bcrypt` separately in some occasions*)
10. RENAME ***./backend/.env-example*** file to ***./backend/.env***
11. EDIT the same ***./backend/.env*** file     
    - Define your existing **MySQL** database connection settings (_if you dont have one see the **docker setup** of the project further below to setup one_).
    - Define SESSION_SECRET to protect the sessions created by [PassportJS](https://www.passportjs.org/) in the present Express NodeJS app.
    - Define FRONT_END_IP as the IP and Port where the **Angular app - frontend** is running (*this is needed to allow the certain IP to exchange cookies between the nodeJS app and the Angular app*)  
    ![image](https://user-images.githubusercontent.com/16209859/154486010-54a3d45d-c20a-4a0c-ba18-33094b8fde48.png)
12. Copy the table ***./backend/db/tbl_users.sql*** inside the **MySQL** Database defined at `DB_DATABASE` previously.     
13. Start the NodeJS application on the ***./backend*** directory (*Runs at Port 3000*) 
    - For **Development** RUN `npm run watch` (*to run the app with Nodemon. This will restart the app at every save.*) 
    - For **Production** RUN `node app.js`
14. **Voila!** You can navigate to [http://localhost:4200/](http://localhost:4200/) and login with the existing users (*admin* and *test*) or create a new one
   
### Setup using Docker (docker-compose)
dd
