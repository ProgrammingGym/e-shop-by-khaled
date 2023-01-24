- NodeJs and NPM have to be installed globally before getting started.

## Client

to init vite for react and typescript inside the client folder:<br/>

- `npm create vite@latest client`
- choose react then choose TypeScript

to install npm in the client folder:<br/>

- `cd client`
- `npm install`

to run the server:<br/>
- `npm run dev`


to install styled components:<br/>
- `npm install --save styled-components`
- `npm install --save-dev @types/styled-components`

to install react icons:<br/>
- `npm install react-icons --save`
- Reference: https://react-icons.github.io/react-icons
---

## Server

useful video1: https://www.youtube.com/watch?v=qy8PxD3alWw<br/>
useful video2: https://www.youtube.com/watch?v=H91aqUHn8sE<br/>

to create a package.json file:<br/>

- `npm init`
- then answer few interactive terminal questions

to install express:<br/>

- `npm install express`
- then create an index.ts file

to install the TypeScript compiler:<br/>

- `npm install typescript --save-dev`

to create the tsconfig.json file:<br/>

- `npx tsc --init`
- then remove everything in tsconfig.json file and paste the following:<br/>

```
{
    "compilerOptions": {
      "module": "NodeNext",
      "moduleResolution": "NodeNext",
      "target": "ES2020",
      "sourceMap": true,
      "outDir": "dist",
    },
    "include": ["src/**/*"],
}
```

to avoid having declaration bugs for importing express:<br/>

- `npm i --save-dev @types/express`
- `npm i --save-dev @types/node`

to compile the index.ts to index.js file:<br/>

- add the following field/key-pair value
  **"build": "tsc"** to the "scripts" object inside the package.json file. Then run the following command while being in serve directory:
- `npm run build`

then to start the server navigate to dist directory and run the compiled index.js normally as a node file as follows:<br/>

- `cd dist`
- `node index.js`
- to make it easier add the following field/key-pair value **"start": "node dist/index.js"** to the "scripts" object inside the package.json file. Then run the following command while being in serve directory:
- `npm run start`

To keep the server live and automatically clean up the dist folder:<br/>

- `npm install -D nodemon`
- `npm install rimraf`
- `npm install concurrently`

adjust the "scripts" object inside the package.json file as follows:

```
"scripts": {
    "build": "rimraf dist && npx tsc",
    "prestart": "npm run build",
    "start": "node dist/index.js",
    "predev": "npm run build",
    "dev": "concurrently \"npx tsc -w\"  \"nodemon dist/index.js\""
}

```

Now: <br/>
to build for production:<br/>

- `npm run build`
  to test/start built file for prod:<br/>
- `npm run start`
  to start live server for dev:<br/>
- `npm run dev`

You also may need to add a .gitignore file here as well to ignore pushing some files and folders to your github repo, such as the auto-generated node_modules folder.
