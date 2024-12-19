<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Khởi động kép Android và Windows một cách liền mạch

### Chuẩn bị trước
- ```Một tablet đã root và đã cài Windows```

- [```UEFI image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)

- [```WoA Helper app```](https://github.com/n00b69/woa-helper/releases/tag/APK)

## Setup dualboot app
> Hướng dẫn này chỉ dùng được khi bạn đã root, nếu chưa, hãy làm theo [hướng dẫn root](2-rootguide-vi.md) trước

### Setup trên Android
- Tải và cài **WOA Helper**, sau đó mở và cấp quyền root
- Tài **UEFI image** và đặt vào thư mục `UEFI` trong bộ nhớ trong của bạn
- Mở WOA Helper và sử dụng **STA CREATOR** trong **WOA TOOLBOX**.
> [!Important]
> Nếu `/sdcard/Windows` không có gì, rom của bạn không hỗ trợ mounting và bạn sẽ phải làm một file boot.img sao lưu trong ứng dụng, sau đó copy thủ công vào Windows khi bạn boot thành công (ví dụ bằng cách tải lên đâu đó rồi tải xuống khi khởi động vào Windows). Tương tự với các tệp StA, cũng được tạo trong bộ nhớ trong của bạn.
>
> Làm tương tự nếu folder đang read-only.
- Nhấn nút **QUICKBOOT TO WINDOWS**.

### Setup trên Windows
> [!Tip]
> Nếu đây là lần đầu tiên bạn khởi động Windows và bạn muốn bỏ qua bước đăng nhập Tài khoản Microsoft, hãy nhấn nút **I don't have internet** trong trang WiFi, sau đó khi được nhắc, hãy nhấn nút **Continue with limited setup**.
- Điều hướng đến `C:\sta` và tạo một shortcut **sta.exe** trên desktop của bạn nếu chưa có.

#### Booting vào Android
- Chạy shortcut mới trên desktop của bạn (bạn cũng có thể ghim nó vào menu bắt đầu / thanh tác vụ để dễ truy cập)

#### Booting vào Windows
- Nhấn `QUICKBOOT TO WINDOWS` trong ứng dụng, hoặc sử dụng toggle mới được tạo trong bảng cài đặt nhanh của bạn
  
## Hoàn tất!

> [!TIP]
> Bạn có thể xem thêm [**```Ứng dụng và hướng dẫn hữu ích```**](Additional-materials-vi.md). Bạn sẽ tìm thấy một hướng dẫn làm sao để activate Windows, cũng như các thông tin hữu ích khác.










