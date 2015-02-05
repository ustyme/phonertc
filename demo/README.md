# Clone the Repo
cd ~/github/ustyme
git clone git@github.com:ustyme/phonertc.git

# Start the signaling server
cd ~/github/ustyme/phonertc/demo/server ; npm install ; node index.js

# Install global Dependencies
npm install -g cordova bower grunt-cli

# Create the client-cordova project and copy the client code to it
cd ~/github/ustyme/phonertc/demo
cordova create client-cordova com.ustyme ClientCordova
cp -r client/ client-cordova/
cd client-cordova/

# Install client dependencies
npm install
bower install - if you get the following question, answer 1. If you don't get the question, you may have to run npm -g uninstall bower ; npm -g install bower
Unable to find a suitable version for angular-ui-router, please choose one:
    1) angular-ui-router#0.2.10 which resolved to 0.2.10 and is required by ionic#1.0.0-beta.12 
    2) angular-ui-router#~0.2.11 which resolved to 0.2.13 and is required by PhoneRTCDemoPrefix the choice with ! to persist it to bower.json

# Install client plugins
cordova plugin add org.apache.cordova.device ; cordova plugin add org.apache.cordova.console ; cordova plugin add https://github.com/alongubkin/phonertc.git

# Add client platforms
cordova platform add browser

# Build client
grunt build —force

# Run clients
cd ~/github/ustyme/phonertc/demo/client-cordova ; cordova run browser ; cordova run browser

# ----------------Important Notes-------------------
# the signaling server details for the client are stored in: ~/github/ustyme/phonertc/demo/client-cordova/app/scripts/signaling.js
# the turn server details for the client are stored in: ~/github/ustyme/phonertc/demo/client-cordova/app/scripts/CallCtrl.js
# to add android or other platforms: platform add android







