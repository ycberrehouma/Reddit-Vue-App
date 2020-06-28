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

Vue.js project created using the Vue CLI webpack-simple template to use Axios and MomentJS for data fetching and date formatting.

``` bash
$ vue init webpack-simple infinite-scroll-vuejs
```

a GET service method with Axios to fetch another Reddit posts from the Reddit API.

Rules for using the reddit API:
- You must read the terms and register in order to use the Reddit API, to then get the client ID and Secure Key to get authentication to call the API
- All API clients must authenticate with OAUTH 2
- All API clients must follow the API rules: https://github.com/reddit/reddit/wiki/API


