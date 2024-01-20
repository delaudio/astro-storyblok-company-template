# Astro Company Website Template with Storyblok

## Run the project

```sh
yarn
yarn dev
```

## Show Storyblok preview

Install mkcert for creating a valid certificate (Mac OS):

```sh
brew install mkcert
mkcert -install
mkcert localhost
```
        
// Then install and run the proxy

```sh
npm install -g local-ssl-proxy
local-ssl-proxy --source 4322 --target 4321 --cert localhost.pem --key localhost-key.pem
```
        
https is now running on port 3010 and forwarding requests to http 3000

## Typescript

If you would like to use TypeScript in your Storyblok project(s), the Universal JavaScript Client, the JavaScript SDK, as well as Storyblok's framework-specific SDKs for React, Vue, Nuxt, Svelte, Astro, and Gatsby, offer full TypeScript support. This results in a significantly improved developer experience, offering auto-completion, static typing, warnings, and more.

It is highly recommended to use the `storyblok-generate-ts` package provided by Storyblok's ambassador Dominic Garms. In combination with the Storyblok CLI, you can generate types for the components defined in the Block Library of your Storyblok space.

To get started, follow these steps:

Install the Storyblok CLI: 

```sh
npm i -g storyblok
````

Login using storyblok login in your terminal
In your project directory, save the schema of your Storyblok components in a .json file by running storyblok 

```sh
pull-components --space SPACE_ID
```

Install storyblok-generate-ts: 

```sh
yarn add -D storyblok-generate-ts
```

Add the following command to your package.json: 

```json
"generate-sb-types": "storyblok-generate-ts source=./components.[SPACE_ID].json target=./component-types-sb"
```

Generate the types: 

```sh
yarn generate-sb-types
```

Import the type in each component, for example: 

```ts
import type { PageStoryblok } from '../component-types-sb'
```

Remember to rerun the `pull-components` and `generate-sb-types` scripts after you've made changes to your component schema in your Storyblok space