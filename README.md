### Gen Tools

#### Setup

This is a library (ish) that I use regularly for code generation. It's hyper specific to what stack I use and how I organize it, but maybe it'll be useful
elsewhere too. Basically, if you have interfaces that you'd like to automatically generate services and MongoDB schemas for, this is how I do it.

To use gentools, your folder structure should look like this:

```
project
  - src
    - gentools (just git clone it here)

    - schema.generate.ts
    - service.generate.ts
    - index.ts
```

the `.generate` files can just be copied straight from gentools. This project requires NPM and you can run this script to install all the necessary packages:

`npm i tsconfig-paths ts-morph code-block-writer && npm i --save-dev @types/node`

There is also an example `tsconfig` file. The important part is the `paths` object. Gentools needs to be in there and also needs to be in the
correct place in the folder hierarchy. The other settings can be changed around, they're just typical default settings in a TS project.

#### Usage

In your `package.json`, you'll need the following in the `scripts` section of the file:

```
"generate:schemas": "ts-node src/schema.generate.ts",
"generate:services": "ts-node src/service.generate.ts"
```

You'll also need to download `ts-node` through NPM. After that, you'll have your services and schemas ready.
