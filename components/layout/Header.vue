<template>
	<header class="sticky top-0 z-50 shadow-md dark:bg-slate-800  bg-white">
		<div class="container mx-auto flex items-center justify-between py-4 px-6">
			<!-- Logo -->
			<div class="text-2xl font-bold">
				<a href="/">Jesús Suárez</a>
			</div>

			<!-- Mobile Menu Toggle -->
			<button
				class="block md:hidden p-2 text-gray-400 hover:text-white"
				@click="toggleMobileMenu"
			>
				<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
				</svg>
			</button>

			<!-- Navigation Links -->
				<div
					:class="{
					'hidden': !mobileMenuOpen,
					'block': mobileMenuOpen,
					'md:flex': true,
					}"
					class="absolute top-16 left-0 w-full p-6 md:static md:w-auto md:p-0 md:flex-row"
				>
				<a
					href="#" 
					class="block py-2 text-lg md:py-0 md:ml-6 hover:text-gray-300 transition"
					@click="closeMobileMenu"
				>
					{{ $t('About me')}}
				</a>
				<a 
					href="#skills"
					class="block py-2 text-lg md:py-0 md:ml-6 hover:text-gray-300 transition" 
					@click="closeMobileMenu"
				>
					{{ $t('Skills')}}
				</a>
				<a 
				href="#projects"
				class="block py-2 text-lg md:py-0 md:ml-6 hover:text-gray-300 transition"
				@click="closeMobileMenu"
				>
				{{ $t('Projects')}}
			</a>
			<a 
				href="#contact" 
				class="block py-2 text-lg md:py-0 md:ml-6 hover:text-gray-300 transition" 
				@click="closeMobileMenu"
			>
				{{ $t('Contacto') }}
			</a>
			</div>

			<!-- Theme and Language Switcher -->
			<div class="hidden md:flex items-center space-x-4">
				<UFormGroup name="toggle" label="">
					<UTooltip text="Color theme">
						<UToggle 
							:model-value="isDarkMode"
							on-icon="i-heroicons-moon-20-solid"
							off-icon="i-heroicons-sun-20-solid"
							size="lg"
							@update:model-value="toggleTheme"						
						/>
					</UTooltip>
				</UFormGroup>

				<!--Language toggle -->
				<button class="text-sm" @click="setLocale(locale === 'en' ? 'es' : 'en')">
					{{ locale === 'en' ? 'ES' : 'EN' }}
				</button>
			</div>

		</div>
	</header>
</template>

<script setup lang="ts">
const { setLocale, locale } = useI18n()

// Color mode setup
const colorMode = useColorMode()
const isDarkMode = ref(colorMode.preference ==='dark')

const toggleTheme = () => {
	colorMode.preference = colorMode.preference === 'dark' ? 'light' : 'dark'

	isDarkMode.value = colorMode.preference === 'dark'
}

watch(() => colorMode.preference, (newValue: any) => {
	isDarkMode.value = newValue === 'dark'
})

// Mobile menu state
const mobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

const closeMobileMenu = () => {
  mobileMenuOpen.value = false;
};
</script>
