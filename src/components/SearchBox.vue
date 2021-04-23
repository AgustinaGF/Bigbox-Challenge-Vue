<template>
	<div class="searchBox">
		<a-input-search
			class="search"
			placeholder="Search by title"
			enter-button="Search"
			:disabled="disabled"
			size="large"
			@search="onSearch"
			@change="onChange"
		/>

		<div v-if="cardBookVisible && !showErrorMessage">
			<div class="container-card">
				<h1>aca va el componente CARDBOOK</h1>
			</div>
		</div>
		<div v-if="!cardBookVisible && !showErrorMessage">
			<div class="container-message">
				<h1>aca va el componente ALERT</h1>
			</div>
		</div>
	</div>
</template>

<script>
import Vue from "vue";
import Antd from "ant-design-vue";
import "ant-design-vue/dist/antd.css";
Vue.config.productionTip = false;
Vue.use(Antd);
export default {
	name: "SearchBox",
	methods: {
		onChange() {
			this.cardBookVisible = false;
			this.showErrorMessage = true;
		},
		onSearch(value) {
			console.log(value);

			const booksForCategory = this.arrayResultsForCategory.data.results.books;

			const titleBookSearch = value.toUpperCase();

			const searchResult = booksForCategory.filter(
				(titleBook) => titleBook.title === titleBookSearch
			);
			console.log(searchResult, "ayy");
			if (searchResult[0]) {
				this.showErrorMessage = false;
				this.cardBookVisible = true;
				console.log("existe");
			} else {
				this.cardBookVisible = false;
				this.showErrorMessage = false;
				console.log("no existe");
			}
			searchResult.forEach((element) => {
				const title = element.title;
				const description = element.description;
				const author = element.author;
				this.bookTitle = title;
				this.authorBook = author;
				this.descriptionBook = description;
			});
		},
	},

	props: ["arrayResultsForCategory", "disabled"],

	data() {
		return {
			cardBookVisible: false,
			showErrorMessage: true,
			bookTitle: undefined,
			authorBook: undefined,
			descriptionBook: undefined,
		};
	},
};
</script>
