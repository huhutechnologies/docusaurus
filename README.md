# Docusaurus - Org documentation
Docusaurus è usato per produrre la documentazione dell'org di github. 

Il sito è creato sulla base di `https://docusaurus.io/docs#fast-track``

## Bootstrap

```bash
npx create-docusaurus@latest github-pages classic
```

## Test - Start localhost

```bash
cd github-pages
yarn # install dependencies
yarn start # start local server
```

## Build and Deploy on Github pages
Lancia la build del sito statico e prova localmente se funziona

```bash
yarn build
yarn serve

```

> basato su https://docusaurus.io/docs/deployment#deploying-to-github-pages

Per avere la documentazione disponibile su `https://huhutechnologies.github.io/`, nell'org di github huhutechnologies creeremo un repository di nome  `huhutechnologies.github.io` dove salveremo le build di docusaurus

![Create a repo with terraform](img/create-repo.png)

(Serve un file perche il comando di deploy cancella l'intero contenuto)

```
mkdir huhutechnologies.github.io
cd huhutechnologies.github.io
git init
echo "README" > README.md
git commit -m "Initial Commit" 
git remote add origin git@github.com:huhutechnologies/huhutechnologies.githu
git branch -M main
git push -u origin main
```

Ora useremo un file di configurazione per deployare il nostro sito 

> docusaurus.config.ts
```
export default {
  // ...
  url: 'https://huhutechnologies.github.io',
  baseUrl: '/',
  projectName: 'huhutechnologies.github.io',
  organizationName: 'huhutechnologies',
  trailingSlash: false,
  deploymentBranch: 'main'
  // ...
};

Infine il seguente comando per deployare

```bash
CURRENT_BRANCH=main yarn deploy 
```