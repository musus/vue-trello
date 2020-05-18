<template>

<div>
	<header>
		Task Checker
	</header>
	<main>
		<p class="info-line">
			すべてのタスク: 0
		</p>
		<div class="list-index">
			<list v-for="(item, index) in lists"
				:key="item.id"
				:title="item.title"
				:cards="item.cards"
				:listIndex="index"
			/>
			<list-add />
		</div>
	</main>
</div>

</template>

<script>
	import ListAdd from './ListAdd'

	import List from './List'
	import { mapState } from 'vuex'

export default {
	components: {
		ListAdd,
		List,
	},
	computed: {
		...mapState([
			'lists'
		]),
	},
}
</script>