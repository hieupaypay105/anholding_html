<template>
  <div id="userDropdown" class="relative mb-5">
    <div class="flex flex-wrap items-center gap-2">
      <button type="button" id="btnSidebar">
        <img src="images/asset/material-symbols_menu-rounded.png" alt="" />
      </button>

      <!-- thay 3F8CFE => 363636 nếu là trường hợp text đen -->
      <h2 class="!text-[#3F8CFE] !text-[16px] !font-bold !uppercase !m-0 !ms-4">
        vinhomes ocean park 2
      </h2>

      <div class="inline-flex items-center gap-6 ms-auto">
        <button
          type="button"
          id="tippyUserDropdown"
          class="inline-flex !gap-2 items-center bg-white !rounded-[8px] p-1"
        >
          <img
            class="w-[30px] h-[30px] rounded-[8px] border border-solid border-[#f4f9fd] object-cover flex-shrink-0"
            src="images/asset/sm-ava.png"
            alt=""
          />
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
          >
            <path
              d="M16 10L12 14L8 10H16Z"
              fill="#3F8CFE"
              stroke="#3F8CFE"
              stroke-width="2"
              stroke-linejoin="round"
            />
          </svg>
        </button>

        <div id="tippyHTMLUser" style="display: none">
          <div class="tippy-user-list">
            <a href="" title=""> Thông tin cá nhân </a>
            <a href="" title=""> Thoát </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const template = document.getElementById('tippyHTMLUser')

    tippy('#tippyUserDropdown', {
      content: template.innerHTML,
      trigger: 'click',
      hideOnClick: true,
      interactive: true,
      theme: 'light',
      allowHTML: true,
    })
  },
}
</script>
