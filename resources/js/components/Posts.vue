<template>
    <div>
        <h1>Posts</h1>
        <div v-for="post in posts" :key="post.id">
        	<p>{{ post.post }}</p>
        	<button @click="fetchSinglePost(post.id)">View</button>
        </div>
    </div>
</template>

<script>
export default {
	data () {
		return {
			posts: []
		}
	},
	created() {

		this.fetchPosts();

	},
	methods: {

		fetchPosts() {

			Vue.axios.get('/api/posts')
			.then( response => {

				console.log(response);
				this.posts = response.data;

			})
			.catch(error => {

				console.log(error)

			})
			.then(() => {

				console.log('Success')

			})
		},
		fetchSinglePost(post) {

			Vue.axios.get('/api/post/' + post)
			.then(response => {

				console.log(response);

			})

		}

	}
}
</script>

<style>

</style>
