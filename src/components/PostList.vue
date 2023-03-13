<template>
	<div class="post" v-for="post in posts" :key="post.id">
    <div>
      <div><strong>Post id: </strong>{{post.id}}</div>
      <input class="input" type="text" v-model="post.name">
    </div>
    <div>
      <button class="button" @click="$emit('remove', post)">Remove</button>
    </div>
	</div>
</template>

<script>
export default{
	props: {
		posts: {
			type: Array,
		}
	},
  data() {
    return {
      post: {
        name: ''
      }
    }
  },
}
</script>

<style scoped>
	.post {
    padding: 15px;
    border: 1px solid grey;
    margin-top: 15px;
    border-radius: 15px;
	}
  .post:hover {
    border: 2px solid darkslateblue;
  }
  .button {
    margin-top: 10px;
    margin-left: 5px;
    width: 10%;
    height: 32px;
    border:1px solid grey;
    border-radius: 10px;
    background: cornflowerblue;
  }
  .input {
    width: 100%;
    height: 32px;
    border:1px solid grey;
    margin-top: 15px;
  }
</style>