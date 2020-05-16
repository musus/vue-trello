<template>

<div>
	<header>
		Task Checker
	</header>
	<main>
		<p class="info-line">
			すべてのタスク: 0
		</p>
		<list-add />
	</main>
</div>

</template>

<script>
	import ListAdd from './ListAdd.vue'

export default {
	components: {
		ListAdd
	}
}
</script>