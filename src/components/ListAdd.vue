<template>
	<form class="addlist" @submit.prevent="addList">
		<input type="text"
		v-model="text"
		class="text-input"
		placeholder="リストを追加"
		>
		<button type="submit" class="add-button">追加</button>
	</form>
</template>

<script>
	export default {
		data: function() {
			return {
				title: '',
			}
		},
		methods: {
			addList: function() {
				this.$store.dispatch('addList', { title: this.title})
				this.title = ''
			}
		}
	}
</script>