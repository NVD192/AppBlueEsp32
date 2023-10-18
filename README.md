# AppBlueEsp32

## Giới thiệu
AppBlueEsp32 là một ứng dụng mã nguồn mở được phát triển cho nền tảng ESP32, cho phép đọc và xử lý dữ liệu từ một thiết bị Bluetooth. Ứng dụng này bao gồm một hàm `readByte` dùng để đọc dữ liệu từ Bluetooth và chuyển đổi nó thành một giá trị nguyên.

## Hàm `readByte`
```c
int readByte()
{
  int value = 0;

  // Kiểm tra xem có đủ dữ liệu để đọc không
  if (ESP_BT.available() >= 4)
  {
    byte byteData1 = ESP_BT.read();
    byte byteData2 = ESP_BT.read();
    byte byteData3 = ESP_BT.read();
    byte byteData4 = ESP_BT.read();

    // Kết hợp các byte thành một giá trị nguyên 32-bit
    value = (byteData4 << 24) | (byteData3 << 16) | (byteData2 << 8) | byteData1;
  }

  return value;
}
