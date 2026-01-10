<template>
    <section class="cta-section">
        <div class="cta-container">
            <div class="cta-card" ref="ctaRef">
                <h2 class="cta-title">Ready to start your journey?</h2>
                <NuxtLink to="/book" class="btn-primary cta-btn">
                    Get Started Now
                </NuxtLink>
                <p class="cta-note">No credit card required for your first demo session.</p>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const ctaRef = ref(null)

onMounted(() => {
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible')
                observer.unobserve(entry.target)
            }
        })
    }, { threshold: 0.3 })

    if (ctaRef.value) observer.observe(ctaRef.value)
})
</script>

<style scoped>
.cta-section {
    padding: 40px 0 100px;
    background: white;
}

.cta-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .cta-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .cta-container {
        padding: 0 64px;
    }
}

.cta-card {
    max-width: 600px;
    margin: 0 auto;
    padding: 48px 40px;
    background: var(--gray-50);
    border-radius: 24px;
    text-align: center;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.7s ease;
}

.cta-card.visible {
    opacity: 1;
    transform: translateY(0);
}

.cta-title {
    font-size: 28px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 28px;
}

@media (min-width: 768px) {
    .cta-title {
        font-size: 32px;
    }
}

.cta-btn {
    padding: 16px 36px;
    font-size: 16px;
    margin-bottom: 20px;
}

.cta-note {
    font-size: 14px;
    color: var(--gray-500);
}
</style>
