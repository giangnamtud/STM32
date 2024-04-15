# I) Giới thiệu tổng quan, cấu trúc vi điều khiển

## 1) Một số khái niệm cơ bản


## 2) Block Diagram
Mỗi Datasheet đều có 1 Block Diagram, trong Block Diagram sẽ có các thành phần:
- Vi xử lý CPU
- Bộ nhớ
- ngoại vi (Peripheral)
- Hệ thống Bus
### a) Bộ nhớ:
Ta thường thấy bộ nhớ Flash, RAM. Bộ nhớ được chia làm 2 loại: Bộ nhớ chương trình và dữ liệu.
- Bộ nhớ chương trình thường là Flash: Khi ta viết code ở trên máy tính, khi biên dịch thì ra file binary chứa cá cái bit để đưa
vào trong vi điều khiển, sau đó vi điều khiển mới dịch ra và chạy. Mã code này sẽ được đưa vào trong Flash. Tính chất của Flash là
non-volaitle (không bay hơi), tức là khi nào thực hiện lệnh xóa thì mới mất còn khi mất điện thì dữ liệu vẫn còn nguyên. Khi đã nạp
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

* So sánh sự tương đồng với PC:
Trong máy tính của mọi người có thể có sự dụng chip core i5, i7 thì đó là bộ vi xử lý. Bên cạnh đó máy tính cũng có bộ nhớ
SSD, HDD, các thanh RAM. Trên máy tính cũng có các cổng USB, cổng HDMI Erthenet,... thì đó là các ngoại vi. Máy tính được thiết kế
tích hợp trên 1 cái mainboard thì đó là bus system để kết nối các thành phần
=> Vi điều khiển cũng có 1 cấu trúc tương tự như vậy.

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
