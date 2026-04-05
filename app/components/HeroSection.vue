<template>
    <section class="hero">
        <div class="hero-container">
            <!-- Left Content -->
            <div class="hero-content">
                <!-- Badge -->
                <div class="badge animate-fade-in">
                    <span class="badge-icon"></span>
                    <span>PERSONALIZED LEARNING</span>
                </div>

                <!-- Heading -->
                <h1 class="hero-title animate-fade-in-up delay-200">
                    The Best Personalized Learning Platform for Your Child
                </h1>

                <!-- Description -->
                <p class="hero-description animate-fade-in-up delay-300">
                    Give your child the learning support they deserve with expert teachers, personalized classes, and future-ready skills. 
                    At Verbo, students from KG to Grade 12 learn through one-to-one classes designed around their unique learning needs.
                </p>

                <!-- CTA Buttons -->
                <div class="hero-buttons animate-fade-in-up delay-400">
                    <NuxtLink to="/book" class="btn-primary">
                        Book a Free Demo
                    </NuxtLink>
                    <NuxtLink to="/programs" class="btn-secondary">
                        Explore Courses
                    </NuxtLink>
                </div>

                <!-- Social Proof -->
                <div class="social-proof animate-fade-in-up delay-500">
                    <div class="avatar-stack">
                        <div class="avatar" style="background: linear-gradient(135deg, #60a5fa, #3b82f6);"></div>
                        <div class="avatar" style="background: linear-gradient(135deg, #a78bfa, #8b5cf6);"></div>
                        <div class="avatar" style="background: linear-gradient(135deg, #4ade80, #22c55e);"></div>
                    </div>
                    <span class="social-text">Joined by <strong>5,000+</strong> students this month</span>
                </div>
            </div>

            <!-- Right Image -->
            <div class="hero-image-wrapper animate-fade-in-right delay-300">
                <div class="hero-image-container">
                    <!-- Main Image -->
                    <div class="hero-image">
                        <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?w=600&h=500&fit=crop&crop=faces"
                            alt="Students learning together" />
                    </div>

                    <!-- Floating Badge -->
                    <div class="verified-badge animate-float">
                        <div class="verified-icon">
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                                <circle cx="12" cy="12" r="10" fill="#22c55e" />
                                <path d="M9 12l2 2 4-4" stroke="white" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" />
                            </svg>
                        </div>
                        <div class="verified-content">
                            <span class="verified-label">Verified Tutors</span>
                            <span class="verified-text">Expert Checked</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Background Gradient -->
        <div class="hero-bg"></div>
    </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
    position: relative;
    padding-top: 100px;
    padding-bottom: 60px;
    overflow: hidden;
}

@media (min-width: 768px) {
    .hero {
        padding-top: 120px;
        padding-bottom: 80px;
    }
}

.hero-container {
    position: relative;
    z-index: 10;
    display: grid;
    grid-template-columns: 1fr;
    gap: 48px;
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
    align-items: center;
}

@media (min-width: 768px) {
    .hero-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .hero-container {
        grid-template-columns: 1fr 1fr;
        gap: 64px;
        padding: 0 64px;
    }
}

/* Hero Content */
.hero-content {
    max-width: 560px;
}

@media (min-width: 1024px) {
    .hero-content {
        max-width: none;
    }
}

.hero-title {
    font-size: 42px;
    font-weight: 800;
    line-height: 1.1;
    color: var(--navy-dark);
    margin-top: 24px;
    margin-bottom: 20px;
    letter-spacing: -1px;
}

@media (min-width: 768px) {
    .hero-title {
        font-size: 52px;
    }
}

@media (min-width: 1024px) {
    .hero-title {
        font-size: 56px;
    }
}

.hero-description {
    font-size: 17px;
    color: var(--gray-600);
    line-height: 1.7;
    margin-bottom: 32px;
    max-width: 440px;
}

/* CTA Buttons */
.hero-buttons {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    margin-bottom: 40px;
}

/* Social Proof */
.social-proof {
    display: flex;
    align-items: center;
    gap: 14px;
}

.social-text {
    font-size: 14px;
    color: var(--gray-500);
}

.social-text strong {
    color: var(--navy-dark);
}

/* Hero Image */
.hero-image-wrapper {
    display: flex;
    justify-content: center;
}

@media (min-width: 1024px) {
    .hero-image-wrapper {
        justify-content: flex-end;
    }
}

.hero-image-container {
    position: relative;
    max-width: 500px;
}

.hero-image {
    position: relative;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 25px 60px rgba(0, 0, 0, 0.15);
}

.hero-image img {
    display: block;
    width: 100%;
    height: auto;
    object-fit: cover;
}

/* Verified Badge */
.verified-badge {
    position: absolute;
    bottom: -16px;
    right: 24px;
    display: flex;
    align-items: center;
    gap: 10px;
    background: white;
    padding: 12px 18px;
    border-radius: 14px;
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
}

@media (min-width: 768px) {
    .verified-badge {
        bottom: 24px;
        right: -20px;
    }
}

.verified-content {
    display: flex;
    flex-direction: column;
}

.verified-label {
    font-size: 11px;
    color: var(--gray-500);
}

.verified-text {
    font-size: 14px;
    font-weight: 700;
    color: var(--navy-dark);
}

/* Background */
.hero-bg {
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 50%, #f1f5f9 100%);
    z-index: 1;
}

@media (min-width: 1024px) {
    .hero-bg {
        width: 55%;
        clip-path: polygon(15% 0, 100% 0, 100% 100%, 0% 100%);
    }
}
</style>
