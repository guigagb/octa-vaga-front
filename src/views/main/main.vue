<template>
	<div id="main">
		<div class="toolbox pa-2 d-flex flex-column">
			<label>Toolbox</label>
			<drag class="drag" :transfer-data="{ type: 'input' }">
				<oc-text-field label="input text" :disabled="true"></oc-text-field>
			</drag>
			<v-divider class="my-4"></v-divider>
			<drag class="drag" :transfer-data="{ type: 'checkbox' }">
				<div class="flex flex-column align-start">
					<label>Checkbox</label>
					<oc-checkbox label="opção 1" :disabled="true"></oc-checkbox>
					<oc-checkbox label="opção 2" :disabled="true"></oc-checkbox>
				</div>
			</drag>
			<v-divider class="my-4"></v-divider>
			<drag class="drag" :transfer-data="{type: 'button'}">
				<div class="flex flex-column">
					<label>Button</label>
					<br />
					<oc-button :disabled="true" :text="'OK'"></oc-button>
				</div>
			</drag>
		</div>
		<div class="pa-2 flex-grow-1">
			<drop
				class="drop flex-grow-1 pa-2"
				:class="{ over }"
				@dragover="over = true"
				@dragleave="over = false"
				@drop="handleDrop"
			>
				<DropedCard class="my-2" v-for="(element, i) in elements" :key="i" :index="i">
					<oc-text-field v-if="element.type == 'input'" label="input text" :disabled="true"></oc-text-field>
					<oc-checkbox v-else-if="element.type == 'checkbox'" label="opção 2" :disabled="true"></oc-checkbox>
					<oc-button v-else-if="element.type == 'button'" :disabled="true" :text="'OK'"></oc-button>
				</DropedCard>
			</drop>
		</div>
		<!-- <v-row>
			<v-col md="3" cols="12" class="toolbox">
				a
				<drag class="drag" :transfer-data="{ example: 'styling' }">
					<oc-text-field></oc-text-field>
				</drag>
				<drag class="drag" :transfer-data="{ example: 'styling' }">drag</drag>
			</v-col>
			<v-col md="9" cols="12">
				<drop
					class="drop"
					:class="{ over }"
					@dragover="over = true"
					@dragleave="over = false"
					@drop="handleDrop"
				>drop</drop>
			</v-col>
		</v-row>-->
	</div>
</template>

<script>
import { Drag, Drop } from "vue-drag-drop";
import OcTextField from "../../components/OCTextField";
import OcCheckbox from "../../components/OCCheckbox";
import OcButton from "../../components/OCButton";
import DropedCard from "../../components/DropedCard";

export default {
	components: { Drag, Drop, OcTextField, OcCheckbox, OcButton, DropedCard },
	data() {
		return {
			over: false,
			elements: [],
		};
	},
	methods: {
		handleDrop(data) {
			console.log(data.type);
			this.elements.push({
				type: data.type,
			});
		},
	},
};
</script>

<style lang="sass">
#main
	height: 100%
	display: flex

#main .toolbox
	background-color: #b9b9b9
	display: flex
	min-width: 250px

.drag
	box-sizing: border-box
	display: inline-block
	border-radius: 10px
	vertical-align: middle
	margin-right: 20px
	position: relative
	padding: 5px

.drop
	box-sizing: border-box
	display: inline-block
	border-radius: 10px

.drag
	color: #fff
	cursor: move

.drop
	background: #eee
	border-top: 2px solid #ccc
	border-left: 2px solid #ddd
	min-height: 100px
	width: 100%

.drop.over
	border-color: #aaa
	background: #ccc
</style>