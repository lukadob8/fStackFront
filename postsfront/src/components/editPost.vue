<template>
    <div>
        <p>New Title</p>
        <input type="text" v-model="title">
        <p>New Post</p>
        <textarea v-model="content"></textarea>
        <br>
        <button @click="editPost()">Edit!</button>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: "EditPost",
        data() {
            return {
                title: "",
                content: "",
            }
        },
        props: {
            post_id: {
                type: Number,
                required: true
            }
        },
        methods: {
            editPost: function() {
                axios.request({
                    url: "http://127.0.0.1:5000/posts",
                    method: "PATCH",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        title: this.title,
                        content: this.content,
                        id: this.post_id
                    }
                }).then((response) => {
                    console.log(response)
                }).catch((error) => {
                    console.log(error)
                })
            }
        },
    }
</script>

<style scoped>

</style>