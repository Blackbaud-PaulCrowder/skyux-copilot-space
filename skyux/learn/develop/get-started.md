            

 1.  [Home](/skyux/)
2.  [Learn](/skyux/learn.md)
3.  [Develop](/skyux/learn/develop.md)
4.  [Setup](/skyux/learn/develop/get-started.md)

Get started
===========

This section describes the initial setup to work with SKY UX and guides you through displaying a basic SKY UX component.

Using Angular
-------------

SKY UX components are Angular components, so you need a working knowledge of Angular to use them. Angular provides their own [getting started guide](https://angular.io/start) that you can use to familiarize yourself with Angular.

Developer setup
---------------

If you are building your first Angular application, follow the [instructions for setting up your local environment](https://angular.io/guide/setup-local) for Angular development. Below are some additional details you may find helpful for setting up your environment.

### Angular CLI

SKY UX requires Angular CLI version 20. To check your version, run `ng version` from the command line. To install Angular CLI version 20, run `npm install -g @angular/cli@20`.

### Node.js

SKY UX requires [Node.js version 20.19.x](https://nodejs.org/en/download/releases/). To check your version, run `node -v` from the command line.

In addition, SKY UX recommends Node Version Manager (NVM) to wrap your Node.js installation. NVM installs Node.js in your user directory to avoid permissions-related issues, and it also allows you to easily upgrade and manage multiple Node.js versions.

*   For Mac OS X and Linux, follow [the installation and update instructions](https://github.com/creationix/nvm#installation-and-update) in the `README.md` file for the NVM GitHub repo.
*   For Windows, follow [the installation and update instructions](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) in the `README.md` file for the NVM for Windows GitHub repo.

### NPM

SKY UX requires NPM version 10.x.x, which is the default JavaScript package manager for Node.js. As of Node.js version 0.6.3, it is bundled and installed automatically with the environment. To check your version, run `npm -v` from the command line. To install a specific version, run `npm install` globally and specify the version.

Installing SKY UX
-----------------

SKY UX is made up of multiple NPM packages, so to use any particular component, you need to install the package that includes that component. In this example, we display a [SKY UX alert component](/skyux/components/alert.md) in an existing Angular application. If you are creating a new Angular application, see Angular's guide for [creating a new project](https://angular.io/tutorial/toh-pt0).

### Install common SKY UX libraries

The `@skyux/packages` NPM package holds Angular CLI schematics that make installing and updating SKY UX component libraries easier. To install common SKY UX libraries for your project, run the following Angular CLI command:

Bash

Copy

ng add @skyux/packages --skip-confirmation

    ng add @skyux/packages --skip-confirmation

### Confirm the SKY UX stylesheet is setup correctly

Open your project's `angular.json` file, locate the `projects/<your-project-name>/architect/build/options/styles` property, and confirm that the SKY UX stylesheets are listed first in the array:

JSON

Copy

"styles": \["@skyux/theme/css/sky.css", "@skyux/theme/css/themes/modern/styles.css", "src/styles.scss"\]

    "styles": ["@skyux/theme/css/sky.css", "@skyux/theme/css/themes/modern/styles.css", "src/styles.scss"]

Using SKY UX
------------

### Install the SKY UX indicators library

In this guide, we use the SKY UX alert component, which is part of the `@skyux/indicators` library. Install the library with the following command:

Bash

Copy

npm i @skyux/indicators --save-exact

    npm i @skyux/indicators --save-exact

After installing the indicators package, add `SkyAlertModule` to the `imports` array in your application's `AppModule`.

TypeScript

Copy

    import { CommonModule } from '@angular/common';
    import { NgModule } from '@angular/core';
    
    import { SkyAlertModule } from '@skyux/indicators';
    
    @NgModule({
      imports: [
        CommonModule,
        SkyAlertModule
      ]
    })
    export class AppModule {}

If you are using a lazy-loaded feature module, import `SkyAlertModule` into your lazy-loaded module instead.

### Add an alert to your component

Pick a component in your application and add the following markup to its template. (If you created an application for this guide, remove the markup from `app.component.html` except for `<router-outlet></router-outlet>` and replace it with this markup.)

Copy

    <sky-alert alertType="info" class="sky-margin-stacked-lg">Hello world!</sky-alert>

### Serve your application

Finally, launch your application to verify the alert is displayed on your component:

Bash

Copy

ng serve --open

    ng serve --open

If adding the component was successful, you should see an alert similar to the following:

Hello world!

### Use other components

To use other SKY UX components, see the [components documentation.](/skyux/components.md) Each component documentation page includes the name of the NPM package that contains the component along with API documentation for using the component in your application.

Updating SKY UX
---------------

Keeping up with updates to individual SKY UX libraries can be tedious. To help with this, you can update all SKY UX packages that are installed in your application by running the following command:

Bash

Copy

ng update @skyux/packages

    ng update @skyux/packages