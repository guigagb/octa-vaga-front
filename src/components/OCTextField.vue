<template>
	<div class="d-flex flex-column align-start">
		<label>{{$attrs.label}}</label>
		<v-text-field
			v-bind="$attrs"
			v-on="$listeners"
			dense
			label
			outlined
			background-color="#f2f2f2"
			border="#000"
			hide-details
			ref="input"
			height="10px"
		></v-text-field>
	</div>
</template>

<script>
export default {};
</script>

<style lang="sass">
label
	color: #2f2f2f
</style>