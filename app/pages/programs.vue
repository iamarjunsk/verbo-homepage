<template>
    <div class="programs-page">
        <ProgramsSection />
        <TestimonialsSection />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'default'
})

useHead({
    title: 'Programs - VerboEdu',
    meta: [
        { name: 'description', content: 'Explore our tailored learning paths. From K-8 foundations to career growth, find the perfect program for your academic journey.' }
    ]
})
</script>

<style scoped>
.programs-page {
    overflow-x: hidden;
}
</style>
