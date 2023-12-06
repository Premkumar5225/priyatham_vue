<template>
  <div id="app">
    <MyHeader :title="appTitle" :subTitle="appSubTitle" :yourName="yourName" />

    <NewsFeedBox :newsData="newsFeedItems" />

    <MyFooter :copyrightYear="currentYear" />

    <div v-if="loading">Loading...</div>
    <div v-if="error">{{ error }}</div>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import NewsFeedBox from './components/NewsFeedBox.vue';
import MyFooter from './components/MyFooter.vue';

export default {
  name: 'App',
  components: {
    MyHeader,
    NewsFeedBox,
    MyFooter,
  },
  data() {
    return {
      appTitle: 'News App',
      appSubTitle: 'Stay Informed',
      yourName: 'PK',
      newsFeedItems: [],
      currentYear: new Date().getFullYear(),
      loading: true,
      error: null,
    };
  },
  methods: {
    async fetchNewsFeed() {
      try {
        const response = await fetch('https://priyatham.onrender.com/api');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }

        const data = await response.json();
        return data[0]['news'];
      } catch (error) {
        console.error('Error fetching news feed:', error.message);
        this.error = 'Error fetching data. Please try again later.';
        return [];
      } finally {
        this.loading = false;
      }
    },
  },
  async created() {
    this.newsFeedItems = await this.fetchNewsFeed();

    console.log(this.newsFeedItems);
  },
};
</script>

<style>
body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}

#app {
  text-align: center;
  margin-top: 20px;
}

#app div {
  margin-top: 10px;
  font-weight: bold;
  color: black;
}

.loading {
  color: #00f;
}

.error {
  color: #f00;
}
</style>