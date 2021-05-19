<template>
  <div class="w-60 mr-10">
    <ul class="w-52 flex flex-col shadow p-2 bg-white rounded">
      <SideNavLink :href="{ name: 'profile-overview' }" :active="$route.name == 'profile-overview'">
        <IconHome />Overview
      </SideNavLink>

      <SideNavLink :href="{ name: 'profile-account-settings' }" :active="$route.name == 'profile-account-settings'">
          <IconSettings />Account settings
      </SideNavLink>

      <div class="border-t">
        <SideNavLinkBottom :href="{ name: 'logout' }" :active="$route.name == 'logout'">
          <IconLogout />Logout
      </SideNavLinkBottom>
      </div>
    </ul>
  </div>
</template>
