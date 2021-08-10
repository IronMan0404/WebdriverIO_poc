Step 1: Creating a New Folder (Ex: WebdriverIOTypScript)
Navigate to any of your drives. Create a fresh new folder (Ex: WebdriverIOTypescript).

Step 2: Creating a Package.json for Your WebdriverIO Project
Create a pacakge.json file.

In your newly created Project Folder, open the command prompt and type:

npm init


Step 4: Installing the WebdriverIO Command Line Interface, Also Known as WDIO CLI

npm install - save-dev @wdio/cli

Step 5: Setting Up the WebdriverIO for Your End to End Test Automation Project

npx wdio config


Step 6: Creating the Directory Structure for the WebdriverIO Typescript Project

-test
--pages
--specs

Step 7: Installing the Typescript and ts-node npm Packages for the WebDriverIO Project

npm install typescript ts-node --save-dev


Step 8: Creating the tsconfig.json File for the WebdriverIO Project

npx tsc --init


Step 9: Configuring the tsconfig.json File in the WebdriverIO Project
Remove the default generated code, and replace it with the below code in tsconfig.json:

`{
  "compilerOptions": {
    "target": "es2019",
    "types": [
      "node",
      "webdriverio/sync",
      "@wdio/jasmine-framework"
    ]
  },
  "include": [
    "./test/**/*.ts",
  ]
} `


Step 10: Configuring the wdio.conf.ts File


`export const config: WebdriverIO.Config = {
 
 specs: [
        './test/**/*.ts'
    ],
 capabilities: [{
        browserName: 'chrome', 
        maxInstances: 1,       
    }],    
    framework: 'Jasmine',  
    jasmineOpts: {
        defaultTimeoutInterval: 120000,
    },
    autoCompileOpts: {
        autoCompile: true,
        // for all available options
        tsNodeOpts: {
            transpileOnly: true,
            project: 'tsconfig.json'
        },
    }
}`


Step 13: Executing the WDIO Typescript Tests
Once you have completed all the above tests, run your tests with the below command:

npx wdio run ./wdio.conf.ts


npx wdio run wdio.conf.js



##########################################



--help                prints WebdriverIO help menu                   [boolean]
--version             prints WebdriverIO version                     [boolean]
--hostname, -h        automation driver host address                  [string]
--port, -p            automation driver port                          [number]
--user, -u            username if using a cloud service as automation backend
                                                                        [string]
--key, -k             corresponding access key to the user            [string]
--watch               watch specs for changes                        [boolean]
--logLevel, -l        level of logging verbosity
                            [choices: "trace", "debug", "info", "warn", "error", "silent"]
--bail                stop test runner after specific amount of tests have
                        failed                                          [number]
--baseUrl             shorten url command calls by setting a base url [string]
--waitforTimeout, -w  timeout for all waitForXXX commands             [number]
--framework, -f       defines the framework (Mocha, Jasmine or Cucumber) to
                        run the specs                                   [string]
--reporters, -r       reporters to print out the results on stdout     [array]
--suite               overwrites the specs attribute and runs the defined
                        suite                                            [array]
--spec                run only a certain spec file - overrides specs piped
                        from stdin                                       [array]
--exclude             exclude spec file(s) from a run - overrides specs piped
                        from stdin                                       [array]
--mochaOpts           Mocha options
--jasmineOpts         Jasmine options
--cucumberOpts        Cucumber options
