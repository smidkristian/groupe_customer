<template>
  <div class="flex flex-col h-screen bg-gray-100">
    <div>
      <NavBar />
    </div>
    <div class="w-full h-full">
      <div class="mx-6 lg:mx-20 xl:mx-96 flex h-full">
        <SideNavBar />
        <div class="w-full flex justify-center">
          <Nuxt />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
</style>
