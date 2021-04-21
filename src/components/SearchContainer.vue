<template>
	<!-- <h1>probando endpoint</h1> -->
	<div class="loading" v-if="isLoading">
		<img alt="loading" :src="gifLoading" />;
	</div>
	<div v-else>
		<category-selector :categories="books"></category-selector>
	</div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import loading from "../assets/loading.gif";
// import CategorySelector from "../components/CategorySelector";
import CategorySelector from "./CategorySelector.vue";
// import CategorySelector from './CategorySelector.vue';
const APIKEY = "HJVz2wUKrZDzMcJgCE6L8SAG43p60Y8Q";
let categoryList = [];
Vue.use(axios);
export default {
	name: "SearchContainer",
	components: {
		CategorySelector,
	},
	data() {
		return { books: undefined, isLoading: true, gifLoading: loading };
	},
	mounted() {
		axios
			.get(
				`https://api.nytimes.com/svc/books/v3/lists/names.json?api-key=${APIKEY}`
			)
			.then((resp) => {
				let data = resp.data.results;
				for (let index = 0; index < 10; index++) {
					const element = data[index];
					categoryList.push(element);
				}
				this.books = categoryList;
				this.isLoading = false;
				console.log(resp);
				console.log(data);
				console.log(categoryList);
				console.log(this.books);
				console.log(this.isLoading);
			});
	},
};
</script>
