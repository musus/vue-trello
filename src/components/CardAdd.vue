<template>
	<form :class="classList" @submit.prevent="addCardToList">
		<input v-model="body"
			type="text"
			class="text-input"
			placeholder="新しいタスクを追加"
			@focusin="startEditing"
			@focusout="finishEditing"
		/>
		<button type="submit" class="add-button">
			追加
		</button>
	</form>
</template>

<script>
export default {
	props: {
		listIndex: {
			type: Number,
			required: true,
		}
	},
	data: function() {
		return {
			body: '',
			isEditing: false,
		}
	},
	computed: {
		classList() {
			const classList = ['addcard']
			if (this.isEditing) {
				classList.push('active')
			}
			return classList
		}
	},
	methods: {
		startEditing: function() {
			this.isEditing = true
		},
		finishEditing: function() {
			this.isEditing = false
		},
		addCardToList: function() {
			this.$store.dispatch('addCardToList', { body: this.body, listIndex: this.listIndex})
			this.body = ''
		}
	}
}
</script>