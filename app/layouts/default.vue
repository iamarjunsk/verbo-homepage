<template>
    <div class="app-layout">
        <AppNavbar />
        <main class="main-content">
            <slot />
        </main>
        <AppFooter />
    </div>
</template>

<script setup>
</script>

<style scoped>
.app-layout {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

.main-content {
    flex: 1;
}
</style>
