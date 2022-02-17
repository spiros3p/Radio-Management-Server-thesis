# Radio-Management-Server-thesis
## Summary

## Initialization
* Download/clone the repository on your local system using the flag --recursive (to download the content of both submodules)     
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
4. (*Optional*) RUN `npm run server`     
which starts a local [JSON-SERVER](https://github.com/typicode/json-server) (fakeRestAPI) at port 5000 that serves your [TMF639](https://www.tmforum.org/resources/specification/tmf639-resource-inventory-management-api-rest-specification-r17-0-1/) Resources 


### Setup using Docker (docker-compose)
dd
