# JavaScript Project

TODO summary

## Project Setup

## Import/Export

## Third-Party Libraries/Frameworks

A programming language thrives with its ecosystem. In JavaScript land, the ecosystem with libraries and frameworks is mainly driven through Node.js and its packages (also called node packages, libraries, frameworks, third-party, dependencies, or as long term: third-party dependencies). Now even though Node.js is used for JavaScript in the backend, like we use it right now by just executing JavaScript on the command line and not inside a browser, the node package manager (npm) is available for JavaScript in the frontend (read: browser) too.

In this section, we will explore how to use the ecosystem to our benefit in our current setup. We will install one library via npm as third-party dependency to our project. Then we will import code (e.g. functions) from the library and use this code. Before we can install a library though, we have to initialize a project first. Go on the command line, stop your running project if neccessary, and initialize the project properly by typing:

```javascript
npm init -y
```

This setup has to be done only once per project and allows you to install packages afterward. Once the command went through successfully, you should see a *package.json* file in the same folder where all your libraries (here called dependencies) will get allocated:



https://lodash.com/docs/4.17.15

### Exercises: