<template>
  <div
    class="
      page-sidebar-content-wrapper page-sidebar-right
      small-mt__40
      tablet-mt__40
    "
  >
    
    <!-- === Popular News Widget Start === -->
    <div class="sidebar-widget widget-blog-post wow move-up">
      <h5 class="widget-title font-weight--light">Popular News</h5>
      <div v-if="isLoading">
        <div class="post-item" v-for="i in 2" :key="i">
          <NewsSkeleton />
        </div>
      </div>
      <div v-else-if="popular_news.length <= 0">
          <div class="post-item">
              <div class="post-info">
                  <div class="post-categories">
                      No news available
                  </div>
              </div>
          </div>
      </div>
      <div
        v-else
        class="post-item"
        v-for="news in popular_news"
        :key="news.news_id"
      >
        <div class="post-info">
          <div class="post-categories">
            <router-link to="/news">{{
              formatDate(news.created_at)
            }}</router-link>
          </div>
          <h6 class="post-title">
            <router-link to="/news">{{
              news.title
            }}</router-link>
          </h6>
        </div>
      </div>
    </div>
    <!-- === Popular News Widget End === -->

   
  </div>
</template>

<script>
/* eslint-disable no-console */
import Api from "@/api/api.js";
import NewsSkeleton from "@/components/dcism/sections/news/NewsSkeleton";

export default {
  components: {
    NewsSkeleton,
  },
  data() {
    return {
      popular_news: [],
      data: {
        page: 1,
        perPage: 5,
      },
      isLoading: false
    };
  },
  async created() {
    try {
      this.isLoading = true;

      const news = await this.getNews(
        this.data.page,
        this.data.perPage
      );

      this.popular_news = news;
    } catch (err) {
      console.log(err.toString());
    }

    this.isLoading = false;
  },
  methods: {
    async getNews(page, perPage) {
      try {
        let news = await Api().get(
          `/get-all-news?page=${page}&items=${perPage}`
        );
        return news.data;
      } catch (e) {
        console.log(e.toString());
      }
      return [];
    },
    formatDate(date) {
      const months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];

      const d = new Date(date);
      const extension = this.getDayDifference(d, new Date());

      return `${
        months[d.getMonth()]
      } ${d.getDate()}, ${d.getFullYear()} ${extension}`;
    },
    getDayDifference(prev, now) {
      // convert to UTC
      const date2_UTC = new Date(
        Date.UTC(now.getUTCFullYear(), now.getUTCMonth(), now.getUTCDate())
      );
      const date1_UTC = new Date(
        Date.UTC(prev.getUTCFullYear(), prev.getUTCMonth(), prev.getUTCDate())
      );

      //--------------------------------------------------------------
      let days = date2_UTC.getDate() - date1_UTC.getDate();
      if (days < 0) {
        date2_UTC.setMonth(date2_UTC.getMonth() - 1);
        days += this.DaysInMonth(date2_UTC);
      }
      //--------------------------------------------------------------
      let months = date2_UTC.getMonth() - date1_UTC.getMonth();
      if (months < 0) {
        date2_UTC.setFullYear(date2_UTC.getFullYear() - 1);
        months += 12;
      }
      //--------------------------------------------------------------
      const years = date2_UTC.getFullYear() - date1_UTC.getFullYear();

      if (years === 1) return `(${years} year ago)`;

      if (years > 1) return `(${years} years ago)`;

      if (months === 1) return `(${months} month ago)`;

      if (months > 1) return `(${months} months ago)`;

      if (days === 1) return `(${days} day ago)`;

      if (days > 1) return `(${days} days ago)`;

      return "(today)";
    },
    DaysInMonth(date2_UTC) {
      const monthStart = new Date(
        date2_UTC.getFullYear(),
        date2_UTC.getMonth(),
        1
      );
      const monthEnd = new Date(
        date2_UTC.getFullYear(),
        date2_UTC.getMonth() + 1,
        1
      );
      const monthLength = (monthEnd - monthStart) / (1000 * 60 * 60 * 24);
      return monthLength;
    },
  },
};
</script>