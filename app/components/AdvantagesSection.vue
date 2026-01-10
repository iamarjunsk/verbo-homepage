<template>
    <section class="advantages section">
        <div class="advantages-container">
            <!-- Section Header -->
            <div class="section-header" ref="headerRef">
                <span class="section-label">THE ADVANTAGE</span>
                <h2 class="section-title">Why Choose VerboEdu?</h2>
                <p class="section-description">
                    We combine the rigor of personalized attention with the collaborative energy of group learning.
                </p>
            </div>

            <!-- Feature Cards -->
            <div class="cards-grid">
                <!-- Card 1: Expert Faculty -->
                <div class="feature-card card-hover" ref="card1Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <path d="M22 10v6M2 10l10-5 10 5-10 5z" />
                            <path d="M6 12v5c0 1 2 3 6 3s6-2 6-3v-5" />
                        </svg>
                    </div>
                    <h3 class="card-title">Expert Faculty</h3>
                    <p class="card-description">
                        Learn from the best educators in the field with years of experience in K-12 and competitive
                        exams.
                    </p>
                </div>

                <!-- Card 2: Personalized Attention -->
                <div class="feature-card card-hover" ref="card2Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2" />
                            <circle cx="12" cy="7" r="4" />
                        </svg>
                    </div>
                    <h3 class="card-title">Personalized Attention</h3>
                    <p class="card-description">
                        Experience 1-on-1 sessions tailored to your unique learning pace, focusing on your specific
                        strengths and weaknesses.
                    </p>
                </div>

                <!-- Card 3: Interactive Groups -->
                <div class="feature-card card-hover" ref="card3Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2" />
                            <circle cx="9" cy="7" r="4" />
                            <path d="M23 21v-2a4 4 0 0 0-3-3.87" />
                            <path d="M16 3.13a4 4 0 0 1 0 7.75" />
                        </svg>
                    </div>
                    <h3 class="card-title">Interactive Groups</h3>
                    <p class="card-description">
                        Join collaborative environments that spark curiosity through peer-to-peer discussion and
                        project-based learning.
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const headerRef = ref(null)
const card1Ref = ref(null)
const card2Ref = ref(null)
const card3Ref = ref(null)

onMounted(() => {
    const observerOptions = {
        threshold: 0.2,
        rootMargin: '0px 0px -50px 0px'
    }

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible')
                observer.unobserve(entry.target)
            }
        })
    }, observerOptions)

    if (headerRef.value) observer.observe(headerRef.value)
    if (card1Ref.value) observer.observe(card1Ref.value)
    if (card2Ref.value) observer.observe(card2Ref.value)
    if (card3Ref.value) observer.observe(card3Ref.value)
})
</script>

<style scoped>
.advantages {
    background-color: white;
}

.advantages-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .advantages-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .advantages-container {
        padding: 0 64px;
    }
}

/* Section Header */
.section-header {
    max-width: 600px;
    margin-bottom: 48px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.7s ease;
}

.section-header.visible {
    opacity: 1;
    transform: translateY(0);
}

.section-label {
    display: inline-block;
    font-size: 13px;
    font-weight: 600;
    color: var(--primary-blue);
    letter-spacing: 1px;
    margin-bottom: 12px;
}

.section-title {
    font-size: 36px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 16px;
    letter-spacing: -0.5px;
}

@media (min-width: 768px) {
    .section-title {
        font-size: 42px;
    }
}

.section-description {
    font-size: 17px;
    color: var(--gray-600);
    line-height: 1.7;
}

/* Cards Grid */
.cards-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 24px;
}

@media (min-width: 768px) {
    .cards-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .cards-grid {
        grid-template-columns: repeat(3, 1fr);
        gap: 32px;
    }
}

/* Feature Card */
.feature-card {
    padding: 32px;
    background: white;
    border: 1px solid var(--gray-200);
    border-radius: 16px;
    opacity: 0;
    transform: translateY(40px);
    transition: all 0.7s ease;
}

.feature-card.visible {
    opacity: 1;
    transform: translateY(0);
}

.feature-card:nth-child(1) {
    transition-delay: 0.1s;
}

.feature-card:nth-child(2) {
    transition-delay: 0.2s;
}

.feature-card:nth-child(3) {
    transition-delay: 0.3s;
}

.feature-card:hover {
    border-color: var(--primary-blue-light);
}

.card-title {
    font-size: 20px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-top: 24px;
    margin-bottom: 12px;
}

.card-description {
    font-size: 15px;
    color: var(--gray-600);
    line-height: 1.7;
}
</style>
