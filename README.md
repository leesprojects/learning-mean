## MEAN_LeesProjects

A MEAN web application with a bunch of custom features I use such as: flashcard memorisation for learning programming concepts and languages

## My Setup Guide

MEAN Setup guide following the [Udemy course by Maximillian S](https://www.udemy.com/course/angular-2-and-nodejs-the-practical-guide/) generated with with [Angular CLI](https://github.com/angular/angular-cli) version 14.1.1.

This installation document was hand-made as of 13/08/2022 as I started to get a good grasp of MEAN

## Initial Setup

Install [NodeJS](https://nodejs.org/en/)  

```
>> npm install -g @angular/cli
>> ng new <<app-name>>
>> cd <<app-name>>
>> npm install
>> ng serve
```

## Packages
```
Packages
>> npm add @angular/materials                     //https://material.angular.io/
>> npm install --save express                     //https://expressjs.com/
>> npm install --save -dev nodemon                //https://www.npmjs.com/package/nodemon
>> npm install --save mongoose                    //https://mongoosejs.com/
>> npm install --save mongoose-unique-validator
>> npm install --save body-parser                 //https://www.npmjs.com/package/body-parser
>> npm install --save bcrypt                      //Hashes passwords 
>> npm install --save jsonwebtoken                //
```

## package.json updates

Add to package.json scripts
  '"start:server": "nodemon server.js"'


## app.module.ts imports
```JS
import { NgModule }                           from '@angular/core';
import { BrowserModule }                      from '@angular/platform-browser';
import { FormsModule }                        from '@angular/forms';
import { MatInputModule }                     from '@angular/material/input';
import { MatButtonModule }                    from '@angular/material/button';
import { MatCardModule }                      from '@angular/material/card';
import { MatToolbarModule }                   from '@angular/material/toolbar';
import { MatIconModule }                      from '@angular/material/icon'
import { MatExpansionModule }                 from '@angular/material/expansion'
import { MatProgressSpinnerModule }           from '@angular/material/progress-spinner'
import { MatSidenavModule }                   from '@angular/material/sidenav';

import { CdkMenuModule }                      from '@angular/cdk/menu';
import { BrowserAnimationsModule }            from '@angular/platform-browser/animations'
import { HttpClientModule }                   from '@angular/common/http';

import { AppRoutingModule }                   from './app-routing.module';
import { AppComponent }                       from './app.component';
import { HeaderComponent }                    from './header/header.component';
import { AppDashboard }                       from './app-dashboard/app-dashboard.component';
import { PostCreateComponent }                from './posts/post-create/post-create.component';
import { PostListComponent }                  from './posts/post-list/post-list.component';
import { FlashcardDashboardComponent }        from './flashcards/flashcards-dashboard/flashcards-dashboard.component';
import { FlashcardViewComponent }             from './flashcards/flashcards-view/flashcards-view.component';
import { FlashcardCreateComponent }           from './flashcards/flashcards-create/flashcard-create.component';
```


## Creating Components   

  [Angular Components](//https://angular.io/guide/component-overview)
```TS
  import { Component } from '@angular/core';

  @Component({
    selector: 'app-root',                          //Name of component
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.scss']
  })

  export class AppComponent { }                    //Export Component to be rendered
```


## Importing Components
```HTML
<app-header></app-header>
  <main>
    <app-post-create></app-post-create>
    <app-post-list></app-post-list>
  </main>
```


## Backend Setup

server.js in the root folder
```JS
const app = require("./backend/app");                   //Imports the backend Express App
const debug = require("debug")("node-angular");
const http = require("http");
const port = process.env.PORT || "3000";                //Uses the provided port or uses 3000
app.set("port", port);
const server = http.createServer(app);                  //Creates an Express server using the backend Express App
server.listen(port);
```
