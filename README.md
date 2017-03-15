# Mattermost plugin for integrating hangouts

**Most Code is from [this](https://github.com/suda/slack-hangout) repository. I just modified it to work with mattermost and added some features.**

## Installation / Configuration

You can ether use docker or just nodejs. However we recomend using docker to install and use this application.
First of all you need to get your client id and client secret from google. How you do this is specified below.
To use this application you ether need a valid domain and a server connected to this domain. If you dont have something like that you can use [Heroku](http://www.heroku.com). 

### Get the stuff from google console

1. Go to Google Developers Console
2. Create Project
3. In APIs & auth select APIs and set Calendar API to ON
4. In APIs & auth select Credentials and click Create new Client ID
  * Set Application Type to Web application
  * Set Authorized JavaScript Origins to your Heroku app URL
  * Set Authorized Redirect URI to your Server URL with /oauth2callback suffix (i.e. http://mydomain.com:5000/oauth2callback)
  * Click Create Client ID

### Docker

To use this repository with docker please follow this link [here](https://github.com/chitter99/mattermost-hangout-docker).

### NodeJS

1. Install NodeJS and NPM
 Just follow the instructions provided [here](https://howtonode.org/how-to-install-nodejs).

2. Download this repository or clone it with git.
 ```
 git init
 git clone https://github.com/chitter99/mattermost-hangout.git
 ```

3. Install dependencies
 To install all dependencies you can use the following command. Ensure you are in the directory where you downloaded this repository and you have installed npm.
 ```
 npm install
 ```
 After that you need to install one additional package with the following command.
 ```
 npm install dotenv
 ```

4. Configuration
 Create a file called ".env" (without the quotes) and enter the following.
 ```
 CLIENT_ID=
 CLIENT_SECRET=
 REDIRECT_URL=
 PORT=5000
 ```
 You now need to add your client id, client secret and redirect url from google. 
 If you want to you can enter a new port (the port must be the same on your redirect url. So if you change him here, change him also in your google console).

5. Start applicatoin
 To run this application only the following command is required.
 ```
 npm -r dotenv/config start
 ```
 If you want to you can put this in a batch, shell or bash file depending on your platform.

6. Link with Google Account
 The last thing you will need to do is link your Application with an Google Account.
 To do this open you Webbrowser and visit `http://<your-ip-or-domain>:5000/auth` and login with an Google Account.
 I recomend creating an extra Google Account, because all meetings will be scheduled as this User.
 When creating a new Google Account, open Google Calendar Settings and change `Automatically add video calls to events I create` to `true` on order to ensure this Application works.
 You can find this setting [here](https://calendar.google.com/calendar/render#settings-general_11).
