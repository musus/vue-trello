<template>
	<div class="list">
		<div class="listheader">
			<p class="list-title">{{ title }}</p>
			<p class="list-counter">合計: {{ totalCardInList }}</p>
			<div class="deletelist" @click="removeList">x</div>
		</div>
		<draggable group="cards" :list="cards" @end="$emit('change')">
			<card v-for="(item, index) in cards"
			:body="item.body"
			:key="item.id"
			:cardIndex="index"
			:listIndex="listIndex"
			/>
		</draggable>
		<card-add :listIndex="listIndex" />
	</div>
</template>

<script>
	import CardAdd from './CardAdd'
	import Card from './Card'
	import draggable from 'vuedraggable'

	export default {
		components: {
			CardAdd,
			Card,
			draggable,
		},
		props: {
			title: {
				type: String,
				required: true
			},
			cards: {
				type: Array,
				required: true
			},
			listIndex: {
				type: Number,
				required: true
			}
		},
		computed: {
			totalCardInList() {
				return this.cards.length
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