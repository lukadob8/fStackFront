<template>
    <div>
        <button @click="deletePost()">Delete Post</button>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: "DeletePost",
        props: {
            post_id: {
                type: Number,
                required: true
            }
        },
        methods: {
            deletePost: function() {
                axios.request({
                    url: "http://firstfullstack.ml/api/posts",
                    method: "DELETE",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
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