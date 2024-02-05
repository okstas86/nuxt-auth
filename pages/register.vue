<template>
	<div
		class="flex items-center justify-center bg-gray-400 mx-[200px] my-[100px] rounded-2xl"
	>
		<div class="w-[600px] h-[350px] p-10">
			<h1 class="mb-4 text-xl font-bold">Register</h1>
			<form @submit.prevent="handleFormSubmit">
				<input
					class="w-full border p-2 rounded-lg mb-4"
					type="email"
					placeholder="Email"
					v-model="form.email"
				/>
				<input
					class="w-full border p-2 rounded-lg mb-4"
					type="text"
					placeholder="Username"
					v-model="form.username"
				/>
				<input
					class="w-full border p-2 rounded-lg mb-4"
					type="password"
					placeholder="Password"
					v-model="form.password"
				/>
				<button
					:disabled="isLoading"
					type="submit"
					class="bg-gray-800 hover:bg-slate-500 transition-all duration-200 w-full text-blue-50 rounded-lg p-2"
					:class="{ 'opacity-50 cursor-not-allowed': isLoading }"
				>
					Register
				</button>
			</form>
		</div>
	</div>
</template>

<script lang="ts" setup>
import { ref } from "vue"
const form = ref({
	email: "",
	username: "",
	password: "",
})

const isLoading = ref(false)

async function handleFormSubmit() {
	try {
		isLoading.value = true
		await useFetch("api/auth/register", {
			method: "POST",
			body: form.value,
		})
		useRouter().push({
			name: "login",
		})
	} catch (e: any) {
		console.log(e.message)
	} finally {
		isLoading.value = false
	}
}
</script>
