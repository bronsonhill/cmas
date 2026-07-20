# cmas
A collaborative agent-based wiki and library for learning computational modelling and simulation.


## Project structure
### The wiki
See the wiki [here](https://bronsonhill.github.io/cmas/). The wiki is based on Andrej Karpathy's idea of an agentic wiki, built with [Quartz](https://quartz.jzhao.xyz/) and published to GitHub Pages. Alternatively, simply clone the repo and open the `content/` folder in your markdown editor of choice (ie. Obsidian or Visual Studio Code) for consumption and/or contribution — Quartz reads a plain Obsidian-style vault, including `[[wikilinks]]`.

```
content/
    index.md
    sources/
        index.md
    entities/
        index.md
    concepts/
        index.md
    materials/
        index.md
```

As The University of Melbourne's learning resources are copyright material, none are stored in the repo. All such sources are indexed as a link to the resource on canvas.

To preview locally: `npm i && npx quartz build --serve`.

## The library
Murmarate is a java library designed for learning agent based modelling and simulation. Thus, the library is optimised for readibility and illustrative examples; not efficiency.


## Contributing
Contribution


This repo is designed to be a resource which students of Computational Modelling and Simulation can use to study, and contribute to. I have used a private wiki in subjects like Natural Language Processing with success, and so am building this one in public.

