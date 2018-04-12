# Zilliqa-Wallet

This project is experimental and still under development.

## Setup

- Nodejs and NPM must be installed on your system; run the following commands:
- `curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -`
- `sudo apt-get install nodejs`
- Navigate to root directory and run the following:
- `sudo npm install -g @angular/cli`
- `npm install`
- `ng serve`

## Running the Zilliqa Wallet

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.


## Desktop App (Linux, Mac, and Windows)

Zilliqa Wallet uses `electron` and `electron-packager` to generate desktop apps from the source code.

TODO - recaptcha does not currently work in electron without some hacks. Temp fix - delete the text `|| !this.recaptchaFilled` around line 112 in `src/app/wallet/walletsend/walletsend.component.ts`, to disable the recaptcha check.

The NODE_URLS in src/app/constants.ts should also be updated before packaging the app.

#### For debugging
Run `ng serve` on one terminal and `npm run electron` on a separate terminal. This uses the `electron.dev.js` config file, in the other cases `electron.prod.js` is used.

#### Generate for Mac
Execute the command
```
npm run package:osx
````
This will generate an .app file in **packages/z-wallet-0.0.1-darwin-x64/**. 

To create a .dmg installer, run 
```
npm install -g electron-installer-dmg appdmg
``` 
then execute 
```
electron-installer-dmg packages/z-wallet-0.0.1-darwin-x64.app "Zilliqa-Wallet"
``` 
to create the .dmg file.

#### Generate for Linux
Execute the command
```
npm run package:linux
```
This will create several folders in **packages/** for different architectures, each containing the executable **./z-wallet-0.0.1**.

To package into a .deb file, run 
```
npm install -g electron-installer-debian
``` 
then execute  
```
electron-installer-debian --src packages/z-wallet-0.0.1-linux-x64/ --dest destName/ --arch x64
```
Change the `--src` and `--arch` flags to generate for different architectures.

#### Generate for Windows
If building from a non-windows platform, see [this link](https://github.com/electron-userland/electron-packager#building-windows-apps-from-non-windows-platforms) for instructions. You would have to install [Wine](https://wiki.winehq.org/Download) and other dependencies - `brew cask install xquartz`, `brew install wine mono` for MacOS.

Execute the command
```
npm run package:win
```
to generate the **packages/z-wallet-0.0.1-win32-x64/** folder.

To create a single setup.exe, run 
```
npm install -g electron-installer-windows
``` 
after the files are generated, rename **z-wallet-0.0.1-win32-x64/z-wallet-0.0.1.exe** to **z-wallet.exe**. Then execute
```
electron-installer-windows --src packages/z-wallet-0.0.1-win32-x64/ --dest destName/
``` 
to create the .exe file.


## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Licence 
You can view our [licence here](https://github.com/Zilliqa/Zilliqa-Wallet/blob/master/LICENSE).
