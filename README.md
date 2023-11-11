# habit-tracker

**CONTEXT:**

This project was inspireed by the GitHub commit tracker on-platform. The commit tracker tool is a great visual way to track your daily porogress, alongside comparing how many commits were made one day versus another. It's satisfying to see the individual cells fill up, and I wanted to emulate that for my own habits through this project.

**WORKFLOW:**
1. The user selects the answer that best aligns with their level of physical activity.
2. The user then hits "Submit".
3. The site displays a grid-like structure that matches the number of days of the current month. When a user submits an activity, that corresponding square (ie. it's Day 1, so the first square is highlighted, etc) is filled with an opacity level. The more intense the activity, the darker the background-color on the square.

**UNDER THE HOOD:**

Stack: Front-End Development
Languages/Framework: Vue.js, (Javascript, HTML, CSS)
   
**LESSONS LEARNED:**
1. Working with Vue.js was surprisingly easy and felt intuitive in comparison to Vanilla JS. There were some learning curves as to the specific v-directives and interacting with components/props, but it was an enjoyable experience over more verboise front-end frameworks like React.
2. The most challenging part of this project was creating the individual cells dynamically (and creating a unique identifier/passing the correct opacity level depending on the user input).
3. What I was able to level-up on from last projects was my eye for CSS styling and planning an approach prior to sitting down and coding.
   
**FUTURE IMPROVEMENTS**
1. State Management: Right now, you can enter in your activity level for the current date, but that progress is erased upon refreshing the page. To get the true experience, I need to incorporate some state management tool so that the styling persists after refresh.
2. CSS: The background/general styling of the page is still quite bland; I'd like to take more time for this (and future projects) to think more creatively on what I want the website to look like.


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

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
