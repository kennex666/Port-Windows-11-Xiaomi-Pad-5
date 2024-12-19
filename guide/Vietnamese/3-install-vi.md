<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Hướng dẫn cài đặt

### Chuẩn bị
- ```Hạt óc chó 🧠```

- [```DriveLetterAssigner```](https://github.com/Misha803/My-Scripts/releases/tag/DriveLetterAssigner)
  
- [```ARM Windows ESD```](https://arkt-7.github.io/woawin/)
    
- [```Drivers```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/tag/Drivers)

- [```UEFI image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)

### Boot vào recovery tuỳ chỉnh
> Thay `path\to\recovery.img` bằng đường dẫn thực tế của recovery image
```cmd
fastboot boot path\to\recovery.img
```

### Thực thi msc 
> Nếu nó yêu cầu chạy lại, hãy thực hiện lại lệnh này
```cmd
adb shell msc
```

### Gán letters cho WINNABU và ESPNABU
> Mở script **DriveLetterAssigner** và nhấn `Y` trên bàn phím để tự động gán các letters **X** và  **Y** cho **WINNABU** và **ESPNABU**

### Cài đặt Windows
> [!Important]
> Chắc chặn rằng bạn đang chạy CMD/Powershell với quyền **Administrator**

> [!Important]
> Để đảm bảo hiệu suất, khuyến nghị bạn nên dùng Windows 11 24H2 (builds bắt đầu bằng 261XX, như 26100.2454)

> Thay `path\to\install.esd` bằng đường dẫn thực tế của install.esd (có thể nó được đặt tên install.wim hoặc 22631.2861.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> Nếu bạn gặp lỗi `Error 87`, hãy kiểm tra chỉ số index của file image `dism /get-imageinfo /ImageFile:path\to\install.esd`, sau đó thay `index:6` bằng chỉ số index của **Windows 11 Pro** trong file image bạn tải.

### Copy boot.img vào Windows
- Kéo và thả file **rooted_boot.img** từ thư mục **platform-tools** vào ổ **WINNABU** trong Windows Explorer, sau đó đổi tên nó thành **boot.img**.

### Cài đặt các trình quản lý thiết bị (Drivers)
- Giải nén Drivers, sau đó mở file `OfflineUpdater.cmd` (nếu có lỗi khi khởi động, hãy chạy thử file `OfflineUpdaterFix.cmd`)

> Nếu có yêu cầu nhập một letter (chữ cái), nhập letter của **WINNABU** (thường là **X**), sau đó nhấn enter.

#### Tạo Windows bootloader files
> Nếu có lỗi xảy ra khi copy files boot, chạy lại **DriveLetterAssigner**, sau đó chạy lệnh sau, thay **Y** bằng **U**
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Gỡ drive letter cho ESPNABU
> Nếu lệnh này không hoạt động, bỏ qua và chuyển sang lệnh tiếp theo. Ổ đĩa ảo này sẽ biến mất sau khi khởi động lại máy.
```cmd
mountvol y: /d
```

### Reboot vào fastboot
```cmd
adb reboot bootloader
```

#### Boot vào UEFI
> Thay `path\to\nabu-uefi.img` bằng đường dẫn thực của UEFI image
```cmd
fastboot boot path\to\nabu-uefi.img
```

### Reboot vào Android
> Thiết bị của bạn sẽ khởi động lại sau khoảng 10 phút chờ, sau đó bạn sẽ được boot vào Android, tiếp theo là bước cuối cùng.

## [Bước cuối: Setup boot song song - dualboot](/guide/Vietnamese/4-dualboot-vi.md)



















