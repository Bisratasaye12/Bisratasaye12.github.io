<template>
  <NuxtLayout>
    <Navbar />
    <CourseDetail />
     <!-- <CourseHeader /> -->
    <main>
      <PreviewCourse />
      <Certeficates />
      <Objectives />
      <RelatedTopic />
      <CourseContent />
      <CourseDescription />
      <FeaturedReview />
      <CourseList />
      <FrequentlyBoughtTogether />
      <InstructorDetails />
      <Reviews />  
 <OtherCourses/>

    </main>
    <Footer />
  </NuxtLayout>
</template>


<script setup>
import Navbar from './components/Navbar/Navbar.vue'
import CourseDetail from "./components/CourseDetail.vue";
import Certeficates from './components/Certeficates.vue';
import Objectives from './components/Objectives.vue';
import RelatedTopic from './components/RelatedTopic.vue';
import CourseContent from './components/CourseContent.vue';
import CourseDescription from './components/CourseDescription.vue';
import Footer from './components/Footer.vue';

import FrequentlyBoughtTogether from './components/FrequentlyBoughtTogather/FrequentlBoughtTogather.vue'
import CourseList from './components/CourseList/CourseList.vue';
import InstructorDetails from './components/InstructorDetails/Instructor.vue'
import Reviews from './components/Reviews/Reviews.vue'
// import PreviewCourse from './components/PreviewCourse.vue';

import PreviewCourse from './components/PreviewCourse.vue';
import OtherCourses from './components/OtherCourses.vue';
                     

</script>

<style lang="css">
/* Add your styles here */
main {
  width: 50%;
  /* Take up 70% of the screen horizontally */
  margin-left: 10%;
  /*    <CourseDetail />Start from 30% of the screen horizontally */
  text-align: justify;
  /* Justify content inside main */

}
</style>
