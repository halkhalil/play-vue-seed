[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

# play-vue
Scala starter app with Play, Vue CLI 3

This app combines a [Play starter app](https://www.playframework.com/documentation/2.6.x/NewApplication) and a [vue-cli-3](https://cli.vuejs.org/guide/creating-a-project.html#installation) based front-end app.

The Vue app is placed under `/frontend` folder and the prod build places the front-end artifacts under /public folder, which is picked up by Play app to serve the artifacts.

## Get Started

Clone the Git Repo & open the terminal in the root dir of the app.

> sbt run

Play [RunHooks](https://www.playframework.com/documentation/2.6.x/SBTCookbook) are in place to run the npm commands as part of the `sbt run` command. 

The hook generates and stores locally a hash of `package.json` to detect changes to it and runs `npm install` when required.

## Production Build

Notice that the Vue app is missing the traditional `webpack.config.js`. And instead we see a `vue.config.js`.  This is because Vue CLI 3 abstracts this out and comes with a bare-bones webpack setup out of the box.
This does not mean though that we cannot add to the webpack config. This can be done by providing webpack config as part of `configureWebpack` object in `vue.config.js`. 
This template keeps all the additional webpack config in a separate file called `vue.webpack.config.js` and imports it in `vue.config.js`.

To invoke the prod build, simply issue below sbt command:
> sbt dist

Utilizing the sbt config as setup in `npm-build.sbt`, this resolves to same as below,
> npm install

> npm build

The production build creates the html, js, css and all other front-end artifacts and places it in `/public` folder.

## Templating Engine?

I have retained a Twirl served page in this app, exposed under `/playApp` route in the app context. However, the intent of this seed app is to provide a template for setting up a completely decoupled web stack wherein Play is used simply to serve an API to front-end.
 
## License

This software is licensed under the Apache license