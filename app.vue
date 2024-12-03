<template>
  <div class="layout flex flex-col min-h-screen">
    <!-- Header -->
    <Header />

    <!-- Main Content -->
    <main class="container mx-auto flex-grow px-4">
      <section class="py-20">
        <div class="container mx-auto px-6">
          <div class="relative h-16 max-w-3xl mx-auto text-center">
            <h1 class="absolute typing-text text-4xl font-bold mb-6">{{ $t(currentText) }}</h1>
            <p class="text-lg text-gray-600 dark:text-gray-300 mb-4">
              Passionate about building scalable applications and solving complex problems
            </p>
            <div class="flex justify-center gap-4">
              <UButton color="primary" to="#projects">{{ $t('View Projects') }}</UButton>
              <UButton color="gray" to="#contact">{{ $t('Contact Me') }}</UButton>
            </div>
          </div>
        </div>
      </section>
    </main>

     <!-- Skills Section -->
    <section id="skills" class="py-12 bg-white dark:bg-gray-800">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12">{{ $t('Technical Skills') }}</h2>
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <UCard v-for="(category, index) in skills" :key="index">
            <template #header>
              <h3 class="text-xl font-semibold text-center">{{ $t(category.title) }}</h3>
            </template>
            <div class="space-y-2">
              <UBadge
                v-for="skill in category.items"
                :key="skill"
                color="primary"
                class="mr-2"
              >
                {{ $t(skill) }}
              </UBadge>
            </div>
          </UCard>
        </div>
      </div>
    </section>

     <!-- Projects Section -->
    <section id="projects" class="py-16">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12">{{ $t('Featured Projects') }}</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <UCard
            v-for="project in projects"
            :key="project.title"
          >
            <template #header>
              <img :src="project.image" :alt="project.title" class="w-full h-48 object-cover">
            </template>
            <h3 class="text-xl font-semibold mb-2">{{ $t(project.title) }}</h3>
            <p class="text-gray-600 dark:text-gray-300 mb-4">{{ $t(project.description) }}</p>
            <div class="flex flex-wrap gap-2 mb-4">
              <UBadge
                v-for="tech in project.technologies"
                :key="tech"
                color="gray"
              >
                {{ tech }}
              </UBadge>
            </div>
            <template #footer>
              <div class="flex justify-between">
                <UButton
                  v-if="project.demo"
                  color="primary"
                  :to="project.demo"
                  target="_blank"
                >
                  {{ $t('Live Demo')}}
                </UButton>
                <UButton
                  v-if="project.github"
                  color="gray"
                  :to="project.github"
                  target="_blank"
                >
                  GitHub
                </UButton>
              </div>
            </template>
          </UCard>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
  <section id="contact" class="py-16 bg-white dark:bg-gray-800">
    <div class="container mx-auto px-4 max-w-2xl">
      <h2 class="text-3xl font-bold text-center mb-12">Get In Touch</h2>
      <UForm :state="form" @submit="onContactSubmit">
        <UFormGroup label="Name">
          <UInput v-model="form.name" />
        </UFormGroup>
        <UFormGroup label="Email">
          <UInput v-model="form.email" type="email" />
        </UFormGroup>
        <UFormGroup label="Message">
          <UTextarea v-model="form.message" :rows="5" />
        </UFormGroup>
        <div class="text-center">
          <UButton type="submit" color="primary" size="lg">
            Send Message
          </UButton>
        </div>
      </UForm>
    </div>
  </section>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup lang="ts">
import Footer from './components/layout/Footer.vue';
import Header from './components/layout/Header.vue';

interface Skill {
  title: string;
  items: string[];
}

interface Project {
  title: string;
  description: string;
  image: string;
  technologies: string[];
  demo?: string;
  github?: string;
}

interface ContactForm {
  name: string;
  email: string;
  message: string;
}

const skills: Skill[] = [
  {
    title: 'Frontend',
    items: ['Vue.js', 'TypeScript', 'Tailwind CSS', 'HTML/CSS']
  },
  {
    title: 'Backend',
    items: ['Node.js', 'SQL', 'Typescript', 'C#']
  },
  {
    title: 'DevOps & Tools',
    items: ['Git', 'Docker', 'AWS', 'CI/CD', 'Linux']
  },
  {
    title: 'Another skills',
    items: ['Clean Architecture', 'Problem Solving', 'Scrum Methodologies', 'SOLID Principles', 'Object Oriented Programming']
  }
];

const projects: Project[] = [
  {
    title: 'Project One',
    description: 'A full-stack application built with Vue.js and Node.js',
    image: '/api/placeholder/600/400',
    technologies: ['Vue.js', 'Node.js', 'MongoDB'],
    demo: 'https://demo.com',
    github: 'https://github.com'
  }
  // Add more projects as needed
];

// Contact form with TypeScript
const form = reactive<ContactForm>({
  name: '',
  email: '',
  message: ''
});

// Type-safe form submission handler
const onContactSubmit = async (formData: ContactForm): Promise<void> => {
  try {
    console.log('Form submitted:', formData);
    // Add your form submission logic here
  } catch (error) {
    console.error('Error submitting form:', error);
  }
};

const texts = ['Full Stack Software Engineer', 'Backend Engineer', 'Frontend Engineer']
const currentText = ref('')
let currentIndex = 0
let textIndex = 0

function typeText() {
  if (textIndex < texts[currentIndex].length) {
    currentText.value += texts[currentIndex].charAt(textIndex)
    textIndex++
    setTimeout(typeText, 100)
  } else {
    setTimeout(eraseText, 2000)
  }
}

function eraseText() {
  if (textIndex > 0) {
    currentText.value = texts[currentIndex].substring(0, textIndex - 1)
    textIndex--
    setTimeout(eraseText, 50)
  } else {
    currentIndex = (currentIndex + 1) % texts.length
    setTimeout(typeText, 500)
  }
}

onMounted(() => {
  typeText()
})
</script>

<style scoped>
.typing-text {
  position: relative;
  display: inline-block;
  white-space: nowrap;
}

.typing-text::after {
  content: '|';
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: -10px; /* Adjust this value to fine-tune position */
  animation: blink 0.7s steps(2) infinite;
}

@keyframes blink {
  0%, 100% { opacity: 0; }
  50% { opacity: 1; }
}
</style>