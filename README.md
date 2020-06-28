# TransPerfect Reddit Vue App



## Build Setup

### Installation

``` bash
# install dependencies
npm install
```

### Running

``` bash
# build to start Webpack and build code
Run npm run 

# start Webpack and build code and watch for code changes
Run npm run watch to 

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

Vue.js project created using the Vue CLI webpack-simple template to use <b>Axios and MomentJS</b> for data fetching and date formatting.
a GET service method with <b>Axios</b> to fetch another Reddit posts from the Reddit API.

``` bash
$ vue init webpack-simple infinite-scroll-vuejs
```


## Rules for using the reddit API:
- You must read the terms and register in order to use the Reddit API, to then get the client ID and Secure Key to get authentication to call the API
- All API clients must authenticate with OAUTH 2
- All API clients must follow the API rules: https://github.com/reddit/reddit/wiki/API


## The Logic behind Implementing the Infinite Scroll:
<i>Sorted by newest post first</i><br>
Once we get the initial data (25 reddit Posts)  we create a new function <b>scroll()</b> and have it loaded in the <b>mounted()</b> method. 

This <b>scroll()</b> method calculates the bottom of the page to know if its reached or not which means that it will evaluates it as true or false. For this, we use  the <b>documentElement.scrollTop, documentElement.offsetHeight properties and of window’s innerHeight properties</b> to find out if scroll is at the bottom.

