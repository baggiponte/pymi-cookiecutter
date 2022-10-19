# Cookiecutter Tutorial 

Single page application (SPA) for the [`cookiecutter`](https://www.cookiecutter.io/) [tutorial](https://www.eventbrite.com/e/double-feature-decoratori-cookiecutter-tickets-433530370007?aff=ebdsoporgprofile) I held @[Python Milano](http://milano.python.it/).

## Repo structure

```bash
.
├── .github
├── assets
├── components
├── pages
├── sample-cookiecutter
├── .gitignore
├── .npmrc
├── netlify.toml
├── package-lock.json
├── package.json
├── README.md
├── slides.md
└── vercel.json
``` 

* [`.github`](./.github): github actions
* [`assets`](./assets): static assets
* [`components`](./components): generated by `slidev`
* [`pages`](./pages): contains the slides that end up in [`slides.md`](./slides.md)
* [`sample-cookiecutter`](./sample-cookiecutter): sample cookiecutter template used to display how the library works
* [`.gitignore`](./.gitignore): ignored files
* [`.npmrc`](./.npmrc): generated by `slidev`
* [`netlify.toml`](./netlify.toml): generated by `slidev`
* [`package-lock.json`](./package-lock.json): generated by `slidev`
* [`package.json`](./package.json): generated by `slidev`
* [`README.md`](./README.md)
* [`slides.md`](./slides.md)
* [`vercel.json`](./vercel.json): generated by `slidev`

## How to run

To start the slide show:

- `npm install`
- `npm run dev`
- visit http://localhost:3030

Edit the [slides.md](./slides.md) to see the changes.

## Credits

* [`slidev`](https://github.com/slidevjs/slidev) is an amazing framework to build slides from markdown and host them.
* [`cookiecutter`](https://github.com/cookiecutter/cookiecutter) is an open source library to build coding project templates.
