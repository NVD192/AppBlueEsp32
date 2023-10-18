# AppBlueEsp32
int readByte()
{
  int value = 0;

  if (ESP_BT.available() >= 4)
  {
    byte byteData1 = ESP_BT.read();
    byte byteData2 = ESP_BT.read();
    byte byteData3 = ESP_BT.read();
    byte byteData4 = ESP_BT.read();

    value = (byteData4 << 24) | (byteData3 << 16) | (byteData2 << 8) | byteData1;
  }

  return value;
}
