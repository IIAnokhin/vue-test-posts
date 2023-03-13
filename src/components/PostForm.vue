<template>
  <form>
    <h3>Создать пост</h3>
    <input class="input" type="text" v-model="post.name">
    <button class="button" @click.prevent="create">Create</button>
  </form>
</template>

<script>
export default {
	data() {
		return {
			post: {
				name: ''
			}
		}
	},
	methods: {
		create(e) {
			this.post.id = Date.now();
			this.$emit('create', this.post)
			this.post = {
				name: '',
			}
		}
	},
}
</script>

<style scoped>
.input {
  width: 30%;
  height: 32px;
  border:1px solid grey;
  border-radius: 10px;
  margin-top: 15px;
  margin-bottom: 15px;
}
.input:hover {
  border: 1px solid darkslateblue;
}
.button {
  margin-left: 5px;
  width: 10%;
  height: 32px;
  border:1px solid grey;
  border-radius: 10px;
  background: cornflowerblue;
}
</style>