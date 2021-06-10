<template>
  <div class="bg-red-800">
    <div class="container py-4 mx-auto">
      <div class="flex justify-around items-center">
        <h1 class="font-sans text-xl md:text-3xl font-bold capitalize text-red-100">
          que_todo
        </h1>
        <ul class="flex">
          <router-link to="/" class="font-sans text-base md:text-lg text-white capitalize mr-4 md:mr-7">Home</router-link>
          <router-link to="/about" class="font-sans text-base md:text-lg text-white capitalize">About</router-link>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    header: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped></style>
