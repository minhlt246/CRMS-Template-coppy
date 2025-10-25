# 🎯 Cách Hoạt Động CSS - CRMS Template

## 📋 Tổng Quan

CRMS Template sử dụng cấu trúc CSS **2 tầng**:
1. **Common CSS** - Load cho tất cả trang
2. **Page-specific CSS** - Load theo nhu cầu từng trang

---

## 🔄 1. Common CSS - Tất Cả Trang Đều Load

### CSS Files được load trong `master.pug`:

```html
<!-- 1. Bootstrap CSS - Framework cơ bản -->
<link rel="stylesheet" href="../client/css/bootstrap.min.css">

<!-- 2. Tabler Icons - Icon fonts -->
<link rel="stylesheet" href="../client/plugins/tabler-icons/tabler-icons.min.css">

<!-- 3. Simplebar - Custom scrollbar -->
<link rel="stylesheet" href="../client/plugins/simplebar/simplebar.min.css">

<!-- 4. Main CSS - CSS chính của template (Common CSS) -->
<link rel="stylesheet" href="../client/css/style.css" id="app-style">

<!-- 5. Additional CSS - CSS bổ sung -->
<link rel="stylesheet" href="../client/css/hover-min.css">
<link rel="stylesheet" href="../client/css/animate.css">
<link rel="stylesheet" href="../client/slick/slick.css">
<link rel="stylesheet" href="../client/fonts/fontstyle.css">
```

### Nội dung `style.css` (Common CSS):

```scss
// ========================================
// Common SCSS - For all pages
// ========================================

// 1. Variables & Mixins
@use "./variables" as *;
@use "./mixins" as *;

// 2. Base Styles
@use "./base" as *;

// 3. Layout Components
@use "./layout" as *;

// 4. UI Components
@use "./components" as *;

// 5. Utilities
@use "./utilities" as *;

// 6. Custom Components
@use "./breakpoint.scss" as *;
@use "./galaxy.scss" as galaxy;
@use "./login-crms.scss" as login-crms;
@use "./notification.scss" as notification;
@use "./animations.scss" as animations;
@use "./sidebar.scss" as sidebar;
```

---

## 🎨 2. Page-specific CSS - Load Theo Nhu Cầu

### Cách hoạt động:

Mỗi trang có file SCSS riêng trong `src/public/scss/pages/` và được load thông qua:

```html
<!-- Trong từng trang cụ thể -->
<style>
  @import url('../../public/scss/pages/activities.css');
</style>
```

---

## 📊 3. Ví Dụ Cụ Thể Theo Từng Trang

### 🏃‍♂️ Trang Activities

**CSS được load:**
```html
<!-- Common CSS (tất cả trang) -->
<link rel="stylesheet" href="../client/css/style.css">

<!-- Page-specific CSS -->
<style>
  @import url('../../public/scss/pages/activities.css');
</style>
```

**Nội dung `activities.css`:**
```scss
// Plugin CSS cho Activities Page
@use "../../plugins/daterangepicker/daterangepicker.css";
@use "../../plugins/choices.js/choices.min.css";
@use "../../plugins/select2/css/select2.min.css";
@use "../../plugins/quill/quill.snow.css";
@use "../../plugins/datatables/css/dataTables.bootstrap5.min.css";
@use "../../plugins/flatpickr/flatpickr.min.css";

// Custom styles cho Activities page
.activities-page {
  // Styles riêng cho trang Activities
}
```

**JavaScript initialization:**
```javascript
$(document).ready(function() {
  // DataTables cho bảng dữ liệu
  $('#activitiesTable').DataTable({
    responsive: true,
    pageLength: 10
  });
  
  // Flatpickr cho date range
  flatpickr("#dateRange", {
    mode: "range",
    dateFormat: "Y-m-d"
  });
  
  // Choices.js cho select dropdowns
  new Choices('#statusFilter');
  new Choices('#categoryFilter');
  
  // Select2 cho search
  $('#searchInput').select2({
    placeholder: 'Search activities...'
  });
  
  // Quill cho rich text editor
  var quill = new Quill('#activityNotes', {
    theme: 'snow'
  });
});
```

---

### 📅 Trang Calendar

**CSS được load:**
```html
<!-- Common CSS (tất cả trang) -->
<link rel="stylesheet" href="../client/css/style.css">

<!-- Page-specific CSS -->
<style>
  @import url('../../public/scss/pages/calendar.css');
</style>
```

**Nội dung `calendar.css`:**
```scss
// Plugin CSS cho Calendar Page
@use "../../plugins/bootstrap-datetimepicker.min.css";
@use "../../plugins/fontawesome/css/fontawesome.min.css";
@use "../../plugins/flatpickr/flatpickr.min.css";
@use "../../plugins/select2/css/select2.min.css";

// Custom styles cho Calendar page
.calendar-page {
  // Styles riêng cho trang Calendar
}
```

**JavaScript initialization:**
```javascript
$(document).ready(function() {
  // Flatpickr cho date range
  flatpickr("#calendarDateRange", {
    mode: "range",
    dateFormat: "Y-m-d"
  });
  
  // Select2 cho các dropdown
  $('#calendarView').select2();
  $('#calendarCategory').select2();
  
  // Calendar interactions
  $('.calendar-day').on('click', function() {
    $('#eventModal').modal('show');
  });
});
```

---

### 💬 Trang Chat

**CSS được load:**
```html
<!-- Common CSS (tất cả trang) -->
<link rel="stylesheet" href="../client/css/style.css">

<!-- Page-specific CSS -->
<style>
  @import url('../../public/scss/pages/chat.css');
</style>
```

**Nội dung `chat.css`:**
```scss
// Chat page chỉ cần CSS cơ bản, không có plugin đặc biệt

// Custom styles cho Chat page
.chat-page {
  // Styles riêng cho trang Chat
}
```

---

## 🚀 4. Lợi Ích Của Cấu Trúc Này

### ✅ Performance Optimization

**Trước (Load tất cả CSS):**
```html
<!-- Load 50+ CSS files cho mọi trang -->
<link rel="stylesheet" href="plugin1.css">
<link rel="stylesheet" href="plugin2.css">
<link rel="stylesheet" href="plugin3.css">
<!-- ... 47 files khác -->
```

**Sau (Load theo nhu cầu):**
```html
<!-- Common CSS - 1 file -->
<link rel="stylesheet" href="style.css">

<!-- Page-specific CSS - 3-6 files tùy trang -->
<style>@import url('pages/activities.css');</style>
```

### ✅ Bandwidth Savings

| Trang | CSS Files | Kích thước ước tính |
|-------|-----------|-------------------|
| **Activities** | 6 plugin files | ~200KB |
| **Calendar** | 4 plugin files | ~150KB |
| **Chat** | 0 plugin files | ~50KB |
| **Dashboard** | 4 plugin files | ~150KB |
| **Domain** | 4 plugin files | ~150KB |

**Tổng tiết kiệm:** ~60-70% bandwidth so với load tất cả CSS

### ✅ Maintainability

- **Dễ quản lý:** Mỗi trang có CSS riêng
- **Dễ debug:** Lỗi CSS chỉ ảnh hưởng trang cụ thể
- **Dễ mở rộng:** Thêm trang mới không ảnh hưởng trang cũ

### ✅ Developer Experience

- **Code splitting:** CSS được chia nhỏ theo chức năng
- **Hot reload:** Thay đổi CSS chỉ reload trang cần thiết
- **Clear structure:** Cấu trúc rõ ràng, dễ hiểu

---

## 🔧 5. Cách Sử Dụng

### Tạo trang mới:

1. **Tạo file SCSS:**
```scss
// src/public/scss/pages/new-page.scss
@use "../../plugins/plugin1.css";
@use "../../plugins/plugin2.css";

.new-page {
  // Custom styles
}
```

2. **Tạo file Pug:**
```pug
extends ../_layouts/master

block content
  .new-page
    // Page content

  style.
    @import url('../../public/scss/pages/new-page.css');
  
  script.
    // Initialize plugins
```

3. **Compile CSS:**
```bash
npm run build:scss
```

---

## 📈 6. Kết Quả

### Trước khi tối ưu:
- ❌ Load 50+ CSS files cho mọi trang
- ❌ Bandwidth cao (~500KB+)
- ❌ Load time chậm
- ❌ Khó maintain

### Sau khi tối ưu:
- ✅ Load 1 common CSS + 3-6 page-specific CSS
- ✅ Bandwidth thấp (~150-200KB)
- ✅ Load time nhanh
- ✅ Dễ maintain và mở rộng

---

## 🎯 Tóm Tắt

**CRMS Template CSS Structure hoạt động theo nguyên tắc:**

1. **Common CSS** - Load cho tất cả trang (Bootstrap, Icons, Main styles)
2. **Page-specific CSS** - Load theo nhu cầu từng trang (Plugin CSS + Custom styles)
3. **Performance** - Tối ưu bandwidth và load time
4. **Maintainability** - Dễ quản lý và mở rộng
5. **Developer Experience** - Cấu trúc rõ ràng, dễ hiểu

**Kết quả:** Website nhanh hơn, tiết kiệm bandwidth, dễ maintain và mở rộng! 🚀

