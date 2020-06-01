## configure typescript
- yarn init -y
- yarn add typescript -D
- yarn tsc --init
    - change outDir to 'dist' and rootDit to 'src' in tsconfig.json file
    - [see documentation to run this](https://www.typescriptlang.org/) 
- yarn add ts-node-dev -D
    - this work transpiling automactilly and restarting server when the code is changed
    - add these settings to packages.json for use well typescript 
        ```json
              "scripts": {
                "build": "tsc",
                "dev:server": "ts-node-dev --inspect --transpileOnly --ignore-watch node_modules src/server.ts"
              },
    - --inspect server to improve debug on vscode
    - --transpileOnly is to not create js files and improve peformance in development
    - --ignore-watch node_modules (is to ignore changes on node_modules)
- install extension editorconfig and create your file on root of project
    - [see documentation](https://editorconfig.org/)
    
## configure eslint and prettier
- yarn add eslint
    - yarn eslint --init
    - see after configurations if has any more configuration on console (maybe have to install more things if eslint request)
- install eslint extension vscode
    - [see at this repository for vscode settings](https://github.com/xdeni/commands/blob/master/vscode.settings.json)
- configure eslintconfig
    - [see at this repository for eslintrc.json](https://github.com/xdeni/commands/blob/master/eslintrc.json)
- configure eslintignore
    - add these
        ```md
            node_modules
            dist
- add prettier
    - at console run this command
        ```console
            sudo yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
   - for use with eslint use same settings.json that was inputed before 
   - add file prettier.config.js for not conflict with eslint
        [here is](https://github.com/xdeni/commands/blob/master/prettier.config.js)

## configure debugging
- goto bug/play icon
    - click on create lauch file, anything that
    - and use those configurations
        ```json
            {
              "version": "0.2.0",
              "configurations": [
                {
                  "type": "node",
                  "request": "attach",
                  "protocol": "inspector",
                  "name": "Denug",
                  "skipFiles": [
                    "<node_internals>/**"
                  ],
                  "outFiles": [
                    "${workspaceFolder}/**/*.js"
                  ]
                }
              ]
            }
## how make the terminal awesome with zsh and more
   - https://blog.rocketseat.com.br/terminal-com-oh-my-zsh-spaceship-dracula-e-mais/
