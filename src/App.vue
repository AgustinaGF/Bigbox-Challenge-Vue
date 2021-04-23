<template>
	<div id="app">
		<SearchContainer />
	</div>
</template>

<script>
import SearchContainer from "./components/SearchContainer";

export default {
	name: "App",
	components: {
		SearchContainer,
	},
};
</script>

<style lang="scss" src="./styles/main.scss"></style>
