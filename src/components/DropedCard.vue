<template>
	<div class="component-droped-card">
		<label @click="$emit('deleteElement')" class="btn-close">x</label>
		<div class="mt-2">
			<slot></slot>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		index: { type: Number, required: true },
	},
};
</script>

<style lang="sass">
.component-droped-card
    width: 100%
    border: 1px dashed #2f2f2f
    border-radius: 5px
    padding: 5px

.component-droped-card .btn-close
    float: right
    font-weight: bold
</style>