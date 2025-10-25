# Page-specific CSS Structure - CRMS Template

## Tổng quan
Dự án CRMS Template đã được cải thiện với cấu trúc **Page-specific CSS** - mỗi trang có CSS riêng với các plugin CSS khác nhau tùy theo nhu cầu sử dụng.

## Cấu trúc Page-specific CSS

### 1. Thư mục Pages: `src/public/scss/pages/`
```
src/public/scss/pages/
├── activities.scss    # Activities page CSS
├── domain.scss        # Domain page CSS
├── dashboard.scss     # Dashboard page CSS
├── chat.scss          # Chat page CSS
└── calendar.scss      # Calendar page CSS
```

### 2. Các trang và CSS tương ứng:

#### 📄 **Trang Activities** (`activities.scss`)
**CSS Plugins:**
- `daterangepicker.css` - Date range picker
- `choices.min.css` - Enhanced select dropdowns
- `select2.min.css` - Advanced select
- `quill.snow.css` - Rich text editor
- `datatables.css` - Data tables
- `flatpickr.min.css` - Date picker

**Tính năng:**
- Quản lý và theo dõi activities
- Date range picker cho filter
- Enhanced select dropdowns
- Rich text editor cho notes
- Data tables với pagination
- Advanced search và filter

#### 📄 **Trang Domain** (`domain.scss`)
**CSS Plugins:**
- `daterangepicker.css` - Date range picker
- `datatables.css` - Data tables
- `flatpickr.min.css` - Date picker
- `select2.min.css` - Advanced select

**Tính năng:**
- Quản lý domains
- Domain statistics dashboard
- Data tables cho domain list
- Date picker cho filter
- Advanced select cho status

#### 📄 **Trang Dashboard** (`dashboard.scss`)
**CSS Plugins:**
- `daterangepicker.css` - Date range picker
- `datatables.css` - Data tables
- `flatpickr.min.css` - Date picker
- `select2.min.css` - Advanced select

**Tính năng:**
- Dashboard chính với widgets
- Charts và graphs
- Statistics cards
- Recent activities
- Data tables cho reports
- Advanced filtering

#### 📄 **Trang Chat** (`chat.scss`)
**CSS Plugins:**
- Chỉ có CSS cơ bản (không có plugin đặc biệt)

**Tính năng:**
- Real-time chat interface
- Message history
- User list sidebar
- Chat notifications
- Responsive design
- Custom animations

#### 📄 **Trang Calendar** (`calendar.scss`)
**CSS Plugins:**
- `bootstrap-datetimepicker.min.css` - DateTime picker
- `fontawesome.css` - Font Awesome icons
- `flatpickr.min.css` - Date picker
- `select2.min.css` - Advanced select

**Tính năng:**
- Calendar grid view
- Event management
- DateTime picker
- Event categories
- Event list sidebar
- Font Awesome icons

## Cách sử dụng Page-specific CSS

### 1. **Import trong HTML/Pug**
```pug
// Trong file .pug của từng trang
style.
  /* Import page-specific CSS */
  @import url('../../public/scss/pages/activities.css');
```

### 2. **Compile SCSS**
```bash
# Compile tất cả pages
npm run build:scss

# Hoặc compile từng page riêng
sass src/public/scss/pages/activities.scss src/public/css/pages/activities.css --style=compressed
```

### 3. **Load CSS trong HTML**
```html
<!-- Common CSS (tất cả trang) -->
<link rel="stylesheet" href="assets/css/style.css" id="app-style">

<!-- Page-specific CSS -->
<link rel="stylesheet" href="assets/css/pages/activities.css">
```

## Cấu trúc CSS cho từng trang

### **Activities Page**
```scss
.activities-page {
  // Date range picker styles
  .daterangepicker { ... }
  
  // Enhanced select dropdowns (Choices.js)
  .choices { ... }
  
  // Advanced select (Select2)
  .select2-container { ... }
  
  // Rich text editor (Quill)
  .ql-editor { ... }
  
  // Data tables
  .dataTables_wrapper { ... }
  
  // Date picker (Flatpickr)
  .flatpickr-input { ... }
  
  // Activities specific components
  .activity-card { ... }
  .activities-filter { ... }
}
```

### **Domain Page**
```scss
.domain-page {
  // Date range picker styles
  .daterangepicker { ... }
  
  // Data tables
  .dataTables_wrapper { ... }
  
  // Date picker (Flatpickr)
  .flatpickr-input { ... }
  
  // Advanced select (Select2)
  .select2-container { ... }
  
  // Domain specific components
  .domain-card { ... }
  .domain-stats { ... }
  .domain-filter { ... }
}
```

### **Dashboard Page**
```scss
.dashboard-page {
  // Date range picker styles
  .daterangepicker { ... }
  
  // Data tables
  .dataTables_wrapper { ... }
  
  // Date picker (Flatpickr)
  .flatpickr-input { ... }
  
  // Advanced select (Select2)
  .select2-container { ... }
  
  // Dashboard specific components
  .dashboard-widgets { ... }
  .dashboard-charts { ... }
  .dashboard-stats { ... }
  .recent-activities { ... }
}
```

### **Chat Page**
```scss
.chat-page {
  // Chat layout
  .chat-container { ... }
  .chat-sidebar { ... }
  .chat-main { ... }
  
  // Chat components
  .chat-header { ... }
  .chat-messages { ... }
  .chat-input { ... }
  
  // Chat notifications
  .chat-notifications { ... }
}
```

### **Calendar Page**
```scss
.calendar-page {
  // Bootstrap DateTime picker styles
  .bootstrap-datetimepicker-widget { ... }
  
  // Font Awesome icons
  .fa { ... }
  
  // Date picker (Flatpickr)
  .flatpickr-input { ... }
  
  // Advanced select (Select2)
  .select2-container { ... }
  
  // Calendar specific components
  .calendar-container { ... }
  .calendar-grid { ... }
  .event-modal { ... }
  .event-list { ... }
}
```

## Plugin CSS Mapping

### **Date Range Picker**
- **File:** `daterangepicker.css`
- **Pages:** Activities, Domain, Dashboard
- **Usage:** Filter by date range
- **Customization:** Colors, borders, hover effects

### **Data Tables**
- **File:** `datatables.css`
- **Pages:** Activities, Domain, Dashboard
- **Usage:** Sortable, searchable tables
- **Customization:** Pagination, styling, responsive

### **Flatpickr**
- **File:** `flatpickr.min.css`
- **Pages:** Activities, Domain, Dashboard, Calendar
- **Usage:** Date/time picker
- **Customization:** Calendar styling, date format

### **Select2**
- **File:** `select2.min.css`
- **Pages:** Activities, Domain, Dashboard, Calendar
- **Usage:** Enhanced select dropdowns
- **Customization:** Dropdown styling, search functionality

### **Choices.js**
- **File:** `choices.min.css`
- **Pages:** Activities
- **Usage:** Multi-select dropdowns
- **Customization:** Choice styling, search

### **Quill Editor**
- **File:** `quill.snow.css`
- **Pages:** Activities
- **Usage:** Rich text editor
- **Customization:** Toolbar, editor styling

### **Bootstrap DateTime Picker**
- **File:** `bootstrap-datetimepicker.min.css`
- **Pages:** Calendar
- **Usage:** DateTime selection
- **Customization:** Picker styling, time format

### **Font Awesome**
- **File:** `fontawesome.css`
- **Pages:** Calendar
- **Usage:** Icons
- **Customization:** Icon colors, sizes

## Responsive Design

Tất cả page-specific CSS đều có responsive design:

```scss
// Responsive design
@media (max-width: 768px) {
  .activities-filter .filter-row {
    flex-direction: column;
    
    .filter-group {
      min-width: 100%;
    }
  }
}
```

## Performance Optimization

### **CSS Loading Strategy:**
1. **Common CSS** - Load trước (tất cả trang)
2. **Page-specific CSS** - Load sau (chỉ trang cần)
3. **Plugin CSS** - Load theo thứ tự dependency

### **File Size:**
- Common CSS: ~111KB
- Page-specific CSS: ~5-15KB mỗi trang
- Plugin CSS: ~2-5KB mỗi plugin

## Customization

### **Thêm trang mới:**
1. Tạo file SCSS trong `src/public/scss/pages/`
2. Import common CSS
3. Thêm page-specific styles
4. Tạo HTML template
5. Compile CSS

### **Thêm plugin mới:**
1. Thêm CSS file vào thư mục plugins
2. Import trong page-specific SCSS
3. Customize styles theo design system
4. Test responsive design

## File Structure

```
src/
├── public/
│   ├── scss/
│   │   ├── common.scss           # Common CSS
│   │   ├── style.scss            # Main entry point
│   │   └── pages/                # Page-specific CSS
│   │       ├── activities.scss
│   │       ├── domain.scss
│   │       ├── dashboard.scss
│   │       ├── chat.scss
│   │       └── calendar.scss
│   └── css/
│       ├── style.css             # Compiled common CSS
│       └── pages/                # Compiled page-specific CSS
│           ├── activities.css
│           ├── domain.css
│           ├── dashboard.css
│           ├── chat.css
│           └── calendar.css
└── views/
    └── pages/                    # Page templates
        ├── activities.pug
        ├── domain.pug
        ├── dashboard.pug
        ├── chat.pug
        └── calendar.pug
```

## Kết luận

Cấu trúc **Page-specific CSS** của CRMS Template đã được tối ưu hóa để:

- ✅ **Mỗi trang có CSS riêng phù hợp**
- ✅ **Plugin CSS được load theo nhu cầu**
- ✅ **Performance cao với CSS tối ưu**
- ✅ **Dễ bảo trì và mở rộng**
- ✅ **Responsive design đầy đủ**
- ✅ **Customization linh hoạt**

Với cấu trúc này, mỗi trang trong CRMS Template sẽ có CSS tối ưu nhất cho chức năng của nó, đảm bảo performance cao và trải nghiệm người dùng tốt nhất.
