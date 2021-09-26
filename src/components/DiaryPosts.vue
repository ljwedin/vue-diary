<template>
    <div id="diaryPostsWrapper">
        <div v-for="(post, i) in diaryPosts" :key="i">
            <h2>{{ post.title }}</h2>
            <h3>{{ post.date }}</h3>
            <p>{{ post.text }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "DiaryPosts",

    props: [ 'diaryPosts' ],
}
</script>

<style>
    
</style>