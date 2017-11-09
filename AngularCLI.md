# git-cheats

## Angular CLI
 
1--to install angular-cli-ghpages package (used for building and displaying your webpage on github):
* npm i -g angular-cli-ghpages
* npm i --save-dev angular-cli-ghpages

2--to build the Angular project (Creates a /dist folder. Adding the production flag, makes use of uglifying and tree-shaking)
* ng build
* ng build --prod 

3--to build the angular project for github using angular cli 
* ng build --prod --base-href https://alextelespanwork.github.io/my-cool-proj/

#### Deploying your build

4--!!!You're only able to use the angular-cli-ghpages CLI if you have a /dist folder. If you do, you can then run: 
* ngh  
* ngh --no-silent  (this spits out more logging)
* ngh --message="First deploy" (add a message to the commit when deploying)
* ngh --branch=production (specify which branch to deploy)
* ngh --dry-run (dry run before actually deploying to see the output)

The Single-Page App Hack for GitHub Pages (You might get 404 Not Found without this hack)
http://www.backalleycoder.com/2016/05/13/sghpa-the-single-page-app-hack-for-github-pages/

-- In order to see your page after you've built it, go to your project on github => Settings => Options => Github Pages => Change the Source to gh-pages branch