<template>
  <form @submit.prevent class="form">
    <MyInput
        v-model="post.title"
        placeholder="Title"
    />
    <MyInput
        v-model="post.body"
        placeholder="Enter text"
    />
    <MyButton
        class="align-end"
        @click="creatPost"
    >Add to base</MyButton>
  </form>
</template>

<script>
export default {
  name: "PostForm",
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    creatPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }

  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}


.align-end {
  align-self: flex-end;
}

</style>