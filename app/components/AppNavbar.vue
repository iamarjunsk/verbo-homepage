<template>
    <header class="navbar" :class="{ 'scrolled': isScrolled }">
        <div class="navbar-container">
            <!-- Logo -->
            <NuxtLink to="/" class="logo animate-fade-in">
                <span class="logo-icon"> <img src="/logo.png" class="w-24 contain" alt="" /> </span>
            </NuxtLink>

            <!-- Desktop Navigation -->
            <nav class="nav-links">
                <NuxtLink to="/programs" class="nav-link link-hover animate-fade-in-down delay-100">Programs</NuxtLink>
                <NuxtLink to="/how-it-works" class="nav-link link-hover animate-fade-in-down delay-200">How it Works
                </NuxtLink>
                <NuxtLink to="/tutors" class="nav-link link-hover animate-fade-in-down delay-300">Tutors</NuxtLink>
                <NuxtLink to="/about" class="nav-link link-hover animate-fade-in-down delay-400">About</NuxtLink>
            </nav>

            <!-- Desktop Actions -->
            <div class="nav-actions">
                <NuxtLink to="/signin" class="sign-in-link link-hover animate-fade-in-down delay-500">Sign In</NuxtLink>
                <NuxtLink to="/book" class="btn-primary animate-fade-in-down delay-600">Book Free Class</NuxtLink>
            </div>

            <!-- Mobile Menu Button -->
            <button class="mobile-menu-btn" @click="toggleMenu" :class="{ 'active': isMenuOpen }">
                <span class="menu-line"></span>
                <span class="menu-line"></span>
                <span class="menu-line"></span>
            </button>
        </div>

        <!-- Mobile Menu -->
        <Transition name="slide">
            <div v-if="isMenuOpen" class="mobile-menu">
                <nav class="mobile-nav">
                    <NuxtLink to="/programs" class="mobile-nav-link" @click="closeMenu">Programs</NuxtLink>
                    <NuxtLink to="/how-it-works" class="mobile-nav-link" @click="closeMenu">How it Works</NuxtLink>
                    <NuxtLink to="/tutors" class="mobile-nav-link" @click="closeMenu">Tutors</NuxtLink>
                    <NuxtLink to="/about" class="mobile-nav-link" @click="closeMenu">About</NuxtLink>
                    <div class="mobile-actions">
                        <NuxtLink to="/signin" class="mobile-sign-in" @click="closeMenu">Sign In</NuxtLink>
                        <NuxtLink to="/book" class="btn-primary" @click="closeMenu">Book Free Class</NuxtLink>
                    </div>
                </nav>
            </div>
        </Transition>
    </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const handleScroll = () => {
    isScrolled.value = window.scrollY > 20
}

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value
    if (isMenuOpen.value) {
        document.body.style.overflow = 'hidden'
    } else {
        document.body.style.overflow = ''
    }
}

const closeMenu = () => {
    isMenuOpen.value = false
    document.body.style.overflow = ''
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    background-color: rgba(255, 255, 255, 0.95);
    transition: all 0.3s ease;
}

.navbar.scrolled {
    background-color: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    box-shadow: 0 2px 20px rgba(0, 0, 0, 0.08);
}

.navbar-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1280px;
    margin: 0 auto;
    padding: 16px 24px;
}

@media (min-width: 768px) {
    .navbar-container {
        padding: 18px 40px;
    }
}

@media (min-width: 1024px) {
    .navbar-container {
        padding: 18px 64px;
    }
}

/* Logo */
.logo {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    font-weight: 700;
    font-size: 22px;
    color: var(--navy-dark);
}

.logo-icon {
    color: var(--primary-blue);
    font-size: 24px;
}

.logo-text {
    letter-spacing: -0.5px;
}

/* Desktop Navigation */
.nav-links {
    display: none;
    align-items: center;
    gap: 36px;
}

@media (min-width: 1024px) {
    .nav-links {
        display: flex;
    }
}

.nav-link {
    position: relative;
    color: var(--gray-600);
    font-size: 15px;
    font-weight: 500;
    text-decoration: none;
    transition: color 0.3s ease;
    padding-bottom: 4px;
}

.nav-link::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background-color: var(--primary-blue);
    transition: width 0.3s ease;
}

.nav-link:hover {
    color: var(--navy-dark);
}

.nav-link:hover::after {
    width: 100%;
}

.nav-link.router-link-active,
.nav-link.router-link-exact-active {
    color: var(--primary-blue);
    font-weight: 600;
}

.nav-link.router-link-active::after,
.nav-link.router-link-exact-active::after {
    width: 100%;
}

/* Mobile nav active */
.mobile-nav-link.router-link-active,
.mobile-nav-link.router-link-exact-active {
    color: var(--primary-blue);
    font-weight: 600;
}

/* Desktop Actions */
.nav-actions {
    display: none;
    align-items: center;
    gap: 24px;
}

@media (min-width: 1024px) {
    .nav-actions {
        display: flex;
    }
}

.sign-in-link {
    color: var(--gray-700);
    font-weight: 600;
    font-size: 15px;
    text-decoration: none;
}

.nav-actions .btn-primary {
    padding: 12px 22px;
    font-size: 14px;
}

/* Mobile Menu Button */
.mobile-menu-btn {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    width: 32px;
    height: 32px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 4px;
}

@media (min-width: 1024px) {
    .mobile-menu-btn {
        display: none;
    }
}

.menu-line {
    display: block;
    width: 100%;
    height: 2px;
    background-color: var(--navy-dark);
    border-radius: 2px;
    transition: all 0.3s ease;
}

.mobile-menu-btn.active .menu-line:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
}

.mobile-menu-btn.active .menu-line:nth-child(2) {
    opacity: 0;
}

.mobile-menu-btn.active .menu-line:nth-child(3) {
    transform: rotate(-45deg) translate(5px, -5px);
}

/* Mobile Menu */
.mobile-menu {
    position: fixed;
    top: 65px;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: white;
    padding: 24px;
    overflow-y: auto;
}

.mobile-nav {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.mobile-nav-link {
    display: block;
    padding: 16px 0;
    color: var(--gray-700);
    font-size: 18px;
    font-weight: 500;
    text-decoration: none;
    border-bottom: 1px solid var(--gray-100);
    transition: color 0.3s ease;
}

.mobile-nav-link:hover {
    color: var(--primary-blue);
}

.mobile-actions {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-top: 24px;
    padding-top: 24px;
    border-top: 1px solid var(--gray-200);
}

.mobile-sign-in {
    display: block;
    text-align: center;
    padding: 14px;
    color: var(--gray-700);
    font-weight: 600;
    font-size: 16px;
    text-decoration: none;
}

/* Transitions */
.slide-enter-active,
.slide-leave-active {
    transition: all 0.3s ease;
}

.slide-enter-from,
.slide-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>
