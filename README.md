# Education_Pathways
# F2022-EP-Janelle
This repo is a clone of https://github.com/ECE444-2022Fall/Assignment_1_starter_template

(These are the lab3 screenshots)
### Activity 1
<img width="354" alt="image" src="https://user-images.githubusercontent.com/46268176/193141875-b61ef71c-c71a-4f96-a931-c45127011aef.png">

### Activity 2
<img width="476" alt="image" src="https://user-images.githubusercontent.com/46268176/193147567-75c51495-c151-46bc-9b1d-f98b67cf98b6.png">

### Activity 3
<img width="753" alt="image" src="https://user-images.githubusercontent.com/46268176/193147707-6df24027-d212-4a78-ac8e-76991c6285ea.png">
<img width="602" alt="image" src="https://user-images.githubusercontent.com/46268176/193147936-64c4168b-b074-4c14-85cc-7c4efd3f301e.png">

# Assignment 1: Education Pathway

This is a modified version of the previous Assignment1 template.

The deploye version can be found at https://lab3-docker.herokuapp.com.

## Changes
+ Removed hardcodes of backend urls.
+ Removed hardcodes of database, and replace the database with dummy static data.


## How to run it locally

+ Enter the repo directory
+ Create a virtual environment if you haven't done this before. Activate it. 
```powershell
# Windows
py -3 -m venv venv
venv\Scripts\activate

# For Mac and Linux, please check the link: https://flask.palletsprojects.com/en/2.2.x/installation/
```
+ Install dependencies (if you haven't done this before).
```powershell
pip install -r requirements.txt
```
+ Enter the `Education_Pathways/` directory, run the backend
```powershell
flask --app index --debug run
```
+ Enter the `Education_Pathways/frontend/` directory
+ Make sure the `baseURL` is set as `localhost:5000`
```javascript
# Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "http://localhost:5000/"
});
```
+ Make sure the proxy link in package.json is set as "http://localhost:5000/"
```json
// Part of Education_Pathways\frontend\package.json
"private": true,
"proxy": "http://localhost:5000/",
```

+ Build and run the frontend:
```powershell
npm run build
npm start
```
+ Then you will see the application at `localhost:3000`


## Build and run with Docker

For detailed instructions on Docker, please refer to the documents for Lab3 on Quercus.

+ Change the proxy link in package. Remember to change it back to "http://localhost:5000/"
```json
// Part of Education_Pathways/frontend/package.json
"private": true,
"proxy": "http://host.docker.internal:5000/",
```

```powershell
# Under the root directory
docker compose up --build
```

## How to deploy (not required for lab3)

Please make sure everything works well before you run it with docker.

+ Make sure the baseURL is set as [URL to your deployed project]
```javascript
// Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "[URL to your deployed project]" -- baseURL for deployment
});
```
+ Re-build the frontend to update the baseURL
```powershell
# Under the frontend/ directory
npm run build
```
+ Deploy your changes to heroku
```powershell
git push heroku main
```

4.6 (`optional`) Add the requirements:

```
Flask==2.1.1
gunicorn==20.0.4
pytest==7.1.2
```

4.7 (`optional`) Create a *.gitignore* file in the project root:

```sh
$ touch .gitignore
```

4.8 (`optional`) And include the following files and folders (so they are not included in version control):

```sh
env
*.pyc
*.DS_Store
__pycache__
test.db
```

4.9 (`optional`) To specify the correct Python runtime, add a new file to the project root called *runtime.txt*:

```
python-3.10.4
```

4.10 (`optional`) Add a local Git repo:

```sh
$ git init
$ git add -A
$ git commit -m "initial"
```

4.11 Login to your Heroku account

```sh
$ heroku login
```

4.12 Deploy to Heroku, give your application a name on Heroku, for example, we name it `myapp-unique-name` here:

```sh
$ heroku create myapp-unique-name
```
4.13 Then set your heroku remote to the application you just created
```sh
$ heroku git:remote -a myapp-unique-name
```
4.14 Commit your local repo to Heroku remote
```sh
$ git add .
$ git commit -am "inital commit to heroku remote"
$ git push heroku main
```

4.15 Then to view the deployed app online, run the following command to open the webpage in your default browser.

```sh
$ heroku open
```
or go to your [Heroku account](https://dashboard.heroku.com/apps) and check your the url of your deployed app. (`https://myapp-unique-name.herokuapp.com/`)
