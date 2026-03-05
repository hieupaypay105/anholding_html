<template>
  <div class="!bg-white !rounded-[12px] !p-2.5">
    <!-- Your Data Grid container -->
    <div id="magicTable" style="height: 500px"></div>
  </div>
</template>

<script>
export default {
  mounted() {
    // Grid API: Access to Grid API methods
    let gridApi
    // Grid Options: Contains all of the Data Grid configurations
    const gridOptions = {
      localeText: {
        // Phân trang
        macan: 'Trang',
        more: 'Thêm',
        to: 'đến',
        of: 'của',
        next: 'Tiếp theo',
        last: 'Cuối',
        first: 'Đầu tiên',
        previous: 'Trước',

        // Tải dữ liệu
        loadingOoo: 'Đang tải dữ liệu...',

        // Bộ lọc header
        selectAll: 'Chọn tất cả',
        searchOoo: 'Tìm kiếm...',
        blanks: 'Trống',

        // Bộ lọc số
        equals: 'Bằng',
        notEqual: 'Không bằng',
        lessThan: 'Nhỏ hơn',
        greaterThan: 'Lớn hơn',
        lessThanOrEqual: 'Nhỏ hơn hoặc bằng',
        greaterThanOrEqual: 'Lớn hơn hoặc bằng',

        // Bộ lọc text
        contains: 'Chứa',
        notContains: 'Không chứa',
        startsWith: 'Bắt đầu với',
        endsWith: 'Kết thúc với',

        // Nhóm (Group Panel)
        group: 'Nhóm',
        columns: 'Cột',
        pivotMode: 'Chế độ Pivot',
        valueAggregation: 'Tổng hợp giá trị',
        pivotColumnGroupTotals: 'Tổng nhóm cột Pivot',
        groupColumn: 'Cột nhóm',

        // Các hàm tổng hợp
        aggFuncNone: 'Không',
        aggFuncSum: 'Tổng',
        aggFuncCount: 'Đếm',
        aggFuncAvg: 'Trung bình',
        aggFuncMin: 'Nhỏ nhất',
        aggFuncMax: 'Lớn nhất',
        aggFuncFirst: 'Đầu tiên',
        aggFuncLast: 'Cuối cùng',

        // Khi không có dữ liệu
        noRowsToShow: 'Không có dữ liệu',

        // Panel công cụ (Tool Panel)
        pinColumn: 'Ghim cột',
        valueColumns: 'Cột giá trị',
        autosizeThisColumn: 'Tự động điều chỉnh cột',
        autosizeAllColumns: 'Tự động điều chỉnh tất cả cột',
        chooseColumns: 'ádasda',
        groupBy: 'Nhóm theo',
        resetColumns: 'Thiết lập lại cột',
        expandAll: 'Mở rộng tất cả',
        collapseAll: 'Thu gọn tất cả',
        copy: 'Sao chép',
        copyWithHeaders: 'Sao chép có bao gồm tiêu đề',
        ctrlC: 'Ctrl+C',
        paste: 'Dán',

        // Row Group Panel
        macan: 'Kéo cột vào đây để nhóm',
      },
      // Row Data: The data to be displayed.
      rowData: [
        {
          stt: '01',
          phankhu: 'Michael Phelps',
          macan: 23,
          loaihinh: 'United States',
          tcbg: 2008,
          huong: 'Swimming',
          ktdat: 8,
          dtdat: 0,
          dtxd: 0,
          giafull: '16.234.556',
          tts: 8,
          thutucky: 'VBCN',
          quydt: 'Phú Thọ Land',
          giobank: 'VPB',
          dl: 'THP',
          dongia: '100',
          linkptg: 'https://www.microsoft.com/',
          linkimage: 'https://www.microsoft.com/',
          csbh: '17/01/2025',
          quatang: 'KCKTG',
          tinhtrangcoc: 'Đã ký cọc',
          uutien: 'Ưu tiên cao',
        },
        {
          stt: '01',
          phankhu: 'Michael Phelps',
          macan: 23,
          loaihinh: 'United States',
          tcbg: 2008,
          huong: 'Swimming',
          ktdat: 8,
          dtdat: 0,
          dtxd: 0,
          giafull: '16.234.556',
          tts: 8,
          thutucky: 'VBCN',
          quydt: 'Phú Thọ Land',
          giobank: 'VPB',
          dl: 'THP',
          dongia: '100',
          linkptg: 'https://www.microsoft.com/',
          linkimage: 'https://www.microsoft.com/',
          csbh: '17/01/2025',
          quatang: 'KCKTG',
          tinhtrangcoc: 'Đã ký cọc',
          uutien: 'Ưu tiên cao',
        },
        {
          stt: '01',
          phankhu: 'Michael Phelps',
          macan: 23,
          loaihinh: 'United States',
          tcbg: 2008,
          huong: 'Swimming',
          ktdat: 8,
          dtdat: 0,
          dtxd: 0,
          giafull: '16.234.556',
          tts: 8,
          thutucky: 'VBCN',
          quydt: 'Phú Thọ Land',
          giobank: 'VPB',
          dl: 'THP',
          dongia: '100',
          linkptg: 'https://www.microsoft.com/',
          linkimage: 'https://www.microsoft.com/',
          csbh: '17/01/2025',
          quatang: 'KCKTG',
          tinhtrangcoc: 'Đã ký cọc',
          uutien: 'Ưu tiên cao',
        },
      ],
      // Column Definitions: Defines the columns to be displayed.
      columnDefs: [
        {
          headerName: 'STT',
          field: 'stt',
          // pinned: 'left',
        },
        {
          headerName: 'Phân khu',
          field: 'phankhu',
          cellClass: colorCellClass,
        },
        {
          headerName: 'Mã căn',
          field: 'macan',
        },
        {
          headerName: 'Loại hình',
          field: 'loaihinh',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'TCBG',
          field: 'tcbg',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Hướng',
          field: 'huong',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'KT đất',
          field: 'ktdat',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'DT đất',
          field: 'dtxd',
        },
        {
          headerName: 'Giá full',
          field: 'giafull',
        },
        {
          headerName: 'TTS',
          field: 'tts',
        },
        {
          headerName: 'DTXD',
          field: 'dtdat',
        },
        {
          headerName: 'Thủ tục ký',
          field: 'thutucky',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Quỹ ĐT',
          field: 'quydt',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Giỏ bank F1',
          field: 'giobank',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'ĐL',
          field: 'dl',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Đơn giá',
          field: 'dongia',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Link PTG',
          field: 'linkptg',
          cellRenderer: CompanyRenderer,
        },
        {
          headerName: 'Hình ảnh đánh dấu',
          field: 'linkimage',
          cellRenderer: MaskImageRenderer,
        },
        {
          headerName: 'CSBH',
          field: 'csbh',
        },
        {
          headerName: 'Quà tặng',
          field: 'quatang',
        },
        {
          headerName: 'Tình trạng cọc',
          field: 'tinhtrangcoc',
        },
        {
          headerName: 'Ưu tiên',
          field: 'uutien',
          filter: 'agSetColumnFilter',
        },
        {
          headerName: 'Edit',
          field: 'actions',
          pinned: 'right',
          cellRenderer: actionCellRenderer,
        },
      ],
      onGridReady: (params) => {
        // optinal : params.api.autoSizeAllColumns(true)
        setTimeout(() => {
          params.api.sizeColumnsToFit()
          params.api.autoSizeAllColumns()
        }, 0)
      },
      defaultColDef: {
        flex: screen.width < 1280 ? 'auto' : null,
        editable: true,
        // resizable: true,
        // maxWidth: 120,
        minWidth: screen.width < 1280 ? 120 : null,
      },
      editType: 'fullRow',
    }

    function actionCellRenderer(params) {
      // Tạo container
      const container = document.createElement('div')
      container.style.display = 'flex'
      container.style.gap = '4px'

      // Nút Edit
      const editBtn = document.createElement('button')
      editBtn.innerHTML = '<img src="images/asset/svg-edit.svg" alt="">'
      editBtn.classList.add('edit-btn')
      editBtn.addEventListener('click', () => {
        // Bắt đầu chỉnh sửa inline cột "athlete" (hoặc cột khác) của row
        params.api.startEditingCell({
          rowIndex: params.node.rowIndex,
          colKey: 'phankhu',
        })
      })

      // Nút Delete
      const deleteBtn = document.createElement('button')
      deleteBtn.innerHTML = '<img src="images/asset/svg-delete.svg" alt="">'
      deleteBtn.classList.add('delete-btn')
      deleteBtn.addEventListener('click', () => {
        // Xóa dòng khỏi dữ liệu
        // applyTransaction({ remove: [...] }) sẽ xóa row khỏi grid
        params.api.applyTransaction({ remove: [params.node.data] })
      })

      container.appendChild(editBtn)
      container.appendChild(deleteBtn)

      return container
    }

    // func render link single user
    function CompanyRenderer(params) {
      const linkptg = `<a href="${params.value}" target="_blank">Link</a>`
      return linkptg
    }

    function MaskImageRenderer(params) {
      const linkimage = `<a href="${params.value}" target="_blank">Link</a>`
      return linkimage
    }

    // func check color name single user
    var colorClasses = [
      'rag-green',
      'rag-blue',
      'rag-red',
      'rag-yellow',
      'rag-purple',
    ]
    var nameColorMap = {}
    var colorIndex = 0
    function colorCellClass(params) {
      let val = params.value
      if (!val) return null // nếu ô trống, không tô màu

      // Nếu chưa có tên này trong map, gán màu mới
      if (!nameColorMap[val]) {
        // Lấy màu theo chỉ số colorIndex, sau đó tăng lên
        nameColorMap[val] = colorClasses[colorIndex % colorClasses.length]
        colorIndex++
      }
      // Trả về class màu đã gán
      return nameColorMap[val]
    }

    // Your Javascript code to create the Data Grid
    const myGridElement = document.querySelector('#magicTable')
    agGrid.createGrid(myGridElement, gridOptions)
  },
}
</script>
