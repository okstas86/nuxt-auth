<template>
	<div class="w-full h-16 bg-gray-200 flex items-center justify-between">
		<img class="mx-10" src="/logo.svg" alt="logo" />
		<div class="w-[250px] flex justify-around mx-10">
			<button
				@click="handleAuthentication"
				class="w-[100px] bg-gray-800 hover:bg-slate-500 px-5 py-2 text-white rounded-lg"
			>
				{{ isAuthenticated ? "Logout" : "Login" }}
			</button>
			<button
				@click="register"
				class="w-[100px] bg-gray-800 hover:bg-slate-500 px-5 py-2 text-white rounded-lg"
			>
				Register
			</button>
		</div>
	</div>
</template>

<script setup>
const { signOut, status } = useAuth()
const isAuthenticated = ref(false)

async function handleLogout() {}

async function handleAuthentication() {
	if (status.value === "authenticated") {
		console.log(status.value)
		await signOut()
		isAuthenticated.value = false
	}
	if (status.value === "unauthenticated") {
		console.log(status.value)
		return navigateTo("/login")
	}
	console.log(isAuthenticated.value)
}

function register() {
	navigateTo("/register")
}
</script>
