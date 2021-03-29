<template>
	<v-btn v-bind="$attrs" v-on="$listeners" ref="button">{{text}}</v-btn>
</template>

<script>
export default {
	props: ["text"],
};
</script>

<style lang="sass">
</style>