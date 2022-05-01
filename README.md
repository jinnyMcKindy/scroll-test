# Frontend technical assessment

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

## Description

You should implement a simple profile search application using Nuxt and Vue frameworks. 

Expected technologies used are: ES6, CSS (with any pre/post processors), HTML, SFC (Single File Component). Feel free to use any other third party libraries and plugins.

## 1. **Expected steps**

- We expect you to implement layout according to design above and a single page application based on Vue and its modules
- Application should be running on a root url (`/`)
- The sample data to use inside application **should be taken** here: [https://gist.github.com/allaud/093aa499998b7843bb10b44ea6ea02dc](https://gist.github.com/allaud/093aa499998b7843bb10b44ea6ea02dc)
- The default app state should show all of the profile cards. When user starts typing, the results should be filtered in realtime, highlighting the matching string
- Search should be stateful (using browser url e.g. `/search/Boris`)
- Application should be published online for testing purposes

## Evaluation criteria

- Attainment of the requirements and of the proposed design
- General SPA application performance, including searching, scrolling and highlighting speed
- Quality of Vue single file components (SFC)
- HTML (JSX) and CSS quality
- JS code quality

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
