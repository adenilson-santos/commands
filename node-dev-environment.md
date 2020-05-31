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
        `
    - --inspect server to improve debug on vscode
    - --transpileOnly is to not create js files and improve peformance in development
    - --ignore-watch node_modules (is to ignore changes on node_modules)
- install extension editorconfig and create your file on root of project
    - [see documentation](https://editorconfig.org/)
    
## configure eslint
- yarn add eslint
    - yarn eslint --init
    - see after configurations if has any more configuration on console (maybe have to install more things if eslint request)
- install eslint extension vscode
    - [see at this repository for vscode settings]()
- configure eslintconfig
    - [see at this repository for eslintrc.json]()
