<template>
	<div
		class="flex items-center justify-center bg-gray-400 mx-[200px] my-[100px] rounded-2xl"
	>
		<div class="w-[600px] h-[300px] p-10">
			<h1 class="mb-4 text-xl font-bold">Login</h1>
			<form @submit.prevent="handleLogin">
				<input
					v-model="form.username"
					class="w-full border p-2 rounded-lg mb-4"
					type="text"
					placeholder="Username"
				/>
				<input
					v-model="form.password"
					class="w-full border p-2 rounded-lg mb-4"
					type="password"
					placeholder="Password"
				/>
				<button
					type="submit"
					class="bg-gray-800 hover:bg-slate-500 transition-all duration-200 w-full text-blue-50 rounded-lg p-2"
				>
					Login
				</button>
			</form>
		</div>
	</div>
</template>

<script lang="ts" setup>
definePageMeta({
	middleware: "guest",
})

const form = ref({
	username: "",
	password: "",
})

const { signIn } = useAuth()

async function handleLogin() {
	try {
		await signIn("credentials", form.value)
		useRouter().push({
			name: "index",
		})
	} catch (error) {
		console.log("error", error)
	}
}
</script>
