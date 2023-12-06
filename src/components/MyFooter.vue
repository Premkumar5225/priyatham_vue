
<template>
  <footer>
    <p>&copy; {{ copyrightYear }} News App. All rights reserved.</p>
  </footer>
</template>

<script>
export default {
  props: {
    copyrightYear: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style scoped>
/* Your footer styles here */
footer {
  background-color: #333;
  color: #fff;
  padding: 10px;
  text-align: center;
}
</style>


