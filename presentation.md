# Webpack

## Introduction
Slide 1.
Hello everyone. My name is Eugenia, and I would like to tell you about Webpack.

## What is Webpack?
Slide 2.
The welcoming image on Webpack’s homepage defines what is webpack in the best way.
So, Webpack is a static module bundler for modern JavaScript applications.
And what is it do?

It takes a bunch of different assets, different files of different type - 
javascript, images (like svg, jpeg, png), css stylesheets or less or sass, all sorts of different files,
and combines them down. It bundles them into a smaller group of files or maybe one file for your javascript and one for you css. It depends of your configuration file.

## Why webpack?
Slide 3.
In addition to just bundling things together it's also managing dependencies.
Webpack puts all assets, including Javascript, images, fonts and CSS in a dependency graph. Which makes importing assets easy.

Webpack making sure that code needs to load first is loading first.
So if you write a file that depends on three other files those three need to be included first.
So often its a very complex web of dependencies and larger apps and would be very difficult to manage it on your own. Webpack does it for us, and it splits out, however many files you tell it, to one bundle.
As shown on the picture - Bundle.js.
All you need in your index.html file is one script tag.

## Webpack advantages.
Slide 4.
In addition to bundling and managing dependecies, 
Webpack provides you with transpiling with babel which basically writing modern javascript in a way that most processors can understand.
Also Webpack can perform tree shaking. Which is the elimination of dead code.
Webpack comes with a built in dev-server which is a blessing for local development.
This means you can serve your local application to your browser with hot-reloading.
Hot-reloading makes sure once you save a .js or .css file, webpack listens to those changes and immediately
'refreshes' the browser.
Can run a development webserver.
Do minification...
And much much more.

## Configuring webpack is painful
Slide 5. (image config)
Lets take a look at one common webpack config file. It's takes more than 100 lines of code.
And you know this is no the limit. Usually a webpack config file consists of three files - 
basic config, one for development and one for production.
Slide 6. (joke) I guess he is saying something in russian.
The problem is when we get into config files at the first time,
it can scare a little. 

## webpack template. Project structure.
Slide 7.
So be brave, 
lets create a simple template of webpack configuration and try find out what for what is there.

We have the following file structure. (Look at the picture).
We have index.html file, couple js files, several svg images, sass files, and main index.js.
Where we should plug our sass and js files.
Also we create an empty package Json file to store our dependencies. 

## webpack install.
Slide 8.
Let’s initialize a new project with npm and install both webpack and webpack command line interface (webpack-cli).

Slide 9.
After you have installed the bundler, it is best to run it using the Node.js. script.
After we added this code you can run webpack by typing 'npm run build'.

## Webpack configuration
Slide 10.
So lets create a webpack configuration file.
The syntax for this file look like this.
So we are going to export an object and it's going to have a couple of properties.

## The entry point
Slide 11.
By default the entry point is ./src/index.js.
The entry point actually tells webpack where to start the application bundling process.
Simple rule: one entry point per HTML page. 
For SPA we use one entry point, for MPA we use multiple entry points.

## The output
Slide 12.
Output key contains set of options instructing webpack on how and where it should output your bundles, assets and anything else you bundle or load with webpack.
By default the output is generated in ./dist/main.js.
The output point actually tells webpack that we want 
to make a file called app.js inside of directory called dist.
You can see more on the documentation page. 

## The webpack mode
Slide 13.
Modes are introduced in Webpack 4. 
This mode sets the environment on which webpack works. You can set the mode to either development or production.
If mode not set, webpack sets production as the default value.

Slide 14.
There are many ways to set mode.
You can just provide the mode option in the config,
or pass it as a CLI argument,
or add to file package.json as value,
or you can use webpack.EnvironmentPlugin or webpack.DefinePlugin which is equivalent.

Slide 15.
If we build the same project in different modes, we will get the following data.
development mode bundle is 2.83 kb while production mode bundle is just 564 bytes.
Thanks to out-of-the-box optimization and minification with Webpack 4.
The resulting JavaScript file is smaller in size, as it removes many things that are not needed in production.

For our project we set mode 'development', because it builds very fast and provides a better debugging experience.

## Loaders
Slide 16.
Loaders are the magic or the key for getting webpack to handle different types of files, besides javascript,
transforms them into valid modules that webpack can understand.

So we need to add some stylesheets into our application.
We're going to start really simple. On the section module (which is an object)
we're going to pass in rules (which is an array) and we can put different types of files.
So we can say in 'test' if a file ends with dot 'sass' (this is a regular expression) use this array of loaders.
We would use style-loader, css-loader and sass-loader.
Before this we need to install all of them.
The trickiest part that you need to know that the order matters, and it's reversed.
The last is executed first.
In our example sass-loader happens first. It turns scss into css. Then css-loader turns css into common.js.
So it's converts css into javascript which is our bundle file.
Then the last step which inject styles into DOM by '<style>' tag.

## Handling images.
Slide 17.
Webpack allows us to use images in a very convenient way, using the file-loader loader.
The concept is the same, but use another regular expression for images.
This simple configuration:

Slide 18.
Allows you to import images in your JavaScript:

## Babel.
Slide 19.
What kind of loaders are there? The answer is simple - Many! More loaders you can find at the documentation page.
A commonly used loader is Babel, which is used to transpile modern JavaScript to ES5 code.

## Plugins
Slide 20.
Plugins are like loaders, but on steroids. They can do things that loaders can’t do, and they are the main building block of webpack. Plugins make webpack flexible.
They are most widely used for bundle optimization, minification, script injection, stats emission and etc.

The HTMLWebpackPlugin plugin has the job of automatically creating an HTML file and adding the output JS bundle path.
You can use it in many ways. 
In the first case, the plugin will generate an HTML5 file for you.
Otherwise you can define the location of your index.html file as a template.

## Generate Source Maps
Slide 21.
Since webpack bundles the code, Source Maps are mandatory to get a reference to the original file that raised an error, for example.
You tell webpack to generate source maps using the devtool property of the configuration.

devtool has many possible values, the most used probably are:

-none: adds no source maps
-source-map: ideal for production, provides a separate source map that can be minimized, and adds a reference into the bundle, so development tools know that the source map is available. Of course you should configure the server to avoid shipping this, and just use it for debugging purposes
-inline-source-map: ideal for development, inlines the source map as a Data URL

## Conclusion
Slide 22.
In conclusion I need to say that webpack is an extremely powerful and the most popular tool for modern development and you need to spend a lot of time for studying it.

Thanks a bunch for your attention!
