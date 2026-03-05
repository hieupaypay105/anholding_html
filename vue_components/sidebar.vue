<template>
  <div
    id="Sidebar"
    class="fixed xl:top-6 xl:left-6 max-xl:top-0 max-xl:left-0 z-50 max-w-[240px] h-full xl:h-[calc(100%-48px)] z-[101]"
  >
    <div
      id="sidebarTranslate"
      class="flex flex-col xl:rounded-[84px] overflow-hidden bg-white h-full"
    >
      <div class="absolute xl:hidden top-4 right-4">
        <button type="button" id="btnSidebar-mb">
          <svg
            width="15"
            height="15"
            viewBox="0 0 15 15"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M7.5 9.09696L1.91065 14.6863C1.70152 14.8954 1.43536 15 1.11217 15C0.788973 15 0.522813 14.8954 0.313688 14.6863C0.104562 14.4772 0 14.211 0 13.8878C0 13.5646 0.104562 13.2985 0.313688 13.0894L5.90304 7.5L0.313688 1.91065C0.104562 1.70152 0 1.43536 0 1.11217C0 0.788973 0.104562 0.522813 0.313688 0.313688C0.522813 0.104562 0.788973 0 1.11217 0C1.43536 0 1.70152 0.104562 1.91065 0.313688L7.5 5.90304L13.0894 0.313688C13.2985 0.104562 13.5646 0 13.8878 0C14.211 0 14.4772 0.104562 14.6863 0.313688C14.8954 0.522813 15 0.788973 15 1.11217C15 1.43536 14.8954 1.70152 14.6863 1.91065L9.09696 7.5L14.6863 13.0894C14.8954 13.2985 15 13.5646 15 13.8878C15 14.211 14.8954 14.4772 14.6863 14.6863C14.4772 14.8954 14.211 15 13.8878 15C13.5646 15 13.2985 14.8954 13.0894 14.6863L7.5 9.09696Z"
              fill="#464661"
            />
          </svg>
        </button>
      </div>

      <div class="p-[10px_15px_5px]">
        <div class="w-full h-auto max-w-full">
          <a href="" title="">
            <img
              class="object-scale-down w-full h-full"
              src="images/asset/logo.png"
              alt=""
            />
          </a>
        </div>
      </div>

      <div
        class="overflow-bar-custom flex flex-col h-full overflow-auto bg-cover bg-center bg-no-repeat xl:rounded-[12px] p-[70px_0_70px_10px]"
        style="background-image: url('./images/asset/bg-sidebar.png')"
      >
        <div class="flex flex-col h-full gap-1">
          <!-- overflow-scroll h-full -->
          <div id="sidebarList" class="flex flex-col gap-1 pb-10 sidebar-list">
            <div class="child" v-for="(item, id) in menuData" :key="id">
              <div class="relative item">
                <a
                  href=""
                  title=""
                  :class="{ active: id === 0 }"
                  class="link flex items-center !gap-2"
                >
                  <div class="icon !p-2">
                    <img
                      :src="item.icon"
                      alt=""
                      class="object-scale-down w-6 h-6"
                    />
                  </div>

                  <div class="text grow !text-[16px] font-bold leading-normal">
                    {{ item.title }}
                  </div>
                </a>

                <button
                  type="button"
                  class="onToggleDropdown inline-flex items-center justify-center w-[24px] h-[24px] text-center absolute right-0 top-1/2 -translate-y-[50%] z-10"
                  v-if="item.sub"
                >
                  <svg
                    width="8"
                    height="6"
                    viewBox="0 0 8 6"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M0.963998 1.16401C1.04757 1.0804 1.1468 1.01408 1.25601 0.968836C1.36523 0.923588 1.48228 0.900299 1.6005 0.900299C1.71871 0.900299 1.83577 0.923588 1.94498 0.968836C2.05419 1.01408 2.15342 1.0804 2.237 1.16401L4 2.92701L5.764 1.16401C5.93388 1.00112 6.16081 0.911265 6.39616 0.913693C6.6315 0.916122 6.85653 1.01064 7.02302 1.177C7.1895 1.34336 7.2842 1.56831 7.28681 1.80365C7.28943 2.03899 7.19975 2.26599 7.037 2.43601L4.637 4.83601C4.55342 4.91961 4.45419 4.98593 4.34498 5.03118C4.23577 5.07643 4.11871 5.09971 4.0005 5.09971C3.88228 5.09971 3.76523 5.07643 3.65602 5.03118C3.5468 4.98593 3.44758 4.91961 3.364 4.83601L0.963998 2.43601C0.795457 2.26726 0.70079 2.03851 0.70079 1.80001C0.70079 1.56151 0.795457 1.33276 0.963998 1.16401Z"
                      fill="white"
                    />
                  </svg>
                </button>
              </div>

              <div class="sub" style="display: none" v-if="item.sub">
                <div class="item-sub" v-for="(sub, id) in item.sub" :key="id">
                  <a
                    href=""
                    title=""
                    class="leading-normal link-sub"
                    :class="{ active: id === 0 }"
                  >
                    {{ sub }}
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const menuData = reactive([
  {
    icon: 'images/asset/akar-icons_dashboard.svg',
    title: 'Dashboard',
    // sub: ['Vinhomes Ocean Park 2', 'Vinhomes Ocean Park 3'],
  },
  {
    icon: 'images/asset/fluent_table-multiple-20-filled.svg',
    title: 'Bảng hàng',
    sub: ['Vinhomes Ocean Park 2', 'Vinhomes Ocean Park 3'],
  },
  {
    icon: 'images/asset/ix_customer.svg',
    title: 'Khách hàng',
    sub: ['Vinhomes Ocean Park 2', 'Vinhomes Ocean Park 3'],
    // sub: ['Vinhomes Ocean Park 2', 'Vinhomes Ocean Park 3'],
  },
  {
    icon: 'images/asset/dashicons_admin-generic.svg',
    title: 'Quản trị',
    // sub: ['Vinhomes Ocean Park 2', 'Vinhomes Ocean Park 3'],
  },
])
</script>

<script>
export default {
  mounted() {
    window.addEventListener('load', () => {
      inputTogglePassword()
      checkVerifyOTP()
      // sidebarMobile()
      checkSidebar()
      // toggleMenuDropdown()
    })
  },
}
</script>

<style></style>
