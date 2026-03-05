# AGENTS.md - An Holdings CRM Project Guide

## Project Overview

**Dự án**: Hệ thống CRM (Customer Relationship Management) cho **An Holdings** - một tập đoàn bất động sản Việt Nam.

**Mục đích**: Quản lý bán hàng bất động sản, theo dõi khách hàng, quản lý bảng hàng (sản phẩm căn hộ/nhà), và quản trị nhân viên.

**Trạng thái**: Static HTML prototype / UI template - chưa có backend integration. Dữ liệu hardcoded, form actions rỗng, một số component chưa hoàn thiện.

**Ngôn ngữ giao diện**: Tiếng Việt (labels, menu, content đều bằng tiếng Việt).

**Domain context**: Các dự án bất động sản tham chiếu bao gồm Vinhomes Ocean Park 2, Vinhomes Ocean Park 3. Đơn vị tiền tệ: VND.

---

## Tech Stack

| Category | Technology | Chi tiết |
|---|---|---|
| **CSS Framework** | Tailwind CSS 4 (Play CDN) | Runtime JIT via `tailwind.min.js`. Utility classes dùng inline. Arbitrary values phổ biến: `!text-[#3F8CFE]`, `!rounded-[8px]` |
| **CSS Framework** | Bootstrap 5 (selective) | Chỉ import: grid, reboot, utilities, modal, dropdown, tooltip, transitions qua SCSS |
| **CSS Preprocessor** | SCSS/Sass | Compiled thành `css/style.min.css`. Dùng mixins, variables, `@for` loops |
| **JS Framework** | Vue 3 (CDN) | `Vue.createApp({...}).mount('#app')`. Global build `vue.global.js` |
| **SFC Loader** | vue3-sfc-loader | Load `.vue` files runtime không cần build step |
| **DOM Library** | jQuery 3.7.1 | Select2, DOM manipulation, jQuery UI interactions |
| **UI Components** | jQuery UI 1.13.2 | Range sliders (price filter), loaded từ CDN |
| **Tooltips** | Tippy.js + Popper.js | User dropdown tooltips |
| **Dropdowns** | Select2 | Enhanced multi-select với checkboxes |
| **Image Cropping** | Croppie | Profile photo cropping trong modal |
| **File Upload** | Dropzone.js | Drag-and-drop file import (Excel) |
| **Carousel** | Swiper | Loaded trên tất cả pages |
| **Icons** | Font Awesome + inline SVGs | Hỗn hợp FA library và embedded SVG icons |
| **Fonts** | Inter (primary), Playfair Display, Italianno, IBM Plex Serif | Inter qua Google Fonts CDN; còn lại self-hosted |
| **Formatting** | Prettier | 2-space indent, no semicolons, single quotes, trailing commas |

---

## Directory Structure

```
anholding_html/
├── css/                           # CSS đã compiled
│   ├── style.css                  # Compiled từ SCSS (unminified)
│   ├── style.css.map              # Source map
│   ├── style.min.css              # Minified production CSS (FILE CHÍNH được load)
│   ├── style.min.css.map          # Source map
│   └── tailwind-base.css          # Tailwind theme override (chỉ --color-primary)
│
├── scss/                          # SCSS source files
│   ├── style.scss                 # <- ENTRY POINT - import tất cả partials
│   ├── _body.scss                 # Base body styles, loader, global classes
│   ├── _fonts.scss                # @font-face declarations (Inter)
│   ├── _reset.scss                # Normalize.css + custom reset (~789 dòng)
│   ├── _variables.scss            # SCSS mixins + utility class generators
│   ├── bootstrap/                 # Cherry-picked Bootstrap SCSS modules
│   ├── components/                # Component-scoped SCSS
│   │   ├── _header.scss           # Empty
│   │   ├── _footer.scss           # Footer styles
│   │   ├── _sidebar.scss          # Sidebar navigation (154 dòng)
│   │   ├── _user-switch.scss      # User dropdown
│   │   ├── _filter-table.scss     # Filter/Select2 styles
│   │   └── _table.scss            # Custom data table styles (543 dòng)
│   └── pages/                     # Page-specific SCSS
│       ├── _index.scss            # Login, OTP, breadcrumbs, forms
│       └── _khachhang-v2.scss     # Customer list v2 page
│
├── js/                            # JavaScript files
│   ├── main.js                    # Custom app logic (718 dòng) <- FILE JS CHÍNH
│   ├── vue.global.js              # Vue 3 runtime
│   ├── vue3-sfc-loader.js         # SFC loader cho .vue files
│   ├── vuedefineasync.js          # Config cho vue3-sfc-loader
│   ├── tailwind.min.js            # Tailwind CSS Play CDN runtime
│   ├── tippy.umd.min.js           # Tippy.js tooltips
│   ├── popper.min.js              # Popper.js positioning
│   ├── select2.min.js             # Select2 dropdowns
│   ├── croppie.min.js             # Image cropper
│   ├── dropzone.min.js            # File upload
│   ├── select2.min.css            # Select2 CSS
│   ├── croppie.min.css            # Croppie CSS
│   └── dropzone.min.css           # Dropzone CSS
│
├── vue_components/                # Vue 3 Single File Components
│   ├── header.vue                 # Empty placeholder
│   ├── footer.vue                 # Empty placeholder
│   ├── sidebar.vue                # Sidebar navigation (149 dòng, data-driven)
│   ├── root-layout.vue            # Root layout wrapper với <slot>
│   ├── user-switch.vue            # User profile dropdown
│   ├── filte-table.vue            # Filter table component
│   └── table-magic.vue            # Data table component
│
├── libs/                          # Third-party libraries (vendored)
│   ├── bootstrap/                 # Bootstrap 5 JS bundle
│   ├── jquery/                    # jQuery 3.7.1 + 3.4.1
│   ├── swiper/                    # Swiper carousel
│   ├── fancybox/                  # Fancybox lightbox
│   ├── flatpickr/                 # Date picker (Vietnamese locale)
│   ├── lightgallery/              # Light Gallery media viewer
│   ├── countup/                   # Count-up animation
│   ├── menu/                      # jQuery mobile menu
│   ├── zoom/                      # Image zoom
│   ├── touch-image-comparison-slider/
│   └── youtube-background-master/
│
├── fonts/                         # Self-hosted fonts
│   ├── fontawesome/               # Font Awesome icons
│   ├── italianno/                 # Italianno decorative font
│   ├── playfair/                  # Playfair Display serif
│   └── plexserif/                 # IBM Plex Serif
│
├── images/
│   └── asset/                     # UI assets (29 files)
│       ├── logo.png               # An Holdings logo
│       ├── bg-login.jpg           # Login background
│       ├── bg-sidebar.png         # Sidebar background
│       ├── *.svg                  # UI icons (edit, delete, filter, search...)
│       └── *.png                  # Avatars, camera icon, menu icon
│
└── *.html                         # 10 HTML pages (xem Pages Map bên dưới)
```

---

## Pages Map

| File | Mục đích | Layout |
|---|---|---|
| `index.html` | Landing/home page (main content rỗng) | Public page với header + footer Vue components |
| `login.html` | Đăng nhập (username + password) | Auth page (fullscreen bg, glassmorphism card) |
| `quen-mat-khau.html` | Quên mật khẩu - nhập email | Auth page |
| `get-otp.html` | Xác thực OTP - nhập 6 số | Auth page |
| `dat-mat-khau.html` | Đặt mật khẩu mới | Auth page |
| `dashboard.html` | Hồ sơ người dùng / cài đặt tài khoản, crop avatar | Dashboard (sidebar + main) |
| `banghang.html` | Bảng hàng - danh sách sản phẩm BĐS, filters, import/export | Dashboard (~1200 dòng, phức tạp nhất) |
| `khachhang.html` | Khách hàng v1 - bảng dữ liệu, modal thêm KH | Dashboard |
| `khachhang-v2.html` | Khách hàng v2 - status chips, accordion detail, chat/notes | Dashboard (phiên bản nâng cấp) |
| `quantri.html` | Quản trị - quản lý user, phân quyền | Dashboard |

### Auth Flow: login.html -> quen-mat-khau.html -> get-otp.html -> dat-mat-khau.html

### Dashboard Pages đều có layout: Sidebar trái + Main content phải

---

## CSS Architecture

### Hybrid Approach: SCSS + Tailwind + Bootstrap

Dự án dùng 3 lớp CSS chồng lên nhau:

1. **Bootstrap (base)**: Grid system, reboot, utilities cơ bản - import selective qua SCSS
2. **SCSS (components)**: Styles cho sidebar, table, filter, pages cụ thể
3. **Tailwind (inline)**: Utility classes trực tiếp trong HTML, dùng `!` prefix để override

### SCSS Entry Point: `scss/style.scss`

Import order:
```scss
@import '_fonts';           // Google Fonts Inter
@import 'bootstrap/...';   // Selective Bootstrap modules
@import '_reset';           // Normalize + custom reset
@import '_variables';       // Mixins + utility generators
@import '_body';            // Base body styles
@import 'components/...';   // Component styles
@import 'pages/...';        // Page-specific styles
```

### Key SCSS Mixins (`_variables.scss`)

```scss
@mixin ratio($width, $height)    // Aspect ratio
@mixin line-clamp($lines)        // Text truncation
@mixin size($width, $height)     // Width + height shorthand
@mixin section-padding()         // Responsive section padding
@mixin title-global()            // Global title styles
@mixin btn-global()              // Global button styles
```

Auto-generated utilities via `@for` loop: `max-w-*`, `p-top-*`, `p-left-*`, `p-x-*`, `p-y-*`, `p-xy-*` (192 classes).

### Design Tokens / Colors

| Token | Hex | Sử dụng |
|---|---|---|
| Primary Blue | `#3F8CFE` | Buttons, active states, links |
| Dark Blue | `#18478D` | Hover states |
| Background Blue | `#D8EEFF` | Dashboard background |
| Text Dark | `#363636` | Primary text |
| Text Muted | `#909090` | Secondary text |
| Border Light | `#ECECEC` | Table borders, dividers |
| Border Purple | `#EDEDF6` | Alternative borders |
| Active Accent | `#00E1FF` | Sidebar active indicator |
| Success Green | `#00B69B` | Status badges |
| Warning Orange | `#F6A723` | Warning badges |
| Error Red | `#EF3826` | Error states |

### Fonts

| Font | Sử dụng | Source |
|---|---|---|
| **Inter** | Primary UI font | Google Fonts CDN (woff2) |
| **Playfair Display** | Decorative headings | Self-hosted (`fonts/playfair/`) |
| **Italianno** | Decorative text | Self-hosted (`fonts/italianno/`) |
| **IBM Plex Serif** | Serif text | Self-hosted (`fonts/plexserif/`) |
| **Font Awesome** | Icons | Self-hosted (`fonts/fontawesome/`) |

---

## JavaScript Architecture

### `js/main.js` - Custom App Logic (718 dòng)

Tất cả functions được khởi tạo trong `window.onload`:

| Function | Mục đích |
|---|---|
| `inputTogglePassword()` | Toggle hiện/ẩn password (eye icon) |
| `toggleMenuDropdown()` | Sidebar sub-menu accordion expand/collapse |
| `checkVerifyOTP()` | Auto-advance giữa 6 ô input OTP |
| `resendOtp()` / `verifyOtp()` | OTP actions (placeholder alerts) |
| `checkSidebar()` | Tính toán sidebar width, set `marginLeft` cho main content |
| `sidebarMobile()` | Mobile sidebar open/close với overlay |
| `toggleMobile()` | Desktop sidebar toggle với CSS transform animation |
| `collapsedFilter()` | Show/hide filter rows mở rộng |
| `croppedimage()` | Croppie image cropper init với Bootstrap modal |
| `filterTable()` | Price range slider (jQuery UI), Select2 multi-select |
| `toggleDropdownFilter()` | Column visibility filter với "Select All" checkbox |
| `fileDropzone()` | Dropzone.js init cho file import |
| `tableMagic()` | Auto-calculate column widths, apply consistent sizing |
| `tbDropdown()` | Table column filter dropdown toggle |
| `mobileDropFilters()` | Mobile filter panel toggle |
| `tableTooltips()` | Bootstrap tooltip initialization |

### Vue 3 Setup Pattern

Mỗi trang HTML tạo Vue app riêng:

```javascript
// 1. Load vue3-sfc-loader config
const options = { /* moduleCache, getFile, addStyle */ }

// 2. Define async components
const app = Vue.createApp({
  components: {
    'sidebar': Vue.defineAsyncComponent(() =>
      loadModule('./vue_components/sidebar.vue', options)
    ),
    'user-switch': Vue.defineAsyncComponent(() =>
      loadModule('./vue_components/user-switch.vue', options)
    ),
  },
  data() {
    return {
      // Inline data: menu items, table headers, table rows
    }
  }
})
app.mount('#app')
```

### `js/vuedefineasync.js` - SFC Loader Config (24 dòng)

Cấu hình `vue3-sfc-loader`:
- Module cache setup
- File fetching via `fetch()`
- Style injection vào DOM

---

## Vue Components (`vue_components/`)

| Component | File | Mô tả | Trạng thái |
|---|---|---|---|
| `sidebar` | `sidebar.vue` | Navigation sidebar, data-driven menu với icons, sub-items | Hoàn thiện (149 dòng) |
| `root-layout` | `root-layout.vue` | Layout wrapper với `<slot>` cho content | Hoàn thiện |
| `user-switch` | `user-switch.vue` | User profile dropdown (avatar, tên, logout) | Hoàn thiện |
| `filte-table` | `filte-table.vue` | Filter controls cho data tables | Hoàn thiện |
| `table-magic` | `table-magic.vue` | Custom data table component | Hoàn thiện |
| `header` | `header.vue` | Header component | Empty |
| `footer` | `footer.vue` | Footer component | Empty |

### Sidebar Menu Structure (`sidebar.vue`)

```
├── Dashboard        (icon: dashboard)
├── Bảng hàng        (icon: inventory)      -> /banghang.html
├── Khách hàng       (icon: customers)      -> /khachhang.html, /khachhang-v2.html
│   ├── Tất cả khách hàng
│   └── Khách hàng v2
└── Quản trị         (icon: admin)          -> /quantri.html
```

---

## Customer Pipeline (Sales Statuses)

Hệ thống quản lý khách hàng theo pipeline bán hàng BĐS:

| Status | Mô tả |
|---|---|
| Mới | Khách hàng mới nhập vào hệ thống |
| Đang tiếp cận | Đang liên hệ lần đầu |
| Đang tư vấn | Đang tư vấn sản phẩm |
| Tiềm năng | Khách có tiềm năng mua |
| Đang hẹn gặp | Đã lên lịch gặp mặt |
| Đã hẹn | Đã gặp mặt |
| Nóng | Khách hàng "nóng" - sắp chốt |
| Chốt | Đã chốt deal |
| Mua tiếp | Khách mua thêm sản phẩm |
| Dừng mua | Khách dừng mua |
| Mua bên khác | Khách mua ở nơi khác |
| Mua dự án khác | Khách mua dự án khác |

---

## Code Conventions

### Prettier Config (`.prettierrc.json`)
- **Indent**: 2 spaces (useTabs: true)
- **Semicolons**: Không
- **Quotes**: Single quotes
- **Trailing commas**: Có (all)

### Naming Conventions
- **HTML files**: kebab-case tiếng Việt không dấu (`khachhang-v2.html`, `quen-mat-khau.html`)
- **SCSS partials**: Underscore prefix (`_sidebar.scss`, `_table.scss`)
- **Vue components**: kebab-case (`root-layout.vue`, `user-switch.vue`)
- **CSS classes**: Mix BEM-like (`table-magic`, `cell-btn-edit`) + Tailwind utilities
- **JS functions**: camelCase (`toggleMenuDropdown`, `checkSidebar`)

### Patterns
- jQuery (`$`) và vanilla JS được trộn lẫn trong cùng file
- Inline SVG icons được ưu tiên hơn icon fonts
- `!important` modifier (`!`) của Tailwind dùng nhiều để override Bootstrap/SCSS
- Arbitrary values Tailwind: `bg-[#d8eeff]`, `min-h-[100vh]`, `p-[6px_24px]`

---

## Development Workflow

### Chạy dự án
Dự án là **static files** - không cần build step:
1. Mở bất kỳ `.html` file trong browser (hoặc dùng Live Server)
2. Vue components được load runtime qua `vue3-sfc-loader` (cần HTTP server, không chạy được từ `file://`)

### SCSS Compilation
- SCSS được compile riêng (có thể qua IDE plugin hoặc local task runner)
- `package.json` tồn tại locally nhưng bị `.gitignore` - không tracked
- Output: `css/style.css` -> `css/style.min.css`

### Không có build tools
- Không webpack, vite, rollup
- Không `tsconfig.json`
- Không `node_modules` tracked
- Tailwind chạy runtime qua Play CDN

---

## Known Issues / Incomplete Areas

| Issue | Chi tiết |
|---|---|
| **Empty components** | `header.vue` và `footer.vue` không có template content |
| **Empty index** | `index.html` có `<main></main>` rỗng |
| **No backend** | Tất cả form `action=""`, không có API calls |
| **Placeholder logic** | OTP verification dùng `alert()` |
| **Empty links** | Nhiều links có `href=""` |
| **Hardcoded data** | Table data inline trong HTML, không fetch từ API |
| **Duplicate Vue mounts** | Một số pages mount 2 Vue apps vào cùng `#app` (ví dụ `khachhang.html`) |
| **Legacy files** | `vue.js` (Vue 2) và `httpvueloaders.js` còn tồn tại nhưng không dùng |
| **Sidebar duplication** | Sidebar HTML được copy-paste giữa các pages thay vì luôn dùng Vue component |

---

## Guidelines for Making Changes

### Thêm trang mới
1. Copy template từ `dashboard.html` (cho dashboard pages) hoặc `login.html` (cho auth pages)
2. Giữ nguyên cấu trúc `<head>` imports (CSS, JS, fonts)
3. Mount Vue app với pattern: `Vue.createApp({...}).mount('#app')`
4. Load shared components: `sidebar`, `user-switch`, `root-layout`
5. Thêm menu item vào `vue_components/sidebar.vue` nếu cần

### Thêm styles
1. **Ưu tiên Tailwind utilities** inline trong HTML cho styles đơn giản
2. **Tạo SCSS partial** trong `scss/components/` hoặc `scss/pages/` cho styles phức tạp
3. Import partial mới vào `scss/style.scss`
4. Compile lại SCSS -> `css/style.min.css`
5. Dùng design tokens (colors, fonts) đã định nghĩa ở trên

### Thêm Vue component
1. Tạo `.vue` file trong `vue_components/`
2. Load qua `Vue.defineAsyncComponent(() => loadModule('./vue_components/ten-component.vue', options))`
3. Register trong `components` object của `Vue.createApp()`

### Thêm thư viện JS/CSS
1. Vendored libraries đặt trong `libs/`
2. Hoặc load từ CDN trong `<head>`
3. JS libraries cũng có thể đặt trong `js/`

### Quy tắc quan trọng
- **Không dùng build step** - mọi thứ phải chạy trực tiếp trong browser
- **Giữ tiếng Việt** cho UI labels và content
- **Follow Prettier config** - no semicolons, single quotes, 2-space indent
- **Tránh duplicate sidebar** - dùng Vue component `<sidebar>` thay vì copy HTML
- **Test trên HTTP server** - vue3-sfc-loader không hoạt động với `file://` protocol
