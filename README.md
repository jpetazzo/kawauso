Kawauso
======
A Simple Otter Example Deployed on Heroku
Visit http://kawauso.herokuapp.com

Prerequisite
------
Assuming that a reader basic knows of git and npm.

Setup
------

Install [otter](https://github.com/bfirsh/otter) by

```
$ git init
$ npm init
$ npm install --save otter
```
Specify node / npm [versions](https://devcenter.heroku.com/articles/nodejs-versions) in package.json to match your development enviroment.

```package.json
{
  "name": "otter-example",
  "version": "0.1.0",
  "dependencies" : {
    "otter": "*"
  },
  "engines": {
    "node": "0.8.x",
    "npm":  "1.2.x"
  }
}
```
Copy the provided example to app/

```
$ cp -r node_modules/otter/example app
```
Procfile

```Procfile
web: ./node_modules/.bin/otter -a api.twitter.com -p $PORT ./app/
```

Run test with foreman if you wish.

```
$ foreman start
09:54:23 web.1     | started with pid 4124
09:54:24 web.1     | Server started on port 5000.
```

Commit everything if it looks alright.

```
$ git add .
$ git commit -m "ready for deploy"
```
Create an app on heroku.
* Install heroku [toolbelt](https://toolbelt.heroku.com) if you don't have one.
* Read [this](https://devcenter.heroku.com/articles/keys) if heroku complains about ssh key.

```
$ heroku login
$ heroku create
Creating sharp-rain-871... done, stack is cedar
http://sharp-rain-871.herokuapp.com/ | git@heroku.com:sharp-rain-871.git
Git remote heroku added
```

Deploy
------

```
$ git push heroku master
```