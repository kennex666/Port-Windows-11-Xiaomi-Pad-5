<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Chạy Windows trên Xiaomi Pad 5

## Phục hồi thiết bị từ EDL Mode
> Hướng dẫn có 2 cách để flash lại máy, nếu cách 1 thất bại, hãy sử dụng cách 2

### Vào EDL Mode
> Có hai cách để boot Xiaomi Pad 5 của bạn vào **EDL mode**. Sử dụng cách nào phù hợp với bạn.

> [!NOTE]
>
> ▶️ Nhấn nút menu mở rộng

<details>
  <summary><strong>Cách 1: Unlocked bootloader</strong></summary>

> Nếu bootloader của bạn đã được mở khóa, chạy lệnh sau trong **fastboot mode**
```cmd
fastboot oem edl
```

</details>

<details>
  <summary><strong>Cách 2: Locked bootloader hoặc thiết bị không thể boot</strong></summary>

- Cắm cáp **EDL** vào thiết bị của bạn và nhấn nút trên cáp để boot vào **EDL mode**.
> Cáp **EDL** có thể được tìm thấy trên mấy chỗ online và nên chọn cáp có chữ **V2** trong tên, ví dụ **Hydra V2 EDL Cable**.
- Còn cách nữa là **chọc vào test points** (yêu cầu mở nắp sau của thiết bị - cái này khá kỹ thuật và rủi ro, nên dùng cáp **EDL** vì mình đã từng sử dụng thành công).

</details>

### Kiểm tra mọi thứ ok hay chưa
- Mở **Device Manager** trên máy tính của bạn và tìm thiết bị, thường là **Qualcomm HS-USB QDLoader 9008**.
- Nếu máy được đặt tên là **QUSB_BULK_CID** và/hoặc có biểu tượng cảnh báo màu vàng ⚠️ trong **Device Manager**, bạn cần cài đặt/cập nhật driver.
- Để làm điều này, hãy tải và giải nén **[QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip)**, chọn thiết bị có lỗi trong **Device Manager**, chọn **Update drivers**, sau đó chọn thư mục **QUD** bạn vừa giải nén.

> [!NOTE]
>
> ▶️ Nhấn để mở rộng menu

<details>
  <summary><strong>Cách 1: Cách free</strong></summary>

## Cách 1: Free method

### Cần chuẩn bị
- [`Patched MiFlash Tool`](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/MiFlashPatched.zip)

- [`Patched firehose (.elf) file`](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/prog_ufs_firehose_sm7150_ddr.elf)

- `Đã giải nén` [`fastboot ROM for Nabu`](http://xmfirmwareupdater.com/miui/nabu/) 

### Chuẩn bị files cần thiết
- Giải nén **fastboot ROM** cho Xiaomi Pad 5 của bạn.
- Giải nén **MiflashPatched.zip** bạn đã tải ở trên.
- Sao chép file **firehose (.elf)** từ thư mục **MiflashPatched.zip** vào thư mục **images** bên trong thư mục **fastboot ROM** bạn vừa giải nén, ghi đè lên file hiện tại.

#### Mở MiFlash Tool 
- Tìm đến thư mục **MiflashPatched.zip** bạn vừa giải nén và mở thư mục **MiFlash**.
- Mở **XiaoMiFlash.exe** với quyền quản trị.

### Flashing the ROM
- Nhấn nút **Select** trong **MiFlash** và chọn tới thư mục bạn đã giải nén **fastboot ROM** của bạn (thư mục mà bạn đã thay thế file **firehose.elf**).
- Ở trong **MiFlash** tool, hãy chắc chắn đã chọn tuỳ chọn **"Clean All"**.
- Click **Refresh** trong **MiFlash** để đảm bảo thiết bị đã kết nối.
- Sau khi chắc chắn máy đã nhận và đã chọn **"Clean All"**, nhấn **Flash** để bắt đầu quá trình flash.

> [!Important]
> Nếu bạn thấy bất kỳ lỗi nào không biến mất sau 2 phút, khởi động lại thiết bị vào **EDL mode** một lần nữa, sau đó nhấn **Refresh** và **Flash** lại để thử lại.

#### Reboot thiết bị
- Sau khi flash hoàn tất, nhấn nút **Reboot** để khởi động lại thiết bị.

</details>

<details>
  <summary><strong>Cách 2: Trả tiền cho EDL method</strong></summary>

## Cách 2: Trả phí Flashing qua HXRU Tool

### Chuẩn bị 
- `$3 USDT` (`75k`) và một crypto wallet để mua credit (vài ngân hàng của Nga cũng được chấp nhận)

- `Telegram account` để liên hệ với HXRU support

- [`MiFlash HXRU Tool`](https://hxrutool.net/tool/Xiaomi_Auth_Tool_v9.0.0.5_mtk.zip)
 
- [`Fastboot ROM gốc cho Nabu`](http://xmfirmwareupdater.com/miui/nabu/)  

### Setup HXRU Tool  
- Tạo acc tại **[HXRU dashboard](https://dashboard.hxrutool.com/Register)**.
- Tải và giải nén **MiFlash HXRU**.

#### Mua Credits 
- Liên hệ **@hxruofficial** trên Telegram để mua **5 credits** (sấp xỉ **75k**). Nếu không mua credit thì có cái nịt mà xài tool nha.

### Flashing thiết bị
- Mở **XiaoMiFlash.exe** và mở quyền Administrator.
- Tải rom fastboot gốc cho máy (có đuôi .tgz) và giải nén. Bên trong sẽ có file .tar. Giải nén file .tar này vào một thư mục bất kỳ.
- Chọn nút **select** trong **XiaoMiFlash** và chọn folder này.
- Nhấn **flash**.
- Nếu bạn gặp lỗi `write time out`, giữ **nút nguồn** + **nút giảm âm lượng** khoảng +- 30 giây để reboot EDL. Sau đó nhấn nút **flash** lại.
- Sau vài giây, một cửa sổ đăng nhập sẽ hiện ra. Nhập tài khoản HRXU của bạn vào đấy và nhấn **Request Auth Flashing**.

#### Reboot thiết bị
- Sau khi nó ghi **flash done**, khởi động lại thiết bị bằng cách giữ **nút nguồn** khoảng +- 14 giây.

</details>

### Reflashing rom với MiFlash
> [!Important]
> Đống tools chỉ flash rom vào một slot. Nếu thiết bị của bạn chuyển slot, nó sẽ boot lại vào EDL mode.
- Reboot vào **fastboot mode**.
- Flash lại rom fastboot một lần nữa bằng **MiFlash** hoặc với file **flash_all.bat** trong rom.
- Reboot sau khi flash xong.

#### Thành công!
Chúc mừng, Xiaomi Pad 5 của bạn đã được khôi phục về trạng thái hoạt động ban đầu!

> [!TIP]
> Note của dịch giả: Mình làm hồi 1 năm trước lúc còn ít hướng dẫn bị dính cái này, tốn 300k cho dịch vụ và 150k cho cọng cáp :))) Hồi đó chưa có patch cho MiFlash, thành ra mình chỉ có thể mua Credit để flash.
> Bạn sẽ không thể flash bằng MiFlash bình thường đâu. Làm theo hướng dẫn cho đỡ mất thời gian.