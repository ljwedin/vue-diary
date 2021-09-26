<template>
  <div id="app">
    <h1>Vue diary</h1>
    <img alt="Vue logo" src="./assets/logo.png">
    <NewDiaryPostForm :post="post"/>
    <DiaryPosts :diaryPosts="diaryPosts" @save="handleSubmit" />
  </div>
</template>

<script>
import DiaryPosts from './components/DiaryPosts.vue';
import NewDiaryPostForm from './components/NewDiaryPostForm.vue';

export default {
  name: 'App',

  components: {
    DiaryPosts,
    NewDiaryPostForm
  },
  
  data() {
    return {
      diaryPosts: JSON.parse(localStorage.getItem('diaryPosts')),
      post: {
        date: '',
        title: '',
        text: ''
      }
    }
  },
  
  methods: {
    handleSubmit(e) {
      e.preventDefault();

    },
    saveLocalStorage(post) {
      let posts = JSON.parse(localStorage.getItem("diaryPosts"));
      posts.push(post);

      localStorage.setItem("diaryPosts", JSON.stringify(posts))
    }
  },

  mounted() {
    const diaryPost = {
      date: new Date(),
      title: "titel",
      text: "text"
    }

    this.saveLocalStorage(diaryPost);
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
