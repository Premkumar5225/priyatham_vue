<template>
    <div class="news-feed">
    <div v-for="item in newsData" :key="item.id" class="news-item">
    <h2>{{ item.title }}</h2>
    <p>{{ item.description }}</p>
    <p>Source: {{ item.source }}</p>
    <p>Published Date: {{ item.publishedDate }}</p>
    <p>Category: {{ item.newsCategory }}</p>
    </div>
    </div>
    </template>
    
    <script>
    export default {
        name: 'NewsFeedBox',
    props: {
    newsData: Array,
    },
    };
    </script>
    
    <style scoped>
    .news-feed {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      grid-gap: 20px;
    }
    
    .news-item {
      border: 1px solid #ccc;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    </style>
    