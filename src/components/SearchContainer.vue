<template>
	<div class="loading" v-if="isLoading">
		<img alt="loading" :src="gifLoading" />;
	</div>
	<div v-else>
		<category-selector :categories="books"></category-selector>
	</div>
</template>

<script>
import Vue from "vue";
import VueAxios from "vue-axios";
import axios from "axios";
import loading from "../assets/loading.gif";

import CategorySelector from "./CategorySelector.vue";

const APIKEY = "HJVz2wUKrZDzMcJgCE6L8SAG43p60Y8Q";
let categoryList = [];
Vue.use(VueAxios, axios);
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
			});
	},
};
</script>
