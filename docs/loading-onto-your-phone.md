# Loading Onto Your iPhone

_Caveat: Given continuously updating toolchains for MacOS, Xcode, golang, iOS and React Native this guide may need your help with updates!_

## Install Dependencies

Install Xcode from the App store.

Run `brew install go node`.

Ensure the GOPATH environment variable is set. 

If it's not, add the following to your `~/.bashrc`:
```
export GOPATH=$HOME/go
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```

Install gomobile
```
go get golang.org/x/mobile/cmd/gomobile
gomobile init
```

## Clone irma_configuration

In your folder with your dev projects:

`git clone https://github.com/InternetNZ/inz-demo-scheme`

## Checkout

Run `go get github.com/internetnz/irma_mobile`

Ignore the error about "no Go files"

## Setup Project

```
cd $GOPATH/src/github.com/internetnz/irma_mobile
go mod vendor
yarn install
```

If you get errors about installing fsevents during `yarn install`, run `npm rebuild fsevents` followed
by `yarn install`.

Install the irma_configuration:
`mkdir -p irma_configuration/inz-demo`
`cp -R <your path to the previously cloned inz-demo-scheme>/* irma_configuration/inz-demo/`

## Running the Project in the Simulator

```
cd $GOPATH/src/github.com/internetnz/irma_mobile
yarn start
```

Open Xcode.

Open the project at `$GOPATH/src/github.com/internetnz/irma_mobile/ios`.

From the menu, open Product > Destination > Add additional simulators.

Ensure "iPhone 8" is in the list on the left. If not, click the plus at the bottom of the list and add it.

From the menu, choose Product > Destination > iPhone 8.

From the menu, click Product > Run.

Once the project is running in the simulator, close it and move on to the next step.

## Running the Project on Your Phone

Open the project in Xcode.

(locations of IDE options and config will change with different versions, sorry)

From the menu, open View > Navigators > Show Project Navigator.

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
