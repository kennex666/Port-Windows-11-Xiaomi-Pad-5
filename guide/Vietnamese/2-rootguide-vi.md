<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Root thiết bị của bạn
> [!NOTE]
> **Nếu bạn đã root rồi thì hãy bỏ qua bước này và chuyển sang trang tiếp theo**

### Chuẩn bị trước
- ```Anh hẹn em Pickleball 🤡🧠```
  
- [```Android boot backup```](/guide/Vietnamese/1-partition-vi.md#Tạo-một-bản-sao-cho-boot-image-hiện-tại) (là cái mà bạn đã sao lưu ở hướng dẫn trước)

### Vá boot image của bạn (Patching boot image)
- Copy ```normal_boot.img``` từ ```platform tools``` vào tablet.

- Download và cài đặt [Magisk app](https://github.com/topjohnwu/Magisk/releases/latest) lên máy.
  
-  Mở Magisk app và nhấn nút ```Install```. Chọn ```Select and Patch a File``` và tìm tới file ```normal_boot.img``` mà bạn copy lên tablet. Nhấn vào ```Let's Go```và chờ quá trình patching hoàn tất.
  
- Copy the ```magisk_patched....img``` từ thư mục ```Downloads``` trên tablet vào folder ```platform tools``` trên máy tính. 

### Reboot vào chế độ fastboot
```cmd
adb reboot bootloader
```

### Flash boot image đã vá
> Thay `magisk_patched.img` bằng tên file ```magisk_patched.img``` mới copy ở trước.
```cmd
fastboot flash boot magisk_patched.img
```

### Reboot vào Android
```cmd
fastboot reboot
```

#### Kết thúc cài đặt
- Mở **Magisk** app lần nữa.
- Làm theo hướng dẫn trên màn hình, và thiết bị của bạn sẽ reboot sau vài giây.

### Copy boot image đã root
> Sau khi thiết bị đã boot được vào Android
- Một yêu cầu superuser cho Shell có thể hiện trên màn hình. Nếu có, grant it access.
- Nếu lệnh bị thất bại, hãy mở **Magisk**, nhấn vào `Superuser`, tìm **Shell**, và grant it access.
```cmd
adb shell "su -c cp /dev/block/by-name/boot$(getprop ro.boot.slot_suffix) /sdcard/rooted_boot.img" & adb pull /sdcard/rooted_boot.img
```

### [Bước kế tiếp: Cài đặt Windows](/guide/Vietnamese/3-install-vi.md)












