<template>
    <div class="header">
      <h1>{{ title }}</h1>
      <p>{{ subTitle }}</p>
      <p>By: {{ yourName }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      subTitle: {
        type: String,
        required: true,
      },
      yourName: {
        type: String,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .header {
    background-color: #4CAF50;
    color: white;
    text-align: center;
    padding: 1em;
  }
  </style>
  
  
