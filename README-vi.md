# VARGG MCP

[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Discussions](https://img.shields.io/badge/discussions-welcome-blue)](https://github.com/var-gg/mcp/discussions)

**Languages / 语言 / 言語 / 언어 / Ngôn ngữ:**
- [![English](https://img.shields.io/badge/English-Click-yellow)](README.md)
- [![한국어](https://img.shields.io/badge/한국어-클릭-yellow)](README-ko.md)
- [![日本語](https://img.shields.io/badge/日本語-クリック-blue)](README-ja.md)
- [![简体中文](https://img.shields.io/badge/简体中文-点击查看-orange)](README-zh.md)
- [![Tiếng Việt](https://img.shields.io/badge/Tiếng_Việt-Nhấn_vào-green)](README-vi.md)

> **Công cụ quản lý siêu dữ liệu dự án thông qua Model Context Protocol**

Quản lý có hệ thống tên biến, hằng số và thuật ngữ tiêu chuẩn cho từng dự án, và tích hợp với Cursor IDE để giúp LLM sử dụng quy ước đặt tên nhất quán.

---

## 🎯 Tổng quan

VARGG MCP là một triển khai Model Context Protocol cho phép tích hợp liền mạch giữa môi trường phát triển của bạn và hệ thống quản lý siêu dữ liệu dự án tập trung. Nó giúp các nhóm duy trì quy ước đặt tên nhất quán giữa các dự án, đặc biệt là khi làm việc với các trợ lý AI như Cursor IDE.

### Các vấn đề giải quyết

- **Đặt tên không nhất quán**: Các nhà phát triển khác nhau sử dụng tên biến khác nhau cho cùng một khái niệm
- **Rào cản ngôn ngữ**: Các nhóm làm việc với nhiều ngôn ngữ gặp khó khăn trong việc duy trì tính nhất quán của thuật ngữ
- **Mất ngữ cảnh AI**: LLM tạo mã mà không biết các quy ước đã được thiết lập của nhóm bạn
- **Kho kiến thức riêng lẻ**: Các mẫu đặt tên cụ thể theo dự án không được chia sẻ hoặc không thể khám phá
- **Khó khăn khi tiếp nhận**: Các thành viên nhóm mới không biết nên tuân theo quy ước đặt tên nào

### Tóm tắt tính năng chính

- **Tổ chức theo dự án**: Quản lý biến và hằng số theo từng dự án
- **Hỗ trợ đa ngôn ngữ**: Hỗ trợ gốc cho tiếng Hàn, tiếng Anh, tiếng Nhật, tiếng Trung và tiếng Việt
- **Tích hợp Cursor IDE**: Tích hợp trực tiếp với Cursor IDE thông qua giao thức MCP
- **Tìm kiếm thời gian thực**: Tìm kiếm ngay lập tức các biến và định nghĩa hiện có
- **Thuật ngữ tiêu chuẩn**: Duy trì các định nghĩa nhất quán giữa các dự án
- **Hợp tác nhóm**: Chia sẻ và khám phá các mẫu đặt tên trong nhóm

### Người dùng mục tiêu

- **Nhóm phát triển**: Các nhóm muốn duy trì quy ước đặt tên nhất quán
- **Dự án đa ngôn ngữ**: Các dự án liên quan đến nhiều ngôn ngữ và địa phương
- **Phát triển hỗ trợ AI**: Các nhà phát triển sử dụng Cursor IDE hoặc các trợ lý mã hóa AI tương tự
- **Quản lý dự án**: Các nhóm quản lý thuật ngữ tiêu chuẩn hóa giữa các dự án

---

## ✨ Tính năng chính

### 🗂️ Quản lý biến theo dự án
Tổ chức biến và hằng số theo dự án, giúp dễ dàng duy trì quy ước đặt tên cụ thể theo dự án trong khi chia sẻ các mẫu chung giữa các nhóm.

### 🌐 Hỗ trợ đa ngôn ngữ
Hỗ trợ đầy đủ 5 ngôn ngữ:
- 🇰🇷 Tiếng Hàn (ko)
- 🇺🇸 Tiếng Anh (en)
- 🇯🇵 Tiếng Nhật (ja)
- 🇨🇳 Tiếng Trung (zh)
- 🇻🇳 Tiếng Việt (vi)

Mỗi ngôn ngữ có các quy tắc xác thực và bộ ký tự riêng cho tên biến và định nghĩa.

### 🔌 Tích hợp Cursor IDE
Tích hợp liền mạch với Cursor IDE thông qua Model Context Protocol. LLM có thể tự động tìm kiếm và sử dụng thuật ngữ tiêu chuẩn của nhóm bạn khi tạo mã.

### 🔍 Tìm kiếm và đề xuất thuật ngữ tiêu chuẩn tự động
Khi LLM tạo mã, chúng có thể tìm kiếm thư viện biến của dự án và đề xuất các thuật ngữ tiêu chuẩn hiện có thay vì tạo mới.

### ⚡ Tìm kiếm và đăng ký biến thời gian thực
Tìm kiếm ngay lập tức các biến hiện có và đăng ký biến mới khi bạn làm việc. Tất cả các thao tác được thực hiện theo thời gian thực thông qua giao thức MCP.

---

## 🚀 Bắt đầu nhanh

### Điều kiện tiên quyết

- Đã cài đặt Cursor IDE
- Tài khoản VARGG (tạo tại [var.gg](https://var.gg))
- Khóa API từ trang web VARGG

### 1. Lấy khóa API của bạn

1. Truy cập [var.gg](https://var.gg) và đăng nhập
2. Điều hướng đến cài đặt tài khoản của bạn
3. Tạo khóa API để truy cập MCP

### 2. Cấu hình Cursor IDE

Thêm VARGG MCP vào cài đặt Cursor IDE:

**Tệp (F) > Tùy chọn > Cài đặt Cursor**

Thêm cấu hình sau:

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/mcp/vi/project",
      "headers": {
        "X-API-KEY": "your-api-key-here"
      }
    }
  }
}
```

**Lưu ý**: Thay `vi` bằng locale ưa thích của bạn (`en`, `ko`, `ja`, `zh`).

Thay `your-api-key-here` bằng khóa API thực tế từ bước 1.

### 3. Tạo dự án đầu tiên của bạn

Trong Cursor IDE, yêu cầu trợ lý AI:

```
Tạo một dự án mới có tên "E-Commerce Payment" với mô tả "Mô-đun xử lý thanh toán cho nền tảng thương mại điện tử"
```

Hoặc sử dụng giao diện web tại [var.gg/projects](https://var.gg/projects).

### 4. Bắt đầu sử dụng biến

Yêu cầu Cursor tìm kiếm hoặc tạo biến:

```
Tìm kiếm các biến liên quan đến "tài khoản người dùng" trong dự án
```

```
Tạo biến TOTAL_COUNT với định nghĩa "total count" dưới dạng viết tắt trong dự án
```

---

## 🛠️ Công cụ có sẵn

VARGG MCP cung cấp các công cụ sau để quản lý dự án và biến:

### Quản lý dự án
- **`projects`** - Liệt kê tất cả các dự án bạn có thể truy cập
- **`create_project`** - Tạo dự án mới
- **`update_project`** - Cập nhật thông tin dự án
- **`open_project_admin`** - Mở trang quản trị dự án để quản lý quyền và mời người dùng

### Quản lý biến
- **`search_variables`** - Tìm kiếm biến trong dự án
- **`create_variables`** - Tạo biến mới trong dự án
- **`list_variables`** - Liệt kê tất cả các biến trong dự án (có phân trang)
- **`remove_variables`** - Xóa biến khỏi dự án

Để biết tài liệu chi tiết về từng công cụ, hãy xem [Tham chiếu công cụ](docs/tools-reference.md).

---

## 📖 Tài liệu

- **[Bắt đầu](docs/getting-started.md)** - Hướng dẫn thiết lập chi tiết
- **[Tham chiếu công cụ](docs/tools-reference.md)** - Tài liệu API đầy đủ cho tất cả các công cụ
- **[Hướng dẫn tích hợp Cursor](docs/integration-guide.md)** - Thiết lập Cursor IDE từng bước
- **[Thực hành tốt nhất](docs/best-practices.md)** - Quy trình làm việc và mẫu được đề xuất
- **[Trường hợp sử dụng](examples/use-cases.md)** - Ví dụ và tình huống thực tế
- **[Trang web chính thức](https://var.gg)** - Bản demo tương tác và hướng dẫn chi tiết

---

## 💡 Trường hợp sử dụng

### Thống nhất quy ước đặt tên trong nhóm
Đảm bảo tất cả các thành viên nhóm sử dụng cùng tên biến cho các khái niệm chung. Ví dụ, luôn sử dụng `USER_ACCOUNT` thay vì trộn lẫn `UserAccount`, `userAccount`, `user_account`, v.v.

### Quản lý thuật ngữ tiêu chuẩn theo dự án
Mỗi dự án có thể có bộ thuật ngữ tiêu chuẩn riêng. Dự án "Payment" có thể có `PAYMENT_AMOUNT`, trong khi dự án "Shipping" có thể có `SHIPPING_COST`.

### Đảm bảo tính nhất quán trong việc tạo mã LLM
Khi bạn yêu cầu Cursor tạo mã, nó sẽ tìm kiếm thư viện biến của dự án và sử dụng các thuật ngữ tiêu chuẩn hiện có, duy trì tính nhất quán trong tất cả mã được tạo.

### Quản lý tên biến trong dự án đa ngôn ngữ
Hỗ trợ đa ngôn ngữ có nghĩa là bạn có thể định nghĩa biến bằng ngôn ngữ mẹ đẻ của mình trong khi duy trì tên biến tiếng Anh cho mã. Ví dụ, `TOTAL_COUNT` với định nghĩa tiếng Việt "tổng số".

---

## 🤝 Cộng đồng

- **[Issues](https://github.com/var-gg/mcp/issues)**: Báo cáo lỗi, đề xuất tính năng, đặt câu hỏi
- **[Discussions](https://github.com/var-gg/mcp/discussions)**: Chia sẻ mẹo, Q&A, thảo luận ý tưởng
- **Lộ trình**: Xem các tính năng và cải tiến đã lên kế hoạch (kiểm tra nhãn vấn đề)

### Cách đóng góp

1. Chia sẻ trường hợp sử dụng của bạn trong [Discussions](https://github.com/var-gg/mcp/discussions)
2. Báo cáo lỗi hoặc yêu cầu tính năng qua [Issues](https://github.com/var-gg/mcp/issues)
3. Chia sẻ thực hành tốt nhất trong danh mục "Show and Tell"

---

## 🌐 Hỗ trợ đa ngôn ngữ

VARGG MCP hỗ trợ các ngôn ngữ sau với xác thực gốc và bộ ký tự:

| Language | Code | Character Set |
|----------|------|---------------|
| 🇰🇷 Tiếng Hàn | `ko` | 한글 + 영문 + 숫자 + 공백 + 괄호 |
| 🇺🇸 Tiếng Anh | `en` | English letters + numbers + spaces |
| 🇯🇵 Tiếng Nhật | `ja` | ひらがな + カタカナ + 漢字 + 영문 + 숫자 |
| 🇨🇳 Tiếng Trung | `zh` | 汉字 + 영문 + 숫자 |
| 🇻🇳 Tiếng Việt | `vi` | Vietnamese + 영문 + 숫자 |

Mỗi ngôn ngữ có các quy tắc xác thực cụ thể cho tên biến và định nghĩa. Xem [Tham chiếu công cụ](docs/tools-reference.md) để biết chi tiết.

---

## 🔗 Liên kết

- **Trang web**: [https://var.gg](https://var.gg)
- **Hướng dẫn MCP**: [https://var.gg/vi/mcp](https://var.gg/vi/mcp) (cũng có sẵn bằng en, ko, ja, zh)
- **Demo tương tác**: [https://var.gg/[locale]/mcp](https://var.gg/vi/mcp) - Thử các công cụ trong trình duyệt
- **Báo cáo vấn đề**: [https://github.com/var-gg/mcp/issues](https://github.com/var-gg/mcp/issues)
- **Thảo luận**: [https://github.com/var-gg/mcp/discussions](https://github.com/var-gg/mcp/discussions)

---

## 📝 Giấy phép

Dự án này được cấp phép theo Giấy phép MIT - xem tệp [LICENSE](LICENSE) để biết chi tiết.

---

## ⚠️ Lưu ý quan trọng

### Xuất bản mã

Hiện tại, kho lưu trữ này chỉ chứa tài liệu và tài nguyên cộng đồng. Mã triển khai máy chủ MCP chưa được mã nguồn mở, nhưng chúng tôi có thể xuất bản trong tương lai. Hãy quay lại để kiểm tra cập nhật!

### Lưu ý về kiến trúc

Triển khai VARGG MCP sử dụng giao diện giao thức JSON-RPC 2.0. Cursor IDE sử dụng JSON-RPC 2.0 để giao tiếp với máy chủ MCP, sau đó chuyển đổi các yêu cầu thành lời gọi REST API đến phụ trợ. Frontend hoạt động như một lớp proxy giữa giao thức MCP của Cursor và REST API phụ trợ.

### Quản lý phiên bản

Mặc dù mã chưa được xuất bản, chúng tôi theo dõi các phiên bản công cụ MCP và thay đổi tính năng trong [CHANGELOG.md](CHANGELOG.md).

### Quyền riêng tư

Khi báo cáo vấn đề hoặc thảo luận về tính năng, vui lòng tránh chia sẻ thông tin cá nhân hoặc khóa API. Nếu bạn cần chia sẻ thông tin nhạy cảm, vui lòng liên hệ với chúng tôi riêng tư.

---

**Được tạo bằng ❤️ bởi nhóm VARGG**

