<template>
    <section class="how-it-works">
        <div class="how-it-works-container">
            <!-- Header -->
            <div class="section-header animate-fade-in-up">
                <h1 class="section-title">How It Works</h1>
                <p class="section-subtitle">
                    Embark on a personalized learning journey designed to help you master new skills with ease and
                    confidence.
                </p>
            </div>

            <!-- Steps Timeline -->
            <div class="steps-container">
                <div class="timeline-line"></div>

                <div class="steps-grid">
                    <div v-for="(step, index) in steps" :key="step.id" class="step-item" ref="stepRefs">
                        <div class="step-icon" :style="{ animationDelay: `${index * 150}ms` }">
                            <component :is="step.icon" />
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
const IconCalendar = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('rect', { x: 3, y: 4, width: 18, height: 18, rx: 2 }),
    h('line', { x1: 16, y1: 2, x2: 16, y2: 6 }),
    h('line', { x1: 8, y1: 2, x2: 8, y2: 6 }),
    h('line', { x1: 3, y1: 10, x2: 21, y2: 10 })
])

const IconMatch = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('circle', { cx: 11, cy: 11, r: 8 }),
    h('path', { d: 'M21 21l-4.35-4.35' }),
    h('circle', { cx: 11, cy: 8, r: 2 }),
    h('path', { d: 'M7 14c0-2 1.5-3 4-3s4 1 4 3' })
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

const IconTrophy = () => h('svg', {
    width: 28, height: 28, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor',
    'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round'
}, [
    h('path', { d: 'M6 9H4.5a2.5 2.5 0 0 1 0-5H6' }),
    h('path', { d: 'M18 9h1.5a2.5 2.5 0 0 0 0-5H18' }),
    h('path', { d: 'M4 22h16' }),
    h('path', { d: 'M10 14.66V17c0 .55-.47.98-.97 1.21C7.85 18.75 7 20.24 7 22' }),
    h('path', { d: 'M14 14.66V17c0 .55.47.98.97 1.21C16.15 18.75 17 20.24 17 22' }),
    h('path', { d: 'M18 2H6v7a6 6 0 0 0 12 0V2Z' })
])

const steps = ref([
    {
        id: 1,
        title: 'Book a Free Demo',
        description: 'Schedule a complimentary session to explore our platform and meet our educational experts.',
        icon: IconCalendar
    },
    {
        id: 2,
        title: 'Get Matched',
        description: 'Our intelligent system pairs you with the perfect educator based on your specific learning needs.',
        icon: IconMatch
    },
    {
        id: 3,
        title: 'Personalized Plan',
        description: 'Receive a custom-tailored curriculum designed to accelerate your unique academic or career path.',
        icon: IconPlan
    },
    {
        id: 4,
        title: 'Achieve Goals',
        description: 'Begin your sessions and track your progress as you reach your milestones with expert guidance.',
        icon: IconTrophy
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

/* Timeline Line */
.timeline-line {
    display: none;
    position: absolute;
    top: 68px;
    left: 10%;
    right: 10%;
    height: 3px;
    background: linear-gradient(90deg, var(--primary-blue) 0%, var(--primary-blue-light) 100%);
    z-index: 1;
}

@media (min-width: 1024px) {
    .timeline-line {
        display: block;
    }
}

/* Steps Grid */
.steps-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 48px;
}

@media (min-width: 640px) {
    .steps-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 40px;
    }
}

@media (min-width: 1024px) {
    .steps-grid {
        grid-template-columns: repeat(4, 1fr);
        gap: 32px;
    }
}

/* Step Item */
.step-item {
    position: relative;
    text-align: center;
    z-index: 2;
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

/* Step Icon */
.step-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 80px;
    margin: 0 auto 24px;
    background: var(--primary-blue);
    color: white;
    border-radius: 50%;
    box-shadow: 0 8px 24px rgba(37, 99, 235, 0.35);
    transition: all 0.3s ease;
}

.step-item:hover .step-icon {
    transform: scale(1.1);
    box-shadow: 0 12px 32px rgba(37, 99, 235, 0.45);
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
