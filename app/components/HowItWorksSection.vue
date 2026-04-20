<template>
    <section class="how-it-works">
        <div class="how-it-works-container">
            <!-- Header -->
            <div class="section-header animate-fade-in-up">
                <h1 class="section-title">How VERBO Works</h1>
                <p class="section-subtitle">
                    A Simple Path to Personalized Learning. We follow a step-by-step approach to ensure every student receives the right guidance, support, and results.
                </p>
            </div>

            <!-- Steps Container -->
            <div class="steps-container">
                <div class="steps-grid">
                    <div v-for="(step, index) in steps" :key="step.id" class="step-item" ref="stepRefs">
                        <div class="step-icon" :style="{ animationDelay: `${index * 150}ms` }">
                            <component :is="step.icon" />
                            <span class="step-badge">{{ index + 1 }}</span>
                        </div>
                        <h3 class="step-title">{{ step.title }}</h3>
                        <p class="step-description">{{ step.description }}</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, h } from 'vue'

// Icon components
const IconInfo = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('circle', { cx: 12, cy: 12, r: 10 }),
    h('line', { x1: 12, y1: 16, x2: 12, y2: 12 }),
    h('line', { x1: 12, y1: 8, x2: 12.01, y2: 8 })
])

const IconUser = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2' }),
    h('circle', { cx: 12, cy: 7, r: 4 })
])

const IconCalendar = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 3, y: 4, width: 18, height: 18, rx: 2 }),
    h('line', { x1: 16, y1: 2, x2: 16, y2: 6 }),
    h('line', { x1: 8, y1: 2, x2: 8, y2: 6 }),
    h('line', { x1: 3, y1: 10, x2: 21, y2: 10 })
])

const IconPlan = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2' }),
    h('circle', { cx: 9, cy: 7, r: 4 }),
    h('path', { d: 'M22 21v-2a4 4 0 0 0-3-3.87' }),
    h('path', { d: 'M16 3.13a4 4 0 0 1 0 7.75' })
])

const IconWallet = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M21 12V7H5a2 2 0 0 1 0-4h14v4' }),
    h('path', { d: 'M3 5v14a2 2 0 0 0 2 2h16v-5' }),
    h('path', { d: 'M18 12a2 2 0 0 0 0 4h4v-4Z' })
])

const IconApp = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 5, y: 2, width: 14, height: 20, rx: 2 }),
    h('line', { x1: 12, y1: 18, x2: 12.01, y2: 18 })
])

const IconChart = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('line', { x1: 18, y1: 20, x2: 18, y2: 10 }),
    h('line', { x1: 12, y1: 20, x2: 12, y2: 4 }),
    h('line', { x1: 6, y1: 20, x2: 6, y2: 14 })
])

const steps = ref([
    {
        id: 1,
        title: 'Know Us',
        description: 'Get introduced to VERBO’s personalized learning approach, expert educators, and unique programs.',
        icon: IconInfo
    },
    {
        id: 2,
        title: 'Understand the Student',
        description: 'We assess your child’s learning level, strengths & challenges, interests and pace.',
        icon: IconUser
    },
    {
        id: 3,
        title: 'Demo Class',
        description: 'Experience our teaching style, evaluate student engagement, and identify learning needs.',
        icon: IconCalendar
    },
    {
        id: 4,
        title: 'Customization of Class',
        description: 'A personalized learning plan tailored to your child’s comfort and pace, and academic goals.',
        icon: IconPlan
    },
    {
        id: 5,
        title: 'Flexible Fees',
        description: 'Choose a plan that suits your needs. We offer flexible and affordable fee structures based on selected courses.',
        icon: IconWallet
    },
    {
        id: 6,
        title: 'App Introduction',
        description: 'Access everything through the VERBO App: track progress, manage schedules, access learning resources.',
        icon: IconApp
    },
    {
        id: 7,
        title: 'Regular Assessment & Evaluation',
        description: 'We ensure continuous improvement through periodic assessments, performance tracking, feedback and updates.',
        icon: IconChart
    }
])

const stepRefs = ref([])

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

    document.querySelectorAll('.step-item').forEach(step => {
        observer.observe(step)
    })
})
</script>

<style scoped>
.how-it-works {
    padding: 120px 0 80px;
    background: linear-gradient(180deg, #f8fafc 0%, #ffffff 100%);
}

.how-it-works-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .how-it-works-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .how-it-works-container {
        padding: 0 64px;
    }
}

/* Section Header */
.section-header {
    text-align: center;
    max-width: 600px;
    margin: 0 auto 80px;
}

.section-title {
    font-size: 42px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 16px;
    letter-spacing: -1px;
}

@media (min-width: 768px) {
    .section-title {
        font-size: 52px;
    }
}

.section-subtitle {
    font-size: 17px;
    color: var(--gray-600);
    line-height: 1.7;
}

/* Steps Container */
.steps-container {
    position: relative;
    padding: 40px 0;
}

/* Steps Flex Container */
.steps-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 48px 32px;
}

@media (min-width: 640px) {
    .steps-grid {
        gap: 64px 40px;
    }
}

/* Step Item */
.step-item {
    position: relative;
    text-align: center;
    z-index: 2;
    flex: 0 1 260px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.6s ease;
}

.step-item.visible {
    opacity: 1;
    transform: translateY(0);
}

.step-item:nth-child(1) {
    transition-delay: 0.1s;
}

.step-item:nth-child(2) {
    transition-delay: 0.2s;
}

.step-item:nth-child(3) {
    transition-delay: 0.3s;
}

.step-item:nth-child(4) {
    transition-delay: 0.4s;
}

.step-item:nth-child(5) {
    transition-delay: 0.5s;
}

.step-item:nth-child(6) {
    transition-delay: 0.6s;
}

.step-item:nth-child(7) {
    transition-delay: 0.7s;
}

/* Step Icon */
.step-icon {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 80px;
    margin: 0 auto 24px;
    background: var(--primary);
    color: white;
    border-radius: 50%;
    box-shadow: 0 8px 24px rgba(21, 168, 156, 0.35);
    transition: all 0.3s ease;
}

/* Step Badge Number */
.step-badge {
    position: absolute;
    top: -4px;
    right: -4px;
    background: #f97316;
    color: white;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    font-size: 13px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 3px solid white;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.step-item:hover .step-icon {
    transform: scale(1.1);
    box-shadow: 0 12px 32px rgba(21, 168, 156, 0.45);
}

.step-title {
    font-size: 18px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 12px;
}

.step-description {
    font-size: 14px;
    color: var(--gray-600);
    line-height: 1.7;
    max-width: 240px;
    margin: 0 auto;
}
</style>
