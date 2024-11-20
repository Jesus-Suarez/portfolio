<template>
	<header class="header">
		<nav class="nav">
			<a href="/" class="logo">
				<img src="/" alt="Logo">
			</a>

			<ul class="nav-links">
				<li><a href="#about-me">About me</a></li>
				<li><a href="#projects">Projects</a></li>
				<li><a href="#Skills">Skill and Technologies</a></li>
				<li><a href="#Experience">Experience</a></li>
			</ul>

			<div class="actions">
				<button @click="toggleTheme" class="theme_switcher">
					{{ theme === 'dark' ? '☀️' : '🌙' }}
				</button>

				<select v-model="selectedLocale" class="language-switcher">
					<option value="en">English</option>
					<option value="es">Español</option>
				</select>
			</div>
		</nav>
	</header>
</template>

<script setup lang="ts">
const selectedLocale: string = 'en';

const colorMode = useColorMode()
const theme = ref(colorMode.value)
watch(colorMode, (newValue:any) => {
	theme.value = newValue
})

const toggleTheme = () => {
	colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark'
}

</script>

<style>
body {
	background-color: #fff;
	color: rgba(0, 0, 0, 0.8);
}

.dark-mode body {
	background-color: #091a28;
	color: #ebf4f1;
}
</style>