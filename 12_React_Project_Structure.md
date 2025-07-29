## React Project Structure:

### .gitignore & README.md:
* These files are reload to GIT integration, if we want to move our ReactJS Application to Central Repository by using GIT at that time we use these files.

### package.json:
* One of the most important file in our project.
* Whenever we try to create application, at that time ReactJS engine downloads some libraries, to download those libraries it will create Package.json.
* In simple, if we need any library in our project that library for our application it must be placed in package.json.
* This file contains dependencies and scripts required for our project. We can see which type React version we are using.
* helps npm rebuild the app on another machine. Or if we delete the node modules folder with all the files that our project needs to run, the package-loc.json file has all the information for npm to be able to rebuild those files reliably. This file is there to ensure the npm tracks all the modules installations properly.

### package-lock.json:
* They maintain all Installed Dependencies Information.

### node_modules:
* It is generated when we run "create react app".
* The node modules folder is automatically added when we install a specific npm package
* Developers use packages when they want to add a piece of functionality that someone else coded and made available to other developers via the npm ecosystem.

### public:
1. favicon.ico 
2. index.html 
3. logo192.png 
4. logo512.png 
5. manifest.json 
6. robots.txt
* It contains the assets that will be displayed to the user in our app.
* For example, image files for logos, the favicon, which displays an icon in the browser tab, and the robots.txt file, which is used for search engine optimization.
* Also, there is a manifest.json file, which is used to provide some metadata to a device when you're React powered web app is installed on it. 

### index.html:
* It is Most Important and Only html file in our entire application. We are building single page application and this is that single page.
* The view may be dynamically changed in browser but this is the file that provides VIEW.
* we are not responsible to control the UI that is taken care by ReactJS. For that purpose we have one DIV Tag with `id="root"`.
* At runtime React Application take over this div tag and it ultimately Responsible for the UI.

### src:
In this folder we place all the Heart of our Application, we place complete code in this folder.
| files | Description |
| :---: | :---------: |
| index.js | This is the Javascript entry point or Starting point for our React Application, whenever we give npm start, it starts from Here... |
| App.js | This is the App Component, represents the `View` that we have seen on Browser |
| App.test.js | This is for simple Test cases |
| App.css | This file is for Styling. The css file contain class which are applied to app component |
| index.css | we also have index.css file which apply styles for body tag |
| logo.svg | which is referred in app component |

