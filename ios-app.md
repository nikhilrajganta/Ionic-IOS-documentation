# Step 1 : Install Prerequisites

## 1.1 Install Node.js

- Download and install the latest LTS version of Node.js from Node.js official website, as it is required for running Ionic applications.

## 1.2 Install Ionic CLI

- Open your terminal and install the Ionic CLI globally using npm:

```bash
npm install -g @ionic/cli
```

- This command allows you to create and manage Ionic projects from the command line.

## 1.3 Install CocoaPods

- Ensure CocoaPods is installed for managing iOS dependencies. If not already installed, you can install it using:

```bash
sudo gem install cocoapods
```

- CocoaPods is essential for integrating third-party libraries into your iOS project.

# Step 2 : Create a New Ionic Angular Project

## 2.1 Start a New Ionic Project

- In your terminal, create a new Ionic project using the blank template:

```bash
ionic start myApp blank --type=angular
```

- Replace myApp with your desired project name; this initializes a new Ionic Angular application.

## 2.2 Navigate to Project Directory

- Change into your newly created project directory:

```bash
cd myApp
```

- This sets your terminal context to the new project folder.

# Step 3: Add iOS Support with Capacitor

## 3.1 Install Capacitor

- Install Capacitor in your project by running:

```bash
npm install @capacitor/core @capacitor/cli
```

- Capacitor allows you to build native mobile applications using web technologies.

## 3.2 Initialize Capacitor

- Initialize Capacitor with your app name and package ID:

```bash
npx cap init myApp
```

- This command sets up the necessary configuration files for Capacitor.

## 3.3 Add iOS Platform

- Add the iOS platform to your project:

```bash
npx cap add ios
```

- This command creates an iOS directory within your project for native development.

# Step 4: Install Ruby and Configure CocoaPods

## 4.1 Install RVM and Ruby

-To manage Ruby versions, install RVM (Ruby Version Manager) and Ruby:

```bash
\curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install 2.7.6
```

- RVM allows you to easily install and manage Ruby versions on your system.

## 4.2 Install CocoaPods Again (if needed)

- If CocoaPods was not installed previously, do so now:

```bash
sudo gem install cocoapods
```

- This installs CocoaPods, which is necessary for managing iOS dependencies.

## 4.3 Verify CocoaPods Installation

- Check that CocoaPods is installed correctly:

```bash
pod --version
```

- This command displays the installed version of CocoaPods to confirm successful installation.

# Step 5: Build the App

## 5.1 Build Your Ionic Project

- Compile your Ionic project to generate web assets:

```bash
ionic build
```

- This command prepares your app for deployment by building the necessary files.

## 5.2 Sync Built Assets with iOS Project

- Copy the built web assets to the native iOS project:

```bash
npx cap copy ios
```

- This ensures that your latest changes are reflected in the iOS app.

# Step 6: Open the Project in Xcode

## 6.1 Open iOS Project in Xcode

- Launch Xcode with the iOS project:

```bash
npx cap open ios
```

- This opens the native iOS project in Xcode for further development and testing.

# Step 7: Run the App in an Emulator

## 7.1 Select a Simulator in Xcode

- Choose a simulator from the device dropdown menu at the top of Xcode.
  This allows you to run your app on a virtual device that mimics an iPhone or iPad.

## 7.2 Build and Run Your App

- Click the `Run` button (the play icon) in Xcode.
  This compiles your app and launches it in the selected simulator for testing.
  Alternatively, run directly from the command line with live reloading:

```bash
npx cap run ios
```

- This command launches your app in a simulator while allowing live reloading of code changes.

# Troubleshooting CocoaPods Installation Issues

- If you encounter issues while installing CocoaPods, follow these steps:

## A. Clean Up RVM Installation

- Update RVM to ensure you have the latest version:

```bash
rvm get stable --auto-dotfiles
```

- Keeping RVM updated can resolve many installation issues.

## B. Reinstall Ruby with Specific Flags

- Reinstall Ruby with paths for OpenSSL and Readline:

```bash
rvm reinstall 2.7.6 --with-openssl-dir=$(brew --prefix openssl@1.1) --with-readline-dir=$(brew --prefix readline)
```

- This ensures that Ruby is compiled with the correct dependencies.

## C. Upgrade Homebrew Packages

- Upgrade Homebrew packages to ensure compatibility:

```bash
brew upgrade
sudo chown -R $(whoami) /usr/local
sudo chmod -R u+rwX /usr/local
sudo brew upgrade
```

- Upgrading Homebrew can help resolve dependency issues.

## D. Install Required Libraries

- Install additional libraries required by CocoaPods:

```bash
brew install openssl readline libyaml gdbm libffi
```

- These libraries are often needed for various gems used by CocoaPods.

## E. Set Environment Variables

- Set environment variables for OpenSSL and Readline:

```bash
export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib -L/usr/local/opt/readline/lib"
export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include -I/usr/local/opt/readline/include"
export PKG_CONFIG_PATH="/usr/local/opt/openssl@1.1/lib/pkgconfig:/usr/local/opt/readline/lib/pkgconfig"
```

- These variables inform Ruby about where to find necessary libraries during installation.

## F. Reinstall Ruby Again

- Reinstall Ruby again with updated flags if needed:

```bash
rvm reinstall 2.7.6 --with-openssl-dir=$(brew --prefix openssl@1.1) --with-readline-dir=$(brew --prefix readline)
```

- This ensures that Ruby has access to all required libraries correctly configured.

## G. Install CocoaPods Again

- Finally, attempt to install CocoaPods again:

```bash
sudo gem install cocoapods
```

- Reinstalling may resolve any previous installation issues encountered.

- By following these steps, you will successfully create an Ionic Angular project, add iOS support using Capacitor, manage Ruby and CocoaPods installations, and troubleshoot any potential issues effectively.
