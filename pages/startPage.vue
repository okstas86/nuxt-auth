<template>
	<div class="w-full">
		<div class="w-full flex justify-between">
			<div class="mt-20 mx-10">
				<h1 class="text-gray-100 font-bold text-6xl mb-10">
					Building Futures Through Smart Investments
				</h1>
				<p class="text-gray-100 w-[400px] mb-10">
					Fostering Prosperity: Guiding Tomorrow's Achievements with Intelligent
					Investment Choices"
				</p>
				<button
					@click="register"
					class="bg-gray-800 hover:bg-slate-500 text-white px-10 py-4 rounded-lg"
				>
					Get Started
				</button>
			</div>
			<img
				class="mt-10 mr-10 w-[50%] rounded-3xl"
				src="/invest_chart.jpg"
				alt=""
			/>
		</div>
	</div>
</template>

<script setup>
function register() {
	navigateTo("/register")
}
</script>
