# jest-unit-test-configuration

## Configure launch.json File for your test framework
#### Click on the Debugging icon in the Activity Bar to bring up the Debug view. Then click on the gear icon to configure a launch.json file, selecting Node for the environment:

#### Replace content of the generated launch.json with the following configurations:
```
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Jest All",
      "program": "${workspaceFolder}/node_modules/.bin/jest",
      "args": ["--runInBand"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen",
      "disableOptimisticBPs": true,
      "windows": {
        "program": "${workspaceFolder}/node_modules/jest/bin/jest",
      }
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Jest Current File",
      "program": "${workspaceFolder}/node_modules/.bin/jest",
      "args": [
        "${fileBasenameNoExtension}",
        "--config",
        "jest.config.js"
      ],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen",
      "disableOptimisticBPs": true,
      "windows": {
        "program": "${workspaceFolder}/node_modules/jest/bin/jest",
      }
    }
  ]
}
```
## Configure package.json File for your test framework
#### Add following Jest configuration to package.json:
```
"jest": {
   "testEnvironment": "node"
}
```
#### test:debug command
```
"test:debug": "node --inspect-brk node_modules/.bin/vue-cli-service test:unit --no-cache --watch --runInBand"
```
#### Note for windows users : if node_modules/jest is not available in your project, but node_modules/jest-cli is installed (e.g. if you are using react-boilerplate) you can replace the windows attribute by this one for both launch configurations :
```
"windows": {
  "program": "${workspaceFolder}/node_modules/jest-cli/bin/jest",
}
```