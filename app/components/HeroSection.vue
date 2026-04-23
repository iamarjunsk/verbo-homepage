<template>
    <section class="hero-section">
        <!-- Background Shapes -->
        <div class="hero-bg-shapes pointer-events-none">
            <!-- Teal Ribbon Wave (Pattern layered) -->
            <svg class="wave-teal" width="100%" height="auto" viewBox="0 0 1440 250" preserveAspectRatio="none"
                xmlns="http://www.w3.org/2000/svg">
                <!-- Solid light teal base -->
                <path fill="#f0fdfa" fill-opacity="1"
                    d="M0,128L60,112C120,96,240,64,360,74.7C480,85,600,139,720,138.7C840,139,960,85,1080,74.7C1200,64,1320,96,1380,112L1440,128L1440,250L1380,250C1320,250,1200,250,1080,250C960,250,840,250,720,250C600,250,480,250,360,250C240,250,120,250,60,250L0,250Z">
                </path>

                <!-- Simple dot pattern overlay to simulate the design's ribbon -->
                <pattern id="dots" x="0" y="0" width="20" height="20" patternUnits="userSpaceOnUse">
                    <circle cx="2" cy="2" r="1.5" fill="var(--primary)" opacity="0.3"></circle>
                    <path d="M10,8 L14,14 L6,14 Z" fill="none" stroke="var(--primary)" stroke-width="0.5" opacity="0.3">
                    </path>
                </pattern>

                <path fill="url(#dots)"
                    d="M0,128L60,112C120,96,240,64,360,74.7C480,85,600,139,720,138.7C840,139,960,85,1080,74.7C1200,64,1320,96,1380,112L1440,128L1440,250L1380,250C1320,250,1200,250,1080,250C960,250,840,250,720,250C600,250,480,250,360,250C240,250,120,250,60,250L0,250Z">
                </path>
            </svg>

            <!-- Main Yellow Wave -->
            <svg class="wave-yellow" width="100%" height="auto" viewBox="0 0 1440 200" preserveAspectRatio="none"
                xmlns="http://www.w3.org/2000/svg">
                <path fill="#ffd740" fill-opacity="1"
                    d="M0,96L80,117.3C160,139,320,181,480,181.3C640,181,800,139,960,122.7C1120,107,1280,117,1360,122.7L1440,128L1440,200L1360,200C1280,200,1120,200,960,200C800,200,640,200,480,200C320,200,160,200,80,200L0,200Z">
                </path>
            </svg>
        </div>


        <div class="hero-container">
            <!-- Left Content: Typography -->
            <div class="hero-content">
                <h1 class="hero-title animate-fade-in-up">
                    Because Every <span class="highlight">Child Deserves</span><br />
                    <span class="highlight">Personal Attention</span>
                </h1>

                <h2 class="hero-subtitle animate-fade-in-up delay-100">
                    The First <span class="highlight">AI-Integrated Individual Learning Platform</span><br />
                    Built for Every Student's Growth.
                </h2>

                <div class="hero-tags animate-fade-in-up delay-200">
                    <span class="tag">K-12 Academic Tuition</span>
                    <span class="tag">Online Schooling</span>
                    <span class="tag">AI & Robotics</span>
                    <span class="tag">Space Education</span>
                    <span class="tag">Non Academic Courses</span>
                </div>
            </div>

            <!-- Right Content: Student Image -->
            <div class="hero-image-wrapper animate-fade-in-right delay-300">
                <!-- Yellow Blob Background -->
                <div class="yellow-blob"></div>

                <!-- Student Image -->
                <div class="image-container">
                    <img src="https://images.unsplash.com/photo-1692269725911-87697c558be1?q=80&w=2232&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                        alt="Indian Student in Uniform" class="student-image" />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.hero-section {
    position: relative;
    padding-top: 140px;
    padding-bottom: 240px;
    background-color: white;
    overflow: hidden;
    min-height: 80vh;
    display: flex;
    align-items: center;
}

/* Background SVGs */
.hero-bg-shapes {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
}

.wave-teal {
    position: absolute;
    bottom: 30px;
    /* Sits slightly higher than yellow wave */
    left: 0;
    width: 100%;
    height: auto;
    min-height: 15vh;
}

.wave-yellow {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: auto;
    min-height: 20vh;
}

.website-url {
    position: absolute;
    bottom: 20px;
    left: 40px;
    color: white;
    font-weight: 500;
    letter-spacing: 0.5px;
    z-index: 10;
    font-size: 15px;
}

/* Container Layout */
.hero-container {
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    max-width: 1300px;
    margin: 0 auto;
    padding: 0 24px;
    width: 100%;
}

@media (min-width: 1024px) {
    .hero-container {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        padding: 0 64px;
    }
}

/* Typography Content */
.hero-content {
    flex: 1;
    max-width: 700px;
    z-index: 10;
}

.hero-title {
    font-size: 38px;
    font-weight: 800;
    line-height: 1.15;
    color: var(--navy-dark, #1e293b);
    letter-spacing: -0.5px;
    margin-bottom: 24px;
}

.hero-title .highlight {
    color: var(--primary);
}

.hero-subtitle {
    font-size: 20px;
    font-weight: 500;
    line-height: 1.5;
    color: var(--gray-700, #334155);
    margin-bottom: 32px;
}

.hero-subtitle .highlight {
    color: var(--primary);
    font-weight: 700;
}

@media (min-width: 768px) {
    .hero-title {
        font-size: 48px;
    }

    .hero-subtitle {
        font-size: 22px;
    }
}

@media (min-width: 1024px) {
    .hero-title {
        font-size: 54px;
    }
}

/* Tags Layout */
.hero-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    align-items: center;
}

.tag {
    font-size: 13px;
    font-weight: 600;
    color: var(--primary);
    letter-spacing: 0.5px;
    text-transform: uppercase;
    position: relative;
}

/* Add small subtle separators between tags not using borders, but maybe absolute · */
.tag:not(:last-child)::after {
    content: '';
    display: inline-block;
    width: 4px;
    height: 4px;
    background-color: var(--primary-light, #99f6e4);
    border-radius: 50%;
    margin-left: 16px;
    vertical-align: middle;
}

/* Student Image */
.hero-image-wrapper {
    flex: 1;
    position: relative;
    display: flex;
    justify-content: flex-end;
    margin-top: 60px;
    z-index: 5;
}

@media (min-width: 1024px) {
    .hero-image-wrapper {
        margin-top: 0;
    }
}

.yellow-blob {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-30%, -50%);
    width: 500px;
    height: 550px;
    background-color: #ffd740;
    border-radius: 40% 60% 70% 30% / 40% 50% 60% 50%;
    z-index: 1;
}

@media (min-width: 1024px) {
    .yellow-blob {
        width: 600px;
        height: 650px;
        transform: translate(-10%, -50%);
    }
}

.image-container {
    position: relative;
    z-index: 2;
    height: 500px;
    width: 100%;
    max-width: 450px;
    /* We add clip-path or rounded corners just as a fallback placeholder style */
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    overflow: hidden;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

@media (min-width: 1024px) {
    .image-container {
        height: 600px;
        max-width: 500px;
    }
}

.student-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
}

/* Animations */
.animate-fade-in-up {
    animation: fadeInUp 0.8s ease-out forwards;
    opacity: 0;
    transform: translateY(20px);
}

.animate-fade-in-right {
    animation: fadeInRight 0.8s ease-out forwards;
    opacity: 0;
    transform: translateX(20px);
}

.delay-100 {
    animation-delay: 100ms;
}

.delay-200 {
    animation-delay: 200ms;
}

.delay-300 {
    animation-delay: 300ms;
}

@keyframes fadeInUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes fadeInRight {
    to {
        opacity: 1;
        transform: translateX(0);
    }
}
</style>
