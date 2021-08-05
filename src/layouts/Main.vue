<template lang="pug">
q-layout(view="lHh Lpr lFf")
	q-header(elevated)
		q-toolbar.glossy(:class="className")
			q-toolbar-title
				|...
			q-btn(flat, dense, round, icon="menu", aria-label="Menu", @click="open")
	q-drawer.bg-drawer(v-model="drawer", show-if-above, bordered)
		.row.justify-center.q-mt-xl
			q-avatar(size="250px", rounded)
				img(src="https://media4.giphy.com/media/69CKkcEr8RuJG/giphy.gif", style="height: 70%")
		q-list.q-mt-sm
			q-item-label
				|Codename: Proyecto S

	q-page-container
		router-view
	
</template>

<script>
	import { ref } from "vue"

	export default {
		setup() {
			const drawer = ref(false)

			return {
				drawer,
				timer: null,
				count: ref(1),
				open: function() {
					drawer.value =! drawer.value
				}
			}
		},
		created: function() {
			this.timer = setInterval(() => {
				this.count = (this.count % 6) + 1
			}, 2000)
		},
		computed: {
			className: function() {
				return `bg bg-${this.count}`
			}
		}
	}
</script>

<style lang="sass">
	.q-drawer--left.q-drawer--bordered
		border-right: 0
	.bg-drawer
		background: #4a4a4a
		.q-list
			.q-item__label
				text-align: center
				color: white
	.bg
		transition: 0.6s linear all
	.bg-0
		background: #113d52
	.bg-1
		background: #0b3634
	.bg-2
		background: #12360b
	.bg-3
		background: #3a400e
	.bg-4
		background: #524111
	.bg-5
		background: #521111
	.bg-6
		background: #481152
</style>