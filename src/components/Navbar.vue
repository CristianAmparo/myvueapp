<script setup>
import { RouterLink, useRoute } from "vue-router";

const isActiveLink = (routhPath) => {
  const route = useRoute();
  return route.path === routhPath;
};
</script>

<template>
  <header
    class="flex fixed top-0 left-0 right-0 items-center justify-center w-full bg-black h-20 text-white"
  >
    <div class="container flex items-center justify-between">
      <h1 class="text-orange-700 text-xl font-bold">Logo</h1>
      <nav class="flex">
        <input type="checkbox" id="sidebar-active" class="opacity-0" />
        <label htmlFor="sidebar-active" class="cursor-pointer md:hidden">
          <img src="/menu.svg" alt="" />
        </label>

        <ul class="md:flex items-center gap-10 font-medium hidden text-white">
          <RouterLink
            to="/"
            :class="[isActiveLink('/') ? 'text-orange-600' : '']"
          >
            Home
          </RouterLink>
          <RouterLink
            to="/jobs"
            :class="[isActiveLink('/jobs') ? 'text-orange-600' : '']"
            >Jobs</RouterLink
          >
          <RouterLink
            to="/jobs/add"
            :class="[isActiveLink() ? 'text-orange-600' : '']"
            >Add Job</RouterLink
          >
          <RouterLink
            to="/blog"
            :class="[isActiveLink() ? 'text-orange-600' : '']"
            >Blog</RouterLink
          >

          <RouterLink to="">
            <button
              class="flex items-center justify-center px-8 py-2 rounded-lg text-white xl:ml-10 lg:ml-5 bg-orange-600"
            >
              Login
            </button>
          </RouterLink>
        </ul>
        <label id="overlay" htmlFor="sidebar-active"></label>
        <aside class="sidebar-container w-96 bg-black fixed top-0 bottom-0 p-7">
          <label htmlFor="sidebar-active" class="cursor-pointer bg-white">
            <img src="/close.svg" alt="" />
          </label>
          <nav class="flex items-center justify-center w-full h-[70vh]">
            <ul
              class="flex flex-col w-full gap-5 p-5 text-center justify-center items-center font-semibold text-white"
            >
              <RouterLink
                to="/"
                :class="[isActiveLink('/') ? 'text-orange-600' : '']"
              >
                Home
              </RouterLink>
              <RouterLink
                to="/jobs"
                :class="[isActiveLink('/jobs') ? 'text-orange-600' : '']"
                >Jobs</RouterLink
              >
              <RouterLink
                to="/product"
                :class="[isActiveLink() ? 'text-orange-600' : '']"
                >Product</RouterLink
              >
              <RouterLink
                to="/blog"
                :class="[isActiveLink() ? 'text-orange-600' : '']"
                >Blog</RouterLink
              >
              <a href="">
                <button
                  class="flex items-center justify-center px-8 py-2 rounded-lg text-white bg-orange-600"
                >
                  Sign In
                </button>
              </a>
            </ul>
          </nav>
        </aside>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.container {
  @apply max-w-[1440px] md:p-20 p-5;
}
a {
  @apply hover:text-orange-500;
}
a.active {
  @apply text-orange-500;
}

.sidebar-container {
  @apply -right-96 transition-all ease-out duration-300 md:hidden;
  box-shadow: -8px 0 15px -5px rgba(0, 0, 0, 0.3);
}
#sidebar-active:checked ~ .sidebar-container {
  @apply right-0;
}

#sidebar-active:checked ~ #overlay {
  @apply md:hidden backdrop-blur-sm bg-gray-100/10 fixed top-0 left-0 right-0 bottom-0;
}
</style>
