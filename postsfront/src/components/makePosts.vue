<template>
    <div>
        <p>Title of your post</p>
        <input id="title" type="text" v-model="title">
        <p>Your Post</p>
        <textarea id="content" v-model="content"></textarea>
        <br>
        <button @click="addPost()">Post!</button>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: "MakePosts",
        data() {
            return {
                title: "",
                content: "",
            }
        },
        methods: {
            addPost: function() {
                axios.request({
                    url: "http://firstfullstack.ml/api/posts",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        title: this.title,
                        content: this.content
                    }
                }).then((response) => {
                    console.log(response)
                    document.getElementById("title").value="";
                    document.getElementById("content").value="";
                }).catch((error) => {
                    console.log(error)
                })
            }
        },
    }
</script>

<style scoped>

</style>