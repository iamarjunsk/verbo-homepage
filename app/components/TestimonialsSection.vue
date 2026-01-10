<template>
    <section class="testimonials section">
        <div class="testimonials-container">
            <!-- Section Header -->
            <div class="section-header" ref="headerRef">
                <div class="header-content">
                    <h2 class="section-title">Real Results from Real Students</h2>
                    <p class="section-description">
                        See how VerboEdu transforms academic journeys through personalized learning.
                    </p>
                </div>
                <div class="carousel-nav">
                    <button class="nav-btn" @click="prevSlide" aria-label="Previous">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2">
                            <polyline points="15 18 9 12 15 6"></polyline>
                        </svg>
                    </button>
                    <button class="nav-btn" @click="nextSlide" aria-label="Next">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2">
                            <polyline points="9 18 15 12 9 6"></polyline>
                        </svg>
                    </button>
                </div>
            </div>

            <!-- Testimonial Cards -->
            <div class="testimonials-grid">
                <div v-for="(testimonial, index) in testimonials" :key="testimonial.id"
                    class="testimonial-card card-hover" ref="cardRefs">
                    <!-- Header -->
                    <div class="testimonial-header">
                        <div class="avatar">
                            <img :src="testimonial.avatar" :alt="testimonial.name" />
                        </div>
                        <div class="user-info">
                            <h4 class="user-name">{{ testimonial.name }}</h4>
                            <div class="stars">
                                <span v-for="star in 5" :key="star" class="star">★</span>
                            </div>
                        </div>
                    </div>

                    <!-- Achievement Badge -->
                    <div class="achievement-badge" :style="{ color: testimonial.badgeColor }">
                        {{ testimonial.achievement }}
                    </div>

                    <!-- Quote -->
                    <p class="testimonial-quote">
                        "{{ testimonial.quote }}"
                    </p>

                    <!-- Read Full Story Link -->
                    <button class="read-story-btn">
                        Read Full Story
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const headerRef = ref(null)
const cardRefs = ref([])
const currentSlide = ref(0)

const testimonials = ref([
    {
        id: 1,
        name: 'Alex R.',
        avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=80&h=80&fit=crop&crop=faces',
        achievement: '98% in Math (Calculus)',
        badgeColor: '#2563eb',
        quote: 'The tutors at VerboEdu helped me break down complex problems into manageable steps. I went from struggling to scoring the highest in my class!'
    },
    {
        id: 2,
        name: 'Priya K.',
        avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=80&h=80&fit=crop&crop=faces',
        achievement: 'SAT Score: 1550',
        badgeColor: '#059669',
        quote: 'The test-taking strategies I learned were game changers. The 1-on-1 focus helped me identify and fix my weak spots in grammar and logic.'
    },
    {
        id: 3,
        name: 'Marcus T.',
        avatar: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=80&h=80&fit=crop&crop=faces',
        achievement: 'Career Pivot to Data Science',
        badgeColor: '#7c3aed',
        quote: 'I was stuck in a rut. VerboEdu\'s career modules gave me the technical edge I needed to land my dream job in tech. Highly recommended!'
    }
])

const nextSlide = () => {
    currentSlide.value = (currentSlide.value + 1) % testimonials.value.length
}

const prevSlide = () => {
    currentSlide.value = currentSlide.value === 0 ? testimonials.value.length - 1 : currentSlide.value - 1
}

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

    document.querySelectorAll('.testimonial-card').forEach(card => {
        observer.observe(card)
    })
})
</script>

<style scoped>
.testimonials {
    background-color: white;
}

.testimonials-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .testimonials-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .testimonials-container {
        padding: 0 64px;
    }
}

/* Section Header */
.section-header {
    display: flex;
    flex-direction: column;
    gap: 24px;
    margin-bottom: 40px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.7s ease;
}

.section-header.visible {
    opacity: 1;
    transform: translateY(0);
}

@media (min-width: 768px) {
    .section-header {
        flex-direction: row;
        justify-content: space-between;
        align-items: flex-end;
    }
}

.header-content {
    max-width: 500px;
}

.section-title {
    font-size: 32px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 12px;
    letter-spacing: -0.5px;
}

@media (min-width: 768px) {
    .section-title {
        font-size: 36px;
    }
}

.section-description {
    font-size: 16px;
    color: var(--gray-600);
    line-height: 1.6;
}

/* Carousel Nav */
.carousel-nav {
    display: flex;
    gap: 12px;
}

.nav-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 44px;
    height: 44px;
    border-radius: 50%;
    border: 1.5px solid var(--gray-200);
    background: white;
    color: var(--gray-600);
    cursor: pointer;
    transition: all 0.3s ease;
}

.nav-btn:hover {
    border-color: var(--primary-blue);
    color: var(--primary-blue);
    background: #eff6ff;
}

/* Testimonials Grid */
.testimonials-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 24px;
}

@media (min-width: 768px) {
    .testimonials-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .testimonials-grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

/* Testimonial Card */
.testimonial-card {
    background: white;
    border-radius: 16px;
    padding: 28px;
    border: 1px solid var(--gray-200);
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.6s ease;
}

.testimonial-card.visible {
    opacity: 1;
    transform: translateY(0);
}

.testimonial-card:nth-child(1) {
    transition-delay: 0.1s;
}

.testimonial-card:nth-child(2) {
    transition-delay: 0.2s;
}

.testimonial-card:nth-child(3) {
    transition-delay: 0.3s;
}

.testimonial-card:hover {
    border-color: var(--primary-blue-light);
}

/* Testimonial Header */
.testimonial-header {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 16px;
}

.avatar {
    width: 52px;
    height: 52px;
    border-radius: 50%;
    overflow: hidden;
    flex-shrink: 0;
}

.avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.user-name {
    font-size: 16px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 4px;
}

.stars {
    display: flex;
    gap: 2px;
}

.star {
    color: #fbbf24;
    font-size: 14px;
}

/* Achievement Badge */
.achievement-badge {
    display: inline-block;
    font-size: 13px;
    font-weight: 600;
    padding: 6px 12px;
    background: var(--gray-50);
    border-radius: 6px;
    margin-bottom: 16px;
}

/* Quote */
.testimonial-quote {
    font-size: 15px;
    color: var(--gray-600);
    line-height: 1.7;
    font-style: italic;
    margin-bottom: 20px;
    min-height: 85px;
}

/* Read Story Button */
.read-story-btn {
    display: block;
    width: 100%;
    padding: 12px;
    background: white;
    color: var(--navy-dark);
    font-weight: 600;
    font-size: 14px;
    border: 1.5px solid var(--gray-200);
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.read-story-btn:hover {
    border-color: var(--gray-300);
    background: var(--gray-50);
}
</style>
