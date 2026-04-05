<template>
    <section id="programs" class="programs-hero">
        <div class="programs-hero-container">
            <!-- Heading -->
            <div class="hero-header animate-fade-in-up">
                <h1 class="hero-title">Tailored Learning Paths</h1>
                <p class="hero-subtitle">
                    Choose between 1-on-1 attention or collaborative group environments designed to accelerate your
                    growth.
                </p>
            </div>

            <!-- Unified Programs List -->

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

// Icon components
const IconAcademic = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M4 19.5v-15A2.5 2.5 0 0 1 6.5 2H20v20H6.5a2.5 2.5 0 0 1 0-5H20' })
])

const IconOnline = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 2, y: 3, width: 20, height: 14, rx: 2 }),
    h('line', { x1: 8, y1: 21, x2: 16, y2: 21 }),
    h('line', { x1: 12, y1: 17, x2: 12, y2: 21 })
])

const IconJRBots = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 5, y: 10, width: 14, height: 10, rx: 2 }),
    h('path', { d: 'M12 2v2' }),
    h('circle', { cx: 12, cy: 6, r: 2 }),
    h('path', { d: 'M10 14h4' })
])

const IconFoundation = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M22 10v6M2 10l10-5 10 5-10 5z' }),
    h('path', { d: 'M6 12v5c0 1 2 3 6 3s6-2 6-3v-5' })
])

const IconLanguage = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z' })
])

const IconElap = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('polyline', { points: '23 6 13.5 15.5 8.5 10.5 1 18' }),
    h('polyline', { points: '17 6 23 6 23 12' })
])

const IconMusic = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M9 18V5l12-2v13' }),
    h('circle', { cx: 6, cy: 18, r: 3 }),
    h('circle', { cx: 18, cy: 16, r: 3 })
])

const IconArt = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('circle', { cx: 12, cy: 12, r: 10 }),
    h('circle', { cx: 7, cy: 10, r: 1 }),
    h('circle', { cx: 12, cy: 7, r: 1 }),
    h('circle', { cx: 17, cy: 10, r: 1 }),
    h('path', { d: 'M17 15s-2 3-5 3-5-3-5-3' })
])

const IconRobotics = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('circle', { cx: 12, cy: 12, r: 3 }),
    h('path', { d: 'M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z' })
])

const IconSpace = () => h('svg', {
    width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z' }),
    h('path', { d: 'M12 15l-3-3a22 22 0 0 1 2-3.95A12.88 12.88 0 0 1 22 2c0 2.72-.78 7.5-6 11a22.35 22.35 0 0 1-4 2z' }),
    h('path', { d: 'M9 12H4s.55-3.03 2-4c1.62-1.08 5 0 5 0' }),
    h('path', { d: 'M12 15v5s3.03-.55 4-2c1.08-1.62 0-5 0-5' })
])

const programs = ref([
    {
        id: 1,
        title: 'Academic Tuition',
        description: 'Comprehensive personalized tutoring mapped to school & college curriculum ensuring concept mastery.',
        image: 'https://images.unsplash.com/photo-1577896851231-70ef18881754?w=400&h=250&fit=crop',
        icon: IconAcademic,
        iconColor: '#2563eb',
        link: '/programs/academic'
    },
    {
        id: 2,
        title: 'Online Schooling',
        description: '1-to-1 live interactive sessions via Verbo Learning Platform. Bringing the school experience home.',
        image: 'https://images.unsplash.com/photo-1516321318423-f06f85e504b3?w=400&h=250&fit=crop',
        icon: IconOnline,
        iconColor: '#0d9488',
        link: '/programs/online'
    },
    {
        id: 3,
        title: 'JR BOTS (Ages 7 to 10)',
        description: 'Early exposure to logic and foundational robotics. Making learning playful, engaging, and highly productive.',
        image: 'https://images.unsplash.com/photo-1485827404703-89b55fcc595e?w=400&h=250&fit=crop',
        icon: IconJRBots,
        iconColor: '#f59e0b',
        link: '/programs/jr-bots'
    },
    {
        id: 4,
        title: 'Foundation Program',
        description: 'Structured foundational program for students struggling with basic mathematical operations & language literacy.',
        image: 'https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=400&h=250&fit=crop',
        icon: IconFoundation,
        iconColor: '#2563eb',
        link: '/programs/foundation'
    },
    {
        id: 5,
        title: 'Language Foundation',
        description: 'Exclusive curriculum for students showing gaps in reading, writing and grammar. Cultivates linguistic proficiency.',
        image: 'https://images.unsplash.com/photo-1543269865-cbf427effbad?w=400&h=250&fit=crop',
        icon: IconLanguage,
        iconColor: '#8b5cf6',
        link: '/programs/language'
    },
    {
        id: 6,
        title: 'ELAP (16 yrs+)',
        description: 'Effective Learning & Academic Planning to navigate higher education paths, manage time, and optimize studies.',
        image: 'https://images.unsplash.com/photo-1541339907198-e08756dedf3f?w=400&h=250&fit=crop',
        icon: IconElap,
        iconColor: '#059669',
        link: '/programs/elap'
    },
    {
        id: 7,
        title: 'Music',
        description: 'Online personalized music classes promoting cognitive development and creativity under professional guidance.',
        image: 'https://images.unsplash.com/photo-1511379938547-c1f69419868d?w=400&h=250&fit=crop',
        icon: IconMusic,
        iconColor: '#ec4899',
        link: '/programs/music'
    },
    {
        id: 8,
        title: 'ARTYX',
        description: 'Guided artistic exploration for all ages. Enhance creativity via structured online art & design sessions.',
        image: 'https://images.unsplash.com/photo-1460661419201-fd4cecdf8a8b?w=400&h=250&fit=crop',
        icon: IconArt,
        iconColor: '#f97316',
        link: '/programs/artyx'
    },
    {
        id: 9,
        title: 'Robotics',
        description: 'Real-world problem solving through coding and robotics classes, sparking critical thinking and logic.',
        image: 'https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?w=400&h=250&fit=crop',
        icon: IconRobotics,
        iconColor: '#3b82f6',
        link: '/programs/robotics'
    },
    {
        id: 10,
        title: 'Space Education',
        description: 'Future-focused program enabling young minds to explore astronomy, astrophysics, and cosmic sciences.',
        image: 'https://images.unsplash.com/photo-1446776811953-b23d57bd21aa?w=400&h=250&fit=crop',
        icon: IconSpace,
        iconColor: '#6366f1',
        link: '/programs/space'
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

.program-card:nth-child(6) {
    transition-delay: 0.6s;
}

.program-card:nth-child(7) {
    transition-delay: 0.7s;
}

.program-card:nth-child(8) {
    transition-delay: 0.8s;
}

.program-card:nth-child(9) {
    transition-delay: 0.9s;
}

.program-card:nth-child(10) {
    transition-delay: 1.0s;
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
