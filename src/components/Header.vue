<script>
import { ref } from 'vue';

export default {
	data() {
		return {
			header: [
				{ id: 1, title: 'All Tasks', route: '/' },
				{ id: 2, title: 'Completed Tasks', route: '/completed' },
			],
		};
	},
	computed: {
		isActive() {
			return (route) => this.$route.path == route;
		},
	},
};
</script>

<template>
	<header class="header">
		<div class="container">
			<h1 class="text-3xl font-semibold mb-10">Tasks Manager</h1>
			<div class="header__row flex items-center justify-between pb-2">
				<div class="header__row-tasks-left flex items-center gap-5">
					<div
						v-for="item in header"
						:key="item.id"
						class="cursor-pointer text-[14px] text-[#fff] hover:text-[#999] transition"
						:class="{ active: isActive(item.route) }"
					>
						{{ item.title }}
					</div>
				</div>

				<div
					class="header__row-tasks-right flex items-center gap-[0.5rem]"
				>
					<div
						class="bg-[transparent] p-[0.35rem] rounded cursor-pointer hover:bg-[#222] transition"
					>
						<img
							src="/src/constants/svgs/filter.svg"
							alt=""
							width="17"
							height="17"
						/>
					</div>
					<div
						class="bg-[transparent] p-[0.35rem] rounded cursor-pointer hover:bg-[#222] transition"
					>
						<img
							src="/src/constants/svgs/search.svg"
							alt=""
							width="18"
							height="18"
						/>
					</div>
					<div
						class="bg-[transparent] p-[0.35rem] rounded cursor-pointer hover:bg-[#222] transition"
					>
						<img
							src="/src/constants/svgs/ellipsis.svg"
							alt=""
							width="18"
							height="18"
						/>
					</div>
					<button
						class="flex items-center justify-center gap-2 bg-white hover:bg-[#999] transition text-black rounded-md p-1 px-[0.65rem]"
					>
						<span class="text-[13px] font-medium">New</span>
						<img
							src="/src/constants/svgs/document-plus.svg"
							alt=""
							width="15"
							height="15"
						/>
					</button>
				</div>
			</div>
		</div>
	</header>
</template>
