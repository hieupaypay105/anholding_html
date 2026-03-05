<template>
  <div id="RootLayout" class="block !p-6">
    <slot />
  </div>
</template>

<script>
export default {
  mounted() {
    window.onload = () => {
      inputTogglePassword()
      checkVerifyOTP()
      checkSidebar()
      // sidebarMobile()
    }
  },
}
</script>

<style></style>
