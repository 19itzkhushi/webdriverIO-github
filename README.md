# Run Selenium Tests With WebDriverIO 5.6.2 — TestMu AI (Formerly LambdaTest)

![JavaScript](https://user-images.githubusercontent.com/95698164/172134732-2e9c780e-10ac-4956-b366-86ffc25bf070.png)

<p align="center">
  <a href="https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/@TestMuAI" target="_bank">YouTube</a>
</p>
&emsp;
&emsp;
&emsp;

*Learn how to use WebDriverIO 5.6.2 framework to configure and run your JavaScript automation testing scripts on the TestMu AI platform*

[<img height="58" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

## Table Of Contents

* [Pre-requisites](#pre-requisites)
* [Installing Selenium Dependencies](#installing-selenium-dependencies)
* [Getting Started](#getting-started)
* [Execute The Test](#execute-the-test)

## Pre-requisites 

Before getting started with Automated Scripts using Selenium with WebDriverIO 5.6.2 on TestMu AI Automation, you need to:

* The first step is to download and install node.js and node package manager or npm. You should be having nodejs v6 or newer. Click [here](https://nodejs.org/en/) to download.
* Make sure to use the latest version of JavaScript.
* Make sure you have WD installed in your system, you can install it using the below command through npm:

`npm install webdriverio`

* Download [Selenium JavaScript bindings](http://www.seleniumhq.org/download/) from the official Selenium website.
* Once you download the JavaScript bindings, extract the ZIP file which you’ve downloaded. * After extracting the file, you need to add Selenium Java bindings which is a JAR file and all the dependent libraries to your classpath.

## Installing Selenium Dependencies

Next step is to install Selenium dependencies for Node.js using npm. Here’s the command to run:

`npm i selenium-webdriver`

* Download TestMu AI tunnel binary file if you wish to test your locally hosted or privately hosted projects.

> Follow our documentation on TestMu AI tunnel to know it all. OS specific instructions to download and setup tunnel binary can be found at the following links.
 * [Documentation For Windows User](https://www.testmuai.com/support/docs/local-testing-windows/)
 * [Documentation For Mac User](https://www.testmuai.com/support/docs/local-testing-macos/)
 * [Documentation For Linux User](https://www.testmuai.com/support/docs/local-testing-linux/)

> Download the binary file of:
 * [TestMu AI tunnel for Windows](https://downloads.lambdatest.com/tunnel/v3/windows/64bit/LT_Windows.zip)
 * [TestMu AI tunnel for Mac](https://downloads.lambdatest.com/tunnel/v3/mac/64bit/LT_Mac.zip)
 * [TestMu AI tunnel for Linux](https://downloads.lambdatest.com/tunnel/v3/linux/64bit/LT_Linux.zip)

## Getting Started

Running WebDriverIO 5.6.2 test scripts on TestMu AI [Selenium Grid](https://www.testmuai.com/blog/why-selenium-grid-is-ideal-for-automated-browser-testing/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium) is as easy as changing a few lines of code. To start with, you would have to invoke Selenium remote webdriver instead of local browser webdriver. In addition, since we are using remote webdriver, we have to define which browser environment we want to run the test. We do that by passing browser environment details to TestMu AI Selenium Grid via desired capabilities class. You can use [TestMu AI Capabilities Generator](https://www.testmuai.com/capabilities-generator/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium) to select & pass those browser environment specifications.

Let’s check out sample WebDriverIO 5.6.2 framework code running TestMu AI Selenium Grid. This is a simple WebDriverIO 5.6.2 automation script that test a sample to-do list app. The code marks two list items as done, adds a list item and then finally gives the total number of pending items as output.

You can also find this code at our [GitHub repository for WebDriverIO](https://github.com/LambdaTest/webdriverio-selenium) 5.6.2.
``` js
var assert = require('assert');
 
describe('Lambdatest Demo Test', function() {
  it('Lambdatest Demo TestCase', function () {
    browser
      .url('https://lambdatest.github.io/sample-todo-app/')
      .click('*[name="li1"]')
      .click('*[name="li2"]')
      .setValue('*[id="sampletodotext"]','Lambdatest\n');
     
    assert(browser.getTitle().match(/Sample page - lambdatest.com/i));
  });
});
```

Below is the config.js file where we will be declaring the desired capabilities.

``` js
user= process.env.LT_USERNAME || "<your username>",
key= process.env.LT_ACCESS_KEY || "<your accessKey>",
 
exports.config = {
 
  updateJob: false,
  user,
  key,
  specs: [
    './tests/specs/single_test.js'
  ],
  exclude: [],
 
  capabilities: [{
    browserName: 'chrome',
    version:"64.0",
    name:"Test webdriverio",
    build:"build 1",
  }],
  sync: true,
  logLevel: 'info',
  coloredLogs: true,
  screenshotPath: './errorShots/',
  baseUrl: '',
  waitforTimeout: 100000,
  connectionRetryTimeout: 90000,
  connectionRetryCount: 1,
  path: '/wd/hub',
  hostname: 'hub.lambdatest.com',
  port: 80,
 
  framework: 'mocha',
  mochaOpts: {
      ui: 'bdd'
  }
}
```

The Selenium WebDriver test would open a URL, mark the first two items in the list as done, add an item in the list, and return the total number of pending item. Your results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on [TestMu AI dashboard](https://accounts.lambdatest.com/dashboard/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium). TestMu AI dashboard will help you view all your text logs, screenshots and video recording for your entire Selenium tests.

## Execute The Test

You would need to execute the below command in your terminal/cmd.

`npm run single`

## Tutorials 📙

Check out our latest tutorials on TestNG automation testing 👇

* [How To Generate HTML Reports With WebdriverIO?](https://www.testmuai.com/blog/webdriverio-html-reporter/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [How To Use Deep Selectors In Selenium WebdriverIO](https://www.testmuai.com/blog/deep-selectors-in-selenium-webdriverio/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [Cross Browser Testing With WebDriverIO [Tutorial]](https://www.testmuai.com/blog/webdriverio-tutorial-with-examples-for-cross-browser-testing/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [How To Speed Up JavaScript Testing With Selenium and WebDriverIO?](https://www.testmuai.com/blog/speed-up-javascript-testing-with-selenium-and-webdriverio/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [WebDriverIO Tutorial: Handling Alerts & Overlay In Selenium](https://www.testmuai.com/blog/webdriverio-tutorial-handling-alerts-overlay-in-selenium/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [WebdriverIO Tutorial: Run Your First Automation Script](https://www.testmuai.com/blog/webdriverio-tutorial-run-your-first-automation-script/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [WebDriverIO Tutorial For Handling Dropdown In Selenium](https://www.testmuai.com/blog/webdriverio-tutorial-for-handling-dropdown-in-selenium/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [WebdriverIO Tutorial: Browser Commands for Selenium Testing](https://www.testmuai.com/blog/webdriverio-tutorial-browser-commands-for-selenium-testing/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [Automated Monkey Testing with Selenium & WebDriverIO (Examples)](https://www.testmuai.com/blog/monkey-testing-with-webdriverio/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [Selenium WebdriverIO Tutorial](https://www.testmuai.com/blog/webdriverio-tutorial-with-examples-for-selenium-testing/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [How To Use Strings In JavaScript With Selenium WebDriver?](https://www.testmuai.com/blog/using-strings-in-javascript-using-selenium-webdriver/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)

## Documentation & Resources :books:
 
Visit the following links to learn more about TestMu AI's features, setup and tutorials around test automation, mobile app testing, responsive testing, and manual testing.

* [TestMu AI Documentation](https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [TestMu AI Blog](https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)
* [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium)    

## TestMu AI Community :busts_in_silhouette:

The [TestMu AI Community](https://community.testmuai.com/?utm_source=github&utm_medium=repo&utm_campaign=webdriverio-selenium) allows people to interact with tech enthusiasts. Connect, ask questions, and learn from tech-savvy people. Discuss best practises in web development, testing, and DevOps with professionals from across the globe 🌎

## What's New At TestMu AI ❓

To stay updated with the latest features and product add-ons, visit [Changelog](https://changelog.lambdatest.com/)

## 🚀 LambdaTest is Now TestMu AI

👋 Welcome to TestMu AI, the next evolution of LambdaTest. As of January 2026, [LambdaTest is Now TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/) - we have evolved from a cross-browser testing cloud into a unified, AI-native quality engineering platform designed for the modern DevOps era.

Whether you have been part of the LambdaTest community for years or are just discovering TestMu AI, our mission remains the same: to help you ship faster with high-scale test execution, autonomous testing, and deep quality analytics.

**🔄 Our Rebrand Journey**

We chose the name TestMu AI to reflect our shift towards intelligent, autonomous testing. While our identity has changed, our core technology and commitment to the testing community stay the same.

👉 Find [LambdaTest's New Home](https://www.testmuai.com/).

**🔭 Explore TestMu AI**

The same infrastructure LambdaTest customers relied on, now delivered through autonomous AI agents.

- [KaneAI](https://www.testmuai.com/kane-ai/)
- [Agent-to-Agent Testing](https://www.testmuai.com/agent-to-agent-testing/)
- [HyperExecute](https://www.testmuai.com/hyperexecute/)
- [Real Device Cloud](https://www.testmuai.com/real-device-cloud/)
- [Pricing](https://www.testmuai.com/pricing/)
- [Documentation](https://www.testmuai.com/support/docs/)