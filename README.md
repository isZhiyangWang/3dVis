# Vis-sieve

Vis-Sieve is a project based on [Observable Framework](https://observablehq.com/framework) and [Three.js](https://threejs.org/). To start the local preview server, run:

## Direct Use of the Code

- Download the code from this [repo](https://github.com/JimmyXwtx/3dVis)
- `npm install` or `npm i` in termninal to install all dependencies
- `npm run dev` for development
    - Then visit <http://localhost:3000> to preview your project.
- `npm run build` for deployment

## Project structure

A typical Framework project looks like this:

```ini
.
├─ src         
│  ├─ data
│  │  ├─ pulications_princeton.db      # the duckdb database for this project
│  ├─ index.md     # welcome page
│  ├─ intro.md        # introduction page
│  ├─ visualDatabase.md        # 2d page
│  └─ viz.md                 # the 3d visualization page
├─ .gitignore
├─ observablehq.config.js      # the project config file
├─ package.json
└─ README.md # the file you are looking at
```

## Below is the use of Obervable  Framework: 

**`src`** - This is the “source root” — where your source files live. Pages go here. Each page is a Markdown file. Observable Framework uses [file-based routing](https://observablehq.com/framework/routing), which means that the name of the file controls where the page is served. You can create as many pages as you like. Use folders to organize your pages.

**`src/index.md`** - This is the home page for your site. You can have as many additional pages as you’d like, but you should always have a home page, too.

**`src/data`** - You can put [data loaders](https://observablehq.com/framework/loaders) or static data files anywhere in your source root, but we recommend putting them here.

**`observablehq.config.js`** - This is the [project configuration](https://observablehq.com/framework/config) file, such as the pages and sections in the sidebar navigation, and the project’s title.

## Command reference

| Command           | Description                                              |
| ----------------- | -------------------------------------------------------- |
| `npm install`            | Install or reinstall dependencies                        |
| `npm run dev`        | Start local preview server                               |
| `npm run build`      | Build your static site, generating `./dist`              |
| `npm run deploy`     | Deploy your project to Observable                        |
| `npm run clean`      | Clear the local data loader cache                        |
| `npm run observable` | Run commands like `observable help`                      |

- For more, see <https://observablehq.com/framework/getting-started>.