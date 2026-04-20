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
        name: 'Parent of Ameya',
        avatar: 'https://ui-avatars.com/api/?name=PO&background=e0f2fe&color=0284c7',
        achievement: 'Grade 4 Student',
        badgeColor: '#15a89c',
        quote: 'I would like to share my feedback about Verbo Institute. My daughter has been attending online Art, English, and Music classes for the past year, and also attended the Arabic class for 10 days. All the classes are well-organized and engaging, with very supportive teachers. I have seen a clear improvement in her creativity, communication skills, and overall confidence.'
    },
    {
        id: 2,
        name: 'Parent of Ahmed Rayyan',
        avatar: 'https://ui-avatars.com/api/?name=PR&background=fce7f3&color=be185d',
        achievement: 'Class 3 Student',
        badgeColor: '#db2777',
        quote: 'I am the parent of Ahmed Rayyan. My son studied in Class 3 and our experience with the institute has been very good. The English and Science teachers are excellent and very supportive. I am very happy with the overall learning environment and we would like to continue with this institute.'
    },
    {
        id: 3,
        name: 'Parent of Johan & Jem',
        avatar: 'https://ui-avatars.com/api/?name=PJ&background=fef3c7&color=b45309',
        achievement: 'Grade 6 & Grade 8 Students',
        badgeColor: '#d97706',
        quote: 'I am the parent of Johan (grade 6) and Jem (grade 8). The online class was informative and the topics were taught in an easy manner. Each topic was explained with proper details, making it simple to learn. Thank you!'
    },
    {
        id: 4,
        name: 'Jensy Sara John',
        avatar: 'https://ui-avatars.com/api/?name=JS&background=dcfce7&color=15803d',
        achievement: 'Ras al Khaimah, UAE',
        badgeColor: '#16a34a',
        quote: 'I would like to express my appreciation for the online tuition. The sessions are well-organized, interactive, and easy to follow. The teacher explains concepts clearly and ensures that the students understand the topics thoroughly. Overall, I appreciate the efforts taken by the teachers.'
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
    border-color: var(--primary);
    color: var(--primary);
    background: #edfafa;
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
    border-color: var(--primary-light);
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
