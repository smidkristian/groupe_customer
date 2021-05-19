<template>
    <div class="grid grid-cols-2 max-w-4xl">
        <div class="grid col-span-1">
            <div class="max-w-lg">
                <div class="flex flex-col items-center bg-white rounded-t-md">
                    <form @submit.prevent="register" class="flex flex-col bg-white rounded w-full px-12">
                        <h1 class="font-bold text-4xl mb-2 pb-4">Sign up</h1>

                        <div class="mb-2">
                            <InputBasic :type="'name'" :label="'Name'" id="name" v-model="form.name" />
                            <div v-if="errors && errors.name" class="text-xs mb-2 text-red-600">
                                <span>{{ errors.name[0] }}</span>
                            </div>
                        </div>

                        <div class="mb-2">
                            <InputBasic :type="'email'" :label="'E-mail'" id="email" v-model="form.email" />
                            <div v-if="errors && errors.email" class="text-xs mb-2 text-red-600">
                                <span>{{ errors.email[0] }}</span>
                            </div>
                        </div>

                        <div class="mb-2">
                            <InputBasic :type="'password'" :label="'Password'" id="password" v-model="form.password" />
                            <div v-if="errors && errors.password" class="text-xs mb-2 text-red-600">
                                <span>{{ errors.password[0] }}</span>
                            </div>
                        </div>

                        <div class="mb-2">
                            <InputBasic :type="'password'" :label="'Confirm Password'" id="password_confirmation" v-model="form.password_confirmation" />
                        </div>

                        <div class="mb-2 mt-1">
                            <InputCheckbox name="gdpr" class="mb-3" :label="'I agree with GDPR'" />
                            <InputCheckbox name="terms"
                                :label="'By signing up you will create GroupeSEB account which you can use also on our other pormo websites: promo.tefal.cz, promo.rowenta.cz, promo.wmf.cz, promo.krups.cz.'" />
                        </div>

                        <ButtonBasic :type="'submit'" class="mt-3 mb-3">Sign up</ButtonBasic>
                    </form>
                </div>

                <div class="flex flex-col items-center py-4 text-gray-500 text-xs rounded-b-md w-full">
                    <Nuxt-Link :to="{ name: 'forgot-password' }" class="hover:text-gray-400 mb-2">Already have an account? Log in!</Nuxt-Link>
                </div>
            </div>
        </div>
        <div class="grid col-span-1">
            <div class="flex flex-col">
                <div class="flex justify-center pb-4 border-b mb-4">
                  <img src="~/assets/logo/groupe_logo_login.png" alt="groupe_seb_logo.png" class="object-none">
                </div>
                <div class="flex justify-center py-4">
                  <img src="~/assets/logo/tefal_logo.png" alt="groupe_seb_logo.png" class="object-none">
                </div>
                <div class="flex justify-center py-4">
                  <img src="~/assets/logo/rowenta_logo.png" alt="groupe_seb_logo.png" class="object-none">
                </div>
                <div class="flex justify-around py-4">
                  <img src="~/assets/logo/wmf_logo.png" alt="groupe_seb_logo.png" class="object-none">
                  <img src="~/assets/logo/krups_logo.png" alt="groupe_seb_logo.png" class="object-none">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    name: '',
                    email: '',
                    password: '',
                    password_confirmation: ''
                },
                errors: null
            }
        },
        methods: {
            async register() {
                try {
                    await this.$axios.get('sanctum/csrf-cookie')

                    await this.$axios.post('api/register', this.form)

                    await this.$auth.loginWith('laravelSanctum', {
                        data: {
                            email: this.form.email,
                            password: this.form.password
                        }
                    })

                } catch (error) {
                    if (error.response) {
                        this.errors = error.response.data.errors;
                    }
                }
            },
        }
    }
</script>

<style scoped>

</style>
