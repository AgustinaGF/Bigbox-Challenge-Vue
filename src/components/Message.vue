<template>
	<div>
		<a-alert
			message="Book Not Found"
			description="The title wasn't found in this category, please try again!"
			type="error"
			closable
			@close="onClose"
			style="borderColor: #cc4e37"
		/>
	</div>
</template>

<script>
export default {
	name: "AlertNotFound",
	methods: {
		onClose(e) {
			console.log(e, "I was closed.");
		},
	},
};
</script>
