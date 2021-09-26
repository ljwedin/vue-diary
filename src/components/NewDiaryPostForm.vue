<template lang="">
    <div>
        <form @submit="handleSubmit">
            Title: <input type="text" v-model="post.title" id="postTitle"><br />
            Text: <input type="text" v-model="post.text" id="postText"><br />
            <button type="submit">Save post</button>
        </form>
    </div>
</template>
<script>
export default {
    name: "NewDiaryPostForm",

    props: {
        post: {
            type: Object,
        }
    }
}
</script>
<style lang="">
    
</style>