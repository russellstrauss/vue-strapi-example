<script>
	import axios from 'axios';
	export default {
		data() {
			return {
				count: 0,
				items: []
			}
		},

		methods: {
			increment() {
				this.count++
			}
		},

		mounted() {
			
			let environment = "http://localhost:1337";
			let worksEndpoint = environment + "/api/works";
			axios.get(worksEndpoint).then((response) => {
				this.items = response.data.data;
			});
			this.increment();
			console.log(`The initial count is ${this.count}.`)
		}
	}
</script>

<template>
	<div>
		
		<h1>You did it!</h1>
		<p>
			Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
			documentation
		</p>
		
		<ul>
			<li class="item" v-for="(item, index) in items" :key="item.documentId" :data-index="index">
				<!-- {{ item }} -->
				Title: {{ item.title }} <br />
				Intro: {{ item.intro }} <br />
				RTE: {{ item.content }} <br />
			</li>
		</ul>
	</div>
</template>

<style scoped></style>
