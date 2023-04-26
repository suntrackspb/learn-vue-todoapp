<template xmlns="http://www.w3.org/1999/html">
  <div v-if="posts.length > 0">
    <h3>Posts List</h3>
    <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </div>
  <div v-else>
    <h2>Posts is empty</h2>
  </div>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  name: "PostList",
  components: {PostItem},
  props:{
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>