# I) Giới thiệu tổng quan, cấu trúc vi điều khiển

## 1) Một số khái niệm cơ bản
- CPU = Processor = vi xử lý
- CPU Core = Processor Core = lõi vi xử lý
- MCU = vi điều khiển
- User manual board: Tổng quan và hướng dẫn sử dụng board mạch thực hành, các thành phần trên board mạch. (F103 BluePill: website). Mạch này được thiết kế từ 1 con MCU và thêm các mạch bên ngoài nữa (mạch cấp nguồn, mạch giao tiếp, nút nhấn, ...)
- Schematic: Sơ đồ nguyên lý mạch của board mạch thực hành, linh kiện nào, chân nào nối với chân nào. 
- Datasheet: Tổng quan về thiết bị và thông số kỹ thuật, thường dùng chung cho 1 dòng vi điều khiển.
- Reference manual: Hướng dẫn sửa dụng thiết bị, các tính năng, bước thực hiện và thanh ghi. 
- Application note: Ghi chú, hướng dẫn sử dụng một tính năng ngoại vi nào đấy
- Description of STM32F3 / 4 / 0 /1 HAL and low-layer drivers: Tài liệu mô tả và hướng dẫn sử dụng thư viện HAL


## 2) Block Diagram
Mỗi Datasheet đều có 1 Block Diagram, trong Block Diagram sẽ có các thành phần:
- Vi xử lý chứa CPU và 1 vài thiết bị ngoại vi hỗ trợ khác (ở phía dưới sẽ gọi tăt là CPU)
- Bộ nhớ
- ngoại vi (Peripheral)
- Hệ thống Bus
### a) Bộ nhớ:
Ta thường thấy bộ nhớ Flash, RAM. Bộ nhớ được chia làm 2 loại: Bộ nhớ chương trình và dữ liệu.
- Bộ nhớ chương trình thường là Flash: Khi ta viết code ở trên máy tính, khi biên dịch thì ra file binary chứa cá cái bit để đưa
vào trong vi điều khiển, sau đó vi điều khiển mới dịch ra và chạy. Mã code này sẽ được đưa vào trong Flash. Tính chất của Flash là
non-volatile (không bay hơi), tức là khi nào thực hiện lệnh xóa thì mới mất còn khi mất điện thì dữ liệu vẫn còn nguyên. Khi đã nạp
chương trình vào vi điều khiển 1 lần thì chương trình sẽ nằm ở trong đó. Khi mất điện thì vi điều khiển không chạy được nữa còn
khi có điện thì lại chạy lại từ đầu, nhấ RESET nó lại chạy lại từ đầu (Giống ổ cứng của máy tính)
- Bộ nhớ dữ liệu thường là RAM: RAM chứa các dữ liệu khi phần mềm chạy
### b) CPU (Central Processing Unit):
Bao gồm nhiều thành phần khác nhau như, VD AT89C51 (xem ảnh dưới):
- ALU: arithmetic logic unit
- Programm Adress Register
- PC Increment
- Program Counter
- ...

![AT89C51 Block Diagram](https://github.com/giangnamtud/STM32/assets/165153939/e3820d18-485d-4528-8452-e164db18db4a)

Vi xử lý phải giao tiếp được với bộ nhớ và đọc được lệnh với bộ nhớ (fetch), sau đó nó phải giải mã được lệnh. Nó phải có mạch logic để
hiểu được các bit trong bộ nhớ(decode). Cuối cùng là thực thi lệnh. 
### c) Port (I/O):
Peripheral (ngoại vi) 
### d) Bus System:
Cá đường nối với nhau
## e) So sánh sự tương đồng với PC:
Trong máy tính của mọi người có thể có sự dụng chip core i5, i7 thì đó là bộ vi xử lý. Bên cạnh đó máy tính cũng có bộ nhớ
SSD, HDD, các thanh RAM. Trên máy tính cũng có các cổng USB, cổng HDMI Erthenet,... thì đó là các ngoại vi. Máy tính được thiết kế
tích hợp trên 1 cái mainboard thì đó là bus system để kết nối các thành phần
=> Vi điều khiển cũng có 1 cấu trúc tương tự như vậy nhưng tài nguyên bị hạn chế. Do đó nó được ứng dụng vào 1 mục đích, chức năng cụ thể nào đó. Không giống như máy tính, điện thoại là general purpose device có thể sử dụng nhiều phần mềm khác nhau; chương trình cho vi điều khiển (firmware) thường được sinh ra để làm 1 tác vụ cụ thể


## 3) Một số vi điều khiển khác:
### a) ATmega328/p
- Vi xử lý AVR
- Bộ nhớ Flash, SRAM
- Hệ thống ngoại vi ADC, UART, TWI, GPIO, ...
- Data Bus

![Atmega328 Block Diagram](https://github.com/giangnamtud/STM32/assets/165153939/848c43bf-de39-4f8e-bfcf-ba825faef12f)

### b) PIC16F873A
- Vi xử lý: ALU, Register lẻ,...
- Bộ nhớ Flash, RAM
- Hệ thống ngoại vi ADC, UART, Comparator,Timer, các Port ...
- Data Bus

![PIC16 Block Diagramm](https://github.com/giangnamtud/STM32/assets/165153939/83d656b4-8571-4b75-8689-5bd86ed0796a)

### c) STM32F103
Vi điều khiển 32 Bit nên phức tạp hơn so với những con 8 Bit ở trên.
- Cortex M3 CPU
- 128 kB Flash, 20kB SRAM
- GPIO để giao tiếp số 1,0 / Timer / UART /USB /CAN /ADC
- Data Bus

![STM32F103 Block Diagram](https://github.com/giangnamtud/STM32/assets/165153939/47e483b3-3d2e-4d15-875d-c450b21a6102)

### d) CYW54907
Có thêm giao tiếp về mạng WLAN được kết nối với 1 hệ thống vi điều khiển
- Bộ nhớ RAM; ROM
- UART, PWM, SPI, GPIO, chuẩn debug JTAG ...
- ARM Cortex R4 CPU
- Data Bus

![CYW54907 Block Diagram](https://github.com/giangnamtud/STM32/assets/165153939/a31524a5-34e6-43bb-a9bf-1a1d69d68e8e)

* Kết luận
  - Vi điều khiển thường có cấu trúc như nhau
  - Khi làm việc vs STM32 thì vi điều khiển được cấu trúc dựa trên vi xử lý ARM Cortex M. Tức là vi xử lý đã có tính đóng gói, rất nhiều hãng có
thể mua thiết kế của vi xử lý về và thiết kế thêm bộ nhớ, ngoại vi, ...


## 4) Vi điều khiển của STM32
Link: https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html

![image](https://github.com/giangnamtud/STM32/assets/165153939/0ca37415-5651-450b-a71b-60b94e03ca16)

STM32 có nhiều dòng vi điều khiển, trong đó có 1385 con sử dụng ARM Cortex M. Ta thấy có 4 dòng chính
- Wireless: Hỗ trợ chuẩn giao tiếp không dây, phù hợp với IoT (Dòng W)
- Ultra Low Power: Được thiết kế đặc thù để tiêu thụ ít năng lượng hơn (Dòng L, U). Thường đc ứng dụng cho wearable device, remote usable
- Mainstream: Sử dụng rộng rãi, vừa đảm bảo được hiệu năng, vừa đảm bảo được năng lượng (Dòng C, F, G). Ví dụ: STM32F103
- High Perfomance: Hiệu năng tốt, xử lý nhanh, ngoại vi nhiều, nhiều bộ nhớ, .. (Dòng F, H). Ví dụ: STM32F407


## 5) Vi xử lý của ARM
Link: https://www.arm.com/

- ARM nổi tiếng về compute technology (về vi xử lý): Arm is the leading technology provider of processor IP, offering the widest range of cores to address the performance, power, and cost requirements of every device—from IoT sensors to supercomputers, and from smartphones and laptops to autonomous vehicles.

- ARM Cortex M có nhiều dòng:
The Cortex-M processor series is designed to enable developers to create cost-sensitive and power-constrained solutions for a broad range of devices. The optimal balance between area, performance, and power makes Cortex-M3 ideal for products such as microcontrollers, automotive body systems, and wireless networking and sensors.

![Screenshot 2024-04-15 131932](https://github.com/giangnamtud/STM32/assets/165153939/cc5d1307-03e9-4a1e-a725-63810ade7efe)
![Screenshot 2024-04-15 131949](https://github.com/giangnamtud/STM32/assets/165153939/fd899552-25ef-4b40-b7b8-e30d114d99e9)
![Screenshot 2024-04-15 132001](https://github.com/giangnamtud/STM32/assets/165153939/7be41189-f5e0-49d8-b30f-c1b65830428c)
![Screenshot 2024-04-15 132012](https://github.com/giangnamtud/STM32/assets/165153939/7095fceb-5c70-49e1-94ba-21d2444620eb)

Với vi điều khiển ta tập trung vào các dòng M0, M3, M4, M7

### a) ARM Cortex M3:
Link: https://www.arm.com/products/silicon-ip-cpu/cortex-m/cortex-m3

Các vi điều khiển thuộc dòng STM32 thường sử dụng vi xử lý này vì cân đối giữa hiệu năng và năng lượng

![image](https://github.com/giangnamtud/STM32/assets/165153939/7385e225-492a-4e4c-ae23-4922b5bbf43e)

Bên trong vi xử lý sẽ có CPU, và các ngoại vi khác để hỗ trợ cho CPU này
- JTAG, Serial Wire: Hỗ trợ nạp chương trình và debug
- Nested vectored interrupt controller: hỗ trợ xử lý ngắt
- Memory Protection Unit: Liên quan đến security, chống truy cập trái phép đến 1 địa chỉ nhớ nào đó

### b) ARM Cortex M4:
Link: https://www.arm.com/products/silicon-ip-cpu/cortex-m/cortex-m4

M4 tập trung vào hiệu năng so với M3

![image](https://github.com/giangnamtud/STM32/assets/165153939/080b1199-b9f0-4b04-be93-7213ad03e5bf)

Có cấu trúc phức tạp hơn so vs M3
- FPU (floating point unit): hỗ trợ tính toán số thực nhanh hơn, xử lý thuật toán AI, DSP nhanh hơn
- DSP: giải mã DSP rất nhanh

