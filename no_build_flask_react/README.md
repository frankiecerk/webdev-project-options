# No build option for Flask app serving pages made up of React components

General file structure of projects like this:

```
project_root/
├── README.md
├── app.py # potentially split into a couple python files to separate page routes and api implementation
├── static/
│   ├── css/
│   └── js/
│       └── pages # React components that replace #content with themselves
|           └── index.jsx
|           └── birds.js
|       └── components # React components that are reused and need to be imported globally
|           └── names.jsx
└── templates/
    └── base.html # include React, babel, axios and other 3rd party libraries, and all components globally, provide div with id #content entrypoint for React
    └── index.html # extend base.html and include the corresponding page.jsx
    └── birds.html # extend base.html and include the corresponding page.jsx
```

To avoid a build step, we include React and babel globally in each HTML page, along with every shared component (for simplicity).

## Pros:

- Avoid build step
- Avoid node in browser

## Cons:

- We can't really teach students about ES6 modules and `import/export` syntax
- Template syntax is too much to cover in this course, and a little off topic. Will probably have to hide
  or not address this part of the project in starter code and make these files un-editable
- Will need some sort of script to include each component in base.html - need some listener on the
  components folder that edits base.html every time a file is added
  (I will not have students write this themselves - its not really something I want them to
  learn and it would be a ridiculous thing to get stuck on)
