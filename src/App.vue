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
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/MyButton";
export default {
  components: {
    MyButton,
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'Name 1', body: 'Text 1'},
        {id: 2, title: 'Name 2', body: 'Text 2'},
        {id: 3, title: 'Name 3', body: 'Text 3'},
        {id: 4, title: 'Name 4', body: 'Text 4'},
      ],
      dialogVisible: false,
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
    }
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
