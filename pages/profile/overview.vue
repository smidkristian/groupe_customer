<template>
  <div class="w-full">
    <PageTitle>Kristán Šmíd</PageTitle>
    <CardComponent>
      <template #body>
        <div class="grid grid-cols-2">
          <div>
            email: smid.kristian@gmail.com
          </div>
          <div>
            phone: +420 603 739 749
          </div>
        </div>
      </template>
    </CardComponent>
    <CardComponent style="padding: 0!important;">
      <template #head>
        <CardHeadTwo class="p-4">My leads</CardHeadTwo>
      </template>
      <template #body>
        <TableComponent :tableData="leads" :tableHeaders="ths" />
      </template>
    </CardComponent>
    <CardComponent>
      <template #body>
        <div class="flex justify-around py-2">
          <img src="~/assets/logo/rowenta_logo_smaller.png" alt="groupe_seb_logo.png" class="object-none">
          <img src="~/assets/logo/tefal_logo_smaller.png" alt="groupe_seb_logo.png" class="object-none">
          <img src="~/assets/logo/wmf_logo_smaller.png" alt="groupe_seb_logo.png" class="object-none">
          <img src="~/assets/logo/krups_logo_smaller.png" alt="groupe_seb_logo.png" class="object-none">
        </div>
      </template>
    </CardComponent>
  </div>
</template>

<script>
	export default {
    layout: 'profile',

    data() {
        return {
            ths: [ 'Date','Brand', 'Promoevent' ]
        }
    },

    async asyncData({ $axios }) {
        const getLeads = await $axios.get('/api/customer-leads');
        let leads = getLeads.data;
        return { leads }
    }

	}
</script>

<style scoped>

</style>
