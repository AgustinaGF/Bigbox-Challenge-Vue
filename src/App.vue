<template>
	<div id="app">
		<!-- <h1>API</h1> -->
		<SearchContainer />
		<!-- <img alt="Vue logo" src="./assets/logo.png" />
		<HelloWorld msg="Welcome to Your Vue.js App" /> -->
	</div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import SearchContainer from "./components/SearchContainer";

export default {
	name: "App",
	components: {
		SearchContainer,
	},
};
</script>

<style lang="scss" src="./styles/main.scss"></style>
