<template>
    <main class="program-page" v-if="program">
        
        <!-- Navbar included if it's not present globally. Typically Nuxt layouts handle this but we assume it's global. -->

        <!-- Hero Section -->
        <section class="program-hero">
            <div class="hero-bg"></div>
            <div class="hero-container">
                <div class="hero-content animate-fade-in-up">
                    <div class="badge">
                        <span>{{ program.title }}</span>
                    </div>
                    <h1 class="hero-title">{{ program.subtitle }}</h1>
                    <p class="hero-description">{{ program.heroDescription }}</p>
                    <div class="hero-cta">
                        <NuxtLink to="/book" class="btn-primary">Book a Free Demo</NuxtLink>
                    </div>
                </div>
            </div>
        </section>

        <!-- Content Sections -->
        <section class="program-content-area">
            <div class="content-container">
                <div v-for="(section, idx) in program.sections" :key="idx" class="content-section animate-fade-in-up" :style="{ animationDelay: `${idx * 100}ms` }">
                    <h2 class="section-title">{{ section.title }}</h2>
                    
                    <p v-if="section.content" class="section-description">{{ section.content }}</p>
                    
                    <!-- Simple List -->
                    <ul v-if="section.list" class="feature-list">
                        <li v-for="(item, itemIdx) in section.list" :key="itemIdx">
                            <span class="check-icon">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                    <polyline points="20 6 9 17 4 12"></polyline>
                                </svg>
                            </span>
                            {{ item }}
                        </li>
                    </ul>

                    <!-- Structured List (Cards) -->
                    <div v-if="section.structuredList" class="structured-grid">
                        <div v-for="(card, cardIdx) in section.structuredList" :key="cardIdx" class="structured-card">
                            <h3 class="card-title">{{ card.title }}</h3>
                            <p v-if="card.desc" class="card-desc">{{ card.desc }}</p>
                            
                            <ul v-if="card.points" class="card-points">
                                <li v-for="(point, pointIdx) in card.points" :key="pointIdx">
                                    <span class="dot-icon"></span>
                                    {{ point }}
                                </li>
                            </ul>
                        </div>
                    </div>

                    <div v-if="section.footer" class="section-footer">
                        <p>{{ section.footer }}</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Call to action -->
        <section class="cta-section">
            <div class="cta-container animate-fade-in-up delay-300">
                <h2>Start your child’s success journey today</h2>
                <NuxtLink to="/book" class="btn-primary-large">Get Started Now</NuxtLink>
            </div>
        </section>

    </main>
    <div v-else class="not-found">
        <h1>Program Not Found</h1>
        <NuxtLink to="/" class="btn-primary">Back to Home</NuxtLink>
    </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { computed } from 'vue'
import { programData } from '../../data/programs'

const route = useRoute()

const program = computed(() => {
    return programData[route.params.slug]
})
</script>

<style scoped>
/* Base Variables & Utilities */
:root {
  --primary-blue: #2563eb;
  --primary-blue-light: #eff6ff;
  --navy-dark: #0f172a;
  --gray-50: #f8fafc;
  --gray-100: #f1f5f9;
  --gray-200: #e2e8f0;
  --gray-500: #64748b;
  --gray-600: #475569;
  --gray-700: #334155;
  --font-main: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
}

/* Page Layout */
.program-page {
    font-family: var(--font-main);
    background: var(--gray-50);
    min-height: 100vh;
}

/* Animations */
.animate-fade-in-up {
    animation: fadeInUp 0.8s ease backwards;
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.delay-300 { animation-delay: 300ms; }

/* Hero Section */
.program-hero {
    position: relative;
    padding: 140px 0 80px;
    background: white;
    text-align: center;
    overflow: hidden;
    border-bottom: 1px solid var(--gray-200);
}

.hero-bg {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: radial-gradient(circle at top center, var(--primary-blue-light), transparent);
    z-index: 1;
}

.hero-container {
    position: relative;
    z-index: 2;
    max-width: 900px;
    margin: 0 auto;
    padding: 0 24px;
}

.badge {
    display: inline-block;
    padding: 8px 16px;
    background: var(--primary-blue);
    color: white;
    border-radius: 30px;
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 24px;
}

.hero-title {
    font-size: 42px;
    font-weight: 800;
    color: var(--navy-dark);
    line-height: 1.2;
    margin-bottom: 24px;
    letter-spacing: -1px;
}

@media (min-width: 768px) {
    .hero-title {
        font-size: 56px;
    }
}

.hero-description {
    font-size: 18px;
    color: var(--gray-600);
    line-height: 1.7;
    margin-bottom: 40px;
    max-width: 750px;
    margin: 0 auto 40px;
}

.btn-primary {
    display: inline-block;
    padding: 14px 28px;
    background: var(--primary-blue);
    color: white;
    font-weight: 600;
    border-radius: 12px;
    text-decoration: none;
    transition: all 0.3s ease;
    box-shadow: 0 8px 20px rgba(37, 99, 235, 0.25);
}

.btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 12px 24px rgba(37, 99, 235, 0.35);
}

/* Content Sections */
.program-content-area {
    padding: 80px 0;
}

.content-container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 0 24px;
}

.content-section {
    background: white;
    border-radius: 24px;
    padding: 40px;
    margin-bottom: 40px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.03);
    border: 1px solid var(--gray-100);
}

@media (min-width: 768px) {
    .content-section {
        padding: 56px;
    }
}

.section-title {
    font-size: 28px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 24px;
    border-bottom: 2px solid var(--gray-100);
    padding-bottom: 16px;
}

.section-description {
    font-size: 16px;
    color: var(--gray-700);
    line-height: 1.8;
    margin-bottom: 24px;
}

/* Simple List */
.feature-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: grid;
    gap: 16px;
}

@media (min-width: 640px) {
    .feature-list {
        grid-template-columns: repeat(2, 1fr);
    }
}

.feature-list li {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    font-size: 16px;
    color: var(--gray-700);
    line-height: 1.6;
    background: var(--gray-50);
    padding: 16px 20px;
    border-radius: 12px;
    border: 1px solid var(--gray-100);
}

.check-icon {
    color: var(--primary-blue);
    flex-shrink: 0;
    margin-top: 2px;
}

/* Structured Grid */
.structured-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 24px;
    margin-top: 32px;
}

@media (min-width: 768px) {
    .structured-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

.structured-card {
    background: var(--gray-50);
    border-radius: 16px;
    padding: 24px;
    border: 1px solid var(--gray-200);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.structured-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.06);
    border-color: var(--primary-blue-light);
}

.card-title {
    font-size: 18px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 12px;
    line-height: 1.4;
}

.card-desc {
    font-size: 14px;
    color: var(--gray-600);
    line-height: 1.6;
    margin-bottom: 16px;
}

.card-points {
    list-style: none;
    padding: 0;
    margin: 0;
}

.card-points li {
    position: relative;
    padding-left: 16px;
    font-size: 14px;
    color: var(--gray-700);
    line-height: 1.6;
    margin-bottom: 8px;
}

.dot-icon {
    position: absolute;
    left: 0;
    top: 8px;
    width: 6px;
    height: 6px;
    background: var(--primary-blue);
    border-radius: 50%;
}

.section-footer {
    margin-top: 32px;
    padding: 20px;
    background: var(--primary-blue-light);
    color: var(--primary-blue);
    border-radius: 12px;
    font-weight: 600;
    font-size: 15px;
    text-align: center;
}

/* CTA */
.cta-section {
    padding: 80px 0;
    background: var(--navy-dark);
    color: white;
    text-align: center;
}

.cta-container h2 {
    font-size: 36px;
    font-weight: 800;
    margin-bottom: 32px;
}

.btn-primary-large {
    display: inline-block;
    padding: 16px 36px;
    background: var(--primary-blue);
    color: white;
    font-weight: 700;
    font-size: 18px;
    border-radius: 14px;
    text-decoration: none;
    transition: all 0.3s ease;
}

.btn-primary-large:hover {
    transform: scale(1.05);
    background: #1d4ed8;
}

.not-found {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 24px;
    background: var(--gray-50);
}

.not-found h1 {
    font-size: 32px;
    color: var(--navy-dark);
}
</style>
