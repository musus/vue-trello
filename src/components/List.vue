<template>
	<div class="list">
		<div class="listheader">
			<p class="list-title">{{ title }}</p>
			<div class="deletelist" @click="removeList">x</div>
		</div>
		<card-add :listIdex="listIndex" />
	</div>
</template>

<script>
	import CardAdd from './CardAdd'
	export default {
		components: {
			CardAdd
		},
		props: {
			title: {
				type: String,
				required: true
			},
			listIndex: {
				type: Number,
				required: true
			}
		},
		methods: {
			removeList: function() {
				if(confirm('リストを削除しますか？')){
					this.$store.dispatch('removeList',{ listIndex: this.listIndex })
				}
			},
		}
	}
</script>