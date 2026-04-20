<template>
  <div class="about-page font-sans">
    
    <!-- Premium Header -->
    <section class="about-header">
      <!-- Background subtle shapes -->
      <div class="header-bg-shapes">
        <svg class="shape-1" fill="currentColor" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="50"></circle>
        </svg>
        <svg class="shape-2" fill="currentColor" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <path d="M0,50 a50,50 0 1,0 100,0 a50,50 0 1,0 -100,0"></path>
        </svg>
      </div>

      <div class="header-content">
        <h1 class="header-title animate-fade-in-up">
          About & Contact Us
        </h1>
        <p class="header-subtitle animate-fade-in-up delay-100">
          Learn more about our mission to provide personalized education, or get directly in touch with our dedicated team.
        </p>
      </div>
    </section>

    <!-- Content / Contact Cards -->
    <section class="contact-section">
      <div class="contact-grid">
        
        <!-- Mehajabin Card -->
        <div class="contact-card animate-fade-in-up delay-200">
          <!-- Accent circle -->
          <div class="card-accent"></div>
          
          <div class="card-content">
            <!-- Avatar -->
            <div class="avatar">
              <span class="avatar-initial">M</span>
            </div>
            
            <h2 class="contact-name">Mehajabin</h2>
            <p class="contact-role">Support & Admissions</p>
            
            <div class="divider"></div>
            
            <a href="tel:+919778493428" class="contact-btn">
              <svg class="phone-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
              </svg>
              <span>+91 97784 93428</span>
            </a>
          </div>
        </div>

        <!-- Kamarul Jamal Card -->
        <div class="contact-card animate-fade-in-up delay-300">
          <!-- Accent circle -->
          <div class="card-accent"></div>
          
          <div class="card-content">
            <!-- Avatar -->
            <div class="avatar reverse-tilt">
              <span class="avatar-initial reverse">K</span>
            </div>
            
            <h2 class="contact-name">Kamarul Jamal</h2>
            <p class="contact-role">Support & Admissions</p>
            
            <div class="divider"></div>
            
            <a href="tel:+919074569745" class="contact-btn">
              <svg class="phone-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
              </svg>
              <span>+91 90745 69745</span>
            </a>
          </div>
        </div>

      </div>

      <!-- Quick Info Strip -->
      <div class="quick-info animate-fade-in-up delay-400">
        <div class="info-item">
          <div class="info-icon-wrap">
            <svg class="info-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path>
            </svg>
          </div>
          <div>
            <h4 class="info-title">Business Hours</h4>
            <p class="info-value">Mon - Sat: 9:00 AM - 6:00 PM</p>
          </div>
        </div>
      </div>

       <!-- New Added Content: Mission Section -->
       <div class="mission-section animate-fade-in-up delay-500">
          <div class="mission-image-container">
               <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?w=600&h=500&fit=crop&crop=faces" alt="Students learning" class="mission-img"/>
               <div class="mission-badge">
                   <span class="badge-number">5k+</span>
                   <span class="badge-text">Happy Students</span>
               </div>
          </div>
          <div class="mission-text-content">
               <h3 class="mission-heading">Empowering Every Student's Potential</h3>
               <p class="mission-paragraph">
                   At VerboEdu, we believe that education is not a one-size-fits-all journey. Every child has a unique learning style, pace, and set of interests. Our mission is to bridge the gap between traditional schooling and individual potential.
               </p>
               <p class="mission-paragraph">
                   By integrating cutting-edge AI technology with experienced tutors, we provide a unified platform that adapts to your child's growth. We are committed to fostering future-ready skills in a supportive, engaging, and personalized environment.
               </p>
          </div>
      </div>

    </section>

  </div>
</template>

<script setup>
definePageMeta({
  title: 'About & Contact Us'
})
</script>

<style scoped>
/* Reset some basics */
.font-sans {
    font-family: inherit; /* will use global body font */
}

/* Page Layout */
.about-page {
    background-color: var(--gray-50, #f8fafc);
    min-height: 100vh;
    padding-bottom: 100px;
}

/* Header Section */
.about-header {
    position: relative;
    background: linear-gradient(135deg, var(--primary, #15a89c), #107b72);
    padding: 180px 24px 160px;
    text-align: center;
    color: white;
    overflow: hidden;
}

.header-bg-shapes {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0.15;
    pointer-events: none;
}

.shape-1 {
    position: absolute;
    top: -50px;
    left: -50px;
    width: 300px;
    height: 300px;
    color: white;
}

.shape-2 {
    position: absolute;
    top: 50%;
    right: -50px;
    width: 250px;
    height: 250px;
    color: #0b5851;
}

.header-content {
    position: relative;
    z-index: 10;
    max-width: 700px;
    margin: 0 auto;
}

.header-title {
    font-size: 42px;
    font-weight: 800;
    margin-bottom: 20px;
    letter-spacing: -0.5px;
}

@media (min-width: 768px) {
    .header-title {
        font-size: 56px;
    }
}

.header-subtitle {
    font-size: 18px;
    line-height: 1.6;
    opacity: 0.9;
    max-width: 600px;
    margin: 0 auto;
}

@media (min-width: 768px) {
    .header-subtitle {
        font-size: 20px;
    }
}

/* Contact Grid Section */
.contact-section {
    position: relative;
    z-index: 20;
    max-width: 1100px;
    margin: -80px auto 0;
    padding: 0 24px;
}

.contact-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 32px;
}

@media (min-width: 768px) {
    .contact-grid {
        grid-template-columns: 1fr 1fr;
        gap: 40px;
    }
}

/* Contact Cards */
.contact-card {
    position: relative;
    background: white;
    border-radius: 24px;
    padding: 40px 32px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.06);
    border: 1px solid var(--gray-100, #f1f5f9);
    transition: transform 0.4s ease, box-shadow 0.4s ease;
    overflow: hidden;
}

.contact-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 25px 50px rgba(21, 168, 156, 0.12);
}

.card-accent {
    position: absolute;
    top: -50px;
    right: -50px;
    width: 150px;
    height: 150px;
    background: var(--primary-light, #1cd0c2);
    opacity: 0.15;
    border-radius: 50%;
    transition: transform 0.6s ease;
    pointer-events: none;
}

.contact-card:hover .card-accent {
    transform: scale(1.6);
}

.card-content {
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

/* Avatar Graphics */
.avatar {
    width: 90px;
    height: 90px;
    background: linear-gradient(135deg, var(--primary-light, #1cd0c2), var(--primary, #15a89c));
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
    box-shadow: 0 10px 25px rgba(21, 168, 156, 0.3);
    transform: rotate(4deg);
    transition: transform 0.4s ease;
}

.avatar.reverse-tilt {
    transform: rotate(-4deg);
}

.contact-card:hover .avatar {
    transform: rotate(8deg);
}

.contact-card:hover .avatar.reverse-tilt {
    transform: rotate(-8deg);
}

.avatar-initial {
    font-size: 36px;
    font-weight: 800;
    color: white;
    transform: rotate(-4deg);
    transition: transform 0.4s ease;
}

.avatar-initial.reverse {
    transform: rotate(4deg);
}

.contact-card:hover .avatar-initial {
    transform: rotate(-8deg);
}
.contact-card:hover .avatar-initial.reverse {
    transform: rotate(8deg);
}

/* Text & Details */
.contact-name {
    font-size: 26px;
    font-weight: 800;
    color: var(--navy-dark, #1e293b);
    margin-bottom: 6px;
}

.contact-role {
    font-size: 15px;
    color: var(--gray-500, #64748b);
    font-weight: 500;
    margin-bottom: 24px;
}

.divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(to right, transparent, var(--gray-200, #e2e8f0), transparent);
    margin-bottom: 24px;
}

/* Buttons */
.contact-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    width: 100%;
    padding: 16px;
    background: var(--gray-50, #f8fafc);
    border: 1px solid var(--gray-200, #e2e8f0);
    border-radius: 12px;
    color: var(--navy-dark, #1e293b);
    font-size: 16px;
    font-weight: 700;
    text-decoration: none;
    transition: all 0.3s ease;
}

.contact-btn:hover {
    background: #f0fdfa; /* light teal */
    border-color: var(--primary-light, #1cd0c2);
    color: var(--primary-dark, #107b72);
}

.phone-icon {
    width: 22px;
    height: 22px;
    color: var(--primary, #15a89c);
}

/* Quick Info Strip */
.quick-info {
    margin-top: 40px;
    background: white;
    border-radius: 20px;
    padding: 24px;
    display: flex;
    flex-direction: column;
    gap: 24px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.04);
    border: 1px solid var(--gray-100, #f1f5f9);
}

@media (min-width: 768px) {
    .quick-info {
        flex-direction: row;
        align-items: center;
        justify-content: center;
        padding: 32px;
        margin-top: 60px;
    }
}

.info-item {
    display: flex;
    align-items: center;
    gap: 16px;
}

.info-icon-wrap {
    width: 48px;
    height: 48px;
    background: #f0fdfa; /* light teal */
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--primary, #15a89c);
    flex-shrink: 0;
}

.info-icon {
    width: 24px;
    height: 24px;
}

.info-title {
    font-size: 16px;
    font-weight: 700;
    color: var(--navy-dark, #1e293b);
    margin-bottom: 4px;
}

.info-value {
    font-size: 14px;
    color: var(--gray-500, #64748b);
}

.info-divider {
    height: 1px;
    width: 100%;
    background: var(--gray-200, #e2e8f0);
}

@media (min-width: 768px) {
    .info-divider {
        width: 1px;
        height: 60px;
    }
}

/* Mission Section */
.mission-section {
    margin-top: 60px;
    background: white;
    border-radius: 24px;
    padding: 32px;
    display: grid;
    grid-template-columns: 1fr;
    gap: 40px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.05);
    border: 1px solid var(--gray-100, #f1f5f9);
    align-items: center;
}

@media (min-width: 1024px) {
    .mission-section {
        grid-template-columns: 1fr 1fr;
        padding: 60px;
        gap: 60px;
        margin-top: 80px;
    }
}

.mission-image-container {
    position: relative;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 20px 40px rgba(0,0,0,0.1);
}

.mission-img {
    width: 100%;
    height: 100%;
    min-height: 300px;
    display: block;
    object-fit: cover;
}

.mission-badge {
    position: absolute;
    bottom: 20px;
    left: 20px;
    background: white;
    padding: 16px 24px;
    border-radius: 16px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    display: flex;
    flex-direction: column;
}

.badge-number {
    font-size: 24px;
    font-weight: 800;
    color: var(--primary, #15a89c);
    line-height: 1.1;
}

.badge-text {
    font-size: 13px;
    color: var(--gray-500, #64748b);
    font-weight: 600;
}

.mission-heading {
    font-size: 32px;
    font-weight: 800;
    color: var(--navy-dark, #1e293b);
    margin-bottom: 24px;
    line-height: 1.25;
    letter-spacing: -0.5px;
}

.mission-paragraph {
    font-size: 16px;
    color: var(--gray-600, #475569);
    line-height: 1.7;
    margin-bottom: 20px;
}

/* Animations */
.animate-fade-in-up {
    animation: fadeInUp 0.8s ease-out forwards;
    opacity: 0;
    transform: translateY(20px);
}
.delay-100 { animation-delay: 100ms; }
.delay-200 { animation-delay: 200ms; }
.delay-300 { animation-delay: 300ms; }
.delay-400 { animation-delay: 400ms; }
.delay-500 { animation-delay: 500ms; }

@keyframes fadeInUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
