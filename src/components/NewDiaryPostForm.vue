<template>
    <div>
        <form @submit="handleSubmit">
            Title: <input type="text" v-model="post.title" id="postTitle"><br />
            Text: <input type="text" v-model="post.text" id="postText"><br />
            <button>Save post</button>
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
    },

    methods: {
        handleSubmit(e) {
            e.preventDefault();
            this.$emit("save", e);
        }
    }
}
</script>
<style>
    
</style>