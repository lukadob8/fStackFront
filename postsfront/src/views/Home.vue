<template>
  <div class="home">
    <make-posts> </make-posts>
    <view-posts> </view-posts>

  </div>
</template>

<script>
import MakePosts from '../components/makePosts.vue'
import ViewPosts from '../components/viewPosts.vue'
export default {
  name: "Home",
  components: {
    ViewPosts,
    MakePosts,
  }
};
</script>
