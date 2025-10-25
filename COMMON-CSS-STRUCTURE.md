# Common CSS Structure - CRMS Template

## Tổng quan
Dự án CRMS Template đã được cải thiện với cấu trúc **Common CSS** - tất cả trang đều có cùng một bộ CSS cơ bản, được tổ chức trong file `common.scss`.

## Cấu trúc Common CSS

### 1. File chính: `src/public/scss/common.scss`
File SCSS chung chứa tất cả CSS cơ bản mà mọi trang đều cần:

```scss
// ========================================
// Common CSS - Tất cả trang đều có
// ========================================

// 1. Bootstrap CSS (Import hoặc sử dụng CDN)
// 2. Tabler Icons CSS (Import hoặc sử dụng CDN)  
// 3. Simplebar CSS (Import hoặc sử dụng CDN)
// 4. Main CSS - Import tất cả components chính
// 5. Custom Components cho tất cả trang
// 6. Common Styles cho tất cả trang
// 7. Global Styles
// 8. Common Layout Elements
// 9. Common Typography
// 10. Common Form Styles
// 11. Common Button Variants
// 12. Common Table Styles
// 13. Common Card Styles
// 14. Common Alert Styles
// 15. Common Navigation Styles
// 16. Common Modal Styles
// 17. Common Utility Classes
// 18. Print Styles
```

### 2. File entry point: `src/public/scss/style.scss`
File SCSS chính chỉ import `common.scss`:

```scss
// ========================================
// Main SCSS File - CRMS Template
// ========================================

// Import Common CSS - Tất cả trang đều có
@use "./common" as *;

// Additional page-specific styles can be added here
// This file now serves as the main entry point that includes common.scss
```

## Thứ tự load CSS trong HTML

```pug
// ========================================
// CSS Loading Order - CRMS Template
// ========================================

// 1. Bootstrap CSS
link(rel='stylesheet' href='../client/css/bootstrap.min.css')

// 2. Tabler Icon CSS
link(rel='stylesheet' href='../client/plugins/tabler-icons/tabler-icons.min.css')

// 3. Simplebar CSS
link(rel='stylesheet' href='../client/plugins/simplebar/simplebar.min.css')

// 4. Main CSS (Common CSS - Tất cả trang đều có)
link(rel='stylesheet' href='../client/css/style.css' id='app-style')

// 5. Additional Plugin CSS (Optional - Load after main CSS)
link(rel='stylesheet' href='../client/css/hover-min.css')
link(rel='stylesheet' href='../client/css/animate.css')
link(rel='stylesheet' href='../client/slick/slick.css')
link(rel='stylesheet' href='../client/fonts/fontstyle.css')
```

## Các thành phần trong Common CSS

### 1. **Bootstrap CSS**
- Framework CSS chính
- Grid system, utilities, components
- Load đầu tiên để làm base

### 2. **Tabler Icons CSS**
- Icon font library
- Cung cấp icons cho toàn bộ template
- Load sau Bootstrap

### 3. **Simplebar CSS**
- Custom scrollbar library
- Cải thiện UX cho scrollbar
- Load sau Tabler Icons

### 4. **Main CSS (style.css)**
- File CSS chính được compile từ `common.scss`
- Chứa tất cả custom styles
- Load cuối cùng để override các CSS khác
- Có `id="app-style"` để dễ quản lý

### 5. **Additional Plugin CSS**
- Các CSS plugin bổ sung
- Load sau main CSS
- Có thể tùy chọn load theo trang

## Nội dung Common CSS

### **Variables & Mixins**
- CSS Variables cho theme
- SCSS Mixins cho responsive, buttons, forms
- Color palette, typography, spacing

### **Base Styles**
- CSS Reset & Normalize
- Base typography, forms, tables
- Scrollbar customization, focus styles

### **Layout Components**
- Container & Grid system
- Flexbox utilities
- Spacing, display, position utilities

### **UI Components**
- Buttons (all variants & sizes)
- Forms (inputs, selects, validation)
- Cards, Alerts, Badges, Progress
- Modals, Dropdowns, Navigation
- Tables

### **Utilities**
- Comprehensive utility classes
- Responsive utilities
- Typography, color, layout utilities

### **Custom Components**
- Breakpoint mixins
- Galaxy theme styles
- Login page styles
- Notification styles
- Animations
- Sidebar navigation

### **Common Styles**
- Global body styles
- Common layout elements
- Common typography
- Common form styles
- Common button variants
- Common table styles
- Common card styles
- Common alert styles
- Common navigation styles
- Common modal styles
- Common utility classes
- Print styles

## Lợi ích của cấu trúc Common CSS

### 1. **Consistency**
- Tất cả trang có cùng look & feel
- Consistent spacing, colors, typography
- Unified component behavior

### 2. **Performance**
- CSS được load một lần cho tất cả trang
- Reduced HTTP requests
- Better caching

### 3. **Maintainability**
- Dễ dàng update styles cho toàn bộ site
- Centralized CSS management
- Clear separation of concerns

### 4. **Scalability**
- Dễ dàng thêm trang mới
- Consistent development workflow
- Easy to onboard new developers

### 5. **Flexibility**
- Có thể override styles cho trang cụ thể
- Plugin CSS có thể load thêm
- Modular architecture

## Cách sử dụng

### **Compile SCSS**
```bash
npm run build:scss
```

### **Watch mode**
```bash
npm run watch:scss
```

### **Build toàn bộ**
```bash
npm run build
```

## Customization

### **Thay đổi theme**
Chỉnh sửa trong `common.scss`:
```scss
:root {
  --primary: #your-color;
  --secondary: #your-color;
  // ... other colors
}
```

### **Thêm styles cho trang cụ thể**
Tạo file SCSS riêng và import sau `common.scss`:
```scss
@use "./common" as *;

// Page-specific styles
.your-page-specific-class {
  // styles here
}
```

### **Override Common CSS**
Sử dụng CSS specificity cao hơn hoặc `!important`:
```scss
.your-override-class {
  color: red !important;
}
```

## File Structure

```
src/public/scss/
├── style.scss              # Main entry point
├── common.scss             # Common CSS - Tất cả trang đều có
├── variables.scss          # CSS Variables
├── mixins.scss            # SCSS Mixins
├── base.scss              # Base styles
├── layout.scss            # Layout components
├── components.scss        # UI components
├── utilities.scss         # Utility classes
├── breakpoint.scss        # Custom breakpoints
├── galaxy.scss            # Galaxy theme
├── login-crms.scss        # Login styles
├── notification.scss      # Notification styles
├── animations.scss        # Animations
└── sidebar.scss           # Sidebar styles
```

## Kết luận

Cấu trúc **Common CSS** của CRMS Template đã được tối ưu hóa để:

- ✅ **Tất cả trang đều có cùng CSS cơ bản**
- ✅ **Performance cao với CSS được load một lần**
- ✅ **Dễ bảo trì và mở rộng**
- ✅ **Consistent design system**
- ✅ **Flexible và customizable**
- ✅ **Tuân theo best practices hiện đại**

Với cấu trúc này, mọi trang trong CRMS Template sẽ có cùng một bộ CSS cơ bản, đảm bảo tính nhất quán và dễ dàng quản lý.
