<template>
    <div class="booking-page">
        <!-- Booking Header -->
        <header class="booking-header">
            <div class="booking-header-container">
                <NuxtLink to="/" class="logo">
                    <span class="logo-icon">✦</span>
                    <span class="logo-text">VerboEdu</span>
                </NuxtLink>
                <NuxtLink to="/" class="exit-btn">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <line x1="18" y1="6" x2="6" y2="18"></line>
                        <line x1="6" y1="6" x2="18" y2="18"></line>
                    </svg>
                    Exit Booking
                </NuxtLink>
            </div>
        </header>

        <!-- Progress Steps -->
        <div class="progress-container">
            <div class="progress-steps">
                <div class="step" :class="{ active: currentStep >= 1, completed: currentStep > 1 }">
                    <div class="step-circle">
                        <svg v-if="currentStep > 1" width="16" height="16" viewBox="0 0 24 24" fill="none"
                            stroke="currentColor" stroke-width="3">
                            <polyline points="20 6 9 17 4 12"></polyline>
                        </svg>
                        <span v-else>1</span>
                    </div>
                    <span class="step-label">Program</span>
                </div>
                <div class="step-line" :class="{ active: currentStep > 1 }"></div>
                <div class="step" :class="{ active: currentStep >= 2, completed: currentStep > 2 }">
                    <div class="step-circle">
                        <svg v-if="currentStep > 2" width="16" height="16" viewBox="0 0 24 24" fill="none"
                            stroke="currentColor" stroke-width="3">
                            <polyline points="20 6 9 17 4 12"></polyline>
                        </svg>
                        <span v-else>2</span>
                    </div>
                    <span class="step-label">Schedule</span>
                </div>
                <div class="step-line" :class="{ active: currentStep > 2 }"></div>
                <div class="step" :class="{ active: currentStep >= 3 }">
                    <div class="step-circle">3</div>
                    <span class="step-label">Details</span>
                </div>
            </div>
        </div>

        <!-- Step Content -->
        <main class="booking-content">
            <Transition name="slide-fade" mode="out-in">
                <!-- Step 1: Program Selection -->
                <div v-if="currentStep === 1" key="step1" class="step-content animate-fade-in-up">
                    <div class="step-header">
                        <h1 class="step-title">Choose Your Program</h1>
                        <p class="step-subtitle">Select the category that best matches your learning goals.</p>
                    </div>

                    <!-- Categories -->
                    <div class="categories-grid">
                        <div v-for="category in categories" :key="category.id" class="category-card"
                            :class="{ selected: selectedCategory?.id === category.id }"
                            @click="selectCategory(category)">
                            <div class="category-icon" :style="{ backgroundColor: category.bgColor }">
                                <component :is="category.icon" />
                            </div>
                            <h3 class="category-title">{{ category.title }}</h3>
                            <p class="category-desc">{{ category.description }}</p>
                        </div>
                    </div>

                    <!-- Subjects -->
                    <div v-if="selectedCategory" class="subjects-section animate-fade-in-up">
                        <h3 class="subjects-title">
                            Select a Subject in <span class="highlight">{{ selectedCategory.title }}</span>
                        </h3>
                        <div class="subjects-grid">
                            <button v-for="subject in selectedCategory.subjects" :key="subject" class="subject-chip"
                                :class="{ selected: selectedSubject === subject }" @click="selectedSubject = subject">
                                {{ subject }}
                            </button>
                        </div>
                    </div>

                    <!-- Footer -->
                    <div class="step-footer">
                        <div class="selection-summary" v-if="selectedCategory && selectedSubject">
                            Selected: <strong>{{ selectedCategory.title }} > {{ selectedSubject }}</strong>
                        </div>
                        <button class="btn-primary next-btn" :disabled="!selectedCategory || !selectedSubject"
                            @click="nextStep">
                            Next Step →
                        </button>
                    </div>
                </div>

                <!-- Step 2: Schedule -->
                <div v-else-if="currentStep === 2" key="step2" class="step-content animate-fade-in-up">
                    <div class="schedule-layout">
                        <!-- Calendar -->
                        <div class="calendar-section">
                            <div class="calendar-header">
                                <h3 class="calendar-month">{{ currentMonthYear }}</h3>
                                <div class="calendar-nav">
                                    <button @click="prevMonth" class="cal-nav-btn">
                                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none"
                                            stroke="currentColor" stroke-width="2">
                                            <polyline points="15 18 9 12 15 6"></polyline>
                                        </svg>
                                    </button>
                                    <button @click="nextMonth" class="cal-nav-btn">
                                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none"
                                            stroke="currentColor" stroke-width="2">
                                            <polyline points="9 18 15 12 9 6"></polyline>
                                        </svg>
                                    </button>
                                </div>
                            </div>
                            <div class="calendar-weekdays">
                                <span v-for="day in ['S', 'M', 'T', 'W', 'T', 'F', 'S']" :key="day">{{ day }}</span>
                            </div>
                            <div class="calendar-days">
                                <button v-for="day in calendarDays" :key="day.date" class="calendar-day" :class="{
                                    'other-month': !day.currentMonth,
                                    'selected': selectedDate === day.date,
                                    'today': day.isToday,
                                    'disabled': day.isPast
                                }" :disabled="day.isPast || !day.currentMonth" @click="selectedDate = day.date">
                                    {{ day.day }}
                                </button>
                            </div>
                        </div>

                        <!-- Time Slots -->
                        <div class="slots-section">
                            <h3 class="slots-title">Available Slots</h3>
                            <div class="slots-grid">
                                <button v-for="slot in timeSlots" :key="slot" class="slot-btn"
                                    :class="{ selected: selectedTime === slot }" @click="selectedTime = slot">
                                    {{ slot }}
                                </button>
                            </div>
                            <p class="timezone-note">
                                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                    stroke-width="2">
                                    <circle cx="12" cy="12" r="10"></circle>
                                    <polyline points="12 6 12 12 16 14"></polyline>
                                </svg>
                                All times are in your local timezone (GMT+5:30)
                            </p>
                        </div>

                        <!-- Summary -->
                        <div class="summary-section">
                            <div class="summary-card">
                                <div class="summary-header">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <rect x="3" y="4" width="18" height="18" rx="2"></rect>
                                        <line x1="16" y1="2" x2="16" y2="6"></line>
                                        <line x1="8" y1="2" x2="8" y2="6"></line>
                                        <line x1="3" y1="10" x2="21" y2="10"></line>
                                    </svg>
                                    Booking Summary
                                </div>
                                <div class="summary-content">
                                    <div class="summary-item">
                                        <span class="summary-label">SUBJECT</span>
                                        <span class="summary-value">{{ selectedSubject }} ({{ selectedCategory?.title
                                            }})</span>
                                        <span class="summary-sub">1-on-1 Personalized Session</span>
                                    </div>
                                    <div class="summary-item" v-if="selectedDate && selectedTime">
                                        <span class="summary-label">SELECTED DATE & TIME</span>
                                        <span class="summary-date">📅 {{ formatSelectedDate }}</span>
                                        <span class="summary-time">🕐 {{ selectedTime }}</span>
                                    </div>
                                    <div class="summary-cost">
                                        <span>Trial Cost</span>
                                        <span class="free-badge">Free</span>
                                    </div>
                                </div>
                            </div>
                            <div class="guarantee-card">
                                <div class="guarantee-icon">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                        stroke-width="2">
                                        <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
                                        <polyline points="22 4 12 14.01 9 11.01"></polyline>
                                    </svg>
                                </div>
                                <div>
                                    <strong>Our Guarantee</strong>
                                    <p>VerboEdu tutors are vetted professionals with verified academic records and
                                        teaching experience.</p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Footer -->
                    <div class="step-footer schedule-footer">
                        <button class="back-btn" @click="prevStep">
                            ← Back to Program
                        </button>
                        <button class="btn-primary next-btn" :disabled="!selectedDate || !selectedTime"
                            @click="nextStep">
                            Next: Your Details
                        </button>
                    </div>
                </div>

                <!-- Step 3: Details -->
                <div v-else-if="currentStep === 3" key="step3" class="step-content animate-fade-in-up">
                    <div class="details-card">
                        <div class="step-header">
                            <h1 class="step-title">Final Step: Contact Details</h1>
                            <p class="step-subtitle">Fill in your information to secure your free trial class.</p>
                        </div>

                        <form @submit.prevent="submitBooking" class="details-form">
                            <div class="form-row">
                                <div class="form-group">
                                    <label class="form-label">Student Full Name</label>
                                    <input type="text" v-model="formData.name" class="form-input"
                                        placeholder="Enter student name" required />
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Email Address</label>
                                    <input type="email" v-model="formData.email" class="form-input"
                                        placeholder="email@example.com" required />
                                </div>
                            </div>

                            <div class="form-group">
                                <label class="form-label">Phone Number</label>
                                <input type="tel" v-model="formData.phone" class="form-input"
                                    placeholder="+1 (555) 000-0000" required />
                            </div>

                            <div class="form-group">
                                <label class="form-label">Tell us your learning goals</label>
                                <textarea v-model="formData.goals" class="form-textarea"
                                    placeholder="What would you like to achieve in this session? (e.g., preparation for SAT, understanding Calculus basics...)"
                                    rows="4"></textarea>
                            </div>

                            <button type="submit" class="btn-primary submit-btn">
                                Confirm Booking →
                            </button>
                        </form>

                        <div class="session-reminder">
                            <div class="reminder-icon">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                                    stroke-width="2">
                                    <rect x="3" y="4" width="18" height="18" rx="2"></rect>
                                    <line x1="16" y1="2" x2="16" y2="6"></line>
                                    <line x1="8" y1="2" x2="8" y2="6"></line>
                                    <line x1="3" y1="10" x2="21" y2="10"></line>
                                </svg>
                            </div>
                            <div class="reminder-content">
                                <span class="reminder-label">Selected Session</span>
                                <span class="reminder-date">{{ formatSelectedDate }} at {{ selectedTime }}</span>
                            </div>
                            <button class="change-btn" @click="currentStep = 2">Change Schedule</button>
                        </div>
                    </div>
                </div>
            </Transition>
        </main>

        <!-- Help Footer -->
        <footer class="booking-footer">
            <p>Need help booking? <a href="#">Contact Support</a></p>
        </footer>
    </div>
</template>

<script setup>
import { ref, computed, h } from 'vue'

definePageMeta({
    layout: false
})

useHead({
    title: 'Book a Free Demo - VerboEdu'
})

const currentStep = ref(1)
const selectedCategory = ref(null)
const selectedSubject = ref(null)
const selectedDate = ref(null)
const selectedTime = ref(null)
const currentMonth = ref(new Date())

const formData = ref({
    name: '',
    email: '',
    phone: '',
    goals: ''
})

// Icons
const IconSchool = () => h('svg', { width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
    h('path', { d: 'M22 10v6M2 10l10-5 10 5-10 5z' }),
    h('path', { d: 'M6 12v5c0 1 2 3 6 3s6-2 6-3v-5' })
])

const IconCode = () => h('svg', { width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
    h('polyline', { points: '16 18 22 12 16 6' }),
    h('polyline', { points: '8 6 2 12 8 18' })
])

const IconExam = () => h('svg', { width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
    h('path', { d: 'M9 11l3 3L22 4' }),
    h('path', { d: 'M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11' })
])

const IconGovernment = () => h('svg', { width: 24, height: 24, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2 }, [
    h('path', { d: 'M3 21h18' }),
    h('path', { d: 'M5 21V7l7-4 7 4v14' }),
    h('path', { d: 'M9 21v-4a2 2 0 0 1 2-2h2a2 2 0 0 1 2 2v4' })
])

const categories = ref([
    {
        id: 1,
        title: 'K-12',
        description: 'School curriculum and foundations',
        icon: IconSchool,
        bgColor: '#f0fdfa',
        subjects: ['Mathematics', 'Science', 'English', 'Social Studies', 'Hindi']
    },
    {
        id: 2,
        title: 'Engineering',
        description: 'Advanced technical subjects',
        icon: IconCode,
        bgColor: '#f0fdfa',
        subjects: ['Mathematics', 'Physics', 'Chemistry', 'Computer Science', 'Mechanical Systems', 'Electronics']
    },
    {
        id: 3,
        title: 'Entrance Exams',
        description: 'JEE, NEET, and more',
        icon: IconExam,
        bgColor: '#f0fdfa',
        subjects: ['JEE Main', 'JEE Advanced', 'NEET', 'CUET', 'SAT', 'GRE', 'GMAT']
    },
    {
        id: 4,
        title: 'PSC Coaching',
        description: 'Civil services preparation',
        icon: IconGovernment,
        bgColor: '#f0fdfa',
        subjects: ['Prelims', 'Mains', 'Interview Prep', 'Current Affairs', 'Essay Writing']
    }
])

const timeSlots = ref([
    '09:00 AM', '10:30 AM', '11:00 AM', '01:00 PM',
    '02:30 PM', '04:00 PM', '05:30 PM', '07:00 PM'
])

const currentMonthYear = computed(() => {
    return currentMonth.value.toLocaleDateString('en-US', { month: 'long', year: 'numeric' })
})

const calendarDays = computed(() => {
    const year = currentMonth.value.getFullYear()
    const month = currentMonth.value.getMonth()
    const firstDay = new Date(year, month, 1)
    const lastDay = new Date(year, month + 1, 0)
    const today = new Date()
    today.setHours(0, 0, 0, 0)

    const days = []

    // Previous month days
    const startPadding = firstDay.getDay()
    for (let i = startPadding - 1; i >= 0; i--) {
        const date = new Date(year, month, -i)
        days.push({
            day: date.getDate(),
            date: date.toISOString().split('T')[0],
            currentMonth: false,
            isPast: date < today,
            isToday: false
        })
    }

    // Current month days
    for (let i = 1; i <= lastDay.getDate(); i++) {
        const date = new Date(year, month, i)
        days.push({
            day: i,
            date: date.toISOString().split('T')[0],
            currentMonth: true,
            isPast: date < today,
            isToday: date.getTime() === today.getTime()
        })
    }

    // Next month days
    const endPadding = 42 - days.length
    for (let i = 1; i <= endPadding; i++) {
        const date = new Date(year, month + 1, i)
        days.push({
            day: i,
            date: date.toISOString().split('T')[0],
            currentMonth: false,
            isPast: false,
            isToday: false
        })
    }

    return days
})

const formatSelectedDate = computed(() => {
    if (!selectedDate.value) return ''
    const date = new Date(selectedDate.value)
    return date.toLocaleDateString('en-US', { weekday: 'long', month: 'short', day: 'numeric', year: 'numeric' })
})

const selectCategory = (category) => {
    selectedCategory.value = category
    selectedSubject.value = null
}

const prevMonth = () => {
    currentMonth.value = new Date(currentMonth.value.getFullYear(), currentMonth.value.getMonth() - 1)
}

const nextMonth = () => {
    currentMonth.value = new Date(currentMonth.value.getFullYear(), currentMonth.value.getMonth() + 1)
}

const nextStep = () => {
    if (currentStep.value < 3) currentStep.value++
}

const prevStep = () => {
    if (currentStep.value > 1) currentStep.value--
}

const submitBooking = () => {
    const number = "919778493428"
    const text = `*New Demo Class Booking*
*Student Name:* ${formData.value.name}
*Email:* ${formData.value.email}
*Phone:* ${formData.value.phone}
*Program:* ${selectedCategory.value?.title} > ${selectedSubject.value}
*Schedule:* ${formatSelectedDate.value} at ${selectedTime.value}
*Goals:* ${formData.value.goals || 'Not provided'}`

    const url = `https://wa.me/${number}?text=${encodeURIComponent(text)}`
    window.open(url, '_blank')
}
</script>

<style scoped>
.booking-page {
    min-height: 100vh;
    background: linear-gradient(180deg, #f8fafc 0%, #ffffff 100%);
    display: flex;
    flex-direction: column;
}

/* Header */
.booking-header {
    background: white;
    border-bottom: 1px solid var(--gray-200);
}

.booking-header-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 16px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
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
}

.exit-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    color: var(--gray-600);
    text-decoration: none;
    font-size: 14px;
    font-weight: 500;
    transition: color 0.3s;
}

.exit-btn:hover {
    color: var(--navy-dark);
}

/* Progress Steps */
.progress-container {
    padding: 32px 24px;
    display: flex;
    justify-content: center;
}

.progress-steps {
    display: flex;
    align-items: center;
    gap: 0;
}

.step {
    display: flex;
    align-items: center;
    gap: 10px;
}

.step-circle {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
    font-size: 14px;
    background: var(--gray-200);
    color: var(--gray-500);
    transition: all 0.3s;
}

.step.active .step-circle {
    background: var(--primary);
    color: white;
}

.step.completed .step-circle {
    background: #10b981;
    color: white;
}

.step-label {
    font-size: 14px;
    font-weight: 500;
    color: var(--gray-500);
}

.step.active .step-label {
    color: var(--primary);
    font-weight: 600;
}

.step-line {
    width: 80px;
    height: 3px;
    background: var(--gray-200);
    margin: 0 16px;
    transition: background 0.3s;
}

.step-line.active {
    background: var(--primary);
}

@media (max-width: 640px) {
    .step-label {
        display: none;
    }

    .step-line {
        width: 40px;
    }
}

/* Content */
.booking-content {
    flex: 1;
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px 48px;
    width: 100%;
}

.step-content {
    max-width: 900px;
    margin: 0 auto;
}

.step-header {
    text-align: center;
    margin-bottom: 40px;
}

.step-title {
    font-size: 32px;
    font-weight: 800;
    color: var(--navy-dark);
    margin-bottom: 12px;
}

.step-subtitle {
    font-size: 16px;
    color: var(--gray-600);
}

/* Categories */
.categories-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
    margin-bottom: 40px;
}

@media (min-width: 768px) {
    .categories-grid {
        grid-template-columns: repeat(4, 1fr);
    }
}

.category-card {
    background: white;
    border: 2px solid var(--gray-200);
    border-radius: 16px;
    padding: 24px 20px;
    cursor: pointer;
    transition: all 0.3s;
}

.category-card:hover {
    border-color: var(--primary-light);
}

.category-card.selected {
    border-color: var(--primary);
    background: #f0fdfa;
}

.category-icon {
    width: 48px;
    height: 48px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 16px;
    color: var(--primary);
}

.category-card.selected .category-icon {
    background: var(--primary) !important;
    color: white;
}

.category-title {
    font-size: 16px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 6px;
}

.category-desc {
    font-size: 13px;
    color: var(--gray-600);
    line-height: 1.5;
}

/* Subjects */
.subjects-section {
    background: white;
    border-radius: 16px;
    padding: 28px;
    border: 1px solid var(--gray-200);
    margin-bottom: 32px;
}

.subjects-title {
    font-size: 18px;
    font-weight: 600;
    color: var(--navy-dark);
    margin-bottom: 20px;
}

.subjects-title .highlight {
    color: var(--primary);
}

.subjects-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
}

.subject-chip {
    padding: 10px 20px;
    border: 1.5px solid var(--gray-300);
    border-radius: 50px;
    background: white;
    font-size: 14px;
    font-weight: 500;
    color: var(--gray-700);
    cursor: pointer;
    transition: all 0.3s;
}

.subject-chip:hover {
    border-color: var(--primary);
    color: var(--primary);
}

.subject-chip.selected {
    background: var(--primary);
    border-color: var(--primary);
    color: white;
}

/* Step Footer */
.step-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 24px;
    border-top: 1px solid var(--gray-200);
}

.selection-summary {
    font-size: 14px;
    color: var(--gray-600);
}

.next-btn {
    padding: 14px 32px;
}

.next-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

/* Schedule Layout */
.schedule-layout {
    display: grid;
    grid-template-columns: 1fr;
    gap: 24px;
}

@media (min-width: 1024px) {
    .schedule-layout {
        grid-template-columns: 320px 1fr 280px;
    }
}

/* Calendar */
.calendar-section {
    background: white;
    border: 1px solid var(--gray-200);
    border-radius: 16px;
    padding: 24px;
}

.calendar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

.calendar-month {
    font-size: 18px;
    font-weight: 700;
    color: var(--navy-dark);
}

.calendar-nav {
    display: flex;
    gap: 8px;
}

.cal-nav-btn {
    width: 32px;
    height: 32px;
    border: 1px solid var(--gray-200);
    border-radius: 8px;
    background: white;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--gray-600);
    transition: all 0.3s;
}

.cal-nav-btn:hover {
    border-color: var(--primary);
    color: var(--primary);
}

.calendar-weekdays {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 4px;
    margin-bottom: 8px;
}

.calendar-weekdays span {
    text-align: center;
    font-size: 12px;
    font-weight: 600;
    color: var(--gray-500);
    padding: 8px 0;
}

.calendar-days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 4px;
}

.calendar-day {
    aspect-ratio: 1;
    border: none;
    background: transparent;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 500;
    color: var(--navy-dark);
    cursor: pointer;
    transition: all 0.2s;
}

.calendar-day:hover:not(.disabled):not(.other-month) {
    background: var(--gray-100);
}

.calendar-day.other-month {
    color: var(--gray-300);
}

.calendar-day.disabled {
    color: var(--gray-300);
    cursor: not-allowed;
}

.calendar-day.today {
    background: var(--gray-100);
}

.calendar-day.selected {
    background: #0d9488;
    color: white;
}

/* Slots */
.slots-section {
    background: white;
    border: 1px solid var(--gray-200);
    border-radius: 16px;
    padding: 24px;
}

.slots-title {
    font-size: 18px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 20px;
}

.slots-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
    margin-bottom: 20px;
}

.slot-btn {
    padding: 12px;
    border: 1.5px solid var(--gray-300);
    border-radius: 10px;
    background: white;
    font-size: 14px;
    font-weight: 500;
    color: var(--gray-700);
    cursor: pointer;
    transition: all 0.3s;
}

.slot-btn:hover {
    border-color: var(--primary);
    color: var(--primary);
}

.slot-btn.selected {
    background: var(--primary);
    border-color: var(--primary);
    color: white;
}

.timezone-note {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 12px;
    color: var(--gray-500);
}

/* Summary */
.summary-section {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.summary-card {
    background: white;
    border: 1px solid var(--gray-200);
    border-radius: 16px;
    padding: 20px;
}

.summary-header {
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 700;
    color: var(--navy-dark);
    margin-bottom: 20px;
}

.summary-item {
    margin-bottom: 20px;
    padding-bottom: 20px;
    border-bottom: 1px solid var(--gray-100);
}

.summary-label {
    display: block;
    font-size: 11px;
    font-weight: 600;
    color: var(--gray-500);
    letter-spacing: 0.5px;
    margin-bottom: 6px;
}

.summary-value {
    display: block;
    font-size: 15px;
    font-weight: 600;
    color: var(--navy-dark);
}

.summary-sub {
    display: block;
    font-size: 12px;
    color: var(--gray-500);
    margin-top: 2px;
}

.summary-date,
.summary-time {
    display: block;
    font-size: 14px;
    color: var(--primary);
    font-weight: 500;
    margin-top: 4px;
}

.summary-cost {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
    color: var(--gray-600);
}

.free-badge {
    color: #10b981;
    font-weight: 700;
}

.guarantee-card {
    background: #f0fdfa;
    border-radius: 12px;
    padding: 16px;
    display: flex;
    gap: 12px;
}

.guarantee-icon {
    width: 36px;
    height: 36px;
    background: var(--primary);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    flex-shrink: 0;
}

.guarantee-card strong {
    display: block;
    font-size: 14px;
    color: var(--navy-dark);
    margin-bottom: 4px;
}

.guarantee-card p {
    font-size: 12px;
    color: var(--gray-600);
    line-height: 1.5;
}

/* Schedule Footer */
.schedule-footer {
    margin-top: 32px;
}

.back-btn {
    background: none;
    border: none;
    color: var(--gray-600);
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: color 0.3s;
}

.back-btn:hover {
    color: var(--navy-dark);
}

/* Details Form */
.details-card {
    background: white;
    border: 1px solid var(--gray-200);
    border-radius: 20px;
    padding: 40px;
    max-width: 700px;
    margin: 0 auto;
}

.details-form {
    margin-top: 32px;
}

.form-row {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
}

@media (min-width: 640px) {
    .form-row {
        grid-template-columns: 1fr 1fr;
    }
}

.form-group {
    margin-bottom: 20px;
}

.form-label {
    display: block;
    font-size: 14px;
    font-weight: 600;
    color: var(--navy-dark);
    margin-bottom: 8px;
}

.form-input,
.form-textarea {
    width: 100%;
    padding: 14px 16px;
    border: 1.5px solid var(--gray-300);
    border-radius: 10px;
    font-size: 15px;
    color: var(--navy-dark);
    transition: border-color 0.3s;
}

.form-input:focus,
.form-textarea:focus {
    outline: none;
    border-color: var(--primary);
}

.form-input::placeholder,
.form-textarea::placeholder {
    color: var(--gray-400);
}

.form-textarea {
    resize: vertical;
    min-height: 100px;
}

.submit-btn {
    width: 100%;
    padding: 16px;
    font-size: 16px;
    margin-top: 8px;
}

.session-reminder {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-top: 24px;
    padding: 16px;
    background: var(--gray-50);
    border-radius: 12px;
}

.reminder-icon {
    width: 44px;
    height: 44px;
    background: #ccfbf1;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--primary);
    flex-shrink: 0;
}

.reminder-content {
    flex: 1;
}

.reminder-label {
    display: block;
    font-size: 12px;
    color: var(--gray-500);
}

.reminder-date {
    font-size: 14px;
    font-weight: 600;
    color: var(--navy-dark);
}

.change-btn {
    background: none;
    border: none;
    color: var(--primary);
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
}

/* Footer */
.booking-footer {
    padding: 24px;
    text-align: center;
    border-top: 1px solid var(--gray-200);
    background: white;
}

.booking-footer p {
    font-size: 14px;
    color: var(--gray-600);
}

.booking-footer a {
    color: var(--primary);
    font-weight: 600;
    text-decoration: none;
}

/* Transitions */
.slide-fade-enter-active,
.slide-fade-leave-active {
    transition: all 0.3s ease;
}

.slide-fade-enter-from {
    opacity: 0;
    transform: translateX(20px);
}

.slide-fade-leave-to {
    opacity: 0;
    transform: translateX(-20px);
}
</style>
