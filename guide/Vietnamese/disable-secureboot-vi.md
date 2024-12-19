<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Vô hiệu secureboot
> [!Important]
> Chỉ làm theo khi bạn cần vô hiệu hóa secureboot

### Chuẩn bị
- ```Một cây vợt Pickleball```

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- [```Recovery Image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```UEFI image (Secureboot off)```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-NoSecureboot-v3.img)

## Lợi và hại khi vô hiệu secureboot
> Mặc định trong hướng dẫn là sẽ bật

##### Ưu và nhược điểm của secureboot
- √ Không có watermark trên màn hình chính
- √ Các ứng dụng không hoạt động với Test mode sẽ hoạt động
- √ Bạn có thể cập nhật các phiên bản lớn (ví dụ: 22h2 lên 23h2) trực tiếp trong bản cập nhật Windows
- × Bạn không thể cài đặt trình điều khiển chưa được ký

##### Pros and cons of secureboot disabled
- √ Bạn có thể cài đặt trình điều khiển chưa được ký
- × Có Test mmode watermark trên màn hình chính
- × Các app/game có anti-cheat có thể không hoạt động
- × Bạn không thể cập nhật các phiên bản lớn (ví dụ: 22h2 lên 23h2) trực tiếp trong bản cập nhật Windows

## Vô hiệu secureboot

#### Tạo một file rooted boot image
> Bạn sẽ cần trở lại Android, nhưng bạn có thể bỏ qua nếu bạn đã làm file backup

Sử dụng tính năng `Backup Android boot` trong WOA Helper app, hoặc boot vào recovery custom và chạy lệnh sau:
```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/rooted_boot.img" && adb pull /tmp/rooted_boot.img
```

#### Boot vào recovery
> Thay <path\to\recovery> bằng đường dẫn thực của recovery image
```cmd
fastboot boot <path\to\recovery.img>
```

#### Activate mass storage mode
> Sau khi Xiaomi Pad 5 khởi động vào chế độ modded recovery, chạy lệnh sau
```cmd
adb shell msc
```

#### Chạy Windows disk manager
> Sau khi Xiaomi Pad 5 được phát hiện là một ổ đĩa
```cmd
diskpart
```

#### Chọn esp volume của tablet
> Dùng lệnh `list volume` để tìm nó, nó có tên "ESPNABU"
```diskpart
select volume <number>
```

#### Gán letter Y
```diskpart
assign letter y
```

#### Thoát diskpart
```diskpart
exit
```

#### Tuỳ chỉnh bootloader
> Để enable test signing
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Gỡ SiPolicy
> Assuming you are disabling secureboot on an existing install, you need to delete this file or the system will not boot
> Đảm bảo bạn đã vô hiệu hóa secureboot trên bản cài đặt hiện có, bạn cần xóa tệp này, nếu không hệ thống sẽ không khởi động
```cmd
del Y:\EFI\Microsoft\Boot\SiPolicy.p7b
```

#### Gỡ drive letter for ESPNABU
> Nếu không hoạt động, bỏ qua và chuyển sang lệnh tiếp theo. Ổ đĩa ảo này sẽ biến mất lần tiếp theo bạn khởi động lại máy tính của bạn.
```cmd
mountvol y: /d
```

#### Reboot vào fastboot
```cmd
adb reboot bootloader
```

#### Flashing the UEFI
> Đảm bảo bạn sử dụng UEFI không secureboot từ trang này, thay <path\to\uefi-NoSecureboot-v3.img> bằng đường dẫn thực tế đến UEFI
```cmd
fastboot flash boot <path\to\uefi-NoSecureboot-v3.img>
```

> [!Important]
> Đảm bảo cũng thay thế UEFI cũ của bạn trong thư mục UEFI trong bộ nhớ trong của Android, bạn sẽ không vô tình flash nó vào lần tiếp theo khi bạn cố gắng chuyển sang Windows từ Android

#### Reboot vào Windows
```cmd
fastboot reboot
```

## Hoàn tất 💖


















