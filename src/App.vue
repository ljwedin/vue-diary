<template>
  <div id="app">
    <h1>Vue diary</h1>
    <img alt="Vue logo" src="./assets/logo.png">
    <DiaryPosts :diaryPosts="diaryPosts" />
  </div>
</template>

<script>
import DiaryPosts from './components/DiaryPosts.vue';

export default {
  name: 'App',

  components: {
    DiaryPosts
  },
  
  data() {
    return {
      diaryPosts: JSON.parse(localStorage.getItem('diaryPosts'))
    }
  },

  mounted() {
    const diaryPostOne = {
      date: new Date(),
      title: "titel",
      text: "text"
    }

    const diaryPostTwo = {
      date: new Date(),
      title: "titel3",
      text: "text2"
    }

    let diaryPosts = [diaryPostOne, diaryPostTwo]
    // console.log(diaryPosts)
    localStorage.setItem("diaryPosts", JSON.stringify(diaryPosts));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
