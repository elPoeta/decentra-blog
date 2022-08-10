<div id="top"></div>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">
  <h3 align="center">Decentra Blog</h3>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#steps">Steps</a></li>
      </ul>
    </li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## About The Project

<div align="center">

#### Web3 blog

</div>

<!-- BUILT -->

### Built With

- [![Node][node.js]][node-url]
- [![Typescript][typescript.ts]][typescript-url]
- [![Next][next.js]][next-url]
- [![Tailwind][tailwind.css]][tailwind-url]
- [![Solidity][solidity]][solidity-url]
- [![Hardhat][hardhat]][hardhat-url]

<p align="right">(<a href="#top">back to top</a>)</p>

<!--  -->

## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

- ###### Enviroment
  - node
    <a href="https://nodejs.org/en/download/" target="_blank">https://nodejs.org/en/download/</a>
- ###### Pacakage manager

  - npm
    <a href="https://docs.npmjs.com/downloading-and-installing-node-js-and-npm" target="_blank">https://docs.npmjs.com/downloading-and-installing-node-js-and-npm</a>
    ###### or
  - yarn
    <a href="https://yarnpkg.com/cli/install" target="_blank">https://yarnpkg.com/cli/install</a>

- ###### Browser
  - Metamask extension
    <a href="https://metamask.io/" target="_blank">https://metamask.io/</a>

### Installation

_I will use yarn to install dependencies_

1. Clone the repo

   ```sh
   git clone https://github.com/elPoeta/decentra-blog.git
   ```

2. Install NPM packages
   ```sh
   yarn install
   ```
3. Clean
   ```sh
   yarn hardhat clean
   ```
4. Compile
   ```sh
   yarn hardhat compile
   ```
5. Start local ethereum network
   ```sh
   yarn hardhat node
   ```
6. Tests
   ```sh
   yarn hardhat test
   ```

### Steps

- ##### Frontend

  1.  Next js
      https://nextjs.org/docs/basic-features/typescript

      ```sh
      yarn create next-app --typescript .
      ```

  2.  Tailwind css
      https://tailwindcss.com/docs/guides/nextjs

      - _Install_

        ```sh
        yarn add -D tailwindcss postcss autoprefixer
        npx tailwindcss init -p
        ```

      - _Configure Paths file._

        `tailwind.config.js`

        ```js
        /** @type {import('tailwindcss').Config} */
        module.exports = {
          content: [
            "./pages/**/*.{js,ts,jsx,tsx}",
            "./components/**/*.{js,ts,jsx,tsx}",
          ],
          theme: {
            extend: {},
          },
          plugins: [],
        };
        ```

      - _Add the Tailwind CSS directives_
        `./styles/globals.css`

        ```css
        @tailwind base;
        @tailwind components;
        @tailwind utilities;
        ```

- ##### Backend

  1. Remove `README.md`
     ```sh
     sudo rm -f README.md
     ```
  2. Hardhat _dev dependencies_
     https://hardhat.org/hardhat-runner/docs/getting-started#overview
     ```sh
     yarn add -D ts-node ethers hardhat hardhat-deploy /
     @nomiclabs/hardhat-ethers dotenv typechain /
     @typechain/hardhat @typechain/ethers-v5 @types/chai /
     @openzeppelin/contracts
     ```
  3. Hardahat config file `hardhat.config.ts`

     ```ts
     import "hardhat-deploy";
     import "@nomiclabs/hardhat-ethers";
     import "@typechain/hardhat";
     import { HardhatUserConfig } from "hardhat/config";

     const config: HardhatUserConfig = {
       defaultNetwork: "hardhat",
       solidity: "0.8.9",
       networks: {
         hardhat: {
           chainId: 31337,
         },
         localhost: {
           chainId: 31337,
         },
       },
       namedAccounts: {
         deployer: 0,
       },
     };

     export default config;
     ```

- ##### Common
  1. Typescript config file `tsconfig.json`
     ```json
     {
       "compilerOptions": {
         "target": "es2020",
         "lib": ["dom", "dom.iterable", "esnext"],
         "allowJs": true,
         "skipLibCheck": true,
         "strict": true,
         "forceConsistentCasingInFileNames": true,
         "noEmit": true,
         "esModuleInterop": true,
         "module": "CommonJS",
         "moduleResolution": "node",
         "resolveJsonModule": true,
         "isolatedModules": true,
         "jsx": "preserve",
         "incremental": true
       },
       "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
       "exclude": ["node_modules"],
       "files": ["./hardhat.config.ts"]
     }
     ```
  2. Package config file `package.json`
     ```json
     {
       "name": "decentra-blog",
       "version": "0.1.0",
       "private": true,
       "scripts": {
         "dev": "next dev",
         "build": "next build",
         "start": "next start",
         "lint": "next lint",
         "deploy:local": "hardhat run --network localhost scripts/deploy.ts",
         "test": "yarn hardhat test",
         "compile": "yarn hardhat compile",
         "start:localNode": "yarn hardhat node",
         "clean": "yarn hardhat clean"
       },
       "dependencies": {
         "next": "12.2.4",
         "react": "18.2.0",
         "react-dom": "18.2.0"
       },
       "devDependencies": {
         "@nomiclabs/hardhat-ethers": "npm:hardhat-deploy-ethers@^0.3.0-beta.13",
         "@openzeppelin/contracts": "^4.7.2",
         "@typechain/ethers-v5": "^10.1.0",
         "@typechain/hardhat": "^6.1.2",
         "@types/chai": "^4.3.3",
         "@types/node": "18.6.5",
         "@types/react": "18.0.17",
         "@types/react-dom": "18.0.6",
         "autoprefixer": "^10.4.8",
         "dotenv": "^16.0.1",
         "eslint": "8.21.0",
         "eslint-config-next": "12.2.4",
         "ethers": "^5.6.9",
         "hardhat": "^2.10.1",
         "hardhat-deploy": "^0.11.12",
         "postcss": "^8.4.16",
         "tailwindcss": "^3.1.8",
         "ts-node": "^10.9.1",
         "typechain": "^8.1.0",
         "typescript": "4.7.4"
       }
     }
     ```

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ROADMAP -->

## Roadmap

- [x] Install dependencies :heavy_check_mark:
  - [x] Config project :heavy_check_mark:
- [ ] Backend
  - [ ] TDD
    - [ ] Tests
  - [ ] Contract
- [ ] Frontend
- [ ] README

<p align="right">(<a href="#top">back to top</a>)</p>

## License

Distributed under the MIT License. See `LICENSE` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>

## Contact

Leonardo Tosetto - leonardo.a.tosetto@gmail.com

Project Link: [https://github.com/elPoeta/decentra-blog](https://github.com/elPoeta/decentra-blog)

<p align="right">(<a href="#top">back to top</a>)</p>

## Acknowledgments

- [Node js](https://nodejs.org/en/)
- [Typescript](https://www.typescriptlang.org/)
- [Solidity](https://soliditylang.org/)
- [Hardhat](https://hardhat.org/)
- [React](https://reactjs.org/)
- [Next js](https://nextjs.org/)
- [Vercel](https://vercel.com)
- [Tailwind css](https://tailwindcss.com/)
- [Metamask](https://metamask.io/)
- [Img Shields](https://shields.io)
- [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
- [Choose an Open Source License](https://choosealicense.com)
- [vscode](https://code.visualstudio.com/)
- [vscode hardhat extension](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity)
- [vscode react snippets extension](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [vscode Tailwind CSS IntelliSense extension](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

<!-- MARKDOWN LINKS & IMAGES -->

[contributors-shield]: https://img.shields.io/github/contributors/elPoeta/decentra-blog.svg?style=for-the-badge
[contributors-url]: https://github.com/elPoeta/decentra-blog/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/elPoeta/decentra-blog.svg?style=for-the-badge
[forks-url]: https://github.com/elPoeta/nft-marketplace/network/members
[stars-shield]: https://img.shields.io/github/stars/elPoeta/decentra-blog.svg?style=for-the-badge
[stars-url]: https://github.com/elPoeta/decentra-blog/stargazers
[issues-shield]: https://img.shields.io/github/issues/elPoeta/decentra-blog.svg?style=for-the-badge
[issues-url]: https://github.com/elPoeta/decentra-blog/issues
[license-shield]: https://img.shields.io/github/license/elPoeta/decentra-blog.svg?style=for-the-badge
[license-url]: https://github.com/elPoeta/decentra-blog/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/leonardo-tosetto
[next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[next-url]: https://nextjs.org/
[node.js]: https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white
[node-url]: https://nodejs.org/
[typescript.ts]: https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=whitehttps://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white
[typescript-url]: https://www.typescriptlang.org/
[tailwind.css]: https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white
[tailwind-url]: https://tailwindcss.com/
[solidity]: https://img.shields.io/badge/solidity-%3E%3D%200.8.9-lightgrey
[solidity-url]: https://soliditylang.org/
[hardhat]: https://img.shields.io/badge/hardhat-2.10.1-yellow
[hardhat-url]: https://hardhat.org/
