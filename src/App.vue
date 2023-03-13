<template>
	<div class="app">
    <div>
      <post-form @create="create"></post-form>
      <div class="search">
        <h3>Search</h3>
        <input class="input" type="text" v-model="searchName">
      </div>
    </div>

		<post-list :posts="searchPosts" @remove="remove"></post-list>
	</div>
</template>

<script>
import PostList from './components/PostList.vue'
import PostForm from './components/PostForm.vue'
import json from './test.json'

export default {
	components: {
		PostList,
		PostForm
	},
	data() {
		return {
      data: json.posts,
      searchName: ''
		}
	},
  methods: {
    create(post) {
      this.data.push(post)
    },
    remove(post) {
      this.data = this.data.filter(p => p.id !== post.id)
    },
  },
  computed: {
    searchPosts() {
      return [...this.data].filter(p => p.name.includes(this.searchName))
    }
  }
}
</script>
<style>
	*{
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	.app {
		padding: 20px;
	}
  .input {
    width: 30%;
    height: 32px;
    border:1px solid grey;
    border-radius: 10px;
    margin-top: 15px;
  }
</style>