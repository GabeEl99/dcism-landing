<template>
  <div class="main-container">
    <HeaderElement />


    <Breadcrumb>
      <template slot="breadcrumb">
        <div class="breadcrumb_box text-center">
          <ul class="breadcrumb-list">
            <li class="breadcrumb-item active" style="font-size: 15px">
              Department of Computer, Information Sciences, and Mathematics
            </li>
          </ul>
          <h2 class="breadcrumb-title">News</h2>
          <!-- breadcrumb-list start -->
          <ul class="breadcrumb-list">
            <li class="breadcrumb-item">
              <router-link :to="{ name: 'Home' }">Home</router-link>
            </li>
            <li class="breadcrumb-item active">News</li>
          </ul>
          <!-- breadcrumb-list end -->
        </div>

        <div class="digital-agency-assistance-area  section-space--ptb_120" id="about">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="digital-agency-section-title text-center section-space--mb_60">
                        <h6 class="section-sub-title mb-20 font-weight--bold wow move-up">Welcome to DCISM News Page :)</h6>
                        <h3 class="section-title font-weight--light mb-15 wow move-up">Miss News no more! View all the News about DCISM here.</h3>
                    </div>
                </div>
            </div>

        </div>
    </div>
      </template>
    </Breadcrumb>
    <!-- breadcrumb end -->

 
    <NewsContent />


    <!-- footer section -->
    <Footer />

    <OffcanvasSearchBox />

    <!-- off-canvas mobile menu -->
    <OffCanvasMobileMenu />

  </div>
</template>

<script>
import HeaderElement from "@/components/dcism/HeaderNews.vue";
import Breadcrumb from "@/components/dcism/Breadcrumb.vue";
import Footer from "@/components/dcism/FooterNews.vue";
import OffcanvasSearchBox from "@/components/dcism/OffcanvasSearchBox.vue";
import OffCanvasMobileMenu from "@/components/dcism/OffCanvasMobileMenu.vue";
import NewsContent from "@/components/dcism/sections/news/NewsContent.vue";

export default {
    name: "AllNews",
    components: {
        HeaderElement,
        Breadcrumb,
        Footer,
        OffcanvasSearchBox,
        OffCanvasMobileMenu,
        NewsContent,
    },

  metaInfo: {
        title: "News | DCISM",
        htmlAttrs: {
            lang: "en",
            amp: true,
        },
    },

    async created() {

    },

    methods: {

    },
};
  
</script>

<style lang="scss">

</style>