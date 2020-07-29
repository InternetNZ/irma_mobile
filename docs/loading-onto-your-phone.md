# Loading Onto Your Phone

## Install Dependencies

Install Xcode from the App store.

Run `brew install go node dep yarn`.

Ensure the GOPATH environment variable is set. 

If it's not, add the following to your `~/.bashrc`:
```
export GOPATH=$HOME/go
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```

## Checkout

Run `go get github.com/internetnz/irma_mobile`

## Setup Project

```
cd $GOPATH/src/github.com/internetnz/irma_mobile
dep ensure
yarn install
```

## Running the Project in the Simulator

```
cd $GOPATH/src/github.com/internetnz/irma_mobile
yarn start
yarn run ios
```

Once the project is running in the simulator, close it and move on to the next step.

## Running the Project on Your Phone

Open the project in Xcode.

(locations of IDE options and config will change with different versions, sorry)

Open Project Settings by clicking on the "IRMA" project.

Choose the "Signing and Capabilities" tab.

Scroll all the way down and (if it exists) remove all "associated domains" and the containing options box.

Change the "Team" to your Apple ID. If you don't have an Apple ID set up in Xcode, click the team dropdown and click add account.

You can make a new account with your work email if you don't want to add your personal Apple account to your work laptop.

You should now be done with the Project Settings.

Plug in your phone, if you haven't already. Click "Trust".

Your phone should be an option in the dropdown of devices (right half of box with "IRMA" in the left). Select it.

Choose "IRMA-Release".

Click the Play button to build and deploy to your phone.

The app may not start up right away on your phone, due to trust. To trust apps created by your Apple ID, open "Device Management" in
Settings and click to trust your account.
