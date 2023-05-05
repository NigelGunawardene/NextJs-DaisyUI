This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## Git commands

NextJs-Portfolio

Adding to git

git init

git add .

git commit -m "message"

git remote add origin https://NigelGunawardene@github.com/NigelGunawardene/NextJs-Portfolio.git <- get this URL from github.com after creating a repo and insert username

git push -u -f origin main/master


from github this worked - 

git init

git add .

git commit -m "first commit"

git branch -M main

git remote add origin https://github.com/NigelGunawardene/NextJs-Portfolio.git

git push -u origin main

## Scalable arch from https://blog.logrocket.com/structure-scalable-next-js-project-architecture/

Enforcing code formatting rules
Code formatting is very important for maintaining code consistency in your project as it scales. You can enforce a strict set of code formatting rules for team members working on the same project, but on different branches or modules.

To achieve this, first, add eslint to your project. Luckily, in our case, Next.js comes with built-in support for ESLint, so you simply need to configure it.

Check for a .eslintrc.json file at the very root level of your project. This file allows you to write eslint rules in key-value pairs.

You can choose from hundreds of rules and add as many rule sets as you want or need in your project. For example, add the following code to this file:

{
  "extends": ["next", "next/core-web-vitals", "eslint:recommended"],
  "globals": {
    "React": "readonly"
  },
  "rules": {
    "no-unused-vars": "warn"
  }
}
In the example above, React has been added as a global package for this project. By doing so, you are ensuring that React is always defined in functional components and JSX code, even if you haven’t explicitly mentioned import React from 'react' at the top of the file.

The second rule added here — no-unused-vars — will warn you if you have a variable defined in your file that is not being used anywhere across the app. This rule can help you with removing unnecessary variable declaration, which happens a lot in team projects.

ESLint does its job pretty well, but when paired with Prettier, it can be even more powerful, providing a consistent coding format for all team members across the organization.

You can achieve this by installing the prettier package to the project like so:

npm i prettier -D
Once the installation has been finished, create two files at the root level — the same level as the eslintrc.json file. These files should be named .prettierrc and .prettierignore.

The .prettierrc file will contain all the Prettier rules that you are introducing in the project. The following code demonstrates a few rules you can add as JSON key-value pairs:

{
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
The .prettierignore file will contain the names of those files and folders that you do not want Prettier to run and analyze. For example, you would never want to run Prettier on the node_modules folder, dist folder, package.json, and other such files. Therefore, add paths to these files in .prettierignore like so:

dist
node_modules
package.json
Now, try changing anything in your code from a single quotation mark to a double quotation mark, as in the following example:

'Hello' => "Hello"
If you run npm run prettier --write and everything runs correctly, you will see Prettier has formatted all your files — changing double quotation marks into single quotation marks again — because of the rule you defined earlier in the .prettierrc file.

Running this command every time can be cumbersome, so it’s better to put this in your package.json file as a script:

 "scripts: {
    "prettier": "prettier --write ."
  }
Now, all you have to do is type npm run prettier. You can also configure your VS Code to run Prettier whenever you hit Cmd + S.

With all this set up, now would be a good time to commit changes to your repo. Make sure to follow proper naming conventions while committing changes. Conventional Commits provides a helpful resource you can follow while handling Git naming conventions.