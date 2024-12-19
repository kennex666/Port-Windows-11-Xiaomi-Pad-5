<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Hướng dẫn cài đặt

### Chuẩn bị trước
- ```Unlocked bootloader``` - (Nếu bootloader của bạn đang bị khoá và chưa biết mở làm sao thì có thể [đọc hướng dẫn này](unlock-bootloader-en.md))

-  ```Pickleball 🤡🧠```

- ```Windows 10 (hoặc cao hơn) PC/Laptop```

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- [```Modified recovery image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

### Lưu ý:
> [!NOTE]
> Bạn có thể dùng bất kỳ Android nào cho dualboot (chạy song song) - MIUI/Hyper OS hoặc bất kỳ ROM tùy chỉnh nào

> [!Warning]
> Tất cả dữ liệu sẽ bị xoá sạch! Hãy nhớ SAO LƯU khi cần nhé.
> 
> ĐỪNG KHỞI ĐỘNG LẠI TABLET nếu bạn nghĩ bạn vừa thực hiện sai, hãy nhờ hỗ trợ tại [Telegram chat](https://t.me/nabuwoa) nhé

### Mở CMD với quyền Administator
> [!NOTE]
> Không biết bắt đầu từ đâu? Hãy giải nén bộ [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools), sau đó mở ```command prompt``` với quyền Admin và thực hiện lệnh, thay thế `"path\to\platform-tools"` bằng đường dẫn thực tế của bộ công cụ vừa tải.
```cmd
cd "path\to\platform-tools"
```
> Bạn sẽ xài cửa sổ này suốt quá trình hướng dẫn, đừng đóng nó nhé!

> [!Note]
> Nếu thiết bị của bạn không được nhận diện trong fastboot hoặc recovery mode, bạn sẽ phải cài đặt USB drivers [theo hướng dẫn này](troubleshooting-en.md#device-is-not-recognized-in-fastboot-or-recovery)

#### Khởi động vào chế độ fastboot
- Khởi động NABU (note của dịch giả: ý là Xiaomi Pad 5 - NABU là mã của máy á) vào chế độ **fastboot** bằng cách giữ nút **`giảm âm lượng`**, đồng thời luôn cắm cáp USB.
- Hoặc chạy lệnh sau nếu bạn đã khởi động máy
```cmd
adb reboot bootloader
```

### Khởi động vào modded recovery
> Trong khi đang ở chế độ fastboot, thay `path\to\recovery.img` bằng đường dẫn thực tế của file recovery
```cmd
fastboot boot path\to\recovery.img
```

### Tạo một bản sao cho boot image hiện tại
```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/normal_boot.img" && adb pull /tmp/normal_boot.img
```

### Phân vùng thiết bị
> Ở đây có 2 cách để phân vùng thiết bị. Hãy chọn một cách mà bạn thấy ổn ở dưới.

#### Cách 1: Phân vùng thủ công

<details>
  <summary><strong>Nhấn vào đây để xem cách thứ nhất</strong></summary> 

#### Unmount data
> Bỏ qua mọi lỗi có thể xảy ra và tiếp tục
```cmd
adb shell umount /dev/block/by-name/userdata
``` 

#### Chỉnh sửa bảng phân vùng (partition table)
```cmd
adb shell sgdisk --resize-table 64 /dev/block/sda
```

#### Chuẩn bị cho việc phân vùng
```cmd
adb shell parted /dev/block/sda
``` 

#### In các phân vùng hiện tại bằng bảng
> Các "phần" sẽ được in dưới dạng bảng phân vùng, **userdata** thường sẽ là phần cuối cùng trong danh sách
```cmd
print
``` 

#### Gỡ bỏ phân vùng userdata
> Thay **$** bằng số của phân vùng **userdata**, thường là **31**
```cmd
rm $
``` 

#### Khởi tạo phân vùng userdata mới
> Thay **10.9GB** bằng giá trị trước đó của **userdata** mà chúng ta vừa xóa
>
> Thay **70GB** bằng giá trị cuối mà bạn muốn **userdata** nhận. Trong ví dụ này, dung lượng có thể dùng trong Android sẽ là 70GB-10.9GB = **59GB**
```cmd
mkpart userdata ext4 10.9GB 70GB
``` 

#### Khởi tạo phân vùng ESP
> Thay **70GB** bằng giá trị cuối của **userdata**
>
> Thay **70.3GB** bằng giá trị bạn vừa dùng trước đó, thêm **0.3GB** vào đó
```cmd
mkpart esp fat32 70GB 70.3GB
``` 

#### Khởi tạo phân vùng Windows
> Thay **70.3GB** bằng giá trị cuối của **esp**
```cmd
mkpart win ntfs 70.3GB -0MB
``` 

#### Làm cho ESP có thể boot
> Sử dụng `print` để xem tất cả các phân vùng. Thay "$" bằng số phân vùng ESP của bạn, thường là **32**
```cmd
set $ esp on
``` 

#### Thoát chia phân vùng
```cmd
quit
``` 

### Format dữ liệu
> Hãy đảm bảo rằng **userdata** chắc chắn có số phân vùng là **31** bằng cách cuộn lên đầu đầu ra của lệnh `print`
```cmd
adb shell mke2fs -t f2fs -f /dev/block/sda31
```

#### Kiểm tra Android có khởi động được không
> Nếu không được, hãy khởi động vào recovery gốc và thực hiện **factory reset**
```cmd
adb reboot
```

### Format phân vùng Windows và ESP
```cmd
adb shell mkfs.ntfs -f /dev/block/by-name/win -L WINNABU
``` 

```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPNABU
``` 

</details>

#### Cách 2: Tự động phân vùng

<details>
  <summary><strong>Nhấn vào đây để xem cách thứ 2</strong></summary> 

### Chạy script phân vùng
> Thay **$** bằng dung lượng bạn muốn Windows sử dụng (không cần thêm GB, chỉ cần viết số)
> 
> Nếu nó yêu cầu bạn phải chạy lại lần nữa thì cứ chạy nhé
```cmd
adb shell partition $
``` 

#### Kiểm tra Android có khởi động được không
> Nếu không được, hãy khởi động vào recovery gốc và thực hiện **factory reset**
```cmd
adb reboot
```

</details>

### [Bước kế tiếp: Root thiết bị của bạn](/guide/Vietnamese/2-rootguide-vi.md)




























