# TÓM TẮT:
## Buổi 1:
- Trong buổi học tối qua chúng ta đã phân tích cấu trúc vi điều khiển, vi xử lý, bộ nhớ, ngoại vi, hệ thống bus dựa vào sơ đồ Block Diagram dựa vào tài liệu Datasheet của vi điều khiển. So sánh tương đương với máy tính laptop để dễ hiểu.
- Vi điều khiển lõi ARM là vi điều khiển có vi xử lý ARM (loại ARM Cortex M), các hãng vi điều khiển sẽ mua thiết kế của vi xử lý ARM và thiết kế thêm bộ nhớ, ngoại vi..vv.. để tạo thành các dòng vi điều khiển của họ với rất nhiều tùy chọn như ít chân, nhiều chân, ít ngoại vi, nhiều ngoại vi, ít hay nhiều bộ nhớ,...vv..
- Một số từ khóa đã được mình nhắc đến: datasheet, block diagram, MCU, CPU/Processor.
- Giới thiệu qua các dòng vi điều khiển STM32 của hãng STMicroelectronics, vi xử lý ARM Cortex M.

## Buổi 2:
- Đầu buổi học, mình đã giải đáp bài tập về nhà - dựa vào tài liệu datasheet kèm một số thông tin bổ sung.
-Khái niệm GPIO Port, Chân vi điều khiển Pin. Cách đặt tên chân, các chân GPIO, mô tả chức năng các chân đặc biệt VDD/VSS, VDDA/VSSA, VBAT, NRST,BOOT.
- Giới thiệu tài liệu User Manual Board, Schematic của mạch thực hành.
- Phân tích sơ đồ nguyên lý mạch LED, mức logic để LED ON/ OFF.
- Giới thiệu các bước thực hiện, giao diện trên phần mềm STM32CubeIDE:
  + Tạo/ chọn workspace: Là nơi lưu trữ các project có sự liên quan với nhau như các project         trong khóa học/ trong 1 dự án.
  + Chọn vi điều khiển
  + Cấu hình vi điều khiển và sinh mã code
  + Dev Code, biên dịch code.
  + Nạp chương trình vào thiết bị
- Hướng dẫn kiểm tra driver, là trung gian đển phần mềm STM32CubeIDE có thể làm việc được với phần cứng thông qua kết nối cổng USB, kiểm tra tại trình Device Manager.
- Viết mã code kiểm tra với hàm HAL_GPIO_WritePin để điều khiển Logic trên chân OUTPUT nối LED.


# TÀI LIỆU: 
- Video ghi lại:
  + Buổi 1: https://youtu.be/g_ax8MDOZ7k
  + Buổi 2: https://www.youtube.com/watch?v=6zNAt5KMVUo
- Slide: https://docs.google.com/presentation/d/1DIUr6NrQVN0oIGe6T2lwTHT5G1ibQRA0/edit?usp=sharing&ouid=109030928772764985009&rtpof=true&sd=true
- Một số vi điều khiển phổ biến:
  + STM32F103 BluePill: https://stm32-base.org/boards/STM32F103C8T6-Blue-Pill.html
  + STM32F103C8T6: https://www.st.com/resource/en/datasheet/stm32f103c8.pdf
  + AT89C51: https://www.keil.com/dd/docs/datashts/atmel/at89c51_ds.pdf
  + Atmega328p in Arduino UNO R3: https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf
  + CYW54907: https://www.infineon.com/dgdl/Infineon-CYW54907_WICED_IEEE_802-DataSheet-v09_00-EN.pdf?fileId=8ac78c8c882315570188262f365b1a87
- Đặc biệt chú ý (Đây là Board mà mình sử dụng) STM32F407VG MCU:
  + STM32F407/417 family: https://www.st.com/en/microcontrollers-microprocessors/stm32f407-417.htm
  + Info: https://www.st.com/en/evaluation-tools/stm32f4discovery.html
  + Datasheet: https://www.st.com/resource/en/datasheet/stm32f405rg.pdf
  + Data Brief: https://www.st.com/resource/en/data_brief/stm32f4discovery.pdf
  + User Manual: https://www.st.com/resource/en/user_manual/um1472-discovery-kit-with-stm32f407vg-mcu-stmicroelectronics.pdf

# BÀI TẬP: 
## Bài 1: 
Dựa vào tài liệu datasheet, trả lời các câu hỏi sau vào phần bình luận (tạo 1 file doc online của google, trả lời vào đấy và share link ở bình luận) , làm được câu nào thì các bạn trả lời câu đó, câu nào chưa được thì cứ để lại. Mỗi câu trả lời các bạn chụp ảnh phần có liên quan trong datasheet để đưa lên.
- Vi điều khiển của bạn có tổng cộng bao nhiêu chân (Pin)?
- Có bao nhiêu I/O Pin?
- Được chia làm bao nhiêu Port?
- Mỗi Port có bao nhiêu Pin?
- Liệt kê những Pin còn lại không phải GPIO?
- Điện áp nguồn hoạt động của vi điều khiển là bao nhiêu?
- Bộ nhớ Flash, SRAM bao nhiêu?
- Tốc độ tối đa của vi xử lý là bao nhiêu?

## Bài 2:
- Video Debug cần xem qua và thực hành theo hướng dẫn: https://youtu.be/50cc5TmiF78 . Chụp lại 1 ảnh màn hình debug.
Lưu ý với phiên bản mới của phần mềm thì cần phải đặt breakpoint để dừng chương trình thì giá trị thanh ghi và giá trị biến mới hiển thị trên giao diện debug.
- Với 1 chân Input thì điện áp mức 0 (LOW) là bao nhiêu vol? Mức 1 (HIGH) là bao nhiêu vol?
- Với 1 chân Output thì điện áp mức 0 (LOW) là bao nhiêu vol? Mức 1 (HIGH) là bao nhiêu vol?
- Dòng điện tối đa vào /ra 1 chân GPIO là bao nhiêu mA?
- Dòng điện tối đa vào 1 chân nguồn là bao nhiêu?
- Dòng điện tối đa vào vi điều khiển là bao nhiêu?
Gửi kết quả vào phần bình luận trước buổi học tiếp theo.
