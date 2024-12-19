<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Ứng dụng và hướng dẫn hữu ích cho Windows trên Xiaomi Pad 5

### Danh sách các app/game có thể chạy được
Đây không phải là một danh sách bao hàm tất cả, chỉ liệt kê những ứng dụng được cộng đồng thử nghiệm. [Xem tại đây](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

Bạn cũng có thể tìm thấy danh sách phần mềm dành cho ARM [tại đây](https://armrepo.ver.lt/)

#### Hoàn tất rồi đó!

## Ẩn ổ D (modem partition)
> [!NOTE]
> Đây là khuyến nghị, bởi vì ổ này không được chỉnh sửa, trong khi một số ứng dụng có thể sẽ cố gắng ghi vào trong ổ này.

- Tải [`ModemHide.vbs`](https://github.com/Misha803/My-Scripts/releases/tag/ModemHide) từ NABU (tablet)
- Chạy script
- Đồng ý tất cả những gì trong UAC dialogs 
- Nhấn `Yes` trong hộp thoại


#### Yahh. Bạn làm được rồi!


## Vô hiệu USB host mode
> [!Warning]
> Các thiết bị USB không được cấp nguồn sẽ ngừng hoạt động

> [!Important]
> Các bước sau phải được thực hiện trên Mi Pad 5 chạy Windows, không phải trên máy tính của bạn.

Chạy [USB Host Mode Control](https://github.com/Misha803/My-Scripts/releases/tag/USB-Host-Mode-Control) để kích hoạt/vô hiệu USB host mode và chắc chắn rằng bạn muốn bật/tắt USB host mode 

#### Yayy. Hoàn tất rồi nha!

## Tôi có thể cập nhật máy từ Windows Update hoặc an ISO image?
- ✅ **Có thế nha!** Bạn có thể cài bất kỳ bản cập nhật nào từ Windows Update hoặc từ ISO image

## Tôi có thể cập nhật Android sau khi cài Windows?
- ✅ **Có thể luôn!** Bạn có thể cập nhật Android, chỉ cần nhớ là phải [Re-rooting Android](Re-rooting-vi.md) sau khi cập nhật

## Tắt secureboot
> [!Warning]
> Chỉ làm khi thật sự cần thiết.

> [**`Xem hướng dẫn disabling secureboot`**](/guide/Vietnamese/disable-secureboot-vi.md)

#### Ok hết rồi nhé!


## Cài Microsoft Office / Microsoft 365
- Tải [file ISO](https://drive.google.com/file/d/10FTyC0XBccj0BkxdIa_W_haixQz-d3to/view?usp=drivesdk) vào tablet
- Chuột phải vào file iso và chọn Mount to open it trong Explorer
- Chuột phải vào file ```Office Tool Plus``` để bắt đầu "pháp sư" cài đặt :v
- Chấp nhận tất cả UAC dialogs 
- Trong cửa sổ hiển thị, click `Yes` để bắt đầu cài đặt
- Chờ cho cài đặt hoàn tất

#### Pickleball!


## Kích hoạt Windows / Office
Ai biết đâu, làm theo hướng dẫn Massgravel [ở đây nè](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Yoshi!


## ~Làm sao để xài Flashlight~
 - Tải [Flashlight.7z](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/flashlight_fix.7z) và giải nén ở đâu cũng được
> Chạy flashlight.exe để bật đèn flash
> Nhấn phím bất kỳ để tắt đèn

#### Cũng dễ he!

## Factory reset Windows 11
> [!Warning]
> Sau khi bạn thực hiện xong, toàn bộ dữ liệu của Windows sẽ bị xoá sạch, bao gồm cả file, cài đặt và ứng dụng.
- Mở Settings app.
- Click vào System.
- Click vào Recovery tab.
- Ở dưới phaanf **Recovery options**, click nút ```Reset PC```trong phần cài đặt **Reset this PC**.
- Click tuỳ chọn ```Remove Everything```.
- Chọn tuỳ chọn ```Local reinstall```.
- Click nút `Next`.
- Click nút `Reset`.
> Sau khi làm xong, bạn sẽ có một bản Windows sạch tinh tươm.

#### Okay, đọc tiếp nha, viết cực lắm à!


## Vô hiệu adaptive brightness

- Mở Windows 11 Settings bằng cách nhấn **`Win + I`** hoặc chuột phải vào Start button và chọn "Settings".

- Điều hướng đến phần **`System`** từ bên trái sidebar.

- Chọn **`Display`** trong phần System settings.

- Ở phần  **`Brightness`**, bạn sẽ nhìn thấy 2 tuỳ chọn:

**```1. Change brightness automatically when lighting changes:```** (Chỉnh ánh sáng theo môi trường)

> Tắt cái này chỉ cần chuyển qua bên **`Off`**.
  
 **```2. Change brightness based on content:```** (Chỉnh ánh sáng dựa trên nội dung)

> Tắt cái này chỉ cần chọn **`Off`** trong dropdown.

>[!NOTE]
> Sau khi thay đổi, adaptive brightness và content-adaptive brightness sẽ bị vô hiệu hóa trên thiết bị của bạn.

 #### Đã xong!













