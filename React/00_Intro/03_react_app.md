
fundamental React concepts that you’ll use frequently, including elements, components, and properties.

a nutshell, elements are instances of components that can be passed properties.

___

#### Creating a new React app

`$ npx create-react-app name-of-app`

>[!note]
>npx is a package runner tool that comes with npm. It
allows us to run commands using packages only present inside this project folder and/or run commands that will be downloaded dynamically when needed.

The command will create a new folder with the passed name, which is name-of-app. 

Inside this folder, the utility will initialize a new Git project, download the required resources for the application, and then download and locally install
all the dependencies required by the project.

```
npx create-react-app name-of-app

		npx requests create-react-app 
	creat-react-app is installed (if not present)
	npx creates a folder of given name
		npx requests dependencies
	dependencies are installed
```

```
cd name-of-app
npm start

	Compiler builds from source file
	Web server watches file system
	Local app is launched in browser

If source file is updated
	Compiler notices updated file
	Compiler rebuilds from fource files
	Web server notices updated files
	Local app is browser is updated
```

___

#### React Project Commands

A new React application created with CRA comes with these four commands:

* start - Launch a local development web server and continuously compile the project as it changes, serving it to any local browser.

* build - Compile all resources into a production-ready package deployable to the right web host.

* test - Launch a test runner that will run all unit tests defined in your project.

* eject - Reveal the inner workings of the project and make it fully configurable.

___

The `start` command will build your project in the background continuously using the development version of React and its utility libraries. This is distinct from the production version of React used in the build command. 

The development version of React includes much better error messages and warnings as well as options for debugging the application as it’s running in the browser. 

However, the development version of React is, for those reasons, also much larger in terms of sheer file size, so you don’t want to publish your application using this version. It will make your application unnecessarily large and hinder users trying to access it.

___

`build` is the command to run when you’re ready to see your application deployed to a real web server and have users try it out. When you run the build command, you’ll be using the production version of React, which is much leaner and optimized for deployment. The result of the build will be put in the `/build` folder.

___

`test` If you want to run all unit tests defined in your project, run this command. You can do that on the empty default template as well because the default template even comes with a default test file.

___

`eject` command can be a bit dangerous because it’s irreversible. If you eject your application, you’ll have access to a lot more configurable options inside the React setup than you do otherwise, but you also lose the option of automatically updating to newer versions of all the tools involved.

___

### File Structure

```
/
	public/
		index.html
	src/
		index.js
		App.js
	package.json
```

When you create a project with CRA, it almost always follows the same file structure. Custom templates can do things differently, but they rarely do.

The `public folder` is for files that will be served directly via the web server. This includes the index.html file that serves your entire application as well as binary files that you don’t want to bundle inside your application, such as content required by the index.html file directly (e.g., favicon, Cascading Style Sheets, fonts, or images for sharing) and large files (e.g., videos and images).


The `source (src) folder` is where all your bundled JavaScript will go as well as any other content that you want to bundle as a single package. 

This is mostly just JavaScript, but could potentially also include CSS, icons, small images, JSON files, and more. The bundling starts at the `index.js` file inside the source folder. 

It’s common place to have the main application reside in a file named `App.js`, but otherwise, you are free to be flexible here. 

Some templates structure the content inside the src folder in subfolders, which is necessary to structure larger projects.

___

`package.json` is the main configuration file for your project is , as required by npm and Yarn. This is the starting file for your project and defines the dependencies as well as the commands that you can run.


___

### Templates

If you want to create a web app using a specific technology stack or using React in a particular way, you probably want to use a different starting template to set you up correctly.

When you use CRA, you can specify a template to use.
```
$ npx create-react-app name-of-app --template name-of-template
```

You can only use the name of a template that already exists; if it doesn’t exist, the application will abort.

if you know that you want a specific setup or want to start your codebase at a certain state, you can use a template that sets you up for exactly that.

Minimal templates with even fewer features than the default one `--template minimal`. 
This one comes without images, CSS, tests, web vitals, and other minor niceness used in the default template.


`--template typescript` or `--template minimal-typescript`. This is useful for starting a new project using TypeScript.

Complex boilerplate setups created by other developers where you have a stack of certain dependencies already baked into your new application,
`--template redux-typescript`, which comes prepackaged with Redux and TypeScript, 

`--template rb`, which is a popular React boilerplate (hence the rb), that comes prepackaged with a ton of reputable libraries, including Redux with Redux-Saga, styled components, ESLint, husky, and many more.


> [!note]
> Template system for CRA is fully decentralized. Anyone can publish a package to npm and structure it in a way that allows you to use it as a base for your own applications.

___

#### Pros an Cons of CRA

Simplicity—You have less to worry about when setting up a new application. You get JavaScript XML (JSX) transpiling, bundling, testing, automatic reloading,
and more for free, without dealing with all the interdependencies.

Upgradability—You can easily upgrade to newer versions of React and all the other libraries used. Just run `npm install --exact react-scripts@VERSION` to upgrade your entire project to the specific version of React scripts. 

Community—With the deluge of available CRA templates and the easy path to making more, you can likely always find a premade template with just the right combination of tools so that you don’t have to deal with mixing them correctly.

Customization—On top of a variety of templates, you still have the option of adding all the other plugins and libraries that you need for your project. 
If your project interface with, Google Maps and Amazon Web Services (AWS), Just add their libraries, and you should be good to go.


Drawbacks

Understanding—Without setting the whole project up from scratch, you won’t know all that goes into such an endeavor. 

Control—You do lose control over which libraries are used. CRA currently uses webpack and BabelJS for JSX bundling and transpiling, but they’re by no means the only players around. Recently, tools such as esbuild, Bun, SWC, and Rome have emerged that partially cover the same ground, but you can’t easily switch to one of those. You’re stuck with the technology stack that CRA currently has chosen for you. 

Integration—If you want to integrate your application in a server-side setup, CRA currently can’t help you. For projects based on website frameworks as described
in the first chapter, you have to use the setups provided by those frameworks rather than CRA.

___

