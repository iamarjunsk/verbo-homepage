<template>
    <footer class="footer">
        <div class="footer-container">
            <!-- Top Section -->
            <div class="footer-top">
                <!-- Logo and Branding -->
                <div class="footer-brand animate-fade-in">
                    <NuxtLink to="/" class="footer-logo">
                        <span class="logo-icon">✦</span>
                        <span class="logo-text">VerboEdu</span>
                    </NuxtLink>
                </div>

                <!-- Navigation Links -->
                <nav class="footer-nav animate-fade-in delay-200">
                    <NuxtLink to="/privacy" class="footer-link link-hover">Privacy Policy</NuxtLink>
                    <NuxtLink to="/terms" class="footer-link link-hover">Terms of Service</NuxtLink>
                    <NuxtLink to="/contact" class="footer-link link-hover">Contact Us</NuxtLink>
                </nav>

                <!-- Social Icons -->
                <div class="footer-social animate-fade-in delay-400">
                    <a href="#" class="social-icon" aria-label="Share">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <circle cx="18" cy="5" r="3"></circle>
                            <circle cx="6" cy="12" r="3"></circle>
                            <circle cx="18" cy="19" r="3"></circle>
                            <line x1="8.59" y1="13.51" x2="15.42" y2="17.49"></line>
                            <line x1="15.41" y1="6.51" x2="8.59" y2="10.49"></line>
                        </svg>
                    </a>
                    <a href="#" class="social-icon" aria-label="Globe">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <circle cx="12" cy="12" r="10"></circle>
                            <line x1="2" y1="12" x2="22" y2="12"></line>
                            <path
                                d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z">
                            </path>
                        </svg>
                    </a>
                    <a href="#" class="social-icon" aria-label="Email">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <circle cx="12" cy="12" r="4"></circle>
                            <path d="M16 8v5a3 3 0 0 0 6 0v-1a10 10 0 1 0-3.92 7.94"></path>
                        </svg>
                    </a>
                </div>
            </div>

            <!-- Bottom Section -->
            <div class="footer-bottom">
                <p class="copyright">
                    © 2024 VerboEdu Learning Systems. Empowering students worldwide.
                </p>
            </div>
        </div>
    </footer>
</template>

<script setup>
</script>

<style scoped>
.footer {
    background-color: var(--gray-50);
    border-top: 1px solid var(--gray-200);
}

.footer-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
}

@media (min-width: 768px) {
    .footer-container {
        padding: 0 40px;
    }
}

@media (min-width: 1024px) {
    .footer-container {
        padding: 0 64px;
    }
}

.footer-top {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 24px;
    padding: 40px 0;
}

@media (min-width: 768px) {
    .footer-top {
        flex-direction: row;
        justify-content: space-between;
        gap: 32px;
    }
}

/* Logo */
.footer-logo {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    font-weight: 700;
    font-size: 20px;
    color: var(--navy-dark);
}

.logo-icon {
    color: var(--primary);
    font-size: 22px;
}

/* Navigation */
.footer-nav {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 24px;
}

@media (min-width: 768px) {
    .footer-nav {
        gap: 32px;
    }
}

.footer-link {
    color: var(--gray-600);
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    transition: color 0.3s ease;
}

.footer-link:hover {
    color: var(--primary);
}

/* Social Icons */
.footer-social {
    display: flex;
    gap: 12px;
}

/* Bottom */
.footer-bottom {
    padding: 24px 0;
    border-top: 1px solid var(--gray-200);
    text-align: center;
}

.copyright {
    color: var(--gray-500);
    font-size: 13px;
}
</style>
