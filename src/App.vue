<template>
  <div id="app">
    <h1>Vue diary</h1>
    <img alt="Vue logo" src="./assets/logo.png">
    <NewDiaryPostForm :post="post" @save="handleSubmit"/>
    <DiaryPosts :diaryPosts="diaryPosts" />
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
    };
  },

  methods: {
    handleSubmit(e) {
      e.preventDefault();

      console.log("event: ", e)
      
      const newPost = {
        date: new Date().toLocaleString(),
        title: e.target.postTitle.value,
        text: e.target.postText.value
      };

      this.saveLocalStorage(newPost);
    },
    saveLocalStorage(post) {
      let posts = JSON.parse(localStorage.getItem("diaryPosts"));
      if (!posts) {
        posts = [];
      }
      posts.push(post);

      this.diaryPosts = posts;

      localStorage.setItem("diaryPosts", JSON.stringify(posts))
    }
  },

  mounted() {
    const diaryPost = {
      date: new Date().toLocaleString(),
      title: "titel",
      text: "text"
    };

    this.saveLocalStorage(diaryPost);
  },

  update() {
    console.log(this.post.title)
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
