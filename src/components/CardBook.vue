<template>
	<div>
		<a-card title="Book Data" class="card" @click="onClick">
			<p>Title: {{ title }}</p>
			<p>Author:{{ author }}</p>
			<p>Description: {{ description }}</p>
		</a-card>
	</div>
</template>

<script>
import Vue from "vue";
import Antd from "ant-design-vue";
import "ant-design-vue/dist/antd.css";
Vue.config.productionTip = false;
Vue.use(Antd);
export default {
	name: "CardBook",
	methods: {
		onClick() {
			window.open(
				`https://www.google.com/search?q=${this.title}+${this.author}`
			);
		},
	},
	props: ["title", "author", "description"],
};
</script>
