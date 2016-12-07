## Repositories

----------

### Add a Git Project
- Open project
- Select project with git enabled
- After it loads an icon confirms it is git compatible

----------

### Clone a project
- Open project
```
  File -> Import -> Git -> Project from Git
  ```
- Chose clone URI
- Look for the URI of your project and paste it on the window
- If you don't have a credential set stored add one now
- Import using a new project wizard
- Choose to create a project from existing source and select the cloned git
project

----------
### New Project with Git Enabled
- Create a project
- Right click on the project
```
  Team -> Share Project
```
- Create. Leave the path and add the project's name
- Add changes to index and make your first commit to kick off the master branch

----------
### Adding a Remote
- Press on the cloud and up arrow icon
- If no remote is setup you'll get a config window
- Stick with the origin name
- Add URL, protocol and credentials

----------

### Troubleshooting
- Some certificates are not accepted such as self signed certs
```
  git config --global http.sslVerify "false"
```  
- Please consider the security implication of using this approach
