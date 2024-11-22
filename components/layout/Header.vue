<template>
	<header class="header">
		<nav class="nav">
			<a href="/" class="logo">
				<img src="/" alt="Logo">
			</a>

			<ul class="nav-links">
				<li><a href="#about-me">{{ $t('About me')}}</a></li>
				<li><a href="#projects">{{ $t('Projects')}}</a></li>
				<li><a href="#Skills">{{ $t('Welcome')}}</a></li>
				<li><a href="#Experience">{{ $t('Experience')}}</a></li>
			</ul>

			<div class="actions">
				<button class="theme_switcher" @click="toggleTheme">
					 {{ colorMode.value === 'dark' ? '☀️' : '🌙' }}
				</button>
				<br>
				<br>
				<button @click="setLocale(locale === 'en' ? 'es' : 'en')">
					{{ locale === 'en' ? 'Switch to Spanish' : 'Switch to English' }}
				</button>
			</div>
		</nav>
	</header>
</template>

<script setup lang="ts">
const { setLocale, locale } = useI18n()

const colorMode = useColorMode()
const theme = ref(colorMode.value)

watch(colorMode, (newValue: any) => {
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

.theme_switcher {
	border: none;
	background: transparent;
	cursor: pointer;
	font-size: 1.5rem;
}
</style>