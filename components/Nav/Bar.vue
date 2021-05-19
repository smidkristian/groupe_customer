<template>
    <div class="bg-gray-50 mb-10 shadow">
      <ul class="flex justify-between mx-6 lg:mx-20 xl:mx-96 text-gray-800 py-4">
        <div class="flex justify-center">
          <img src="~/assets/logo/tefal_logo_smaller.png" alt="groupe_seb_logo.png" class="object-none">
        </div>
        <div>
            <Nuxt-Link :to="{ name: 'index' }" class="px-2">Home</Nuxt-Link>
            <Nuxt-Link :to="{ name: 'profile-overview' }" class="px-2">Profile</Nuxt-Link>
            <button
              class="bg-red-600 text-white px-4 py-1 text-sm tracking-wide font-bold rounded-md focus:outline-none"
              @click="modalShowing = true">
                Register
            </button>
            <Modal :showing="modalShowing" @close="modalShowing = false">
                <FormRegister></FormRegister>
            </Modal>

            <!-- <Nuxt-Link v-if="$auth.loggedIn" :to="{ name: 'dashboard' }" class="px-2">Dashboard</Nuxt-Link> -->
        </div>

        <!-- <div class="flex">
            <template v-if="$auth.loggedIn">
                <a href="" class="px-2" @click.prevent="logout">Logout</a>
                <Nuxt-Link :to="{ name: 'profile' }" class="px-4 text-gray-400">{{ $auth.user.name }}</Nuxt-Link>
            </template>

            <template v-if="!$auth.loggedIn">
                <Nuxt-Link :to="{ name: 'login' }" class="px-2">Login</Nuxt-Link>
                <Nuxt-Link :to="{ name: 'register' }" class="px-2">Register</Nuxt-Link>
            </template>
        </div> -->
    </ul>
    </div>
</template>

<script>
    export default {

        data() {
              return {
                  modalShowing: false,
              }
        },
        methods: {
            // async logout () {
            //     await this.$auth.logout()
            //     this.$router.replace({ name: 'login' })
            // }
        }
    }
</script>

<style scoped>

</style>
