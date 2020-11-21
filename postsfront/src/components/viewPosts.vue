<template>
    <div class="grid">
        <h3>Press to see Posts</h3>
        <button @click="getPosts()">Posts</button>
        <div>
            <div class="post" v-for="post in posts" :key="post[3]">
                <h2>{{ post[0] }}</h2>
                <p>{{ post[1] }}</p>
                <h6>{{ post[2] }}</h6>

                <edit-posts :post_id="post[3]"> </edit-posts>
            
                <delete-post :post_id="post[3]"> </delete-post>
                

            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import EditPosts from './editPost.vue'
import DeletePost from './deletePost.vue'
    export default {
        name: "ViewPosts",
        components: {
            EditPosts,
            DeletePost,
        },
        data() {
            return {
                posts: []
            }
        },
        methods: {
            getPosts: function() {
                axios.request({
                    url: "http://firstfullstack.ml/api/posts",
                    method: "GET",
                }).then((response) => {
                    this.posts = response.data
                    console.log(response)
                }).catch((error) => {
                    console.log(error)
                })
            }
        },
    }
</script>

<style scoped>
.gird {
    display: grid;
    align-items: center;
    justify-items: center;
}

.post {
    display: grid;
    align-items: center;
    justify-items: center;
    margin-bottom: 50px;
    margin-top: 30px;
    
    
}

</style>