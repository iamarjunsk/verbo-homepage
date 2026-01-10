<template>
    <section class="programs-hero">
        <div class="programs-hero-container">
            <!-- Heading -->
            <div class="hero-header animate-fade-in-up">
                <h1 class="hero-title">Tailored Learning Paths</h1>
                <p class="hero-subtitle">
                    Choose between 1-on-1 attention or collaborative group environments designed to accelerate your
                    growth.
                </p>
            </div>

            <!-- Tab Buttons -->
            <div class="tab-buttons animate-fade-in-up delay-200">
                <button class="tab-btn" :class="{ active: activeTab === 'personal' }" @click="activeTab = 'personal'">
                    Personal Tuition
                </button>
                <button class="tab-btn" :class="{ active: activeTab === 'group' }" @click="activeTab = 'group'">
                    Group Classes
                </button>
            </div>

            <!-- Tab Content - Comparison Section -->
            <div class="tab-content animate-fade-in-up delay-300">
                <!-- Personal Tuition Content -->
                <Transition name="fade" mode="out-in">
                    <div v-if="activeTab === 'personal'" key="personal" class="comparison-section">
                        <div class="comparison-header">
                            <div class="comparison-icon personal">
                                <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                    stroke-width="2">
                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2" />
                                    <circle cx="12" cy="7" r="4" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="comparison-title">Personal Tuition</h3>
                                <p class="comparison-subtitle">Dedicated 1-on-1 attention for accelerated learning</p>
                            </div>
                        </div>
                        <div class="comparison-grid">
                            <div class="merits-card">
                                <h4 class="card-label merits">
                                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <polyline points="20 6 9 17 4 12"></polyline>
                                    </svg>
                                    Advantages
                                </h4>
                                <ul class="feature-list">
                                    <li>Fully customized curriculum to your learning pace</li>
                                    <li>Flexible scheduling based on your availability</li>
                                    <li>Immediate feedback and doubt resolution</li>
                                    <li>Focused attention on weak areas</li>
                                    <li>Faster progress and goal achievement</li>
                                </ul>
                            </div>
                            <div class="demerits-card">
                                <h4 class="card-label demerits">
                                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <circle cx="12" cy="12" r="10"></circle>
                                        <line x1="12" y1="8" x2="12" y2="12"></line>
                                        <line x1="12" y1="16" x2="12.01" y2="16"></line>
                                    </svg>
                                    Considerations
                                </h4>
                                <ul class="feature-list">
                                    <li>Higher investment compared to group classes</li>
                                    <li>No peer interaction or group dynamics</li>
                                    <li>May lack competitive motivation</li>
                                </ul>
                            </div>
                        </div>
                        <div class="best-for">
                            <strong>Best for:</strong> Students needing focused attention, busy professionals, or those
                            preparing for competitive exams.
                        </div>
                    </div>

                    <!-- Group Classes Content -->
                    <div v-else key="group" class="comparison-section">
                        <div class="comparison-header">
                            <div class="comparison-icon group">
                                <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                    stroke-width="2">
                                    <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2" />
                                    <circle cx="9" cy="7" r="4" />
                                    <path d="M23 21v-2a4 4 0 0 0-3-3.87" />
                                    <path d="M16 3.13a4 4 0 0 1 0 7.75" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="comparison-title">Group Classes</h3>
                                <p class="comparison-subtitle">Collaborative learning with peer support</p>
                            </div>
                        </div>
                        <div class="comparison-grid">
                            <div class="merits-card">
                                <h4 class="card-label merits">
                                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <polyline points="20 6 9 17 4 12"></polyline>
                                    </svg>
                                    Advantages
                                </h4>
                                <ul class="feature-list">
                                    <li>More affordable than personal tuition</li>
                                    <li>Learn from peers' questions and discussions</li>
                                    <li>Builds teamwork and communication skills</li>
                                    <li>Healthy competition motivates progress</li>
                                    <li>Networking opportunities with like-minded students</li>
                                </ul>
                            </div>
                            <div class="demerits-card">
                                <h4 class="card-label demerits">
                                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <circle cx="12" cy="12" r="10"></circle>
                                        <line x1="12" y1="8" x2="12" y2="12"></line>
                                        <line x1="12" y1="16" x2="12.01" y2="16"></line>
                                    </svg>
                                    Considerations
                                </h4>
                                <ul class="feature-list">
                                    <li>Fixed schedule may not suit everyone</li>
                                    <li>Less individual attention from tutor</li>
                                    <li>Pace set by group, not individual needs</li>
                                </ul>
                            </div>
                        </div>
                        <div class="best-for">
                            <strong>Best for:</strong> Students who thrive in social settings, those on a budget, or
                            learners seeking peer motivation.
                        </div>
                    </div>
                </Transition>
            </div>

            <!-- Program Cards -->
            <div class="programs-grid">
                <div v-for="(program, index) in programs" :key="program.id" class="program-card card-hover"
                    :class="`delay-${(index + 1) * 100}`" ref="cardRefs">
                    <!-- Image -->
                    <div class="program-image">
                        <img :src="program.image" :alt="program.title" />
                    </div>

                    <!-- Content -->
                    <div class="program-content">
                        <div class="program-icon" :style="{ color: program.iconColor }">
                            <component :is="program.icon" />
                        </div>
                        <h3 class="program-title">{{ program.title }}</h3>
                        <p class="program-description">{{ program.description }}</p>
                        <NuxtLink :to="program.link" class="learn-more-btn">
                            Learn More
                        </NuxtLink>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, h } from 'vue'

const activeTab = ref('personal')

// Icon components
const IconFoundation = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M22 10v6M2 10l10-5 10 5-10 5z' }),
    h('path', { d: 'M6 12v5c0 1 2 3 6 3s6-2 6-3v-5' })
])

const IconHighSecondary = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 2, y: 3, width: 20, height: 14, rx: 2 }),
    h('line', { x1: 8, y1: 21, x2: 16, y2: 21 }),
    h('line', { x1: 12, y1: 17, x2: 12, y2: 21 })
])

const IconUniversity = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M3 21h18' }),
    h('path', { d: 'M5 21V7l7-4 7 4v14' }),
    h('path', { d: 'M9 21v-4a2 2 0 0 1 2-2h2a2 2 0 0 1 2 2v4' })
])

const IconCompetitive = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M22 10v6M2 10l10-5 10 5-10 5z' }),
    h('path', { d: 'M6 12v5c0 1 2 3 6 3s6-2 6-3v-5' })
])

const IconCareer = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('polyline', { points: '23 6 13.5 15.5 8.5 10.5 1 18' }),
    h('polyline', { points: '17 6 23 6 23 12' })
])

const programs = ref([
    {
        id: 1,
        title: 'Foundational (K-8)',
        description: 'Build a strong academic base with personalized attention in core subjects.',
        image: 'https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=400&h=250&fit=crop',
        icon: IconFoundation,
        iconColor: '#2563eb',
        link: '/programs/foundation'
    },
    {
        id: 2,
        title: 'Higher Secondary',
        description: 'Excel in board exams and core science, math, and commerce subjects.',
        image: 'https://images.unsplash.com/photo-1427504494785-3a9ca7044f45?w=400&h=250&fit=crop',
        icon: IconHighSecondary,
        iconColor: '#f59e0b',
        link: '/programs/higher-secondary'
    },
    {
        id: 3,
        title: 'University Prep',
        description: 'Navigate university applications and academic entry requirements smoothly.',
        image: 'https://images.unsplash.com/photo-1541339907198-e08756dedf3f?w=400&h=250&fit=crop',
        icon: IconUniversity,
        iconColor: '#0d9488',
        link: '/programs/university'
    },
    {
        id: 4,
        title: 'Competitive Exams',
        description: 'Master SAT, GRE, and GMAT with proven strategic preparation modules.',
        image: 'https://images.unsplash.com/photo-1434030216411-0b793f4b4173?w=400&h=250&fit=crop',
        icon: IconCompetitive,
        iconColor: '#2563eb',
        link: '/programs/competitive'
    },
    {
        id: 5,
        title: 'Career Growth',
        description: 'Upskill for the modern workforce with professional business tutoring.',
        image: 'https://images.unsplash.com/photo-1497215842964-222b430dc094?w=400&h=250&fit=crop',
        icon: IconCareer,
        iconColor: '#059669',
        link: '/programs/career'
    }
])

const cardRefs = ref([])

onMounted(() => {
    const observerOptions = {
        threshold: 0.1,
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

    document.querySelectorAll('.program-card').forEach(card => {
        observer.observe(card)
    })
})
</script>

<style scoped>
.programs-hero {
    padding: 100px 0 60px;
    background: linear-gradient(180deg, #f8fafc 0%, #ffffff 100%);
}

.programs-hero-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .programs-hero-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .programs-hero-container {
        padding: 0 64px;
    }
}

/* Hero Header */
.hero-header {
    text-align: center;
    max-width: 600px;
    margin: 0 auto 40px;
}

.hero-title {
    font-size: 40px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 16px;
    letter-spacing: -1px;
}

@media (min-width: 768px) {
    .hero-title {
        font-size: 48px;
    }
}

.hero-subtitle {
    font-size: 17px;
    color: var(--gray-600);
    line-height: 1.7;
}

/* Tab Buttons */
.tab-buttons {
    display: flex;
    justify-content: center;
    gap: 0;
    margin-bottom: 48px;
    background: var(--gray-100);
    border-radius: 12px;
    padding: 6px;
    width: fit-content;
    margin-left: auto;
    margin-right: auto;
}

.tab-btn {
    padding: 12px 28px;
    font-size: 15px;
    font-weight: 600;
    border: none;
    background: transparent;
    color: var(--gray-600);
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.tab-btn:hover {
    color: var(--navy-dark);
}

.tab-btn.active {
    background: white;
    color: var(--navy-dark);
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

/* Tab Content Transitions */
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(10px);
}

/* Tab Content */
.tab-content {
    margin-bottom: 48px;
}

.comparison-section {
    background: white;
    border-radius: 20px;
    padding: 32px;
    border: 1px solid var(--gray-200);
    box-shadow: 0 4px 24px rgba(0, 0, 0, 0.06);
}

.comparison-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 28px;
}

.comparison-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 56px;
    height: 56px;
    border-radius: 14px;
    flex-shrink: 0;
}

.comparison-icon.personal {
    background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);
    color: var(--primary-blue);
}

.comparison-icon.group {
    background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
    color: #059669;
}

.comparison-title {
    font-size: 24px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 4px;
}

.comparison-subtitle {
    font-size: 15px;
    color: var(--gray-600);
}

.comparison-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
    margin-bottom: 24px;
}

@media (min-width: 768px) {
    .comparison-grid {
        grid-template-columns: 1fr 1fr;
    }
}

.merits-card,
.demerits-card {
    padding: 24px;
    border-radius: 14px;
}

.merits-card {
    background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
    border: 1px solid #bbf7d0;
}

.demerits-card {
    background: linear-gradient(135deg, #fefce8 0%, #fef9c3 100%);
    border: 1px solid #fde047;
}

.card-label {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 15px;
    font-weight: 700;
    margin-bottom: 16px;
}

.card-label.merits {
    color: #059669;
}

.card-label.demerits {
    color: #ca8a04;
}

.feature-list {
    list-style: none;
    padding: 0;
    margin: 0;
}

.feature-list li {
    position: relative;
    padding-left: 20px;
    font-size: 14px;
    color: var(--gray-700);
    line-height: 1.6;
    margin-bottom: 10px;
}

.feature-list li:last-child {
    margin-bottom: 0;
}

.feature-list li::before {
    content: '•';
    position: absolute;
    left: 0;
    color: var(--gray-400);
}

.merits-card .feature-list li::before {
    color: #059669;
}

.demerits-card .feature-list li::before {
    color: #ca8a04;
}

.best-for {
    padding: 16px 20px;
    background: var(--gray-50);
    border-radius: 10px;
    font-size: 14px;
    color: var(--gray-700);
    line-height: 1.6;
}

.best-for strong {
    color: var(--navy-dark);
}

/* Programs Grid */
.programs-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 24px;
}

@media (min-width: 640px) {
    .programs-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .programs-grid {
        grid-template-columns: repeat(5, 1fr);
        gap: 20px;
    }
}

/* Program Card */
.program-card {
    background: white;
    border-radius: 16px;
    overflow: hidden;
    border: 1px solid var(--gray-200);
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.6s ease;
}

.program-card.visible {
    opacity: 1;
    transform: translateY(0);
}

.program-card:nth-child(1) {
    transition-delay: 0.1s;
}

.program-card:nth-child(2) {
    transition-delay: 0.2s;
}

.program-card:nth-child(3) {
    transition-delay: 0.3s;
}

.program-card:nth-child(4) {
    transition-delay: 0.4s;
}

.program-card:nth-child(5) {
    transition-delay: 0.5s;
}

.program-card:hover {
    border-color: var(--primary-blue-light);
}

/* Program Image */
.program-image {
    height: 140px;
    overflow: hidden;
}

.program-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.4s ease;
}

.program-card:hover .program-image img {
    transform: scale(1.05);
}

/* Program Content */
.program-content {
    padding: 20px;
}

.program-icon {
    margin-bottom: 12px;
}

.program-title {
    font-size: 16px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 8px;
}

.program-description {
    font-size: 13px;
    color: var(--gray-600);
    line-height: 1.6;
    margin-bottom: 16px;
    min-height: 60px;
}

/* Learn More Button */
.learn-more-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 10px 16px;
    background: white;
    color: var(--primary-blue);
    font-weight: 600;
    font-size: 13px;
    border-radius: 8px;
    border: 1.5px solid var(--primary-blue);
    text-decoration: none;
    transition: all 0.3s ease;
}

.learn-more-btn:hover {
    background: var(--primary-blue);
    color: white;
}
</style>
