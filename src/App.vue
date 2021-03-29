<template>
	<v-app>
		<v-app-bar app color="primary" dark>
			<div class="d-flex align-center">
				<v-img
					alt="Vuetify Logo"
					class="shrink mr-2 rounded-circle"
					contain
					src="./assets/logo.png"
					transition="scale-transition"
					width="40"
				/>
				<h3>OctaTeste</h3>
			</div>
		</v-app-bar>

		<v-main>
			<Main />
		</v-main>
	</v-app>
</template>

<script>
import Main from "./views/main/main";

export default {
	name: "App",

	components: {
		Main,
	},

	data: () => ({
		//
	}),
};
</script>

<style lang="sass">
</style>
