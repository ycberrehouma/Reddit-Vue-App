    <template>
      <div id="app">
        <h1>Reddit Posts from r/aww</h1>
        <div class="redditPosts" v-for="post in redditPosts">
            <h4>{{post.subreddit-name}}</h4>
            <reddit-list-container></reddit-list-container>
            <reddit-list-item></reddit-list-item>
        </div>
        </div>
      </div>
    </template>
      
      
    <script type = "text/javascript">
    Vue.component('reddit-list-container', {
          data () {
            return {
              redditPosts: []
            }
          },
          template: '<a href="https://www.reddit.com/r/aww/comments/{{post.id}}/{{post.title}}">{{ post.title }}</a> <img :src="post.picture">'
          methods: {
            getInitialUsers () {// This function call the API, fetch and set some initial data ( 25 reddit posts) on page load:
              var j =0;
              for (var i = 0; i < 25; i++) {
              var axios = require("axios");
              axios.request({
                url: "/oauth/token",
                method: "get",
                baseURL: "https://www.reddit.com/api/v1/collections/subreddit_collections",
                auth: {
                  username: "LBEVzt5QdykXAQ", // This is the client_id
                  password: "-x0uJv47L50nVxc2q5CnvSpwZv0" // This is the client_secret
                },
                data: {
                  "grant_type": "client_credentials",
                  "scope": "public"    
                }
              }).then(response => {
                if(response.status == 200 ) {
                  this.redditPosts.push(response.data.children[j]);
                  j++;  
                }
              });
              .catch((error) => {
                return Promise.reject(error)
              })
              }
            }
          },  
          beforeMount() {
            this.getInitialUsers();
          }
      
    }
        
    Vue.component('reddit-list-item', {
          data () {
            return {
              redditPosts: []
            }
          },
          template: '<a href="https://www.reddit.com/r/aww/comments/{{post.id}}/{{post.title}}">{{ post.title }}</a> <img :src="post.picture">'
          methods: {    
            scroll (posts) {//This function calls the API and adds a new reddit post to the posts array when scrolling reaches the bottom of the page.
                var j = 25;
                window.onscroll = () => {
                  let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;

                  if (bottomOfWindow) {
                    for (var i = 0; i < 25; i++) {
                      axios.request({
                      url: "/oauth/token",
                      method: "get",
                      baseURL: "https://www.reddit.com/api/v1/collections/subreddit_collections",
                      auth: {
                        username: "LBEVzt5QdykXAQ",
                        password: "-x0uJv47L50nVxc2q5CnvSpwZv0"
                      },
                      data: {
                        "grant_type": "client_credentials",
                        "scope": "public"    
                      }
                      }).then(response => {
                        if(response.status == 200 ) {
                          this.redditPosts.push(response.data.children[j]); 
                          j++; 
                        }
                      });
                      .catch((error) => {
                        return Promise.reject(error)
                      })
                    } 
                  }
                };
            },
          }, 
          mounted() {
            this.scroll(this.redditPosts);
          }
    }
      </script>
      
      
      <style lang="scss">
      .redditPosts {
          border-radius: 2px;
          width: 20%;
          margin: 0 auto 15px auto;
          padding: 15px;
      }
 
      img {
          width: 100%;
          height: auto;
          }
      </style>
