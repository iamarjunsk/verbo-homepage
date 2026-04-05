<template>
    <section class="advantages section">
        <div class="advantages-container">
            <!-- Section Header -->
            <div class="section-header" ref="headerRef">
                <span class="section-label">THE ADVANTAGE</span>
                <h2 class="section-title">Why Choose VERBO?</h2>
                <p class="section-description">
                    We combine the rigor of personalized attention with the collaborative energy of group learning.
                </p>
            </div>

            <!-- Feature Cards -->
            <div class="cards-grid">
                <!-- Card 1 -->
                <div class="feature-card card-hover" ref="card1Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2" />
                            <circle cx="12" cy="7" r="4" />
                        </svg>
                    </div>
                    <h3 class="card-title">Need-based Customization</h3>
                    <p class="card-description">
                        One-on-one sessions structured entirely around the student's individual capability, learning speed, and specific academic or skill goals.
                    </p>
                </div>

                <!-- Card 2 -->
                <div class="feature-card card-hover" ref="card2Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14" />
                            <polyline points="22 4 12 14.01 9 11.01" />
                        </svg>
                    </div>
                    <h3 class="card-title">Verified, Top Tier Educators</h3>
                    <p class="card-description">
                        Learn from thoroughly vetted teachers with proven track records.
                    </p>
                </div>

                <!-- Card 3 -->
                <div class="feature-card card-hover" ref="card3Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <rect x="2" y="3" width="20" height="14" rx="2" />
                            <line x1="8" y1="21" x2="16" y2="21" />
                            <line x1="12" y1="17" x2="12" y2="21" />
                        </svg>
                    </div>
                    <h3 class="card-title">Real World Application</h3>
                    <p class="card-description">
                        Projects, coding, robotics, and applied learning meant to move beyond rote memorization.
                    </p>
                </div>

                <!-- Card 4 -->
                <div class="feature-card card-hover" ref="card4Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <line x1="12" y1="1" x2="12" y2="23" />
                            <path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6" />
                        </svg>
                    </div>
                    <h3 class="card-title">Transparent & Affordable Pricing</h3>
                    <p class="card-description">
                        Providing high-quality education globally without imposing a financial strain on families.
                    </p>
                </div>

                <!-- Card 5 -->
                <div class="feature-card card-hover" ref="card5Ref">
                    <div class="icon-container">
                        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#2563eb" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round">
                            <circle cx="12" cy="12" r="10" />
                            <line x1="2" y1="12" x2="22" y2="12" />
                            <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z" />
                        </svg>
                    </div>
                    <h3 class="card-title">Global Reach, Local Approach</h3>
                    <p class="card-description">
                        Understanding diverse curriculums and student mentalities worldwide to deliver localized excellence.
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
const card4Ref = ref(null)
const card5Ref = ref(null)

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
    if (card4Ref.value) observer.observe(card4Ref.value)
    if (card5Ref.value) observer.observe(card5Ref.value)
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
