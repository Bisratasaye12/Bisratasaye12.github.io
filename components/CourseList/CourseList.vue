<!-- CourseList.vue -->
<template>
    <div class="max-w-3xl mx-auto p-4 space-y-4 m-3 ml-3">
        <h2 class="text-2xl font-bold mb-6">Students also bought</h2>

        <div class="space-y-4">
            <CourseCard v-for="course in displayedCourses" :key="course.id" :course="course"
                @toggle-wishlist="toggleWishlist" />
        </div>

        <button v-if="hasMoreCourses" @click="loadMore"
            class="w-full py-2 px-4 text-center text-gray-600 hover:text-gray-900 transition-colors">
            Show more
        </button>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import CourseCard from './CourseCard.vue'

const courses = ref([
    {
        id: 1,
        title: 'Google Cloud Professional Data Engineer Certification Course',
        rating: 4.4,
        students: 2692,
        hours: '10.5',
        updated: '5/2023',
        price: 59.99,
        image: 'https://img-c.udemycdn.com/course/50x50/4482292_8b02_3.jpg',
        isWishlisted: false
    },
    {
        id: 2,
        title: 'Google Cloud Professional Data Engineer: Get Certified 2022',
        rating: 4.6,
        students: 58225,
        hours: '6.5',
        updated: '1/2023',
        price: 69.99,
        image: 'https://img-c.udemycdn.com/course/50x50/3125272_9408_4.jpg',
        isWishlisted: false
    },
    {
        id: 3,
        title: 'Google Cloud Professional Data Engineer Course [2019 Update]',
        rating: 4.5,
        students: 10795,
        hours: '4.5',
        updated: '7/2019',
        price: 69.99,
        image: 'https://img-c.udemycdn.com/course/50x50/1510852_3367_4.jpg',
        isWishlisted: false
    },
    {
        id: 4,
        title: 'Hands-On Data Engineering in Google Cloud Platform | Python',
        rating: 4.7,
        students: 1479,
        hours: '6',
        updated: '1/2024',
        price: 39.99,
        image: 'https://img-c.udemycdn.com/course/50x50/3125272_9408_4.jpg',
        isWishlisted: false
    },
    {
        id: 5,
        title: 'GCP: Google Cloud Platform: Data Engineer, Cloud Architect',
        rating: 4.2,
        students: 8688,
        hours: '8.5',
        updated: '4/2019',
        price: 19.99,
        image: 'https://img-c.udemycdn.com/course/50x50/3125272_9408_4.jpg',
        isWishlisted: false
    }
])

const itemsPerPage = 3
const currentPage = ref(1)

const displayedCourses = computed(() => {
    return courses.value.slice(0, currentPage.value * itemsPerPage)
})

const hasMoreCourses = computed(() => {
    return displayedCourses.value.length < courses.value.length
})

const loadMore = () => {
    currentPage.value++
}

const toggleWishlist = (courseId) => {
    const course = courses.value.find(c => c.id === courseId)
    if (course) {
        course.isWishlisted = !course.isWishlisted
    }
}
</script>