<template>
    <div>
        <!-- portfolio item wrapper start -->
            <div class="portfolio-pages-wrapper section-space--ptb_100 border-bottom gray-gradient">
                <div class="container">
                    <div class="row" v-if="news.news">
                        <div class="col-lg-4 col-md-6 mb-30 wow move-up" v-for="news in news.news" :key="news.id">
                            <div class="portfolio-grid-caption">
                                <router-link to="#" class="single-grid-caption">
                                    <div class="single-portfolio__thumbnail">
                                        <img class="img-fluid" :src="news.image" alt="">
                                    </div>
                                </router-link>
                                <div class="post-info">
                                    <h5 class="post-title font-weight--bold">
                                        <router-link to="#">{{ news.title }}</router-link>
                                    </h5>
                                    <div class="post-categories">
                                        <p>News date: {{ news.news_date }}</p>
                                    </div>
                                    <p>{{ news.desc }}</p>
                                    <router-link to="#" style=" font-weight:normal; color:rebeccapurple; text-align:right">Read More ></router-link>
                                </div>
                            </div>
                        </div>
                    </div>

                   
                    <div class="row" v-if="news.news == 0">
                        <div class="post-info lg-blog-post-info">

                            <h4 class="post-title font-weight--light text-center">
                                There are currently no new news to be displayed.
                            </h4>

                            <div class="post-read-more mt-20">
                                <router-link to="/" >
                                    <span class="font-weight--original" style="font-size:20px;">Back to Home</span>
                                </router-link>
                            </div>

                        </div>
                    </div>
                   

                </div>
            </div>
        <!-- portfolio item wrapper end -->

    </div>
    
</template>

<script>
   import axios from 'axios';
    
    export default {
        name: 'News',
        components: {
        },

        data () {
            return {
                news: [],
            }
        },

        mounted(){
            this.getNews();
        },

        methods:{
      getNews(){
          let self = this;
          axios.get('http://localhost:8080/api/news')
          .then(res=>{
             if(res.status==200){
                  self.news = res.data;
             }
          })
          .catch(err=>{
             window.console.log(err)
         });
      }    
    }
    }
    
</script>

<style lang="scss">

</style>