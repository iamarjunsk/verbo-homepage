<template>
    <div class="how-it-works-page">
        <HowItWorksSection />
        <CtaSection />
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'default'
})

useHead({
    title: 'How It Works - VerboEdu',
    meta: [
        { name: 'description', content: 'Learn how VerboEdu works. Book a demo, get matched with expert tutors, receive a personalized plan, and achieve your goals.' }
    ]
})
</script>

<style scoped>
.how-it-works-page {
    overflow-x: hidden;
}
</style>
