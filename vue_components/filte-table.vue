<template>
  <div class="bg-white rounded-[12px] p-2.5">
    <div class="rounded-[8px] bg-[#F4F9FD] py-2.5 px-2">
      <div class="text-end">
        <button id="collapseFilter" class="relative z-10 cursor-pointer">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
          >
            <path
              d="M4 18C3.71667 18 3.47934 17.904 3.288 17.712C3.09667 17.52 3.00067 17.2827 3 17C2.99934 16.7173 3.09534 16.48 3.288 16.288C3.48067 16.096 3.718 16 4 16H20C20.2833 16 20.521 16.096 20.713 16.288C20.905 16.48 21.0007 16.7173 21 17C20.9993 17.2827 20.9033 17.5203 20.712 17.713C20.5207 17.9057 20.2833 18.0013 20 18H4ZM4 13C3.71667 13 3.47934 12.904 3.288 12.712C3.09667 12.52 3.00067 12.2827 3 12C2.99934 11.7173 3.09534 11.48 3.288 11.288C3.48067 11.096 3.718 11 4 11H20C20.2833 11 20.521 11.096 20.713 11.288C20.905 11.48 21.0007 11.7173 21 12C20.9993 12.2827 20.9033 12.5203 20.712 12.713C20.5207 12.9057 20.2833 13.0013 20 13H4ZM4 8C3.71667 8 3.47934 7.904 3.288 7.712C3.09667 7.52 3.00067 7.28267 3 7C2.99934 6.71733 3.09534 6.48 3.288 6.288C3.48067 6.096 3.718 6 4 6H20C20.2833 6 20.521 6.096 20.713 6.288C20.905 6.48 21.0007 6.71733 21 7C20.9993 7.28267 20.9033 7.52033 20.712 7.713C20.5207 7.90567 20.2833 8.00133 20 8H4Z"
              fill="#363636"
            />
          </svg>
        </button>
      </div>

      <div id="toggleCollapseFilter">
        <div class="grid grid-cols-12 gap-2.5">
          <div class="col-span-12 xl:col-span-3 md:col-span-6">
            <div class="group-filter">
              <div class="group-input">
                <span>Phân khu/Block</span>
                <select
                  id="phankhu"
                  data-attr="Phân khu/Block"
                  class="block-selector"
                  multiple="multiple"
                >
                  <option value="all">Tất cả</option>
                  <option value="thoi-dai">Thời Đại</option>
                  <option value="pho-bien">Phố Biển</option>
                  <option value="hai-au">Hải Âu</option>
                  <option value="sao-bien">Sao Biển</option>
                  <option value="ngoc-trai">Ngọc Trai</option>
                </select>
              </div>
            </div>
          </div>

          <div class="col-span-12 xl:col-span-3 md:col-span-6">
            <div class="group-filter">
              <div class="group-input">
                <span>Mã căn</span>

                <div class="macan-input-searchbox">
                  <input
                    type="text"
                    name=""
                    id="macanSearchbox"
                    placeholder="Nhập từ khóa"
                  />
                  <label for="macanSearchbox">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="24"
                      height="24"
                      viewBox="0 0 24 24"
                      fill="none"
                    >
                      <path
                        d="M11.2222 17.4444C14.6587 17.4444 17.4444 14.6587 17.4444 11.2222C17.4444 7.78578 14.6587 5 11.2222 5C7.78578 5 5 7.78578 5 11.2222C5 14.6587 7.78578 17.4444 11.2222 17.4444Z"
                        stroke="#909090"
                        stroke-width="2"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                      />
                      <path
                        d="M19 19L15.6555 15.6555"
                        stroke="#909090"
                        stroke-width="2"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                      />
                    </svg>
                  </label>
                </div>
              </div>
            </div>
          </div>

          <div class="col-span-12 xl:col-span-3 md:col-span-6">
            <div class="group-filter">
              <div class="group-input">
                <span>Loại hình sản phẩm</span>
                <select
                  id="loaihinhsp"
                  class="block-selector"
                  multiple="multiple"
                  data-attr="Chọn loại hình"
                >
                  <option value="all">Tất cả</option>
                  <option value="thoi-dai">Thời Đại</option>
                  <option value="pho-bien">Phố Biển</option>
                  <option value="hai-au">Hải Âu</option>
                  <option value="sao-bien">Sao Biển</option>
                  <option value="ngoc-trai">Ngọc Trai</option>
                </select>
              </div>
            </div>
          </div>

          <div class="col-span-12 xl:col-span-3 md:col-span-6">
            <div class="group-filter">
              <div class="group-input">
                <span>Hướng</span>
                <select
                  id="huongnha"
                  class="block-selector"
                  multiple="multiple"
                  data-attr="Chọn hướng nhà"
                >
                  <option value="all">Tất cả</option>
                  <option value="thoi-dai">Thời Đại</option>
                  <option value="pho-bien">Phố Biển</option>
                  <option value="hai-au">Hải Âu</option>
                  <option value="sao-bien">Sao Biển</option>
                  <option value="ngoc-trai">Ngọc Trai</option>
                </select>
              </div>
            </div>
          </div>

          <div
            class="col-span-12 onOptinal xl:col-span-3 md:col-span-6"
            style="display: none"
          >
            <div class="group-filter">
              <div class="group-input">
                <span>Tiêu chuẩn bàn giao</span>
                <select
                  id="tieuchuan"
                  class="block-selector"
                  multiple="multiple"
                  data-attr="Chọn tiêu chuẩn bàn giao"
                >
                  <option value="all">Tất cả</option>
                  <option value="thoi-dai">Thời Đại</option>
                  <option value="pho-bien">Phố Biển</option>
                  <option value="hai-au">Hải Âu</option>
                  <option value="sao-bien">Sao Biển</option>
                  <option value="ngoc-trai">Ngọc Trai</option>
                </select>
              </div>
            </div>
          </div>

          <div
            class="col-span-12 onOptinal xl:col-span-3 md:col-span-6"
            style="display: none"
          >
            <div class="group-filter">
              <div class="group-input">
                <span>Khoảng giá Full (tỷ)</span>

                <div class="dropdown dropdown-range">
                  <button
                    type="button"
                    class="dropdown-toggle inline-flex !gap-2 items-center bg-white !rounded-[8px] p-1"
                    data-bs-toggle="dropdown"
                  >
                    Khoảng giá
                  </button>

                  <ul class="dropdown-menu">
                    <li>
                      <div class="dropdown-item">
                        <div class="p-[8px_24px]">
                          <h3
                            class="!text-[#363636] !text-[12px] !font-normal leading-normal !mb-3"
                          >
                            Mức giá
                          </h3>
                          <!-- Thanh trượt (range slider) -->
                          <div
                            id="priceSlider"
                            class="slider-container !mb-5"
                          ></div>

                          <h3
                            class="!text-[#363636] !text-[12px] !font-normal leading-normal !mb-2"
                          >
                            Hoặc nhập khoảng (Đơn vị VNĐ)
                          </h3>

                          <div class="range-inputs-container">
                            <div class="item">
                              <label for="minPrice">Giá từ</label>
                              <input type="number" id="minPrice" />
                            </div>

                            <div class="item">
                              <label for="maxPrice">Giá đến</label>
                              <input type="number" id="maxPrice" />
                            </div>
                          </div>
                        </div>

                        <div
                          class="flex flex-wrap items-stretch justify-center bg-[#F5F5F5] rounded-[4px] p-[12px_24px] !gap-2"
                        >
                          <!-- Nút Đặt lại & Áp dụng -->
                          <button
                            id="resetButton"
                            class="flex-[0_0_calc(50%-4px)] text-[#363636] !text-[12px] font-bold !rounded-[8px] border border-solid border-[#ddd] bg-white !p-2 transition hover:shadow-[inset_0_200px_0_#0000002d]"
                          >
                            Đặt lại
                          </button>
                          <button
                            id="applyButton"
                            class="flex-[0_0_calc(50%-4px)] text-white !text-[12px] font-bold !rounded-[8px] !bg-[#3F8CFE] border border-solid border-[#3F8CFE] !p-2 transition hover:shadow-[inset_0_200px_0_#0000002d]"
                          >
                            Áp dụng
                          </button>
                        </div>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <div
            class="col-span-12 onOptinal xl:col-span-3 md:col-span-6"
            style="display: none"
          >
            <div class="group-filter">
              <div class="group-input">
                <span>Khoảng diện tích đất (m2)</span>
                <select
                  id="khoangdt"
                  class="block-selector"
                  multiple="multiple"
                  data-attr="Khoảng diện tích"
                >
                  <option value="all">Tất cả</option>
                  <option value="thoi-dai">Thời Đại</option>
                  <option value="pho-bien">Phố Biển</option>
                  <option value="hai-au">Hải Âu</option>
                  <option value="sao-bien">Sao Biển</option>
                  <option value="ngoc-trai">Ngọc Trai</option>
                </select>
              </div>
            </div>
          </div>

          <div
            class="col-span-12 onOptinal xl:col-span-3 md:col-span-6"
            style="display: none"
          >
            <div class="group-filter">
              <div class="group-input">
                <span>Giá TTS tạm tính</span>

                <div class="dropdown">
                  <button
                    type="button"
                    class="dropdown-toggle inline-flex !gap-2 items-center bg-white !rounded-[8px] p-1"
                    data-bs-toggle="dropdown"
                  >
                    Khoảng giá
                  </button>

                  <ul class="dropdown-menu">
                    <li class="!mb-4">
                      <div class="dropdown-item">
                        <div class="filter-group">
                          <label class="filter-label">Đơn giá m2/ đất</label>
                          <select id="price-sort" class="filter-select">
                            <option value="asc" selected>
                              Giá từ thấp tới cao
                            </option>
                            <option value="desc">Giá từ cao tới thấp</option>
                          </select>
                        </div>
                      </div>
                    </li>

                    <li>
                      <div class="dropdown-item">
                        <div class="filter-group">
                          <label class="filter-label">Mức độ ưu tiên</label>
                          <select id="priority-sort" class="filter-select">
                            <option value="high" selected>Ưu tiên cao</option>
                            <option value="medium">Ưu tiên trung bình</option>
                            <option value="low">Ưu tiên thấp</option>
                          </select>
                        </div>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    $(document).ready(function () {
      inputTogglePassword()
      checkVerifyOTP()
      checkSidebar()
      // sidebarMobile()
      initFieldSelect2()
      initPriceSame()
      priceRangeSlider()
      collapseFilter()
    })

    // init range slider
    function priceRangeSlider() {
      // Thiết lập giá trị mặc định
      var minDefault = 0
      var maxDefault = 300000000 // 300 triệu, bạn có thể đổi thành 3000000000 (3 tỉ), ...

      // Khởi tạo Slider
      $('#priceSlider').slider({
        range: true,
        min: 0,
        max: 300000000, // Giới hạn tối đa
        step: 500000, // Bước nhảy, ví dụ: 500k
        values: [minDefault, maxDefault],
        slide: function (event, ui) {
          // Cập nhật hai ô input khi kéo slider
          $('#minPrice').val(ui.values[0])
          $('#maxPrice').val(ui.values[1])
        },
      })

      // Gán giá trị ban đầu cho ô nhập
      $('#minPrice').val($('#priceSlider').slider('values', 0))
      $('#maxPrice').val($('#priceSlider').slider('values', 1))

      // Khi người dùng thay đổi giá trị trong ô input
      $('#minPrice, #maxPrice').on('change', function () {
        var minVal = parseInt($('#minPrice').val(), 10)
        var maxVal = parseInt($('#maxPrice').val(), 10)

        // Kiểm tra nếu người dùng nhập sai, đặt về mặc định
        if (isNaN(minVal)) minVal = 0
        if (isNaN(maxVal)) maxVal = 300000000

        // Ràng buộc minVal không nhỏ hơn 0, maxVal không lớn hơn 300 triệu
        if (minVal < 0) minVal = 0
        if (maxVal > 300000000) maxVal = 300000000

        // Nếu minVal lớn hơn maxVal thì hoán đổi
        if (minVal > maxVal) {
          var temp = maxVal
          maxVal = minVal
          minVal = temp
        }

        // Cập nhật slider
        $('#priceSlider').slider('values', [minVal, maxVal])
      })

      // Nút Đặt lại
      $('#resetButton').click(function () {
        $('#priceSlider').slider('values', [minDefault, maxDefault])
        $('#minPrice').val(minDefault)
        $('#maxPrice').val(maxDefault)
      })

      // Nút Áp dụng
      $('#applyButton').click(function () {
        var minVal = $('#priceSlider').slider('values', 0)
        var maxVal = $('#priceSlider').slider('values', 1)
        alert(
          'Giá từ: ' +
            minVal.toLocaleString() +
            ' VND\nGiá đến: ' +
            maxVal.toLocaleString() +
            ' VND',
        )
      })
    }

    // init select2 khoang gia
    function initPriceSame() {
      // Initialize Select2 on all filter selects
      $('.filter-select').select2({
        minimumResultsForSearch: Infinity, // Hide the search box
        width: '100%',
      })

      // Handle the Khoảng giá dropdown toggle
      $('#price-range-toggle').click(function () {
        // This would typically show a custom dropdown or dialog
        // For demonstration, we'll just log a message
        console.log('Price range dropdown clicked')
        // Here you would normally toggle a custom dropdown component
        // You could add your own code to show a price range selector
      })

      // Handle changes for price sorting
      $('#price-sort').on('change', function () {
        console.log('Price sort changed to:', $(this).val())
        // Add your sorting logic here
      })

      // Handle changes for priority
      $('#priority-sort').on('change', function () {
        console.log('Priority sort changed to:', $(this).val())
        // Add your priority filtering logic here
      })

      $('.group-input .dropdown-item').click(function (e) {
        e.stopPropagation() // Ngừng sự kiện click
      })

      $('.block-selector').each(function (id, el) {
        const name = $(el).attr('id')
        const dataAttr = $(el).data('attr')

        // When "Tất cả" is selected, select all options
        $('#' + name + '.block-selector').on('select2:select', function (e) {
          if (e.params.data.id === 'all') {
            $('#' + name + '.block-selector option').prop('selected', true)
            $('#' + name + '.block-selector').trigger('change')
          }
        })

        // When "Tất cả" is unselected, unselect all options
        $('#' + name + '.block-selector').on('select2:unselect', function (e) {
          if (e.params.data.id === 'all') {
            $('#' + name + '.block-selector option').prop('selected', false)
            $('#' + name + '.block-selector').trigger('change')
          }
        })
      })

      // Update checkboxes when dropdown opens
      $('#block-selector').on('select2:open', function () {
        setTimeout(function () {
          updateCheckboxes()
        }, 0)
      })
    }

    // init select2
    function initFieldSelect2() {
      $('.block-selector.filter').select2({
        placeholder: 'Chọn khoảng giá',
        minimumResultsForSearch: Infinity,
        allowClear: true,
      })

      $('.block-selector').each(function (id, el) {
        const name = $(el).attr('id')
        const dataAttr = $(el).data('attr')

        // Initialize Select2
        $('#' + name + '.block-selector').select2({
          placeholder: dataAttr,
          minimumResultsForSearch: Infinity,
          closeOnSelect: false,
          // allowClear: true,
          templateResult: formatOption,
          templateSelection: formatSelection,
        })
      })
    }

    // Format each option to include a checkbox
    function formatOption(option) {
      if (!option.id) {
        return option.text
      }

      // Check if this option is selected
      var isSelected = $(option.element).prop('selected')
      var selectedClass = isSelected ? 'option-selected' : ''

      var $option = $(
        '<div class="checkbox-container ' +
          selectedClass +
          '">' +
          '<span class="checkbox"></span>' +
          '<span>' +
          option.text +
          '</span>' +
          '</div>',
      )

      return $option
    }

    // Format the selected options
    function formatSelection(option) {
      return option.text
    }

    // Update checkboxes to reflect current selection state
    function updateCheckboxes() {
      var selectedValues = $('.block-selector').val() || []

      $('.select2-results__option').each(function () {
        var optionId = $(this).data('select2-id')
        if (optionId) {
          // Extract the actual value from the select2-id
          var value = optionId.replace('block-selector-', '')

          if (selectedValues.includes(value)) {
            $(this).find('.checkbox-container').addClass('option-selected')
          } else {
            $(this).find('.checkbox-container').removeClass('option-selected')
          }
        }
      })
    }
  },
}
</script>
