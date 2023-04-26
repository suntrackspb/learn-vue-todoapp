<template>
  <div class="post">
    <div style="padding: 10px 0">
      <p><strong>Name: </strong>{{ post.title }}</p>
      <p><strong>Desc: </strong>{{ post.body }}</p>
    </div>
    <div class="post__btn">
      <MyButton
        @click="$emit('remove', post)"
        style="margin: 10px"
      >Delete</MyButton>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostItem",
  props: {
    post: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>
.post {
  margin: 10px 0;
  padding-left: 20px;
  border-radius: 10px;
  border-top:   2px solid;
  border-bottom: 2px solid;
  border-right:  2px solid;
  border-left:   10px solid;
  border-color: blueviolet;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #130b13;
}
p {
  padding-bottom: 5px;
}
</style>