<template>
	<header class="bg-gray-800 text-white shadow-md">

		<div class="container mx-auto flex items-center justify-between py-4 px-6">
			<!-- Logo -->
			<div class="text-2xl font-bold">
				<a href="/">My portfolio</a>
			</div>

			<nav class="hidden md:flex space-x-6">
				<a href="#about-me" class="hover:text-gray-300" transition>{{ $t('About me') }}</a>
				<a href="#Skills" class="hover:text-gray-300" transition>{{ $t('Skills') }}</a>
				<a href="#Experience" class="hover:text-gray-300" transition>{{ $t('Experience') }}</a>
				<a href="#projects" class="hover:text-gray-300" transition>{{ $t('Projects') }}</a>
			</nav>

			<div class="flex items-center space-x-4">
				<button class="text-xl" @click="toggleTheme">
					{{ colorMode.value === 'dark' ? '☀️' : '🌙' }}
				</button>

				<button class="text-sm" @click="setLocale(locale === 'en' ? 'es' : 'en')">
					{{ locale === 'en' ? 'ES' : 'EN' }}
				</button>
			</div>
		</div>

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
