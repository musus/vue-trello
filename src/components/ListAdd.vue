<template>
	<form :class="classList" @submit.prevent="addList">
		<input type="text"
		v-model="title"
		class="text-input"
		placeholder="リストを追加"
		@focusin="startEditing"
		@focusout="finishEditing"

		>
		<button
		type="submit"
		class="add-button"
		v-if="isEditing || titleExists">
		追加</button>
	</form>
</template>

<script>
	export default {
		data: function() {
			return {
				title: '',
				isEditing: false,
			}
		},
		computed: {
			classList() {
				const classList = ['addList']

				if (this.isEditing) {
					classList.push('active')
				}
				if (this.titleExists) {
					classList.push('addable')
				}
				return classList
			},
			titleExists() {
				return this.title.length > 0
			},
		},
		methods: {
			addList() {
				this.$store.dispatch('addList', { title: this.title})
				this.title = ''
			},
			startEditing() {
				this.isEditing = true
			},
			finishEditing() {
				this.isEditing = false
			},
		}
	}
</script>