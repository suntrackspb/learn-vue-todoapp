<template>
  <div class="app">
    <div class="app__head">
      <h1>Posts Page</h1>
      <MyButton
          @click="showDialog"
      >Add Post</MyButton>
    </div>

    <MyDialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </MyDialog>

    <post-list
        :posts="posts"
        @remove="removePost"
        v-if="!isPostLoaded"
    />
    <div v-else>
      <MyLoader></MyLoader>
    </div>
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/MyButton";
import MyLoader from "@/components/UI/MyLoader.vue";
import axios from "axios";
export default {
  components: {
    MyButton,
    PostList,
    PostForm,
    MyLoader
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoaded: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
      this.dialogVisible=false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
    async fetchPosts()
    {
      try {
        this.isPostLoaded = true;
        setTimeout(async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
          this.posts = response.data
          this.isPostLoaded = false;
        }, 1000)
      } catch (e) {
        console.log(`Error: ${e}`)
      }
      finally {

      }
    }
  },
  mounted() {
    this.fetchPosts()
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: #212121;
  color: white;
}
.app {
  padding: 20px;
}
.app__head {
  display: flex;
  justify-content: space-between;
  padding-bottom: 50px;
}
</style>
