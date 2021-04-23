<template>
	<div class="searchBox">
		<a-input-search
			class="search"
			placeholder="Search by title"
			enter-button="Search"
			:disabled="disabled"
			size="large"
			style="width:60%"
			@search="onSearch"
			@change="onChange"
		/>

		<div class="container-card" v-if="cardBookVisible && !showErrorMessage">
			<card-book
				:title="bookTitle"
				:author="authorBook"
				:description="descriptionBook"
			></card-book>
		</div>
		<div v-if="!cardBookVisible && !showErrorMessage">
			<div class="container-message">
				<alert-not-found></alert-not-found>
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
import CardBook from "./CardBook.vue";
import AlertNotFound from "./Message.vue";
export default {
	name: "SearchBox",
	components: {
		CardBook,
		AlertNotFound,
	},
	methods: {
		onChange() {
			this.cardBookVisible = false;
			this.showErrorMessage = true;
		},
		onSearch(value) {
			const booksForCategory = this.arrayResultsForCategory.data.results.books;

			const titleBookSearch = value.toUpperCase();

			const searchResult = booksForCategory.filter(
				(titleBook) => titleBook.title === titleBookSearch
			);

			if (searchResult[0]) {
				this.showErrorMessage = false;
				this.cardBookVisible = true;
			} else {
				this.cardBookVisible = false;
				this.showErrorMessage = false;
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
