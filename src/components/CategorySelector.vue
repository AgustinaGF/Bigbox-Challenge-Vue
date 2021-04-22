<template>
	<div class="body">
		<div class="header">
			<img alt="logo" :src="logo" class="logo" />;
			<h1 class="titlePage">The New York Times - Books</h1>
		</div>
		<div class="all-container">
			<div class="container-Row">
				<a-row align="middle" justify="center">
					<a-col :span="8">
						<h3 class="filterCategoryText">Filter by category</h3>
					</a-col>
					<a-col :span="12">
						<a-select
							placeholder="Select Category"
							class="select"
							size="large"
							style="width: 100%"
							@change="handleChange"
						>
							<a-select-option
								v-for="category in categories"
								:key="category.list_name_encoded"
								:value="category.list_name"
							>
								{{ category.list_name }}</a-select-option
							>
						</a-select>
					</a-col>
				</a-row>
			</div>
		</div>
	</div>
</template>

<script>
import Vue from "vue";
import logo from "../assets/logo.png";
import Antd from "ant-design-vue";
import "ant-design-vue/dist/antd.css";
Vue.config.productionTip = false;
Vue.use(Antd);

// import { Select } from "antd";
// import { Row, Col } from "antd";
// const { Option } = Select;
// const APIKEY = "HJVz2wUKrZDzMcJgCE6L8SAG43p60Y8Q";

// console.log(this.props);
export default {
	name: "CategorySelector",
	// a esto tengo que hacerle un map
	methods: {
		handleChange(value) {
			console.log(`selected ${value}`);
		},
	},
	props: ["categories"],
	data() {
		return { selectCategoryList: undefined, logo: logo };
	},
};
</script>

<style>
/* @import "ant-design-vue/dist/antd.css"; */
</style>
